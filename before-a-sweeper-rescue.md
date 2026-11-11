---
layout: default
title: Before a sweeper bot rescue, have these ready
description: What to gather before you or anyone else tries to recover a wallet from a sweeper bot, and the red flags that mean a "rescuer" is another scam.
---

# Before a sweeper bot rescue, have these ready

Rescues mostly don't fail on the bundle. They fail cause nobody knew what was in the wallet, or the helper was thief number two.

This is what we ask for before touching anything. Worth gathering even if you go DIY.

## Just the address

Public address first. With just that we can see balances, stakes, approvals and if a bot's sweeping. Nobody needs your seed to look, ever.

Yes, eventually the rescue needs the hacked key, since that wallet signs the transfer out. Give it late, to someone you checked out, after you've moved whatever you can move without it. Asked for it in message one? Bye.

## What's stuck

List everything you think is in there. Tokens, NFTs, stakes, vesting, airdrops. Then check on Etherscan, because people forget the LP from 2023 and sometimes that's the biggest thing left lol.

Got a lock or cooldown on something? Write down the end date. In a staked rescue that date is everything.

## A clean wallet

New seed, new device if you can. Malware that got the first key will happily get the second one too.

## 7702 check

If you signed something strange recently, check whether the address now delegates to a contract. A malicious EIP-7702 delegation changes how a rescue works. Our note on [checking an EIP-7702 delegation](eip-7702-delegation-check.html) covers the quick look.

## Rescuer red flags

Upfront fee and no clue how the bundle works? Run. Same if they promise the ETH back (it's gone), or they DMed you first on Telegram, or they can't tell you which transactions they'll send. More on [how fake recovery services work](https://mevdao.org/blog/crypto-recovery-scams-how-to-spot-fake-wallet-recovery-services).

## Then pick a path

Comfortable signing raw transactions? The [Flashbots token rescue guide](https://mevdao.org/blog/how-to-rescue-tokens-from-a-compromised-wallet-with-a-sweeper-bot-flashbots-guid) walks through a DIY bundle. If you'd rather hand it off, this is how the [MEV DAO sweeper bot rescue](https://mevdao.org/blog/rescue-tokens-from-a-compromised-wallet-sweeper-bot-rescue-service) works, what it costs and what it can't do. Either way, have the list above ready first.

MEV DAO Engineering. Back to the [field notes](./).
