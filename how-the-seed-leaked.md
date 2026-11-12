---
layout: default
title: How did my seed phrase leak? Where to look after a sweeper bot
description: The usual ways a seed phrase or private key ends up with a sweeper bot operator, and why finding the leak matters before you set up a new wallet.
---

# How did my seed phrase leak?

We hear this right after "can you get it back", almost every time. It's a good question. If you don't work out how the first seed got out, the new one can go the same way, and then you're back here in a month.

You might never know for sure, and that's ok. Ruling enough out is all you need to decide where the new wallet lives.

## You typed it into a website

Probably the most common. You click an ad for your wallet, it looks right, and it asks for the seed phrase to resync or claim something. Your browser history from before the first sweep is worth a scroll.

## Somebody helped you

You asked a question in a Discord and got a DM from "support" a minute later. That wasn't support. If you typed the seed for them, or shared your screen with the wallet open, that's probably it.

## It was saved online

Check if you ever took a photo of the seed. Phones back those up to the cloud without asking. Same with notes apps and emails to yourself. If someone got into that account, they got the seed.

## Malware on your computer

Info stealers copy wallet extension data and whatever's on the clipboard. They usually come with cracked software, or a "beta" a stranger sent, or a fake extension. If that's your case, don't create the new seed on that computer.

Developers have their own version. A private key in a .env file that got pushed to a public repo gets swept fast, because bots scan GitHub for keys all day.

## What next

Make the new wallet somewhere the leak can't reach. Different device if you suspect malware, and the seed goes on paper.

The old address still holds whatever the bot didn't take. Sending it gas won't work, the bot takes it. Things come out in a bundle instead, and our [Flashbots token rescue guide](https://mevdao.org/blog/how-to-rescue-tokens-from-a-compromised-wallet-with-a-sweeper-bot-flashbots-guid) has the steps. If you want someone else to [recover a wallet from a sweeper bot](https://mevdao.org/blog/rescue-tokens-from-a-compromised-wallet-sweeper-bot-rescue-service), that page explains how we do it. A stranger offering to recover it in your DMs is almost always the next scam, so read [how fake recovery services work](https://mevdao.org/blog/crypto-recovery-scams-how-to-spot-fake-wallet-recovery-services) first.

MEV DAO Research. More in the [field notes](./).
