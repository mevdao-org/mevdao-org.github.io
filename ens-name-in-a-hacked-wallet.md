---
layout: default
title: Your ENS name is in a hacked wallet. Now what?
description: Why an ENS name usually survives a sweeper bot, what actually puts it at risk, and how to get it out of a compromised wallet.
---

# Your ENS name is in a hacked wallet. Now what?

Ok, breathe. Sweeper bots want stuff they can sell in the same block. Your ENS name usually isn't that, so it tends to still be there.

## Check where it points

Owner and records aren't the same thing. The key holder can change your address record without moving the name. Look it up in the ENS app before anyone sends money to it.

## Check expiry

This one bites people. Renewing from the hacked wallet means sending ETH to the bot. Don't. Anyone can renew any name, so renew it from your clean wallet and buy yourself time.

## Getting it out

The transfer has to be signed by the hacked key, and that needs gas, and gas is what the sweeper takes. A Flashbots bundle fixes that: the clean wallet pays, the transfer lands in the same block, the bot sees nothing to grab. Wrapped names use a different call, so check if yours is wrapped first.

Longer version on [rescuing ENS names and vesting contracts](https://mevdao.org/blog/rescue-ens-vesting-contracts-from-a-compromised-wallet). The bundle part is in the [step by step Flashbots rescue guide](https://mevdao.org/blog/how-to-rescue-tokens-from-a-compromised-wallet-with-a-sweeper-bot-flashbots-guid).

## Skip the "ENS recovery agent"

DMed you on X, wants a fee first? Nope. Wants your seed in some web form? Also nope. If you want a hand, this is how we [recover a wallet from a sweeper bot](https://mevdao.org/blog/rescue-tokens-from-a-compromised-wallet-sweeper-bot-rescue-service), and what we'll never ask for.

MEV DAO Engineering. Back to the [field notes](./).
