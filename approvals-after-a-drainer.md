---
layout: default
title: Which approvals to revoke after a drainer hit you
description: A short order of operations for cleaning up token approvals, Permit2 signatures, NFT operator rights and EIP-7702 delegations after a wallet drainer.
---

# Which approvals to revoke after a drainer hit you

You clicked a link, signed a popup, and a token or two is gone. Before anything else: did they get your key, or just a permission? Very different days.

If it was just a permission, the key is fine and this is mostly revoking. If the key leaked, revoking won't help. Jump to the bottom.

## How to tell which one it was

Look at the drain on Etherscan. Was it sent **from** your address by your own key? Then they probably have the key. Did someone else's address call `transferFrom` on your tokens? That's an approval being used. Native ETH leaving on its own almost always means the key.

## The order we clean up in

**1. EIP-7702 delegation.** On chains past Pectra, a drainer can get you to sign a delegation so your account runs their code. Check this before anything. If it's there, revoking token approvals won't help, because the contract can just move things.

**2. Unlimited ERC-20 approvals.** Revoke anything you don't recognise, and anything you set to unlimited for a site you no longer use. Start with stablecoins and whatever you hold most of.

**3. Permit2.** People forget this one. A token can have zero normal approvals and still be wide open through Permit2. Check it on its own.

**4. setApprovalForAll on NFTs.** One signature hands over a whole collection. Drainers love these.

**5. Old signatures.** Off-chain permits you signed but nobody used yet can still be submitted later. You can't see them all, so if the stakes are high, move the assets.

The full walkthrough on [revoking token approvals and Permit2 signatures](https://mevdao.org/blog/how-to-revoke-token-approvals-and-permit2-signatures) covers the tools and the gas. If you want to know how each trick works first, read [how drainers abuse Permit, setApprovalForAll and 7702](https://mevdao.org/blog/wallet-drainer-approvals-permit-setapprovalforall-7702).

## If the key is gone

Then the address is dead. Every revoke costs gas, and a sweeper bot will grab that ETH before your tx lands. Stop sending money to it. What's left (staked tokens, vesting, NFTs) has to come out in one bundle where a clean wallet pays. Our notes on an [EIP-7702 sweeper rescue](https://mevdao.org/blog/rescue-tokens-from-a-compromised-wallet-sweeper-bot-rescue-service) explain how we do that.

MEV DAO Engineering. Back to the [field notes](./).
