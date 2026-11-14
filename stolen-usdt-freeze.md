---
layout: default
title: Your stolen USDT is still in the thief's wallet. Can it be frozen?
description: How to check whether stolen USDT or USDC on Ethereum is still sitting where a freeze can reach it, whether it's already frozen, and what actually gets an issuer to act.
---

# Your stolen USDT is still in the thief's wallet. Can it be frozen?

ETH can't be frozen. USDT and USDC can. Tether and Circle each have a blacklist built into their token contract, and once an address is on it, those tokens don't move. Not for the thief, not for anyone.

Drained, and some of it was stablecoins? Then go look where they ended up. Takes ten minutes, and it's the one part of a theft where time is sort of on your side, at least for a bit.

**Find where it went.** Your address on Etherscan, Token Transfers tab, not the main one. Click the address your USDT went to. Is it all still sitting there? Then you've got a window. If it's been swapped to ETH on Uniswap or pushed through a bridge, that part's gone as far as a freeze goes. Chase only what's still USDT or USDC.

**See if it's frozen already.** Open the USDT contract on Etherscan, Read Contract, and query isBlackListed with the thief's address. For USDC it's under Read as Proxy, called isBlacklisted. True means it's already done. No wallet, bot or bundle can move it. Don't pay anyone who offers to.

**Get a report filed fast.** Thieves know about freezes, and that's why stablecoins often get swapped quickly. Issuers don't freeze off a DM from a stranger. What tends to move them is a police report, or an exchange flagging the funds. Put down the tx hashes, addresses, amounts and UTC times in one document, file with the police, and hand it to the issuer and any exchange the trail touches.

**Keep your expectations honest.** A freeze stops the thief from spending it. It doesn't send it back to you. That takes the issuer's own process, usually with law enforcement involved, and it can take a long time.

Also, a stranger in your replies promising a guaranteed recovery for an upfront fee is a scam. Every time.

The longer guide on [following stolen ETH on-chain](https://mevdao.org/blog/can-stolen-crypto-be-traced-how-to-follow-stolen-eth-on-chain) covers the rest of the trail. If you want the contract details, read [how USDT and USDC blacklists work on Ethereum](https://mevdao.org/blog/is-my-wallet-blacklisted-how-usdt-and-usdc-freezes-work-on-ethereum).

MEV DAO Research. Back to the [field notes](./).
