---
layout: default
title: Three checks before a sniper bot buys a new token
description: Quick checks for honeypots, anti-snipe taxes and blacklists before an Ethereum sniper bot buys a freshly launched token.
---

# Three checks before a sniper bot buys a new token

Sniping a launch in the same block feels great right up until you find out you can't sell. Most of the losses we see from sniper bots aren't about speed at all. The bot bought something it should never have touched.

These are the three checks we'd run before any buy goes out.

## 1. Can you actually sell it?

A honeypot lets you buy and blocks the sell, usually with a transfer rule that only whitelisted addresses pass. The cheap test is simulating a buy and then a sell against current state before you send anything. If the sell reverts or returns a fraction of what it should, skip it. More on the patterns in [how to spot a honeypot token](https://mevdao.org/blog/honeypot-tokens-how-to-spot-one-before-you-buy).

## 2. What are the taxes in the first blocks?

Launch taxes are the other trap. 90% for the first few blocks, then it drops. Guess who that's for. Read the tax variables, and check who can change them and when. Our write-up on [anti-snipe taxes, blacklists and trading delays](https://mevdao.org/blog/anti-snipe-token-launches-taxes-blacklists-and-trading-delays) goes through the common ones.

## 3. Can the owner blacklist you?

We've lost count of contracts that blacklist whoever bought in block zero. If there's an owner-only freeze, it's for you. Search for blacklist, maxWallet, tradingEnabled.

## Where the bot fits

Speed won't save you from any of the above. If you want to compare bots anyway, we looked at [the best ETH sniper bots in 2026](https://mevdao.org/blog/best-eth-sniper-bot-in-2026-fees-speed-key-custody) by fees, speed and who holds the keys. And if you want to understand the mechanics, start with [how Ethereum sniper bots work with Flashbots](https://mevdao.org/blog/how-ethereum-sniper-bots-work-same-block-buys-with-flashbots-and-the-real-risks).

Also, a sniper bot needs a hot key. Keep only what you're willing to lose in it, and if that wallet ever gets drained, read our [sweeper bot checklist](sweeper-bot-checklist.html) before you send it more ETH.

MEV DAO Engineering. Back to the [field notes](./).
