---
layout: default
title: Check an address for an EIP-7702 delegation with eth_getCode
description: Read the 0xef0100 delegation designator on any Ethereum address, find the contract it points to, and clear it with a zero-address authorization.
---

# Check an address for an EIP-7702 delegation

With EIP-7702 your plain old wallet can run contract code. People use it to batch transactions, or to let someone else pay the gas. Drainers figured out fast that one bad signature from you gives them an address that forwards every deposit.

The upside is that it's visible. It's stored as the account's code, and anybody can read that.

## Reading the code

Call eth_getCode on the address. Any public RPC works.

```bash
curl -s -X POST https://ethereum-rpc.publicnode.com \
  -H 'content-type: application/json' \
  -d '{"jsonrpc":"2.0","id":1,"method":"eth_getCode","params":["0xYourAddress","latest"]}'
```

A normal wallet gives you back "0x". A delegated one gives back 23 bytes. 0xef0100 comes first, then 20 bytes of delegate contract address.

```text
0xef0100 <20-byte delegate contract address>
```

Paste the delegate address into a block explorer. If it's a known wallet implementation you set up on purpose, fine. If it's unverified, or you don't remember signing anything, treat the wallet as compromised.

## Checking more than one chain

Delegations live on one chain at a time. Mainnet looking clean says nothing about Base. Also, drainers like signing with chain ID 0, which works on any EVM chain that has 7702.

So run it on every network you've touched. Our open source [delegation checker](https://github.com/mevdao-org/eip-7702-delegation-checker-revoker) checks them all at once if you'd rather not.

## Clearing it

The fix is another authorization that points the address at the zero address. Once it's included, the account's code is empty again.

Here's the problem. It has to be signed by the same key. So if the key leaked, the attacker just signs a fresh delegation right after you clear theirs. Clearing is really for phishing signatures, where the key itself never left your hands.

If the key's gone as well, clearing buys you very little on its own. The remaining assets still have to leave in the same block, before the drainer notices. Our [guide to checking and removing a malicious EIP-7702 delegation](https://mevdao.org/blog/how-to-check-and-remove-a-malicious-eip-7702-delegation) goes through both situations. If you're unsure which approach fits, read [EIP-7702 rescues vs Flashbots bundles](https://mevdao.org/blog/eip-7702-rescue-vs-flashbots-bundles-saving-tokens).

## When to stop and get help

Still holding staked tokens or vesting positions in there? Then a mistake costs real money, and a [sweeper bot rescue](https://mevdao.org/blog/rescue-tokens-from-a-compromised-wallet-sweeper-bot-rescue-service) from people who've run them before is worth a look.

MEV DAO Engineering. See also the [sweeper bot checklist](sweeper-bot-checklist.html).
