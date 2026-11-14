---
layout: default
title: Why your Ethereum backrun bot does nothing on Solana
description: No public mempool, Jito bundles capped at 5 txs with a tip inside, 400ms slots and leader rotation. What changes when an Ethereum searcher moves to Solana.
---

# Why your Ethereum backrun bot does nothing on Solana

why does an Ethereum backrun bot do nothing on Solana? fair question, its not the same game.

first, no public mempool to watch. Jito killed theirs in 2024. you mostly react after the tx is already in.

bundles are a thing but they're max 5 txs and you pay with a tip transfer to a Jito tip account, inside the bundle. no tip, no landing. easy to miss.

slots are ~400ms, leader changes every few slots, so being near the leader matters more than your gas math ever did.

and if that leader isn't running the Jito client your bundle doesn't land anyway. most stake does run it, not all.

Longer write-up: [Solana MEV bots explained, Jito bundles vs Flashbots on Ethereum](https://mevdao.org/blog/solana-mev-bots-explained-jito-bundles-vs-flashbots-on-ethereum). Still on the Ethereum side? Here's [why eth_sendBundle keeps missing blocks](https://mevdao.org/blog/flashbots-bundles-explained-how-to-send-eth-sendbundle-and-why-yours-isn-t-landi).

MEV DAO Research. Back to the [field notes](./).
