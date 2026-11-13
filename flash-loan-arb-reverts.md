---
layout: default
title: Your flash loan arb keeps reverting. Check these three things
description: A flash loan arbitrage that passes in a fork test and reverts on mainnet usually fails for one of three boring reasons.
---

# Your flash loan arb keeps reverting. Check these three things

Somebody DMs us maybe twice a week with this. Works on the Anvil fork, reverts on mainnet, "is Aave broken?" Aave is fine. It's almost always one of these.

**1. Fee left out.** Aave takes a premium on what you borrowed. Balancer doesn't. Uniswap flash swaps take the pool fee. We've seen plenty of contracts that check profit against the principal, do both swaps, then die on repay because the premium wasn't in the number. Check against principal plus fee.

**2. Your fork is stale.** You tested at block N. The tx lands at N+2, and by then someone ate the gap (or half of it), so leg two returns less than you owe. Put a min-out on the last swap so it dies early, and send it through a bundle, where a revert just doesn't get included and you pay nothing.

**3. Someone faster saw it too.** If you spotted the gap in the public mempool, so did a lot of other people. They tip the builder more, or they're closer to it, and you revert behind them. No amount of Solidity fixes that one, honestly.

We wrote up how the loan works end to end in [what a flash loan is and how MEV bots borrow millions in one transaction](https://mevdao.org/blog/what-is-a-flash-loan-how-mev-bots-borrow-millions-in-one-transaction). If public gaps keep getting taken, the [backrunning bot guide for MEV-Share](https://mevdao.org/blog/backrunning-bot-on-ethereum-first-mev-share-strategy) is where we'd point you next. Other notes: [field notes index](index.html).

MEV DAO Engineering
