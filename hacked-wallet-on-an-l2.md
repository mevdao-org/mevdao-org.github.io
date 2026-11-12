---
layout: default
title: Your hacked wallet is on Base or Arbitrum
description: Why the usual Flashbots rescue doesn't carry over to Base, Arbitrum or Optimism, and what we try instead when a sweeper bot watches an L2 address.
---

Your hacked wallet is on Base or Arbitrum
=========================================

Almost every rescue guide out there, ours included, is written for Ethereum mainnet. Gas and token transfers go into one private bundle, a builder puts them in the same block, the sweeper never gets a look at the gas. Fine. We get a lot of DMs where the tokens are on Base or Arbitrum though.

That trick mostly doesn't work there. People usually find out by losing another round of gas.

Why the bundle idea breaks
--------------------------

These chains have one sequencer and no public mempool. Sounds great, right? Nobody sees your tx before it lands. Except there's usually no bundle either. You can't ask the sequencer to keep your gas top-up and your transfer together, so they get ordered as two separate transactions.

And blocks are fast. Arbitrum makes one about every 250 ms, Base cuts its 2 second blocks into 200 ms Flashblocks. The sweeper doesn't need your pending tx. It watches the balance, sees ETH arrive and pays a higher priority fee to move it out before your transfer runs. Topping up "a bit faster" won't win that. We wrote up [how Arbitrum, Base and Optimism order transactions](https://mevdao.org/blog/mev-on-layer-2-how-arbitrum-base-and-optimism-order-transactions) if you want the details.

What still works
----------------

What we do now is skip the ETH. Don't send any to the hacked address, ever. EIP-7702 is live on Base, Optimism and Arbitrum too. So a clean wallet can pay the gas for a type-4 transaction that runs the transfers as the hacked address, all in one go. There's no gap for the bot to use. We compare the two approaches in [EIP-7702 rescue vs Flashbots bundles](https://mevdao.org/blog/eip-7702-rescue-vs-flashbots-bundles-saving-tokens).

It isn't a sure thing. The attacker holds the same key and can sign their own delegation, so check the address code first. Some tokens also have bridge or claim contracts with their own rules, so read those before you build anything.

Before you send anything
------------------------

Check every chain the wallet ever used, not just the one that got drained. Sweepers often run on several at once, but leftover tokens sometimes sit on a chain the bot ignores.

And if you'd rather not try this on your own, here's how our [rescue service for swept L2 and mainnet wallets](https://mevdao.org/blog/rescue-tokens-from-a-compromised-wallet-sweeper-bot-rescue-service) works.

MEV DAO Research. Back to the [field notes](./).
