---
layout: default
title: An airdrop is about to land in your hacked wallet
description: What happens when an airdrop lands in a wallet a sweeper bot watches, why claiming it the normal way fails, and how a same-block claim works.
---

# An airdrop is about to land in your hacked wallet

Yep, that address. The one that got drained and you stopped looking at. Now it's eligible for an airdrop, and the bot that emptied it is very likely still around.

## Why claiming it normally fails

You need gas to claim. So you send ETH in, and the bot takes it out, usually in the same block. People try this over and over. Don't be that person, it only pays the bot.

If the claim does get through, the tokens get swept right after. The bot waits for them too.

## Before you touch it

Open the claim contract on Etherscan. Does the claim function take a recipient? Some do, and then you just claim to a clean wallet. Easy win.

If not, it's about timing. Find the start block. The bots know it, so you should too.

Vesting? Lots of drops give you a bit now and lock the rest for months. That locked part is often worth more, so plan for it now.

Also worth a look: did this wallet ever sign an EIP-7702 delegation? If it did, the account might be running someone else's code, and that changes how you get anything out.

## The same-block claim

What works is one Flashbots bundle. A clean wallet pays the gas, the hacked key signs the claim and then the transfer out, and it all lands in one block or not at all. By the time the bot notices, there's nothing left to sweep.

Getting it right takes some fiddling, mostly gas and the merkle proof. We went through it step by step in [how to claim an airdrop from a compromised wallet](https://mevdao.org/blog/how-to-claim-an-airdrop-from-a-compromised-wallet-before-the-sweeper-does), and the [Flashbots token rescue guide](https://mevdao.org/blog/how-to-rescue-tokens-from-a-compromised-wallet-with-a-sweeper-bot-flashbots-guid) has the bundle code.

## Please don't

Somebody on X offers to claim it for you, fee first? Nope. Wants your seed phrase in a form? Also nope. Fake support accounts show up fast in these threads.

If you'd rather have someone run it, here's how we handle a [sweeper bot rescue for a hacked wallet](https://mevdao.org/blog/rescue-tokens-from-a-compromised-wallet-sweeper-bot-rescue-service), including what we will never ask you for.

MEV DAO Engineering. Back to the [field notes](./).
