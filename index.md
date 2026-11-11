---
layout: default
title: MEV DAO field notes
description: Short, practical notes from MEV DAO on compromised wallets, sweeper bots, EIP-7702 delegations and Flashbots bundles, plus our open source tools.
---

# MEV DAO field notes

We build MEV tooling and spend a lot of time pulling tokens out of wallets that someone else controls. These pages are the short versions of things we keep explaining in DMs. Our main site is [mevdao.org](https://mevdao.org).

## If your wallet was hacked

Start with the [sweeper bot checklist](sweeper-bot-checklist.html). It tells you in a few minutes whether a bot is watching the address.

Then see [what a rescue can still save](what-a-rescue-can-save.html). Staked tokens, NFTs and unclaimed airdrops are often still there.

Signed something odd lately? [Check the address for an EIP-7702 delegation](eip-7702-delegation-check.html) before anything else.

If you'd rather not do it yourself, read about our [sweeper bot rescue service](https://mevdao.org/blog/rescue-tokens-from-a-compromised-wallet-sweeper-bot-rescue-service).

## If you build bots

Bundles that never land are their own special kind of pain. Our [Flashbots bundle debugging list](flashbots-bundle-not-included.html) is the order we check things in.

On the main blog, the pieces people ask about most are how [Ethereum sniper bots work with Flashbots](https://mevdao.org/blog/how-ethereum-sniper-bots-work-same-block-buys-with-flashbots-and-the-real-risks) and what to know before paying for [custom MEV bot development](https://mevdao.org/blog/custom-mev-bot-development-what-to-know-before-you-hire). If someone on YouTube offered you a free bot, please read about the [Remix MEV bot scam](https://mevdao.org/blog/the-youtube-mev-bot-scam-how-the-remix-contract-drains-your-eth) first.

## Code

Everything here has a matching repo on [GitHub](https://github.com/mevdao-org). The [compromised wallet rescue toolkit](https://github.com/mevdao-org/compromised-wallet-sweeper-rescue) and the [EIP-7702 delegation checker](https://github.com/mevdao-org/eip-7702-delegation-checker-revoker) are the ones that pair with these notes.

MEV DAO Engineering.
