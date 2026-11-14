---
layout: default
title: What an MEV searcher actually does all day
description: A plain look at an MEV searcher's day, from watching the mempool to tipping builders, and why winning a bundle doesn't mean keeping the profit.
---

# What an MEV searcher actually does all day

People hear MEV searcher and picture some guy printing ETH while he sleeps. We run searcher code ourselves, so here's the duller version.

Most of it is just sitting there. The bot reads pending txs and every new block, reprices the pools it tracks, and checks if a trade would pay for itself. It almost never would. You're looking at millions of checks for a handful of real ones.

Say it does spot something, a token a bit cheaper on Sushi than on Uniswap. It builds the two swaps, runs them on a fork of the next block, and if the sim still shows a profit it ships the bundle to a few builders with a tip attached. Then you find out you weren't alone. Builders pick whoever tips them most, so on an easy gap the tip goes up and up and by the time you win, you've paid most of it away.

There's a longer write up on [what an MEV searcher is and how they get paid](https://mevdao.org/blog/what-is-an-mev-searcher-what-they-do-and-how-they-get-paid) if you want it. And if you're trying to figure out whether it's worth doing at all, read [how MEV bots make money on Ethereum and who keeps the profit](https://mevdao.org/blog/how-mev-bots-make-money-on-ethereum-and-who-keeps-the-profit) first. Other notes: [field notes index](index.html).

MEV DAO Engineering
