---
layout: default
title: Your eth_callBundle came back green. Now read the numbers
description: What coinbaseDiff, ethSentToCoinbase, gasFees and bundleGasPrice in a Flashbots simulation response tell you, and which one a builder looks at.
---

# Your eth_callBundle came back green. Now read the numbers

No revert just means it runs. Doesn't mean any builder wants it. That part's in the same response, and most people scroll right past it.

Our order:

**1. Every entry in results.** Top level fine, one tx with an error or revert field. Not in revertingTxHashes? Then the whole bundle's dead. Look at all of them.

**2. stateBlockNumber.** Which state you simulated on. Two blocks behind your target and the reserves you priced against have likely moved. Sim on the parent of the block you want, and again right before sending.

**3. coinbaseDiff.** What the fee recipient gains from your bundle, so it's what the builder sees. It's gasFees (priority fee only, base fee is burned) plus ethSentToCoinbase, i.e. any transfer to block.coinbase from your contract. On competitive flow most searchers keep the priority fee tiny and tip by coinbase transfer, so the tip only goes out if the trade works. That's also why a near-zero gasFees isn't a bug. And if coinbaseDiff looks too big, check whether another tx in the bundle, like the one you're backrunning, pays its own priority fee. That counts too.

**4. bundleGasPrice.** Roughly coinbaseDiff over totalGasUsed. Per gas, that is. Builders care about this more than your total, since your gas is block space someone else could've filled. Big tip, heavy bundle? It can lose to a small tip on a lean one.

**5. gasUsed per tx.** One tx eating most of it is where you trim. Cold storage reads, an approval you didn't need, a pointless router hop.

Green sim and still nothing lands? Usually you're getting outbid per gas, or state moved under you. Re-sim on the newest block and compare bundleGasPrice with your last run. And if the profit only shows up at one exact block, put a min-out check in the contract and revert when it's not there. Cheaper than paying for empty runs.

Haven't wired up the call yet? Here's how to [simulate a Flashbots bundle with eth_callBundle](https://mevdao.org/blog/simulate-a-flashbots-bundle-with-eth-callbundle-2026). Sim passes but it won't land? Go through [why your eth_sendBundle keeps missing blocks](https://mevdao.org/blog/flashbots-bundles-explained-how-to-send-eth-sendbundle-and-why-yours-isn-t-landi). More in the [field notes index](index.html).

MEV DAO Research
