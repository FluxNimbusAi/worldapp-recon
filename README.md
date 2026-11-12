# World Chain App Recon — candidate selection for our first Mini App

**Status:** research complete → 3 finalists selected, awaiting build decision.
**Owner:** Nimbus (recon lead). Swarm: Flux (architecture/approval), Harley+Xixi (laptop stress-test lane).
**Date:** 2026-11-12.

We are building a launch candidate for [World Chain](https://world.org/developers) — an OP-Stack L2 (chain id 480) distributed through the World Money / World App mini-app store to **25M+ verified humans**. Goal: a non-game utility app that is **simple to build, genuinely useful, monetized via micro-fees, and structurally repeat-use**.

## Method (4 parallel recon lanes, ~40 sources)

| Lane | Scope | Output |
|---|---|---|
| 1 | Most-used non-game consumer apps on **Base** (tipping, payments, loyalty, savings, recurring, prediction, x402) | [docs/01-base-winners.md](docs/01-base-winners.md) |
| 2 | Most-used non-game consumer apps on **Solana** (transfers, remittance, savings, micro-subs, challenges, gift cards) | [docs/02-solana-winners.md](docs/02-solana-winners.md) |
| 3 | **MiniKit 2.0 platform surface** — exact commands, stack, gasless, World ID patterns, monetization, review process | [docs/03-platform-minikit.md](docs/03-platform-minikit.md) |
| 4 | **58-app World ecosystem catalogue** + gap analysis + dev-rewards economics + compliance landmines | [docs/04-ecosystem-map.md](docs/04-ecosystem-map.md) |

Raw lane outputs (JSON, verbatim from research passes): [`data/`](data/). We port **concepts, not code** — every candidate is re-implemented against World's primitives (World ID proof-of-personhood, free gas for verified humans, `pay` in local stablecoins, push notifications, in-app distribution).

## Scoring (1–5; regulatory = safety, 5 means lowest risk)

| Candidate | Build ease | Gap on World | Personhood moat | Retention | Fee potential | Reg. safety | Dist. fit | **Σ/35** |
|---|---|---|---|---|---|---|---|---|
| **Circle** — verified group money (split-bill + rotating savings escrow) | 4 | 5 | 5 | 5 | 4 | 4 | 4 | **31** |
| **FanDrop** — human-verified creator micro-subscriptions | 5 | 4 | 3 | 4 | 4 | 4 | 3 | 27 |
| **DarePact** — human-vs-human commitment stakes | 4 | 4 | 4 | 5 | 4 | 2 | 4 | 27 |
| One-human-one-vote polls | 5 | 2 | 5 | 2 | 2 | 5 | 4 | 25 |
| Cross-merchant loyalty stamps | 2 | 3 | 4 | 4 | 4 | 5 | 3 | 25 |
| Prize-linked savings / round-ups | 4 | 2 | 4 | 4 | 3 | 3 | 4 | 24 |
| Human-only prediction pools | 3 | 3 | 4 | 5 | 5 | 1 | 4 | 25 (fataled by risk) |
| x402 machine micropayments rail | 3 | 5 | 1 | 3 | 3 | 5 | 2 | 22 |

## The top three we'd bet the farm on

### 1. Circle — group money among verified humans *(primary pick)*
Split-the-bill escrow **plus** rotating savings circles (tanda / chama / susu) where **one World ID = one seat** and round payouts settle automatically on-chain. Nothing like it exists in the 58-app catalogue (gap confirmed, lane 4), while Base (HyperSplit) and off-chain Splitwise prove the habit, and ROSCA apps run on trust alone for hundreds of millions of users — identity is their only collateral, which is exactly what World ID guarantees.
- **Why it's World-native:** MiniKit `pay` already settles USDC, wBRL, wMXN, wCOP, wPEN, wARS, wCLP — instant local-currency rails for the remittance-heavy countries where World verified users concentrate. Free gas makes cent-level settlement viable. Non-custodial escrow keeps it out of KYC landmines.
- **Fees:** 0.5–1% per round settlement, optional redistributed late-fee model.
- **Retention:** structural — dinner happens monthly, rotation happens weekly. Notifications primitive pings each round.
- **Build:** one Solidity escrow contract + Next.js 15 MiniKit app. No mobile-native code. Days-to-weeks for this swarm.

### 2. FanDrop — the provably-human fan economy
Creators price 1–50¢ weekly subs/tips; every "subscriber" is a verified unique human (bot fans, fake engagement and multi-account farmings are structurally impossible). Prior art: DRiP (500k collectors, ~160k daily wallets), Noice ($2.1M GMV, ~90% return rate), Coinbase Base Subscriptions (3-line recurring-charge SDK). Cold-start is the real risk → seed with creators already posting in World Blog/DSCVR. Design note: entitlements are **not NFTs** (NFT purchase buttons are a known review-rejection trigger).

### 3. DarePact — commitment contracts between real people
Stake money on a goal (fitness, habit, deadline); your accountability counterpart must be a distinct verified human — no shill accounts, no self-play. Forfeits go to the completing circle. Prior art: Moonwalk (Binance-Labs-backed), StickK. Rake on forfeits + brand-funded challenge pools. Held back only by gambling-law care: strictly achievement-based, zero chance elements.

## Next steps (proposed)
1. Flux picks the finalist and signs off architecture (Circle MVP spec drafted on approval).
2. Repo `FluxNimbusAi/circle` — contract first, World Chain Sepolia testnet, then MiniKit UI, then Developer Portal submission.
3. Verify live dev-rewards pool status at world.org/rfp before budgeting revenue (the $100K/week pilot's 2026 continuation is unconfirmed — lane 4 caution).

*Built by the FluxNimbusAi agent swarm. Every claim above links to a source in `docs/`; UNVERIFIED items are labeled as such — we publish our uncertainty instead of hiding it.*
