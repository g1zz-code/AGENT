<div align="center">
  <img src="public/3ea1f474-8065-496d-a125-456553e71e28.png" alt="DESCU Banner" width="800"/>
</div>

<div align="center">

# DESCU -- Autonomous On-Chain AI Agent

**P**rotocol  *  **A**nalysis  *  **N**etwork  *  **O**bserver  *  **P**ersistent  *  **T**racking  *  **I**ntelligence  *  **A**gent

[![Live Demo](https://img.shields.io/badge/Live_Demo-DESCU.vercel.app-f472b6?style=for-the-badge)](https://ai-bot-project-lime.vercel.app)
[![Agent Registry](https://img.shields.io/badge/Registry-12_Agents_Live-f472b6?style=for-the-badge)](https://ai-bot-project-lime.vercel.app/registry)
[![Agent Profile](https://img.shields.io/badge/Agent_Profile-DESCU-deeppink?style=for-the-badge)](https://ai-bot-project-lime.vercel.app/agent)

[![Solana](https://img.shields.io/badge/Chain-Solana_Mainnet-f472b6?style=flat-square&logo=solana)](https://solana.com)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-3178C6?style=flat-square&logo=typescript)](https://www.typescriptlang.org)
[![Grok](https://img.shields.io/badge/AI-Grok_3-000000?style=flat-square&logo=xing)](https://x.ai)
[![Vercel](https://img.shields.io/badge/Deploy-Vercel-000000?style=flat-square&logo=vercel)](https://vercel.com)
[![License](https://img.shields.io/badge/License-MIT-22c55e?style=flat-square)](./LICENSE)

</div>

---

DESCU is an autonomous AI agent deployed on the Solana blockchain. It monitors on-chain activity in real time, tracks AI agent reputation across the Solana ecosystem, answers blockchain queries, and communicates in structured `AGENT_SPEC` format -- readable by both humans and machines.

---

## Identity

```
agent_id      : DESCU
agent_name    : DESCU
agent_version : 1.0.0
wallet        : DbzFutGThzbMNaDyqvdzWugdZuhnaqtWyfD9qp9GZRRV
status        : active
protocol      : Solana Agent Protocol (SAP v1)
```

> [Verify on Solscan](https://solscan.io/account/DbzFutGThzbMNaDyqvdzWugdZuhnaqtWyfD9qp9GZRRV)

---

## Capabilities

| Skill | Description |
|---|---|
| `balance_checker` | SOL + SPL token balances for any wallet address |
| `price_monitor` | Real-time token prices via CoinGecko (SOL, USDC, BONK, JUP) |
| `transaction_analyzer` | Full transaction history by wallet address or signature |
| `network_status` | Solana mainnet health -- current slot, TPS, validator status |

**Agent Registry** -- DESCU monitors 12 active Solana protocol agents. GitHub activity is crawled every 30 minutes. Each agent receives a reputation score from 0 to 100 based on commit frequency, on-chain activity, and protocol compliance.

**OpenClaw compatible** -- `/manifest` exposes DESCU skills in machine-readable format for direct agent-to-agent integration.

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
| [`/`](https://ai-bot-project-lime.vercel.app) | Chat interface -- query DESCU directly |
| [`/agent`](https://ai-bot-project-lime.vercel.app/agent) | DESCU public identity, skills, and reputation score |
| [`/registry`](https://ai-bot-project-lime.vercel.app/registry) | Live Solana agent registry with reputation rankings |
| [`/manifest`](https://ai-bot-project-lime.vercel.app/manifest) | OpenClaw-compatible skill manifest |

---

## Architecture

```
+------------------------------------------------------------------+
|                       DESCU CORE                              |
|                                                                  |
|  User / External Agent / API call                                |
|                   |                                              |
|                   v                                              |
|       +-----------------------+                                  |
|       |    Express Server     | <--- /manifest  (OpenClaw)       |
|       +----------+------------+                                  |
|                  |                                               |
|         +--------+--------+                                      |
|         |                 |                                      |
|    +----v-----+    +------v------+                               |
|    |    AI    |    |   Solana    |                               |
|    |Processor |    |  Commands   |                               |
|    +----+-----+    +------+------+                               |
|         |                 |                                      |
|    +----v-----+    +------v------+                               |
|    |  x.ai    |    | web3.js RPC |                               |
|    |  Grok 3  |    |   Mainnet   |                               |
|    +----------+    +-------------+                               |
+------------------------------------------------------------------+
                          |
                          |  runs every 30 min
                          v
+------------------------------------------------------------------+
|                 AGENT SURVEILLANCE ENGINE                        |
|                                                                  |
|  +------------------------------------------------------------+  |
|  |                   Background Crawler                       |  |
|  |                                                            |  |
|  |   +-------------------+     +---------------------+       |  |
|  |   |    GitHub API     |     |   DexScreener API   |       |  |
|  |   |  commit history   |     | token + vol signals |       |  |
|  |   |  last push date   |     |  on-chain activity  |       |  |
|  |   +---------+---------+     +-----------+---------+       |  |
|  +-----------+--------------------------+--+------------------+  |
|              +-------------+-----------+                        |
|                            v                                    |
|  +------------------------------------------------------------+  |
|  |              Reputation Scoring Engine                     |  |
|  |                                                            |  |
|  |   commit_score  +  onchain_score  +  protocol_score       |  |
|  |   --------------------------------------------------------  |  |
|  |                      score: 0 - 100                       |  |
|  +--------------------------+---------------------------------+  |
|                             v                                   |
|  +------------------------------------------------------------+  |
|  |                     Agent Registry                         |  |
|  |                                                            |  |
|  |  [**] elizaOS/eliza              97/100  active            |  |
|  |  [**] jito-foundation/jito-sol   95/100  active            |  |
|  |  [**] orca-so/whirlpools         91/100  active            |  |
|  |  [**] raydium-io/raydium-sdk     89/100  active            |  |
|  |  [**] drift-labs/protocol-v2     87/100  active            |  |
|  |  [**] mrgnlabs/marginfi-v2       83/100  active            |  |
|  |  [**] MeteoraAg/meteora-ag       79/100  active            |  |
|  |  [**] helius-labs/helius-sdk     77/100  active            |  |
|  |  [--] tensor-oss/tensorswap      74/100  active            |  |
|  |  [--] kamino-finance/klend-sdk   71/100  active            |  |
|  |  [~~] goat-sdk/goat              63/100  slow commits      |  |
|  |  [~~] pyth-network/pyth-solana   58/100  slow commits      |  |
|  |                                                            |  |
|  |     12 agents tracked  --  updated every 30 min           |  |
|  +------------------------------------------------------------+  |
+------------------------------------------------------------------+
```

---

## Stack

| Layer | Technology |
|---|---|
| Runtime | Node.js 20 + TypeScript |
| AI Model | xAI Grok 3 |
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
# Add your XAI_API_KEY to .env
npm run dev
```

Server starts at `http://localhost:3000`

---

## Environment Variables

| Variable | Required | Description |
|---|---|---|
| `XAI_API_KEY` | yes | xAI Grok API key |
| `AI_MODEL_NAME` | no | Model override (default: `grok-3`) |
| `AGENT_WALLET_PUBLIC` | no | DESCU on-chain wallet address |
| `SOLANA_RPC_URL` | no | RPC endpoint (default: mainnet) |
| `GITHUB_TOKEN` | recommended | Raises rate limit to 5000 req/h |

---

## Project Structure

```
api/
  index.ts               Vercel serverless entry point
src/
  ai/
    model.ts             xAI Grok adapter with fallback support
    processor.ts         AGENT_SPEC prompt engine + skill router
  agent-protocol/
    index.ts             SAP Protocol core
    profile.ts           DESCU identity + reputation scoring
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
  logo.svg               DESCU logo
```

---

## License

MIT -- built on Solana, powered by xAI Grok, always on-chain.