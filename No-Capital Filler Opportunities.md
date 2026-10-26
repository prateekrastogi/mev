solver research · measured on solver-stage · window 2026-09-17 to 2026-10-16 (30 UTC days) · report 2026-10-17

# No-capital filler opportunities beyond UniswapX and PancakeSwapX

We searched every DefiLlama category for venues where a stranger can fill, execute or settle other people's orders with no approval and with no money locked up after the transaction, the way Across fails and UniswapX works. Each survivor was then measured over 30 days on Ethereum, Base, BSC, Arbitrum and Robinhood Chain. The answer is small: **about $11k to $14k a month for every participant combined, before competition**, almost all of it on Ethereum.

**$11k–$14k**whole-market net pool per month, all venues, ceiling (Kyber's unrealisable premium excluded)

**$5.5k–$7k**our share per month if we took 50% of that

**\~91%**of the pool is on Ethereum

**0**venues near the $100k–$1M a month bar

## How to read the numbers

- **Whole market, not our share.** Every figure is what all takers together could earn on the open flow, before any competition for it.
- **Net is a ceiling.** It is gross taker gain minus gas on each fill. The taker usually also needs an offsetting swap, whose fee and slippage were not measured, so real net is lower.
- **Open means no named party we can see.** Where gating is invisible on chain, every fill counts as open, which is an upper bound.
- **Never priced by symbol.** Only verified token addresses and on-chain feeds. Tokens without a source are withheld by address and not extrapolated, so several pools could be larger than shown.
- **Top 3 share** is given by the address that sent the filling transaction, and by the contract that did the fill where an agent measured it. The contract view is usually far more concentrated.

## Ranking by whole-market net pool per month

| # | Venue and chain | Role | Capital | Open fills | Net pool / month | Top 1 / 2 / 3 by sender | Top 1 / 2 / 3 by contract | Read |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | **Reserve RToken Dutch trades**, Ethereum | Bid in a Dutch auction | Atomic callback | 69 | **$6.0k–$8.5k** | 26 / 46 / 60% | n/m | best open pool 53 priced fills; the range is the stable-pricing method (stable=$1 inflates cross-stable fills by 30%); 15 trusted-filler fills excluded; 37% unpriced |
| 2 | **1inch plain limit orders**, Ethereum | Taker of plain orders | Atomic callback | 16,056 | **$3.9k** | 16 / 31 / 41% | 41 / 82 / 88% | thin +4.17 bp on $9.8M; only 440 of 16,056 open fills priced; 89% of all fills named or gated |
| 3 | Kyber limit orders, Ethereum | Taker (needs Kyber's co-signature) | Atomic callback | 8,712 (upper bound) | $65.9k headline | 8 / 13 / 18% | 60 / 84 / 88% | not realisable the gain is a premium over a reference price (+49.8 bp) won by one contract; 78 USDT-to-WETH fills carry it; reference prices disagreed by 1.3%; 98% of fills unpriced; operator co-signature gate not observable |
| 4 | Keep3r network, Ethereum | Keeper for one Yearn harvest job | Bond, no funds, 3-day wait | 470 | $347 | by calls: 50.6 / 90.8 / 95.1% | top keeper is a contract | thin reward is about 1.14x gas; six keepers |
| 5 | Kyber limit orders, Arbitrum | Taker | Atomic callback | 818 | $433 | 29 / 40 / 48% | 33 / 57 / 78% | small; 93% unpriced |
| 6 | Reserve RToken Dutch trades, Base | Bid in a Dutch auction | Atomic callback | 35 | $256 | 46 / 66 / 83% | n/m | small; 32% unpriced |
| 7 | Orbs TWAP v4 fills, BSC, Arbitrum, Base, Ethereum | Fill a TWAP order for the dst fee | Gas only | 5,641 / 528 / 132 / 2 | $98 / $59 / $11 / $0.6 (about $169) | 100 / 100 / 100% | one helper contract wins everything | held by the venue every winning fill is Orbs' allowlisted helper contract; behind it 90, 40, 37 and 2 operator addresses; its fee is 1.4x to 2.3x its gas |
| 8 | SynFutures V3, Base | Convert filled limit orders, take the 0.02 USDC tip | Gas only | 35,790 (335 organic) | $319 total; **$6.70 organic** | 6.9 / 13.7 / 20.3% | 21 operator contracts | closed ring 20 of 21 operators are paired with traders on the venue itself (99.06% of fills) |
| 9 | Kyber limit orders, Base | Taker | Atomic callback | 6,536 | $2.3 | 13 / 25 / 37% | 45 / 69 / 81% | nothing; 90% unpriced |

n/m = not measured. The Kyber Ethereum headline is shown for transparency and is excluded from every total on this page.

## By chain

| Chain | Whole-market net pool / month | Made of | Note |
| --- | --- | --- | --- |
| **Ethereum** | **$10.3k–$12.8k** | RToken $6.0k–$8.5k, 1inch $3.9k, Keep3r $0.35k | All the size is here, and one bidder is already prominent in RToken trades |
| Arbitrum | about $0.5k | Kyber $433, Orbs $59 | 1inch is negative (−$399) |
| Base | about $0.3k | RToken $256, Orbs $11 | Clober is negative for takers (−$182) |
| BSC | about $0.1k | Orbs $98 | 1inch and Kyber have nothing priceable |
| Robinhood | not priced | Raindex 3,027 takes | The tokens are tokenized equities with no on-chain reference price, so the gain is withheld. Stable-side volume was $942k; break-even edge to cover gas is 4.6 bp |

## What a share would be worth to us

| Our share of the open pool | 10% | 25% | 50% |
| --- | --- | --- | --- |
| Per month, on $11k–$14k (excluding Kyber Ethereum's premium) | $1.1k–$1.4k | $2.8k–$3.5k | $5.5k–$7k |
| Per month, Ethereum RToken + 1inch only | $1.0k–$1.2k | $2.5k–$3.1k | $5.0k–$6.2k |

The shares are not free to take. On both Ethereum venues three actors already hold 60% to 88% of the fills, and the net figures are ceilings before the offsetting swap. A 50% share of a market this concentrated is a stretch target, not a base case.

## Measured, but zero or negative

| Venue | Chains | Result | Top 3 share |
| --- | --- | --- | --- |
| Reserve Folio bids | Base | −$4.5k signed (+$1.4k counting only winning fills); 59 bids; 41% unpriced; dominated by one thin-pool bid of about $625k at −87 bp | 75 / 88 / 98% by sender; one bidder takes 75% |
| Reserve Folio bids | Ethereum, BSC | 0 bids. The larger Folio flow is trusted fills (113 on Base), which are gated to CoW solvers and emit no amounts | none |
| Clober V2 | Base, Arbitrum | Base −$182 on $301k notional (takers lose to Chainlink); Arbitrum 2 fills | Base 19.9 / 38.6 / 50.1% |
| 1inch plain orders | Arbitrum, Base, BSC, Robinhood | Arbitrum −$399; Base and BSC nothing priceable; Robinhood a measured zero | Arbitrum 31 / 45 / 49% |
| Beefy harvest | All five | Call fee is dust against gas everywhere; net −$49 to −$221 per family per chain. One address is the top harvester on all five chains (70% to 99%) | 89 / 98 / 99% (Robinhood, CLM) |
| Raindex | Robinhood, Base (older version), Arbitrum (V4) | Robinhood 3,027 takes and Base 8,098 takes, gain withheld (no reference price for the equity tokens). Arbitrum $7.61 and nearly all dust. Ethereum, Base, BSC, Arbitrum V6: no events | Robinhood 34.2 / 44.0 / 52.8% by sender, 88.1 / 93.1 / 95.2% by contract; Base 15.1 / 29.0 / 34.2% |
| Trueo resolver | Base | 54 proposals; 49 on markets with no reward; five paid 430 TRUE in total (about $26 at an outside price); bond 50 to 250 TYD or 250 USDC; 3 of 54 challenged | 28 / 41 / 50% |
| Balmy DCA, Revert Compoundor v1 | Ethereum, Base, BSC, Arbitrum | 0 events; the last events were between May 2025 and December 2025, each found by walking back with the same filter (dormant) | none |
| Element NFT matchers | Ethereum, Base, BSC, Arbitrum | 0 matches. Witness: 57,388 events with no pairs on Ethereum and 94,277 transactions with no match call. The deployed contract needs an Element oracle signature for flagged orders | none |
| Synthetix V3, GMX V1, Perennial V2 | Base, Arbitrum | 0 events. Last settlements: Synthetix Base 2025-08, Arbitrum 2025-05; GMX V1 2025-07; Perennial keeper oracles 2026-06 | none |

## How wide the search was

| Batch | List entries | Read in depth | Passed the capital and access test |
| --- | --- | --- | --- |
| Derivatives, synthetics | 232 | 34 | SynFutures V3, Keep3r, Synthetix V3, GMX V1, Perennial V2 |
| Prediction markets, options | 121 | 30 | Trueo resolver only |
| OTC, NFT, credit, insurance | 98 | all four parts | Element (matches); Handshake OTC passes structurally with no reward and almost no flow |
| Automation and order executors | 335 | 29 | Reserve Folio and RToken, Balmy, Revert, Index Coop (gated per product) |
| Robinhood Chain listings | 273 | 30 | Raindex, Beefy, Tacit (Ethereum only) |
| BSC-native protocols | 285 | 14 | Orbs TWAP v4, 1inch plain orders |
| Earlier 87-role map, re-tested for capital | 120 records | 31 | 1inch plain orders, Clober V2, Kyber limit orders, Balmy DCA |

Entries not read in depth were triaged from DefiLlama's batch data (category, chains, TVL) with a one-line reason each, so "not read" is not a finding about the protocol. Per protocol the method was documentation read through, GitHub sources, web search, then an on-chain address check.

### Why almost everything fails

- **Cross-chain intent fillers all have the capital cliff.** Across, DLN, Eco, LI.FI Intents, Synapse, Mayan, Garden, Omni and Aori fill on the destination chain from their own funds and are repaid later. Confirmed by reading the repayment mechanics.
- **Same-chain order venues that pass are few,** and the ones with real volume gate their flow (1inch Fusion needs a KYC token, CoW needs a bond and approval, Bebop and 0x name the taker).
- **Maintenance calls that pay nothing** (Wildcat, Union, Goldfinch, Ensuro, Symbiotic, Nexus Mutual) and **dead or dormant protocols** (Balmy, Revert v1, Synthetix V3 perps, GMX V1, Perennial V2) make up most of the rest.

## What this means

- Nothing outside UniswapX and PancakeSwapX gets near the $100k–$1M a month you set as the bar. The best case is two Ethereum venues worth about $10k a month combined to everyone, both already concentrated in a few solvers.
- The only venues we could enter with no capital and no approval, and that have measurable size, are **Reserve RToken Dutch trades** and **1inch plain limit orders**, both on Ethereum. Their combined ceiling is $9.9k to $12.4k a month for the whole market.
- BSC, Base and Robinhood have almost nothing priced in these venues. Robinhood's Raindex flow may be real, but it cannot be priced without a reference feed for tokenized equities.
- Across stays the largest pool outside the two venues we already run (about $126k a month before funding costs), and its funding problem is the open item.

## Limits of this measurement

- **Unpriced share.** 83% of 1inch Ethereum open fills, 98% of Kyber Ethereum fills, 37% of RToken Ethereum fills and 58% of Orbs BSC fills are in tokens without a verified price. The BSC Orbs fills carry an implied fee of about $404, not counted in any total. The real pools could be larger than shown.
- **Gating is mostly invisible on chain.** Kyber's co-signature, Raindex order expressions and Element's oracle signature were not tested from outside, so open counts are upper bounds.
- **Witnesses.** Ethereum results have independent explorer matches. On Base, BSC and Arbitrum the explorers refused automated reads, so those chains rest on receipt checks, state-versus-log checks and recounts.
- **Provider limits.** The RPC refuses address-less log queries and long ranges, and Ethereum receipts are pruned, so some gas figures come from traces or explorer data. Each is stated in the venue's file.
- **Not measured:** Handshake OTC's fill history (needs an archive RPC), non-CLM Beefy vaults, Tacit, Synthetix V3 on Ethereum, and the offsetting swap on every spread-type venue.
- **Source files.** Code, per-chain results and definitions are in `research/nocliff/` on branch `research/margin-pool`.