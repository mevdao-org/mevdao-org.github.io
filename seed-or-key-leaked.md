---
layout: default
title: Only one account got swept. Did the seed leak or just a key?
description: How to tell from the drained accounts whether a seed phrase or a single private key leaked, and why the answer changes what you move first.
---

# Only one account got swept. Did the seed leak or just a key?

"my wallet got drained." ok, which accounts? we ask that before anything about tokens. it tells you roughly what leaked, and what leaked tells you what's still at risk.

quick background. your 12 words make every account in the wallet, account 1, 2, 3, all of them, on every EVM chain. a private key is one account. so a leaked seed and a leaked key look different on chain if you know where to look.

every account from the phrase got hit, around the same time? thats the seed. sweepers usually derive a batch of addresses from the phrase and empty them in one go. if account 1 and account 4 lost funds within minutes of each other, stop hoping it was one key.

just the one you exported got hit? like you pasted it into a bot or a script or some .env file once. then its probably just that key. others untouched for days, decent sign. not proof. some drainers skip small balances so a near empty account 3 sitting there means less than a full one would.

an imported account got hit and none of the phrase accounts did? that account was never part of the phrase anyway. it has its own key and it leaked on its own.

xpubs though. one leaked key usually doesnt expose the other accounts. usually. leak it along with the xpub (portfolio trackers and watch-only apps love asking for that) and yeah, someone can do the math backwards to the whole branch. pasted your xpub somewhere ever? treat it like the seed leaked.

passphrase users, the 25th word. if only the 12 words leaked and your passphrase is long and random, the accounts behind it are probably fine. if the passphrase is your dogs name, assume its gone too.

so. key only: move that account, leave the rest, watch them for a week. seed: all of it goes to a new phrase, made on a device you trust, untouched accounts too. and please dont restore the old phrase anywhere "just to check" lol.

the long version with derivation paths and all that is [seed phrase vs private key, and how to tell which one leaked](https://mevdao.org/blog/seed-phrase-vs-private-key-what-s-the-difference-and-which-leaked). rebuilding and some accounts didnt come back from the phrase? [recovering an Ethereum wallet](https://mevdao.org/blog/forgot-your-crypto-wallet-password-how-to-recover-an-ethereum-wallet) explains why imported ones need their own key.

MEV DAO Research. More in the [field notes](./).
