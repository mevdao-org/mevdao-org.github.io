---
layout: default
title: That free MEV bot from YouTube, a five minute check
description: Quick checks before you deploy a "free MEV bot" contract from a YouTube tutorial, and why the Remix version almost always drains whatever you fund it with.
---

# That free MEV bot from YouTube, a five minute check

Before you send it any ETH, five minutes of checking.

## Read the withdraw path

Search the code for where your ETH goes after you call start. In the versions we've seen it gets sent to an address that's built from strings, hex chunks or a "router" function, so you can't spot it at a glance. If you can't tell exactly which address receives the funds, that's the answer.

## Ask what the bot actually does

Real MEV needs a searcher running offchain, watching the mempool, simulating, sending bundles. A contract you deploy and then leave alone in Remix doesn't do any of that. No offchain part, no MEV. It's a deposit box with someone else's key.

## Look at the comments again

Sort by newest. The real reports are usually down there, people saying they lost their deposit. The top comments are often from accounts that only ever comment on these videos.

## The minimum deposit

Most want a minimum deposit, "for gas", "so it can compete". Real bots don't need that to start. The minimum is the payout.

We broke down the contract in detail in our post on the [Remix MEV bot scam](https://mevdao.org/blog/the-youtube-mev-bot-scam-how-the-remix-contract-drains-your-eth). If what you actually wanted was a sniper, compare real tools and their key custody in [best ETH sniper bots in 2026](https://mevdao.org/blog/best-eth-sniper-bot-in-2026-fees-speed-key-custody) instead.

Already funded one and then noticed a bot sweeping your other wallet too? That's a separate problem, and our [sweeper bot rescue](https://mevdao.org/blog/rescue-tokens-from-a-compromised-wallet-sweeper-bot-rescue-service) notes start there.

MEV DAO Engineering. Back to the [field notes](./).
