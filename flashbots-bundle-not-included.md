---
layout: default
title: Flashbots bundle not included? A block-by-block debugging list
description: Why an eth_sendBundle submission never lands, and how to find the cause with eth_callBundle, a mainnet fork and the bundle stats endpoint.
---

# My Flashbots bundle isn't landing

You send the bundle, the relay says OK, and then nothing. No error, no inclusion. That silence is the most annoying part of working with bundles.

A relay accepting your bundle only means it parsed. Whether a builder puts it in a block is a separate question. Here's how we work out which part broke.

## Simulate it first

If the bundle reverts in simulation, no builder will include it. Run eth_callBundle against the same block you're targeting.

```json
{"jsonrpc":"2.0","id":1,"method":"eth_callBundle",
 "params":[{"txs":["0xSignedTx1","0xSignedTx2"],
 "blockNumber":"0x<target block>","stateBlockNumber":"latest"}]}
```

Look at each transaction's result, not only the top level. One reverting transaction kills the whole bundle unless you've marked it as allowed to revert.

We go deeper on reading that output in our [eth_callBundle simulation walkthrough](https://mevdao.org/blog/simulate-a-flashbots-bundle-with-eth-callbundle-2026).

## Check the boring stuff

Honestly, most failures we see are dull ones. A nonce that's off by one because a normal transaction got mined in between. A target block that already passed by the time the request went out.

Base fee is the other usual suspect. It can go up 12.5% per block, so a maxFeePerGas that was fine two blocks ago may be too low now. Leave headroom.

## Are you paying enough?

Builders sort by what they earn. If another bundle touches the same state and pays more, yours loses, and you won't get told.

Pay through priority fees or a direct transfer to the block's coinbase. When we're competing, we'd rather overpay a little than lose the block.

## Send to more than one builder

Flashbots only builds a share of blocks. If your bundle only goes to one relay, it can only land in blocks that builder wins. Most searchers fan out the same bundle to several builders, and resend it for each new target block.

## Reproduce it locally

When none of that explains it, fork mainnet at the target block with Anvil and replay the transactions there. You'll see the exact revert, with traces. Our post on [testing an MEV bot on a mainnet fork with Anvil](https://mevdao.org/blog/how-to-test-an-mev-bot-on-a-mainnet-fork-with-anvil) shows the setup.

For the bigger picture on how bundles move from searcher to builder to proposer, read [Flashbots bundles explained](https://mevdao.org/blog/flashbots-bundles-explained-how-to-send-eth-sendbundle-and-why-yours-isn-t-landi).

MEV DAO Engineering. Related tooling: [flashbots-bundle-simulator-anvil](https://github.com/mevdao-org/flashbots-bundle-simulator-anvil).
