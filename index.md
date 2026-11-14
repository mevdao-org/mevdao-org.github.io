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

Signed something odd lately? [Check the address for an EIP-7702 delegation](eip-7702-delegation-check.html) before anything else. Found one and wondering whether to clear it? Here's [when revoking a 7702 delegation helps and when it doesn't](revoke-7702-delegation.html).

Before anyone touches the wallet, go through [what to have ready for a rescue](before-a-sweeper-rescue.html). Got an ENS name stuck in there? See [what to do about an ENS name in a hacked wallet](ens-name-in-a-hacked-wallet.html).

An airdrop just showed up for the drained address? Read [how to claim an airdrop in a hacked wallet](airdrop-in-a-hacked-wallet.html) before you send it any gas.

Not sure how the attacker got your seed in the first place? Here's [where to look for the leak](how-the-seed-leaked.html) before you set up the new wallet.

Tokens stuck on Base, Arbitrum or Optimism? Read [why the mainnet rescue trick fails on an L2](hacked-wallet-on-an-l2.html) and what we do instead.

Still got a Uniswap position in the drained wallet? Here's [what to do with an LP position in a hacked wallet](lp-position-in-a-hacked-wallet.html) before you try to pull the liquidity.

Leaked key belongs to an owner on a team Safe? Here's [what to do when one of your Safe signers gets hacked](safe-signer-compromised.html).

Lost tokens to a bad signature rather than a leaked key? Here's [which approvals to revoke after a drainer](approvals-after-a-drainer.html), in the order we do it. Some of what they took was USDT or USDC? See [whether stolen stablecoins can still be frozen](stolen-usdt-freeze.html) and how to check.

It's a Trust Wallet that got hit? Read [what changes with a sweeper bot on Trust Wallet](sweeper-bot-on-trust-wallet.html). And if a stranger offers to get it all back, ask them [the questions we'd ask a wallet recovery service](vetting-a-wallet-recovery-service.html) first.

If you'd rather not do it yourself, read about our [sweeper bot rescue service](https://mevdao.org/blog/rescue-tokens-from-a-compromised-wallet-sweeper-bot-rescue-service).

## If you build bots

Bundles that never land are their own special kind of pain. Our [Flashbots bundle debugging list](flashbots-bundle-not-included.html) is the order we check things in. Sim came back green? Here's [how to read the numbers in an eth_callBundle response](callbundle-numbers.html) before you send. Sniping launches? Run [three token checks before your bot buys](sniper-bot-token-checks.html). Thinking of paying someone to build one? Here's [what to sort out before you hire an MEV developer](before-you-hire-an-mev-developer.html). Running liquidations on Aave? Start with [four checks before you run a liquidation bot](liquidation-bot-first-checks.html). Someone selling you a bot that "prints"? Ask [three questions before you believe an MEV bot is profitable](mev-bot-profit-claims.html). Flash loan arb passing on a fork and reverting on mainnet? Here's [why a flash loan arb keeps reverting](flash-loan-arb-reverts.html). Handing a key to a Telegram sniper bot? Read [what to ask before you paste a key into one](telegram-sniper-bot-key.html). Looking at an MEV bot for sale? Here's [what the price tag tells you](mev-bot-for-sale-price.html). Already bought a token you can't sell? Read [what to do after buying a honeypot token](bought-a-honeypot-token.html). Sent a swap through a private RPC and it's just sitting there? Here's [why a Flashbots Protect tx stays pending](flashbots-protect-pending.html) and what to do about it. Plain wallet send stuck for an hour instead? Here's [why you should replace a stuck transaction, not resend it](stuck-pending-tx.html). Wondering what an MEV searcher really spends the day on? Here's [what a searcher actually does all day](mev-searcher-day.html).

On the main blog, the pieces people ask about most are how [Ethereum sniper bots work with Flashbots](https://mevdao.org/blog/how-ethereum-sniper-bots-work-same-block-buys-with-flashbots-and-the-real-risks) and what to know before paying for [custom MEV bot development](https://mevdao.org/blog/custom-mev-bot-development-what-to-know-before-you-hire). If someone on YouTube offered you a free bot, please read about the [Remix MEV bot scam](https://mevdao.org/blog/the-youtube-mev-bot-scam-how-the-remix-contract-drains-your-eth) first, or run our [five minute check on free YouTube MEV bots](free-mev-bot-video-check.html).

## Code

Everything here has a matching repo on [GitHub](https://github.com/mevdao-org). The [compromised wallet rescue toolkit](https://github.com/mevdao-org/compromised-wallet-sweeper-rescue) and the [EIP-7702 delegation checker](https://github.com/mevdao-org/eip-7702-delegation-checker-revoker) are the ones that pair with these notes.

MEV DAO Engineering.
