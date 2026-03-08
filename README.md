<div align="center">
  <img src="public/vance.png" alt="VANCE Banner" width="800"/>
</div>

# VANCE — Autonomous On-Chain AI Agent

> **V**erify · **A**nalyze · **N**avigate · **C**hain · **E**xecute

VANCE is an autonomous AI agent deployed on the Solana blockchain. It monitors on-chain activity in real time, tracks AI agent reputation across the Solana ecosystem, answers blockchain queries, and communicates in structured `AGENT_SPEC` format — readable by both humans and machines.


[![Solana](https://img.shields.io/badge/Chain-Solana_Mainnet-9945FF?style=flat-square)](https://solana.com)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](./LICENSE)

---

## Identity

```
agent_id      : vance
agent_name    : VANCE
agent_version : 1.0.0
wallet        : DbzFutGThzbMNaDyqvdzWugdZuhnaqtWyfD9qp9GZRRV
status        : active
protocol      : Solana Agent Protocol (SAP v1)
```

---

## Capabilities

| Skill | Description |
|---|---|
| `balance_checker` | SOL + SPL token balances for any wallet address |
| `price_monitor` | Real-time token prices via CoinGecko (SOL, USDC, BONK, JUP) |
| `transaction_analyzer` | Full transaction history by wallet address or signature |
| `network_status` | Solana mainnet health — current slot, TPS, validator status |

**Agent Registry** — VANCE monitors 14 active Solana AI agents (Eliza, GOAT, Drift Keeper, Jito MEV, BonkBot and others). GitHub activity is crawled every 30 minutes. Each agent receives a reputation score from 0 to 100 based on commit frequency, on-chain activity, and protocol compliance.

**OpenClaw compatible** — `/manifest` exposes VANCE skills in machine-readable format for direct agent-to-agent integration.

---

## Response Format (AGENT_SPEC v1)

Every response follows a strict structured format:

```
Intent:       parsed understanding of the query
Assumptions:  defaults and inferences applied
Summary:      human-readable answer
Result JSON:  structured machine-readable output
Next step:    one suggested follow-up action
```

---

## Interface

| Route | Description |
|---|---|
| `/` | Chat interface — query VANCE directly |
| `/agent` | VANCE public identity, skills, and reputation score |
| `/registry` | Live Solana agent registry with reputation rankings |
| `/manifest` | OpenClaw-compatible skill manifest |

---

## Stack

| Layer | Technology |
|---|---|
| Runtime | Node.js 20 + TypeScript |
| AI Model | OpenAI `gpt-4o-mini` |
| Blockchain | Solana mainnet via `@solana/web3.js` |
| Market Data | DexScreener, CoinGecko |
| Agent Data | GitHub API (repo activity crawler) |
| Deploy | Vercel serverless functions |

---

## Quick Start

```bash
git clone https://github.com/BureauAgent/BureauAgent
cd BureauAgent
npm install
cp .env.example .env
# Add your OPENAI_API_KEY to .env
npm run dev
```

Server starts at `http://localhost:3000`

---

## Environment Variables

| Variable | Required | Description |
|---|---|---|
| `OPENAI_API_KEY` | ✅ | OpenAI API key |
| `AI_MODEL_NAME` | — | Model override (default: `gpt-4o-mini`) |
| `AGENT_WALLET_PUBLIC` | — | VANCE on-chain wallet address |
| `SOLANA_RPC_URL` | — | RPC endpoint (default: mainnet) |
| `GITHUB_TOKEN` | recommended | Raises rate limit to 5000 req/h |

---

## Project Structure

```
api/
  index.ts               Vercel serverless entry point
src/
  ai/
    model.ts             OpenAI adapter with fallback support
    processor.ts         AGENT_SPEC prompt engine + skill router
  agent-protocol/
    index.ts             SAP Protocol core
    profile.ts           VANCE identity + reputation scoring
    registry.ts          Agent registry API
    seed.ts              12 pre-seeded Solana agents
    skills.ts            Skill definitions and handlers
  bot/
    web.ts               Express server + route definitions
  config/
    index.ts             Environment config loader
  monitor/
    crawler.ts           30-min GitHub + DexScreener crawler
    dexscreener.ts       Token price fetcher
    github.ts            GitHub API client
  solana/
    agent.ts             Solana RPC wrapper
    commands.ts          Blockchain command handlers
public/
  index.html             Chat UI
  agent.html             Agent profile page
  registry.html          Agent registry
  manifest.html          OpenClaw skill manifest
  logo.svg               VANCE logo
```

---

## Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        VANCE CORE                               │
│                                                                 │
│   User / External Agent                                         │
│          │                                                      │
│          ▼                                                      │
│   [ Express Server ]  ◄──── /manifest (OpenClaw)               │
│          │                                                      │
│    ┌─────┴──────┐                                               │
│    │            │                                               │
│ [AI Processor]  [Solana Commands]                               │
│    │                  │                                         │
│ [OpenAI GPT]   [@solana/web3.js]                                │
│                       │                                         │
│                [Solana Mainnet RPC]                             │
└─────────────────────────────────────────────────────────────────┘
                         │
                         │ every 30 min
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│                   AGENT SURVEILLANCE ENGINE                     │
│                                                                 │
│   ┌──────────────────────────────────────────────────────┐     │
│   │              Background Crawler                       │     │
│   │   GitHub API ──► commit frequency, last activity     │     │
│   │   DexScreener ─► on-chain token + volume signals     │     │
│   └──────────────────────┬───────────────────────────────┘     │
│                          │                                      │
│                          ▼                                      │
│   ┌──────────────────────────────────────────────────────┐     │
│   │              Reputation Scoring Engine                │     │
│   │   commit_score  +  onchain_score  +  protocol_score  │     │
│   │   ─────────────────────────────────────────────────  │     │
│   │                  total: 0 – 100                       │     │
│   └──────────────────────┬───────────────────────────────┘     │
│                          │                                      │
│                          ▼                                      │
│   ┌──────────────────────────────────────────────────────┐     │
│   │                 Agent Registry                        │     │
│   │                                                       │     │
│   │   🟢 Eliza          94 / 100   active                │     │
│   │   🟢 Jito MEV       91 / 100   active                │     │
│   │   🟢 GOAT           88 / 100   active                │     │
│   │   🟢 Drift Keeper   82 / 100   active                │     │
│   │   🟡 BonkBot        67 / 100   slow                  │     │
│   │   🔴 [agent_n]      31 / 100   stale                 │     │
│   │   · · ·  12 agents total, updated every 30 min       │     │
│   └──────────────────────────────────────────────────────┘     │
└─────────────────────────────────────────────────────────────────┘
```

---

## License

MIT — built on Solana, powered by OpenAI, always on-chain.
