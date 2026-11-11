---
layout: default
title: Sweeper bot on a Trust Wallet address
description: What changes when the hacked wallet is Trust Wallet, why importing the seed somewhere else doesn't help, and what you can still move out.
---

# Sweeper bot on a Trust Wallet address

We get this one a lot. Someone's Trust Wallet got drained, they send a bit of ETH in to move a token out, and it's gone before they can hit confirm. That's a sweeper bot. It has your seed and it's faster than your thumb.

## The app isn't the problem

People uninstall Trust Wallet, put the seed into MetaMask or Rabby, and try again. Same result. The bot doesn't care which app you use. It watches the address, and the address comes from the seed. A new app with the old seed is the same hacked wallet.

## Make a new wallet first

Fresh seed, written on paper, never typed into a site or a chat. This is where anything you save will go. Don't reuse a wallet you created on the same phone if you think the phone itself is the leak.

## Stop sending gas

Every top up is a gift to the bot. If there are tokens, NFTs or staked funds left, the way out is a Flashbots bundle: a clean wallet pays the gas and the transfers land in the same block, so the bot never sees ETH to grab. The steps for each app are in our [sweeper bot steps for Trust Wallet, Ledger and Rabby](https://mevdao.org/blog/sweeper-bot-on-trust-wallet-ledger-rabby-rescue-steps).

## Multi chain wallets have a catch

Your Trust Wallet seed is also your BNB Chain wallet, and your Polygon one, and so on. Flashbots is mainnet only. So stuff on other chains is harder, and sometimes we just can't get it. If someone says they'll do every chain, ask how.

## Getting help

If someone writes to you first, offering to "recover" it, read [how fake recovery services work](https://mevdao.org/blog/crypto-recovery-scams-how-to-spot-fake-wallet-recovery-services). If you want us to do it, this is how our [sweeper bot rescue](https://mevdao.org/blog/rescue-tokens-from-a-compromised-wallet-sweeper-bot-rescue-service) works and what we'll never ask for.

MEV DAO Engineering. Back to the [field notes](./).
