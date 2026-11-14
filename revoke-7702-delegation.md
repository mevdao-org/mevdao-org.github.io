---
layout: default
title: Should you revoke that 7702 delegation?
description: Pointing your EOA's delegation back at the zero address clears it. Whether that saves you depends on who else has your key.
---

# Should you revoke that 7702 delegation?

Quick version. It comes down to one thing: is your key still yours.

**1. What a revoke is.** A type 4 tx carrying an authorization to address(0). Once mined, eth_getCode on the wallet returns 0x again. Wallet's back to a normal EOA. No ETH left? A sponsor can submit it for you.

**2. Key safe, you just signed something dumb.** Revoke. Done, mostly. Nobody else can sign a new authorization, so it stays cleared. Then go kill your token approvals, drainers usually take those in the same visit.

**3. Seed or key leaked.** Don't bother. They re-sign within seconds and you've paid gas for nothing. Their sweeper is probably waiting for you to send ETH in, too. Stop fighting for the address. Move the tokens out, usually in one bundle that pays gas and transfers in the same block.

**4. Not sure which one you are?** Check the code on the address, the nonce on the authorization, and any outgoing transfers you never sent. Takes three minutes.

Full walkthrough: [how to check and remove a malicious EIP-7702 delegation](https://mevdao.org/blog/how-to-check-and-remove-a-malicious-eip-7702-delegation). Key gone? See [7702 rescue vs Flashbots bundles for saving tokens](https://mevdao.org/blog/eip-7702-rescue-vs-flashbots-bundles-saving-tokens). Code: [eip-7702-delegation-checker-revoker](https://github.com/mevdao-org/eip-7702-delegation-checker-revoker). Other notes: [field notes index](index.html).

MEV DAO Engineering
