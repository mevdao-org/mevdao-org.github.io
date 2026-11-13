---
layout: default
title: Your swap went through Flashbots Protect and it's still pending
description: Why a transaction sent through a private RPC like Flashbots Protect can sit pending, how to check it, and when to cancel or resend.
---

# Your swap went through Flashbots Protect and it's still pending

You switched your wallet to a private RPC so you wouldn't get sandwiched, hit swap, and now the wallet says pending. Etherscan shows nothing. A few people have messaged us thinking the tx got lost or stolen. Usually it's neither.

That's kind of the point of the thing. A private RPC doesn't drop your tx into the public mempool, it hands it to block builders directly. So the explorers that only watch the public mempool have nothing to show until it lands in a block. Silence on Etherscan for a minute or two is normal.

Been more than a few minutes? Flashbots has its own lookup, protect.flashbots.net/tx/ with your hash on the end. It says pending, included or failed. We see failed a lot and people panic, but most of the time the price moved past their slippage, the swap would've reverted, so Protect never sent it. You didn't pay gas for it either. Annoying, sure. Still better than paying for a revert.

Stuck for real? Check the gas. A max fee set too low during a busy hour won't get picked up, private or not. Replace it with the same nonce and a higher fee, and send the replacement through the same RPC. Don't fire a new swap from a public RPC while the old one's still out there, you can end up with both.

We wrote up [Flashbots Protect vs MEV Blocker and which private RPC to pick](https://mevdao.org/blog/flashbots-protect-vs-mev-blocker-which-private-rpc-should-you-use) if you're still choosing. And if you're not sure you need any of this, start with [what MEV protection on Ethereum actually does](https://mevdao.org/blog/what-is-mev-protection-on-ethereum-should-you-use-it). Other notes: [field notes index](index.html).

MEV DAO Engineering
