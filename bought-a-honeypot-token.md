---
layout: default
title: You bought a honeypot token. Now what?
description: What to do, and what not to do, after you buy a token you can't sell, from failed sell transactions to approvals and recovery offers.
---

# You bought a honeypot token. Now what?

The buy went through fine. Chart looked great. Then you hit sell and the transaction reverted, or it went through and you got back a few cents. That's a honeypot. We get this message a lot, usually a day after the fact, so here's what we tell people.

## Stop retrying the sell

Every failed sell still costs gas. People bump slippage to 49%, then 99%, then try a different DEX, and it fails every time because the block isn't in the router. It's in the token contract. A transfer rule says only certain addresses get to sell. Fiddling with slippage won't get past that.

If you want to know whether any sell can work, simulate it first. An eth_call of the swap against the current block costs nothing. Some contracts allow a tiny sell under a max amount, or flip a sell tax down later. Most don't. If the sim reverts at every size, you have your answer without burning more ETH.

## Read the contract for a minute

Open it on Etherscan and search for a few words. tradingEnabled, whitelist, blacklist, sellTax. If there's an owner who can set the sell tax to 100 whenever they like, well, there's your honeypot. Owner renounced and the tax is stuck at 99? That's not getting fixed. Owner still around? They could change it, sure, but we've never seen one do it for the buyers. Our guide on [how to spot a honeypot token before you buy](https://mevdao.org/blog/honeypot-tokens-how-to-spot-one-before-you-buy) has the patterns we run into most, so you catch the next one before the buy.

## Check what you approved, not just what you bought

The router approval for the honeypot token itself? Doesn't matter, that token's worth nothing. What we'd worry about is anything else you signed while you were on that site. A USDC approval, a WETH one, some Permit2 message you clicked through at 2am. Those can still be used later. We have a post on [how to revoke token approvals and Permit2 signatures](https://mevdao.org/blog/how-to-revoke-token-approvals-and-permit2-signatures), and yeah, a few of them don't show up in the wallet app at all.

## Ignore the recovery DMs

Say you complain in a Telegram group. Within an hour somebody DMs you offering to "unlock" it for a fee. There's nothing to unlock, only the owner can touch that sell logic. Pay them and you've lost twice.

## Keep the hashes

Token address, your buy tx, the failed sells. Stick them in a note. Same deployer pops up again a week later, you'll know. Token scanners ask for exactly this if you report it.

Honestly the money is almost always gone. Next time, simulate the sell before you buy. That's it.

MEV DAO Engineering. Back to the [field notes](./).
