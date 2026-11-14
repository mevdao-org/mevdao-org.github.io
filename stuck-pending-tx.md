---
layout: default
title: Ethereum transaction stuck pending? Replace it, don't resend it
description: Why an Ethereum transaction sits pending, how to speed it up or cancel it with the same nonce, and why sending it again makes things worse.
---

# Ethereum transaction stuck pending? Replace it, don't resend it

You hit send an hour ago and Etherscan still says pending. The instinct is to just send it again. Don't. The second one lines up behind the first and now you've got two stuck.

Before anything else, check the nonce, the counter on each tx you send. They only get mined in order. Look up the stuck one on Etherscan and note its nonce, then check the last one that confirmed. Last confirmed 41 and stuck one 43? Then it's waiting on a 42 that doesn't exist, often a tx sent from another wallet app on the same address.

Most of the time though it's just the fee. Base fee went up after you signed, so your max fee is now below it. Nothing's broken. It's waiting for gas to drop back to what you offered, which might take ten minutes or might never happen.

Speed up is the fix for that. MetaMask, Rabby and most wallets have the button, and all it does is sign a new tx with the same nonce and a bigger tip. Nodes only swap it in if the fee is clearly higher, about 10% more on both max fee and tip, so don't bump it by a cent.

Cancel works the same way, it's just a 0 ETH send to yourself with that nonce and a higher fee. Whichever one gets mined first wins and the other gets dropped. So yes, a cancel can lose to the original. That's normal.

If you sent it through Flashbots Protect or some other private RPC, it was never in the public mempool, so Etherscan might show nothing for a while. Give it a few minutes and check the RPC's own status lookup before replacing it, since a replacement sent the normal way is visible to everyone.

And if someone in your DMs offers to unstick it and asks for your seed phrase, that's the scam. Nobody needs it to replace a transaction.

The longer guide on [how to speed up or cancel a stuck Ethereum transaction](https://mevdao.org/blog/ethereum-transaction-stuck-pending-how-to-speed-up-or-cancel-it) has the steps wallet by wallet. If you want to know where pending transactions actually sit and who's watching them, read [what the Ethereum mempool is and how bots see pending transactions](https://mevdao.org/blog/what-is-the-ethereum-mempool-how-bots-see-pending-transactions).

MEV DAO Research. Back to the [field notes](./).
