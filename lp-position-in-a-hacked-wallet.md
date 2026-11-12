---
layout: default
title: Your hacked wallet still holds an LP position
description: What to do with a Uniswap LP position or LP NFT left in a wallet a sweeper bot watches, and why you move the NFT instead of pulling liquidity.
---

Your hacked wallet still holds an LP position
=============================================

The ETH went first. Then the big tokens. But when you open the address on a portfolio tracker, there's still a Uniswap position sitting there, sometimes worth more than what got stolen. Why didn't the bot take it?

Mostly because it's not a balance. Plenty of sweepers watch for ETH and a list of tokens. An LP position is something else, so it can sit there for weeks. Don't count on that lasting, though.

Figure out what you actually hold
---------------------------------

Look at the position first. It's one of three things.

A v2 style pool gives you an ERC-20 LP token. That's just a token, you can move it like any other.

A v3 or v4 position is an NFT. The liquidity and the fees live inside it, and whoever holds the NFT controls them.

If you staked the LP in a farm or gauge, the wallet holds a receipt, or nothing at all, and you need to withdraw from that contract first. Read its withdraw function on Etherscan. Does it pay msg.sender, or can you pass a recipient?

Move the NFT, not the liquidity
-------------------------------

People try to remove liquidity from the hacked wallet. That's two or three transactions, and the tokens land right where the bot is waiting.

You don't need to. Send the position NFT itself to a clean wallet with safeTransferFrom, then close it out from there, at your own pace. If you do want to pull fees on the spot, the collect call takes a recipient, so point it at the clean address.

Either way, the hacked key still needs gas. Send gas on its own and it's gone in the same block. So the gas and the transfer have to go in one private bundle. Our [step by step Flashbots rescue guide](https://mevdao.org/blog/how-to-rescue-tokens-from-a-compromised-wallet-with-a-sweeper-bot-flashbots-guid) shows how that's built.

Check approvals before anything
-------------------------------

Did the wallet ever call setApprovalForAll on the position manager for an address you don't know? Then the attacker can move the NFT without your key, and it's a race already. Same story if the address carries an EIP-7702 delegation: your transfer runs through their code.

Farm positions with a cooldown are a timing problem. We cover that in [unstaking from a compromised wallet](https://mevdao.org/blog/unstake-from-a-compromised-wallet-rescue-locked-tokens).

If you'd rather not sign raw transactions, here's how our [rescue service for swept wallets](https://mevdao.org/blog/rescue-tokens-from-a-compromised-wallet-sweeper-bot-rescue-service) works, and what we never ask for.

MEV DAO Research. Back to the [field notes](./).
