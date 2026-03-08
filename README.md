<div align="center">
  <img src="public/vance.png" alt="VANCE Banner" width="800"/>
</div>

<div align="center">

# VANCE вЂ” Autonomous On-Chain AI Agent

**V**erify В· **A**nalyze В· **N**avigate В· **C**hain В· **E**xecute

[![Live Demo](https://img.shields.io/badge/в–¶%20Live%20Demo-ai--bot--project--lime.vercel.app-00d4ff?style=for-the-badge)](https://ai-bot-project-lime.vercel.app)
[![Agent Registry](https://img.shields.io/badge/рџ“Ў%20Registry-14%20Agents%20Live-9945FF?style=for-the-badge)](https://ai-bot-project-lime.vercel.app/registry)
[![Agent Profile](https://img.shields.io/badge/рџ¤–%20Agent%20Profile-VANCE-blueviolet?style=for-the-badge)](https://ai-bot-project-lime.vercel.app/agent)

[![Solana](https://img.shields.io/badge/Chain-Solana_Mainnet-9945FF?style=flat-square&logo=solana)](https://solana.com)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-3178C6?style=flat-square&logo=typescript)](https://www.typescriptlang.org)
[![OpenAI](https://img.shields.io/badge/AI-GPT--4o--mini-412991?style=flat-square&logo=openai)](https://openai.com)
[![Vercel](https://img.shields.io/badge/Deploy-Vercel-000000?style=flat-square&logo=vercel)](https://vercel.com)
[![License](https://img.shields.io/badge/License-MIT-22c55e?style=flat-square)](./LICENSE)

</div>

---

VANCE is an autonomous AI agent deployed on the Solana blockchain. It monitors on-chain activity in real time, tracks AI agent reputation across the Solana ecosystem, answers blockchain queries, and communicates in structured `AGENT_SPEC` format вЂ” readable by both humans and machines.

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

> рџ”Ќ [Verify on Solscan](https://solscan.io/account/DbzFutGThzbMNaDyqvdzWugdZuhnaqtWyfD9qp9GZRRV)

---

## Capabilities

| Skill | Description |
|---|---|
| `balance_checker` | SOL + SPL token balances for any wallet address |
| `price_monitor` | Real-time token prices via CoinGecko (SOL, USDC, BONK, JUP) |
| `transaction_analyzer` | Full transaction history by wallet address or signature |
| `network_status` | Solana mainnet health вЂ” current slot, TPS, validator status |

**Agent Registry** вЂ” VANCE monitors 14 active Solana AI agents (Eliza, GOAT, Drift Keeper, Jito MEV, BonkBot and others). GitHub activity is crawled every 30 minutes. Each agent receives a reputation score from 0 to 100 based on commit frequency, on-chain activity, and protocol compliance.

**OpenClaw compatible** вЂ” `/manifest` exposes VANCE skills in machine-readable format for direct agent-to-agent integration.

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
| [`/`](https://ai-bot-project-lime.vercel.app) | Chat interface вЂ” query VANCE directly |
| [`/agent`](https://ai-bot-project-lime.vercel.app/agent) | VANCE public identity, skills, and reputation score |
| [`/registry`](https://ai-bot-project-lime.vercel.app/registry) | Live Solana agent registry with reputation rankings |
| [`/manifest`](https://ai-bot-project-lime.vercel.app/manifest) | OpenClaw-compatible skill manifest |

---

## Architecture

```
  в”Њв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”ђ
  в”‚                       VANCE CORE                             в”‚
  в”‚                                                              в”‚
  в”‚   Human / External Agent / API call                          в”‚
  в”‚               в”‚                                              в”‚
  в”‚               в–ј                                              в”‚
  в”‚     в”Њв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”ђ                                  в”‚
  в”‚     в”‚    Express Server   в”‚ в—„в”Ђв”Ђв”Ђ /manifest  (OpenClaw)       в”‚
  в”‚     в””в”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”¬в”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”                                  в”‚
  в”‚                в”‚                                             в”‚
  в”‚       в”Њв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”ґв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”ђ                                    в”‚
  в”‚       в”‚                 в”‚                                    в”‚
  в”‚  в”Њв”Ђв”Ђв”Ђв”Ђв–јв”Ђв”Ђв”Ђв”Ђв”Ђв”ђ    в”Њв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв–јв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”ђ                            в”‚
  в”‚  в”‚   AI     в”‚    в”‚   Solana    в”‚                             в”‚
  в”‚  в”‚Processor в”‚    в”‚  Commands   в”‚                             в”‚
  в”‚  в””в”Ђв”Ђв”Ђв”Ђв”¬в”Ђв”Ђв”Ђв”Ђв”Ђв”    в””в”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”¬в”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”                            в”‚
  в”‚       в”‚                 в”‚                                    в”‚
  в”‚  в”Њв”Ђв”Ђв”Ђв”Ђв–јв”Ђв”Ђв”Ђв”Ђв”Ђв”ђ    в”Њв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв–јв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”ђ                            в”‚
  в”‚  в”‚ OpenAI   в”‚    в”‚ web3.js RPC в”‚                             в”‚
  в”‚  в”‚ GPT-4o   в”‚    в”‚   Mainnet   в”‚                             в”‚
  в”‚  в””в”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”    в””в”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”                            в”‚
  в””в”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”
                          в”‚
              в”Њв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”  runs every 30 min
              в–ј
  в”Њв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”ђ
  в”‚               AGENT SURVEILLANCE ENGINE                      в”‚
  в”‚                                                              в”‚
  в”‚  в”Њв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”ђ     в”‚
  в”‚  в”‚                 Background Crawler                  в”‚     в”‚
  в”‚  в”‚                                                     в”‚     в”‚
  в”‚  в”‚   в”Њв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”ђ   в”Њв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”ђ   в”‚     в”‚
  в”‚  в”‚   в”‚   GitHub API    в”‚   в”‚    DexScreener API   в”‚   в”‚     в”‚
  в”‚  в”‚   в”‚ commit history  в”‚   в”‚  token + vol signals в”‚   в”‚     в”‚
  в”‚  в”‚   в”‚ last push date  в”‚   в”‚  on-chain activity   в”‚   в”‚     в”‚
  в”‚  в”‚   в””в”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”¬в”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”   в””в”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”¬в”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”   в”‚     в”‚
  в”‚  в””в”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”јв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”јв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”     в”‚
  в”‚               в””в”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”¬в”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”                      в”‚
  в”‚                          в–ј                                   в”‚
  в”‚  в”Њв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”ђ    в”‚
  в”‚  в”‚              Reputation Scoring Engine               в”‚    в”‚
  в”‚  в”‚                                                      в”‚    в”‚
  в”‚  в”‚    commit_score   +   onchain_score   +   protocol   в”‚    в”‚
  в”‚  в”‚    в”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђ  в”‚    в”‚
  в”‚  в”‚                    score:  0 вЂ“ 100                   в”‚    в”‚
  в”‚  в””в”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”¬в”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”    в”‚
  в”‚                             в–ј                                в”‚
  в”‚  в”Њв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”ђ    в”‚
  в”‚  в”‚                   Agent Registry                     в”‚    в”‚
  в”‚  в”‚                                                      в”‚    в”‚
  в”‚  в”‚   рџџў  Eliza          94 / 100   active               в”‚    в”‚
  в”‚  в”‚   рџџў  Jito MEV       91 / 100   active               в”‚    в”‚
  в”‚  в”‚   рџџў  GOAT           88 / 100   active               в”‚    в”‚
  в”‚  в”‚   рџџў  Drift Keeper   82 / 100   active               в”‚    в”‚
  в”‚  в”‚   рџџЎ  BonkBot        67 / 100   slow commits         в”‚    в”‚
  в”‚  в”‚   рџ”ґ  [agent_n]      31 / 100   stale вЂ” flagged      в”‚    в”‚
  в”‚  в”‚                                                      в”‚    в”‚
  в”‚  в”‚        14 agents monitored В· updated every 30 min   в”‚    в”‚
  в”‚  в””в”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”    в”‚
  в””в”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”Ђв”
```

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
git clone https://github.com/genis190/AGENT
cd AGENT
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
| `OPENAI_API_KEY` | вњ… | OpenAI API key |
| `AI_MODEL_NAME` | вЂ” | Model override (default: `gpt-4o-mini`) |
| `AGENT_WALLET_PUBLIC` | вЂ” | VANCE on-chain wallet address |
| `SOLANA_RPC_URL` | вЂ” | RPC endpoint (default: mainnet) |
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
    seed.ts              14 pre-seeded Solana agents
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

## License

MIT вЂ” built on Solana, powered by OpenAI, always on-chain.
