---
layout: default
title: What to check before you run an Aave liquidation bot
description: A few plain checks before you point a liquidation bot at Aave, from health factor math to who actually wins the race.
---

# What to check before you run an Aave liquidation bot

Short list. Four things people skip.

**1. Your own position book.** Don't ask the pool every block who's underwater. Track borrowers yourself (collateral, debt, which reserves) and recompute health factors when the oracle answer changes. Polling getUserAccountData for 10k accounts per block is how you end up both slow and broke on RPC.

**2. Repay funds.** Own capital or a flash loan. Flash loan = tiny capital, more gas, two extra places to revert. Do the math at a busy-hour gas price. Sunday 3am gas lies to you.

**3. The exit swap.** You get paid in collateral. If the collateral is a thin token, the swap back can eat the whole liquidation bonus, and then some. Check pool depth before you count the bonus as profit.

**4. The race itself.** Same oracle update, same block, a dozen searchers. On mainnet the builder tip decides it most of the time and the proposer keeps most of the value. Smaller markets and L2 deployments are friendlier to a solo bot, though not by a lot.

More detail in [how liquidation bots work on Aave and why they're hard to win](https://mevdao.org/blog/how-liquidation-bots-work-on-aave-and-why-they-re-hard-to-win). Weighing liquidations vs arb? See [building an MEV arbitrage bot](https://mevdao.org/blog/how-to-build-a-profitable-mev-arbitrage-bot). Reference code: [mev-arbitrage-and-liquidation-reference](https://github.com/mevdao-org/mev-arbitrage-and-liquidation-reference). Other notes: [field notes index](index.html).

MEV DAO Engineering
