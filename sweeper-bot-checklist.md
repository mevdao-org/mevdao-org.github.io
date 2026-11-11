---
layout: default
title: Is there a sweeper bot on my wallet? A field checklist
description: How to confirm a sweeper bot is watching an Ethereum address, using only a block explorer and a public RPC, before you send it any more ETH.
---

# Is there a sweeper bot on my wallet?

Usually you learn about it by losing more money. You top up the wallet with a little ETH for gas, refresh, and the balance is zero again.

Before you send that address anything else, run through this. It's about ten minutes of work with Etherscan open, plus a terminal if you're comfortable in one.

## The last deposit

Pull the address up on Etherscan, newest first. Sweepers are boring and predictable, which helps here. Every deposit gets answered by an outgoing transfer in the same block, or one block later.

Usually it all goes to the same address. They leave dust behind, since the script prices gas first and takes the rest.

Seen that twice? Somebody else has your key. Stop topping it up.

## The nonce

The nonce counts every transaction that key has signed. You probably know your own number, give or take.

```bash
cast nonce 0xYourCompromisedAddress --rpc-url https://ethereum-rpc.publicnode.com
```

Way higher than yours? They've been at it a while then.

## A 7702 delegation

Pectra gave drainers a shortcut. They don't need a bot running anymore if you signed the wrong thing once, because your address now runs their contract.

```bash
cast code 0xYourCompromisedAddress --rpc-url https://ethereum-rpc.publicnode.com
```

0x back? Good, nothing's delegated. Anything starting with 0xef0100 means it is, and the tail end of that string is the contract address. We cover how to read that contract and clear it on the [EIP-7702 delegation check page](eip-7702-delegation-check.html).

## What's left to save

The key itself can't be fixed. What you can still move is anything the sweeper hasn't taken yet. Typical examples are ERC-20 balances, NFTs, staked positions and unclaimed airdrops.

Moving them costs gas, and gas sent the usual way just gets swept. So rescues go out as a private bundle. The gas top-up and the transfer land in the same block, or neither lands.

We wrote up the full method in the [Flashbots token rescue guide](https://mevdao.org/blog/how-to-rescue-tokens-from-a-compromised-wallet-with-a-sweeper-bot-flashbots-guid). Wallet specific notes for Trust Wallet, Ledger and Rabby users are in the [sweeper bot wallet rescue steps](https://mevdao.org/blog/sweeper-bot-on-trust-wallet-ledger-rabby-rescue-steps).

## Avoiding the second scam

Post about a drained wallet anywhere and your DMs fill up with "recovery agents". Ignore them. Nearly every one is a scammer.

A real rescue works with the old key, the one that's already burned. That's all. Anyone asking for your new wallet's seed is trying to rob you twice. Confirmed transfers can't be reversed either, whatever they claim.

Don't want to run the bundle yourself? That's fair, it's fiddly. Our [sweeper bot rescue service](https://mevdao.org/blog/rescue-tokens-from-a-compromised-wallet-sweeper-bot-rescue-service) page says how we do it and what it costs. Whoever you end up talking to, have a look at [how fake recovery services work](https://mevdao.org/blog/crypto-recovery-scams-how-to-spot-fake-wallet-recovery-services) first. It'll save you a bad week.

MEV DAO Engineering. Page source is on [GitHub](https://github.com/mevdao-org/mevdao-org.github.io).
