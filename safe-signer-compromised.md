---
layout: default
title: One of your Safe signers got hacked
description: What a leaked owner key means for a Safe multisig, how to swap the owner out with the remaining signers, and what to do about the drained signer wallet itself.
---

One of your Safe signers got hacked
===================================

This one comes up more than you'd think. Someone's seed leaks, a sweeper empties their personal wallet, and then they remember that same address is an owner on the team Safe. Panic follows. Usually it doesn't need to.

How bad it is
-------------

Look at the threshold first. A 2 of 3 Safe with one leaked key is still a 2 of 3 Safe. The attacker can sign whatever they like, but one signature doesn't execute anything. So the money in the Safe isn't moving unless a second owner signs too.

If the threshold is 1, it's a different story. Treat the Safe as drained-in-progress and move funds out right now, from a clean owner, before you do anything else.

Swap the owner out
------------------

With the remaining owners, queue a swapOwner transaction that replaces the leaked address with a fresh one. Don't create the new key on the same laptop or browser profile, since that's often where the leak came from. Our note on [seed phrase vs private key leaks](https://mevdao.org/blog/seed-phrase-vs-private-key-what-s-the-difference-and-which-leaked) helps you work out which one actually got out.

Any owner can pay the gas to execute, so the leaked wallet never needs ETH for this. Good, because anything you send it gets swept.

While you're in there, check the settings tab. Look for modules or a guard you don't recognise, and reject anything the leaked owner queued. Safe runs transactions in nonce order, so one stuck at the current nonce holds yours up.

Then the personal wallet
------------------------

The Safe was the easy part. The signer's own wallet is usually where the real loss is, and it can still hold staked tokens, NFTs or vesting claims the bot can't touch on its own. Go through [what to do in the first hour after a wallet is drained](https://mevdao.org/blog/wallet-drained-what-to-do-in-the-first-hour-ethereum-checklist) and don't fund it with gas.

If there's something worth saving in there and you'd rather not race the bot yourself, here's how our [rescue service for wallets a sweeper bot is watching](https://mevdao.org/blog/rescue-tokens-from-a-compromised-wallet-sweeper-bot-rescue-service) works.

MEV DAO Research. Back to the [field notes](./).
