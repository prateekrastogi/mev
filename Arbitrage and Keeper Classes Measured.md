Measurement report - 2026-10-17 - read-only - 30 UTC days on solver-stage

# Arbitrage and keeper classes: market size, concentration and entry capital

Five classes beyond the protocol-bounty search: Pendle arbitrage, oracle and order-flow-auction backruns, ERC-4337 and EIP-7702 bundlers, Chainlink Automation and CCIP execution, and DEX backrun and cross-DEX arbitrage. Swap and bridge filling and lending liquidations are excluded as classes.

## Bottom line

**Only atomic arbitrage is a large market, and its money is concentrated: on Ethereum the top three hold 90% and bribes take 63% of gross, and on BSC the top account is builder-linked.** Pendle arbitrage, Chainlink Automation and CCIP execution pay nothing. Bundlers pay, but flow goes to the wallet's own bundler. Fluid DEX arbitrage is the one new live opportunity outside the DEX backrun class.

- **DEX backrun arbitrage:** about $10.2M a month of net across five chains as measured, but the top three entities hold 90% on Ethereum, 82% on Base and 97.5% on BSC. Robinhood is the open one (top three hold 62%, about $0.94M sits outside them).
- **Standalone cross-DEX arbitrage:** about $1.7M a month, and most of it is on Robinhood (top three hold 20%, 118 entities, about $0.52M outside the top three).
- **Fluid DEX arbitrage (Ethereum), separate from N5:** about $1.48M a month (CI $0.44-2.8M), but 7 events hold 92% of core gross. About 61% of gross is a backrun-style arbitrage right after a swap and about 39% is state-based, and three events carry 96% of the state-based part.
- **ERC-4337 bundlers:** about $246k a month, of which one service fleet lands 42-65% of userops.

**Read every figure as a ceiling.** Market net is after estimated failed attempts but each arbitrage headline could be 2 to 3 times high (a second block draw gave 2.3-3.6 times less gross per block). A share of a concentrated, bribe-heavy market is not free: winning means bidding as high as the incumbents and, on BSC, Arbitrum and Robinhood, matching their latency and builder or sequencer access, and what that access costs is unknown.

## DEX backrun arbitrage (N5)

An arbitrage that lands in the same block directly after a price-moving swap. Net per month, after bribes and gas. The share columns are 0.01%, 0.1% and 1% of the chain's class net.

| Chain / class | Market net / mo | Top-3 share of net | Top-3 dollars | Outside top 3 | 0.01% | 0.1% | 1% | Note |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Ethereum | $631k | 90% (49-98%) | $568k | $63k | $63 | $631 | $6,306 | bribes take 63% of gross; 12 s slots, so the contest is bid size and builder access |
| Base | $468k | 82% (45-94%) | $385k | $82k | $47 | $468 | $4,676 |  |
| BSC (as measured) | $6.60M | 97.5% (86-100%) | $6.43M | $165k | $660 | $6,599 | $66k | inflated by one builder-linked account; 0.45 s blocks, so latency and builder access |
| Arbitrum | $27k | 92% (83-99%) | $25k | $2,167 | $2.7 | $27 | $269 | chain nets negative after failed attempts |
| Robinhood | $2.46M | 62% (53-81%) | $1.53M | $939k | $246 | $2,465 | $25k | least concentrated backrun market |
| **Total** | $10.19M |  | n/a | n/a | $1,019 | $10k | $102k |  |

## Standalone cross-DEX arbitrage (N5)

No earlier swap on its pools in its own block, so the mispricing is visible in the previous block's state.

| Chain / class | Market net / mo | Top-3 share of net | Top-3 dollars | Outside top 3 | 0.01% | 0.1% | 1% | Note |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Ethereum | $36k | above 100% (others net negative) | $38k | -$1,419 | $3.6 | $36 | $364 |  |
| Base | $868k | 99.9% (88-100%) | $867k | $911 | $87 | $868 | $8,680 | 60 arbs, mostly 16: low confidence |
| BSC | $114k | 69% (45-87%) | $79k | $35k | $11 | $114 | $1,139 |  |
| Arbitrum | $31k | 78% (67-94%) | $24k | $7,045 | $3.1 | $31 | $314 |  |
| Robinhood | $656k | 20% (18-40%) | $133k | $524k | $66 | $656 | $6,563 | most open market in the study |
| **Total** | $1.71M |  | n/a | n/a | $171 | $1,706 | $17k |  |

Distinct entities, and how many earn more than $100 / $1,000 / $10,000 a month (scaled from a small window sample, so the counts are noisy). Columns: Ethereum, Base, BSC, Arbitrum, Robinhood.

| Class | Ethereum | Base | BSC | Arbitrum | Robinhood |
| --- | --- | --- | --- | --- | --- |
| Backrun | 114 / 46 / 22 / 4 | 53 / 35 / 22 / 4 | 35 / 29 / 18 / 8 | 14 / 8 / 4 / 1 | 45 / 42 / 38 / 18 |
| Standalone | 59 / 7 / 2 / 1 | 18 / 6 / 3 / 1 | 34 / 22 / 15 / 1 | 15 / 10 / 6 / 1 | 118 / 105 / 79 / 18 |

Format: entities / above $100 / above $1,000 / above $10,000.

## Fluid DEX arbitrage (N2, separate from N5)

A venue-specific measurement from Fluid's `Swap` events. Fluid is not one of the venues N5's arbitrage rule decodes, so these figures are **not included in N5's totals**. A transaction that touches two decoded pools and a Fluid pool could appear in both; that overlap was not deduplicated.

| Chain / class | Market net / mo | Top-3 share of net | Top-3 dollars | Outside top 3 | 0.01% | 0.1% | 1% | Note |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Fluid DEX, Ethereum (all arbitrages) | $1.48M | 64% | $950k | $535k | $148 | $1,485 | $15k | CI $0.44-2.8M; 7 events hold 92% of core gross |
| of which right after a swap on the same pool (24 of 49 sampled) | $906k | n/a | n/a | n/a | $91 | $906 | $9,056 | needs mempool visibility and a bundle right after the mover; on 12 s slots this runs on commodity infrastructure (own node plus a public relay); about 61% of sample gross |
| of which state-based (25 of 49 sampled) | $579k | n/a | n/a | n/a | $58 | $579 | $5,790 | commodity-feasible in principle; 3 events hold about 96% of it |
| Fluid DEX, Base | $8,467 | not reported | n/a | n/a | $0.8 | $8.5 | $85 | 127 arbitrages, median $5.7 |
| Fluid DEX, Arbitrum (core, 7 days) | $8,015 | one contract | n/a | n/a | $0.8 | $8.0 | $80 | all 8 events at block index 1-4 |

- **Two kinds of arbitrage in one venue:** in the 49 sampled Ethereum arbitrages, 24 (61% of gross, $25.9k) landed within one or two slots after a swap on the same pool, and 22 of those in the very next slot. That part is backrun-style: it needs to see the swap (public mempool, or the free MEV Blocker and MEV-Share feeds for private flow) and to submit a bundle placed right after it. With Ethereum's 12 s slots that is feasible on commodity infrastructure; the contest is bribe size and builder access. A swap sent through private order flow that those feeds do not show cannot be seen, and the private share of Fluid's movers was not measured. The other 25 (39% of gross, $16.3k) were not adjacent to a swap and are visible from the previous block's state.
- **Concentration:** 7 events of $2k to $9k hold 92% of core gross. The three largest state-based events (about $9.4k at block index 99, $3.4k at index 2, $2.8k at index 298) carry about 96% of the state-based gross. The two late-block ones were not top-of-block bundles, which is the evidence that some large Fluid arbitrages can be taken without specialised latency. The sample is 2.79% of the span, so this is indicative.
- **Entrant range:** $0 / $13.3k / $207k a month. The agent set the low case to 0 for the backrun part by a rule, not because 12 s slots exclude a commodity entrant. Arbitrum's 8 events in one week all came from one contract at block index 1 to 4.
- `swapIn` has no caller check, from a summary of the source, not the raw file. Fluid is also on your keeper repo's protocol list; the operation is DEX arbitrage, not liquidation, but you should rule on it.

## Oracle-update backruns, order-flow auctions, Pendle, Chainlink and CCIP (N1, N2, N4)

| Chain / class | Market net / mo | Top-3 share of net | Top-3 dollars | Outside top 3 | 0.01% | 0.1% | 1% | Note |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| MEV-Share / MEV Blocker backruns | $86k | not reported | n/a | n/a | $8.6 | $86 | $860 | upper bound; CI $59-122k; 236 entities |
| Spark PSM3 arbitrage, Base | $1,500 | not reported | n/a | n/a | $0.1 | $1.5 | $15 |  |
| Chainlink ETH/USD update backruns | $1,400 | not reported | n/a | n/a | $0.1 | $1.4 | $14 | gross before bribes |
| Pendle PT/YT arbitrage (N1) | $0.0 | n/a | n/a | n/a | $0 | $0 | $0 | no atomic arbitrage found on 4 chains |
| Chainlink Automation (N4) | $0.0 | n/a | n/a | n/a | $0 | $0 | $0 | network deprecated 2026-07-31 |
| CCIP manual execution (N4) | $0.0 | n/a | n/a | n/a | $0 | $0 | $0 | permissionless, pays the caller nothing |

- **Chainlink updates:** ETH/USD got 1,001 updates on Ethereum, 5,022 on Base, 19,211 on Arbitrum and 41,583 on BSC. Arbitrages after an update beat the control by only 17 per 1,001 updates. Liquidations after an update are about 5 times as frequent and were filtered out.
- **Order-flow auctions:** bundles could not be counted directly (0 hint-hash matches in about 540k hints), so the figure is an upper bound from arbitrages behind private swaps: 63k transactions a month, $0.84M gross, $0.69M of bribes, $86k net. The user keeps 90% of the bid.
- **Pendle:** 26,217 market-instants were sampled with Pendle's own quoter. Best-side parity was negative every time (Ethereum median about -10.6 bp), and none of 3,679 traced Ethereum swaps was a searcher arbitrage. The zero means none identified, not none exists.
- **Chainlink Automation:** deprecated on 2026-07-31, with zero `UpkeepPerformed` events in the 30 days on four chains; the registry's transmitter list is owner-set. Of 840 upkeeps, 284 accept an arbitrary caller and only one pays it (about $0.00002).
- **CCIP:** 7,990 messages on Ethereum, 7,811 on Base, 6,795 on BSC and 1,223 on Arbitrum in 30 days. The off-ramp pays the caller nothing; Chainlink's own executors made 183 of 275 recoveries.

## Bundlers and relayers (N3)

| Chain / class | Market net / mo | Top-3 share of net | Top-3 dollars | Outside top 3 | 0.01% | 0.1% | 1% | Note |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Base | $124k | Pimlico fleet 42% of userops | n/a | n/a | $12 | $124 | $1,240 |  |
| Ethereum | $34k | Pimlico fleet 65% of userops | n/a | n/a | $3.4 | $34 | $340 |  |
| Arbitrum | $31k | Pimlico fleet 59% of userops | n/a | n/a | $3.1 | $31 | $310 |  |
| Polygon | $25k | n/a | n/a | n/a | $2.5 | $25 | $250 | 6 sampled days, scaled |
| Optimism | $23k | n/a | n/a | n/a | $2.3 | $23 | $230 |  |
| BSC | $9,000 | Pimlico fleet 50% of userops | n/a | n/a | $0.9 | $9.0 | $90 |  |
| **Total ERC-4337** | $246k |  | n/a | n/a | $25 | $246 | $2,460 | entrant range $0 / \~$970 / \~$3,030 |
| EIP-7702 relayers | $3,000 | n/a | n/a | n/a | $0.3 | $3.0 | $30 | labelled extrapolation; large inflows are phishing sweepers |

- **Why an entrant gets little:** flow is routed by the wallet or paymaster to its configured bundler, so an independent bundler has to run an endpoint for wallets and apps. That fails the not-customer-facing test. About 40% of Ethereum and Base bundles carry zero on-chain compensation (0 of 1,044 traced samples showed any inflow), so any income there is off-chain.
- **EIP-7702:** 9.7M type-4 transactions a month, 7.1M relayed by third parties. The large inflows are phishing sweepers (the top delegate target and relayer are labelled "Fake_Phishing") and are not treated as an earning class.
- Permissionless from code: `handleOps` has no role or stake check.

## Entry capital

Capital at risk per attempt is gas only for every class that works, because the position is funded inside the transaction (Uniswap v4, Balancer and Morpho flash at 0 fee, Aave at 5 bp). The real entry cost is access, infrastructure and build time.

| Class | Capital at risk per attempt | Infrastructure and access | Gas float | Bond or stake | Build effort (estimate) |
| --- | --- | --- | --- | --- | --- |
| DEX backrun (N5) | 0 (flash-funded) | UNKNOWN: bloXroute lists no price; Base Flashblocks endpoint is for node infrastructure | $16 (BSC) to about $990 (Ethereum) for 1,000 attempts (assumption) | none in pool code; builder or sequencer access unknown | 60-150 days (90 central) |
| Cross-DEX standalone (N5) | 0 (flash-funded) | none needed; inclusion speed matters on Arbitrum and Robinhood | same as above | none | 30-80 days (45 central) |
| Fluid DEX arbitrage (N2) | 0 per attempt; a landed revert costs $0.12 median | free MEV Blocker simulation and feeds; server EUR 55-90, RPC $49 a month | about 0.1 ETH (about $260) | none documented | 15-25 days |
| Order-flow-auction backrun (N2) | gas only | free feeds; MEV-Share reputation thresholds unknown | about 0.1 ETH | none documented on MEV Blocker | 25-40 days |
| Pendle arbitrage (N1) | $0 by private bundle; $0.07-4.80 per public revert | server $20-60 (estimate); no stream access | about 0.05 ETH plus $10-20 per chain | none | 12-20 days (4-8 on your existing executor) |
| ERC-4337 bundler (N3) | refunded in the same transaction for paid bundles | node with debug_traceCall; price not sourced | about $129 (3 executors per chain), about $650 with 5x buffer | none for bundlers | 3-5 days one chain; 10-20 six chains |
| Chainlink Automation / CCIP (N4) | gas of one attempt | $40-150 a month (estimate) | $50-100 per chain | transmitter slot not obtainable | 10-15 days (moot: income is zero) |

## The pasted table, audited

A table from another AI rated three strategies. Lending liquidations were removed as an excluded class.

| Strategy | Claim | Measured |
| --- | --- | --- |
| DEX backrun arbitrage | Capital: low-medium with atomic execution | Right on trade capital (zero at risk); misses the real entry cost, which is stream and builder access (price unknown) plus failed-attempt spam: 66 failed attempts per success on Base, 14 on Robinhood (9.5-9.6% of gross). |
|  | Edge: fast state detection, simulation, inclusion | Partly wrong. Seeing and simulating is not enough: 92% of Ethereum gross and 98% of BSC is a same-block backrun, the winners bid heavily (bribes are 63% of Ethereum gross) and hold builder relationships, and BSC's top entity is an EIP-7702 account at gas price 0 paying builder addresses. On Ethereum's 12 s slots latency itself is not the barrier. |
|  | Assessment: good starting point | Hard on Ethereum (top 3 hold 90% of net, bribes 63% of gross) and BSC (top 3 hold 97.5%, builder-linked top account); negative on Arbitrum after failed attempts. The measurement's entrant take of 0 there is a rule, not proof of exclusion. On Base and Robinhood 0.01-0.1% of backrun net is $47-$469 and $246-$2,465 a month. |
| Cross-DEX arbitrage | Capital: low with flash liquidity | Right on trade capital. |
|  | Edge: pricing, routing, gas optimisation | Only partly: standalone arbitrage still lands early in the block on Arbitrum (51% at index 2 or below) and Robinhood (33%). |
|  | Assessment: strong candidate | Not supported as a class: standalone is 5.5% of Ethereum net and 1.7% of BSC. It is real only on Robinhood (20% top-3, 118 entities, about $524k outside the top 3) and, on thin evidence, Base. |
| Lending liquidations |  | Excluded vertical B, removed at the operator's instruction; not measured. |

## Limits

- The arbitrage totals are scaled from a 0.07% to 2.8% block sample. The split into backrun and standalone comes from four contiguous windows per chain, whose gross per block is 2.3-3.6 times lower than the random sample. Bootstrap intervals are lower bounds on the true uncertainty.
- Entity counts above a dollar threshold are noisy extrapolations. Ethereum's standalone top-3 share exceeds 100% because other entities in that class have negative net.
- BSC's headline is inflated by one builder-linked account (about $2.0M of gross); the open market outside it nets about $0.36M, and the corrected gross is 3.5-6 times a published estimate.
- Not measured: HyperEVM, Monad and X Layer for Pendle; DODO PMM, Gyroscope, Uniswap v4 oracle hooks, Fluid on Polygon and Plasma; EntryPoint v0.9; stream and builder-access prices.
- Network reads ran on solver-stage with protected endpoints and a known-positive check before any "no events" claim; tokens were priced by verified address, never by symbol.

Sources: scratchpad vertical/results/ M_N1, M_N2, M_N3, M_N4, M_N5, REDTEAM_MH.