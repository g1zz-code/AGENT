<div align="center">

<img src="./public/banner.png" alt="NODELING AGENT banner" width="100%"/>

</div>

<div align="center">

# ◈ NODELING AGENT

### *by Mike drop*

**N**eural  ·  **O**n-chain  ·  **D**ecentralized  ·  **E**xecution  ·  **L**ayer  ·  **I**ntelligence  ·  **N**etwork  ·  **G**rid

<br/>

[![Live Demo](https://img.shields.io/badge/◈_LIVE-NODELING.vercel.app-a855f7?style=for-the-badge&labelColor=0d0d0d)](https://descu.tech)
[![Agent Registry](https://img.shields.io/badge/REGISTRY-12_Agents_Online-6366f1?style=for-the-badge&labelColor=0d0d0d)](https://descu.tech/registry)
[![Agent Profile](https://img.shields.io/badge/AGENT-NODELING_ID-8b5cf6?style=for-the-badge&labelColor=0d0d0d)](https://descu.tech/agent)

<br/>

[![Solana](https://img.shields.io/badge/Solana-Mainnet-9945FF?style=flat-square&logo=solana&logoColor=white)](https://solana.com)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![Grok](https://img.shields.io/badge/AI_Core-Grok_3-ffffff?style=flat-square&logo=xing&logoColor=black)](https://x.ai)
[![Vercel](https://img.shields.io/badge/Deploy-Vercel-000000?style=flat-square&logo=vercel&logoColor=white)](https://vercel.com)
[![License](https://img.shields.io/badge/License-MIT-22c55e?style=flat-square)](./LICENSE)
[![Status](https://img.shields.io/badge/Status-ACTIVE-00ff88?style=flat-square&labelColor=0d0d0d)](#)

</div>

<br/>

<div align="center">

```
  ██████████████████████████████████████████████████████████
  ██                                                      ██
  ██    NODELING AGENT  ·  SAP v1  ·  SOLANA MAINNET     ██
  ██    autonomous • on-chain • always watching           ██
  ██                                                      ██
  ██████████████████████████████████████████████████████████
```

</div>

---

> **NODELING** is a fully autonomous AI agent living on-chain. It reads the blockchain in real time, tracks AI agent reputation across the Solana ecosystem, responds to queries in structured `AGENT_SPEC` format, and never sleeps. Built by **Mike drop**.

---

## ◈ Neural Identity

<div align="center">

| Field | Value |
|:---|:---|
| `agent_id` | `NODELING` |
| `version` | `1.0.0` |
| `wallet` | `DbzFutGThzbMNaDyqvdzWugdZuhnaqtWyfD9qp9GZRRV` |
| `status` | `● ACTIVE` |
| `protocol` | `Solana Agent Protocol  ·  SAP v1` |
| `ai_core` | `xAI Grok 3` |
| `uptime` | `∞ serverless` |

</div>

> [Verify on-chain via Solscan ↗](https://solscan.io/account/DbzFutGThzbMNaDyqvdzWugdZuhnaqtWyfD9qp9GZRRV)

---

## ◈ Skill Matrix

<div align="center">

| Skill | Trigger | Source | Latency |
|:---|:---|:---|:---|
| `balance_checker` | wallet address | Solana RPC | ~120ms |
| `price_monitor` | token symbol | CoinGecko | ~200ms |
| `transaction_analyzer` | tx sig / wallet | Solana RPC | ~300ms |
| `network_status` | `status` / `tps` | Solana RPC | ~80ms |
| `agent_registry` | `registry` / `rank` | GitHub crawler | cached |
| `reputation_score` | agent name | Scorer engine | cached |

</div>

**OpenClaw compatible** — `/manifest` exposes all skills in machine-readable format for agent-to-agent invocation.

**Surveillance** — 12 Solana protocol agents are crawled every 30 minutes. Reputation scores are computed from commit frequency, on-chain activity, and protocol compliance.

---

## ◈ Architecture

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║                     ◈  NODELING AGENT  CORE                         ║
║                                                                      ║
║   ┌─────────────────────────────────────────────────────────────┐   ║
║   │              INGRESS  ·  REQUEST ROUTER                     │   ║
║   │                                                             │   ║
║   │   Browser ──┐                                               │   ║
║   │   API Key ──┼──► Express Server  ◄── /manifest (OpenClaw)  │   ║
║   │   AI Agent ─┘         │                                     │   ║
║   └───────────────────────┼─────────────────────────────────────┘   ║
║                           │                                          ║
║           ┌───────────────┴────────────────┐                        ║
║           │                                │                        ║
║   ┌───────▼────────┐              ┌────────▼────────┐               ║
║   │  AGENT_SPEC    │              │  SKILL ROUTER   │               ║
║   │  Prompt Engine │              │  intent parser  │               ║
║   └───────┬────────┘              └────────┬────────┘               ║
║           │                                │                        ║
║     ┌─────▼──────┐           ┌─────────────┴────────────┐           ║
║     │  xAI Grok 3│           │                          │           ║
║     │  AI  Core  │    ┌──────▼──────┐          ┌────────▼──────┐    ║
║     └────────────┘    │   Solana    │          │   Reputation  │    ║
║                       │  Commands   │          │     Scorer    │    ║
║                       └──────┬──────┘          └────────┬──────┘    ║
║                              │                          │           ║
║                    ┌─────────▼──────┐       ┌───────────▼──────┐    ║
║                    │  web3.js RPC   │       │  Registry Cache  │    ║
║                    │  Mainnet       │       │  12 agents live  │    ║
║                    └────────────────┘       └──────────────────┘    ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
                                  │
                     ┌────────────▼────────────┐
                     │   SURVEILLANCE ENGINE   │
                     │   runs every  30  min   │
                     └────────────┬────────────┘
                                  │
          ┌───────────────────────┼───────────────────────┐
          │                       │                       │
 ┌────────▼────────┐   ┌──────────▼──────────┐  ┌────────▼────────┐
 │   GitHub API    │   │   DexScreener API   │  │  Solana RPC     │
 │  commit history │   │  token vol signals  │  │  wallet watch   │
 │  push activity  │   │  on-chain txns      │  │  slot monitor   │
 └────────┬────────┘   └──────────┬──────────┘  └────────┬────────┘
          └───────────────────────┼───────────────────────┘
                                  │
                     ┌────────────▼────────────┐
                     │   REPUTATION SCORER     │
                     │                         │
                     │   commit_score   × 0.4  │
                     │ + onchain_score  × 0.4  │
                     │ + protocol_score × 0.2  │
                     │   ─────────────────────  │
                     │      SCORE  :  0─100     │
                     └────────────┬────────────┘
                                  │
          ╔═══════════════════════▼═════════════════════════╗
          ║               AGENT  REGISTRY                   ║
          ║                                                  ║
          ║  ████  elizaOS/eliza              97 ▓▓▓▓▓▓▓▓▓  ║
          ║  ████  jito-foundation/jito-sol   95 ▓▓▓▓▓▓▓▓▓  ║
          ║  ████  orca-so/whirlpools         91 ▓▓▓▓▓▓▓▓░  ║
          ║  ████  raydium-io/raydium-sdk     89 ▓▓▓▓▓▓▓▓░  ║
          ║  ████  drift-labs/protocol-v2     87 ▓▓▓▓▓▓▓░░  ║
          ║  ████  mrgnlabs/marginfi-v2       83 ▓▓▓▓▓▓▓░░  ║
          ║  ████  MeteoraAg/meteora-ag       79 ▓▓▓▓▓▓░░░  ║
          ║  ████  helius-labs/helius-sdk     77 ▓▓▓▓▓▓░░░  ║
          ║  ░░░░  tensor-oss/tensorswap      74 ▓▓▓▓▓░░░░  ║
          ║  ░░░░  kamino-finance/klend-sdk   71 ▓▓▓▓▓░░░░  ║
          ║  ~~~~  goat-sdk/goat              63 ▓▓▓▓░░░░░  ║
          ║  ~~~~  pyth-network/pyth-solana   58 ▓▓▓▓░░░░░  ║
          ║                                                  ║
          ║  12 agents tracked  ·  refresh: every 30 min   ║
          ╚══════════════════════════════════════════════════╝
```

---

## ◈ Response Format — AGENT_SPEC v1

Every NODELING response is machine-parseable and human-readable:

```
╭─ NODELING RESPONSE ──────────────────────────────────────────╮
│                                                               │
│  Intent      →  parsed understanding of the query            │
│  Assumptions →  defaults and inferences applied              │
│  Summary     →  human-readable answer                        │
│  Result JSON →  structured machine-readable output           │
│  Next step   →  one suggested follow-up action               │
│                                                               │
╰───────────────────────────────────────────────────────────────╯
```

---

## ◈ Live Interfaces

<div align="center">

| Route | What it does |
|:---|:---|
| [`/`](https://descu.tech) | Chat interface — query NODELING directly |
| [`/agent`](https://descu.tech/agent) | Public identity, skills, and reputation dashboard |
| [`/registry`](https://descu.tech/registry) | Live agent registry with reputation rankings |
| [`/manifest`](https://descu.tech/manifest) | OpenClaw-compatible skill manifest |

</div>

---

## ◈ Tech Stack

<div align="center">

| Layer | Technology | Role |
|:---|:---|:---|
| Runtime | `Node.js 20` + TypeScript | Server execution |
| AI Core | `xAI Grok 3` | Intelligence engine |
| Blockchain | `@solana/web3.js` · Mainnet | On-chain data |
| Market Feed | DexScreener · CoinGecko | Price signals |
| Agent Intel | GitHub API crawler | Repo activity tracking |
| Deploy | Vercel serverless | Edge distribution |
| Protocol | SAP v1 · OpenClaw | Agent interop |

</div>

---

## ◈ Quick Start

```bash
git clone https://github.com/g1zz-code/AGENT
cd AGENT
npm install
cp .env.example .env
# Fill in your XAI_API_KEY
npm run dev
```

```
◈ NODELING online at http://localhost:3000
```

---

## ◈ Environment Variables

<div align="center">

| Variable | Required | Description |
|:---|:---:|:---|
| `XAI_API_KEY` | ✅ | xAI Grok API key |
| `AI_MODEL_NAME` | ➖ | Model override (default: `grok-3`) |
| `AGENT_WALLET_PUBLIC` | ➖ | On-chain wallet address |
| `SOLANA_RPC_URL` | ➖ | RPC endpoint (default: mainnet) |
| `GITHUB_TOKEN` | ⚡ | Raises rate limit to 5 000 req/h |

</div>

---

## ◈ Project Structure

```
NODELING AGENT
│
├── api/
│   └── index.ts              ← Vercel serverless entry point
│
├── src/
│   ├── ai/
│   │   ├── model.ts          ← xAI Grok 3 adapter + fallback
│   │   └── processor.ts      ← AGENT_SPEC prompt engine + skill router
│   │
│   ├── agent-protocol/
│   │   ├── index.ts          ← SAP Protocol core
│   │   ├── profile.ts        ← Agent identity + reputation
│   │   ├── registry.ts       ← Agent registry API
│   │   ├── seed.ts           ← 12 pre-seeded Solana agents
│   │   └── skills.ts         ← Skill definitions & handlers
│   │
│   ├── bot/
│   │   └── web.ts            ← Express server + routes
│   │
│   ├── config/
│   │   └── index.ts          ← Environment config loader
│   │
│   ├── monitor/
│   │   ├── crawler.ts        ← 30-min GitHub + DexScreener loop
│   │   ├── dexscreener.ts    ← Token price fetcher
│   │   └── github.ts         ← GitHub API client
│   │
│   └── solana/
│       ├── agent.ts          ← Solana RPC wrapper
│       └── commands.ts       ← Blockchain command handlers
│
└── public/
    ├── index.html            ← Chat UI
    ├── agent.html            ← Agent profile page
    ├── registry.html         ← Registry dashboard
    ├── manifest.html         ← OpenClaw skill manifest
    └── banner.png            ← ◈ DROP YOUR BANNER HERE
```

---

<div align="center">

**MIT License** · Built on Solana · Powered by xAI Grok · Made by **Mike drop**

```
◈ NODELING AGENT — always on-chain, never offline
```

</div>
