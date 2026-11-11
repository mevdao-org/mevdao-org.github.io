---
layout: default
title: Compromised wallet? What a rescue can still save
description: Which assets can still be pulled out of a wallet whose key has leaked, from staked tokens and vesting contracts to NFTs, ENS names and unclaimed airdrops.
---

# What can you still save from a compromised wallet?

Once a key leaks, the ETH is usually gone in seconds. Sweeper bots are built for that.

Bots are lazy about anything that isn't a plain balance, though. That's usually where a rescue earns its keep.

## Tokens the sweeper skips

Plenty of sweepers just watch ETH plus whatever big tokens the operator cared about. A small ERC-20 balance might sit there for weeks.

You'll still need gas to move them. Send gas on its own and the bot eats it, so gas and transfer go together in one private bundle. Our [step by step Flashbots rescue guide](https://mevdao.org/blog/how-to-rescue-tokens-from-a-compromised-wallet-with-a-sweeper-bot-flashbots-guid) shows how to put one together.

## Staked and locked positions

Staking is a pain. You unstake, sit through a cooldown, then withdraw, and the attacker is watching the same countdown.

What works is timing it. The last withdrawal and the transfer out go in a single bundle, aimed at the block where the lock ends. More on that in our post on how to [unstake from a compromised wallet](https://mevdao.org/blog/unstake-from-a-compromised-wallet-rescue-locked-tokens).

## ENS and vesting

Don't skip the ENS name just because it was cheap. It probably still points at the old address somewhere you've forgotten about.

Vesting contracts are similar. Tokens unlock to the beneficiary on a schedule, and the sweeper will be waiting. See [rescuing ENS names and vesting contracts](https://mevdao.org/blog/rescue-ens-vesting-contracts-from-a-compromised-wallet) for both.

## What about NFTs?

NFTs move with transferFrom or safeTransferFrom, so the bundle looks a lot like a token rescue. Watch out for old setApprovalForAll approvals. The attacker may already be able to move them without your key. The [NFT rescue guide](https://mevdao.org/blog/recover-nft-from-a-hacked-wallet-sweeper-bot-guide) goes through it.

## Airdrops you haven't claimed

People don't expect this one. If an airdrop was allocated to the hacked address, you can still claim it, as long as the claim and the transfer out share a bundle. We wrote up [claiming an airdrop before the sweeper does](https://mevdao.org/blog/how-to-claim-an-airdrop-from-a-compromised-wallet-before-the-sweeper-does).

## DIY or hand it off

You can do every one of these yourself, if signing raw transactions doesn't scare you. If it does, or the amounts are big, our [sweeper bot rescue service](https://mevdao.org/blog/rescue-tokens-from-a-compromised-wallet-sweeper-bot-rescue-service) is one option. Read how it works first.

MEV DAO Engineering. Start with the [sweeper bot checklist](sweeper-bot-checklist.html) if you're not sure the wallet is watched.
