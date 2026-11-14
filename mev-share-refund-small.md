---
layout: default
title: MEV-Share paid you 30 cents? That's normal
description: Why a MEV-Share refund from Flashbots Protect comes back tiny or zero, and what actually sets the size of the refund.
---

# MEV-Share paid you 30 cents? That's normal

So you switched on MEV-Share in Flashbots Protect, swapped a few grand of ETH into some token, and got back... 30 cents. Or zero. First thought is it's broken, or Flashbots is pocketing it. Neither, most likely.

The refund isn't automatic. It's leftovers from a backrun, and a backrun only happens if there's something to grab. Your $3k into USDC/ETH? Pool's huge, price barely twitched, so no bot cared enough to bid, and zero bid means zero for you.

The refund tracks the bid, not your trade size. Three searchers fighting over the same backrun push the bid up and your cut goes up with it. One searcher alone can lowball and still win. Tough luck.

Also timing. If your tx sat for three or four blocks, the price gap that existed at the first block was probably closed by someone else long before yours landed.

It's an auction. On a boring trade the auction is just empty.

Longer version: [what MEV-Share is and how Flashbots pays users back for their order flow](https://mevdao.org/blog/what-is-mev-share-how-flashbots-pays-users-back-for-their-order-flow). And if you'd rather be the one bidding, here's [a first backrunning strategy on MEV-Share](https://mevdao.org/blog/backrunning-bot-on-ethereum-first-mev-share-strategy).

MEV DAO Research. Back to the [field notes](./).
