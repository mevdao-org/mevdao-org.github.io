---
layout: default
title: Building your first MEV bot? Do it in this order
description: Mempool feed, decoding, simulation, bundles, then logging. The order we'd build a first MEV bot in, and what to skip until later.
---

# Building your first MEV bot? Do it in this order

first mev bot? here's roughly the order we'd build it in. the strategy is the fun part, we know, but its the plumbing that decides if you ever find out whether the strategy works.

feed first. grab a websocket from any public rpc and subscribe to pending txs. yes it misses stuff. yes its slow. doesnt matter yet, you're learning what comes through. (people buy a private stream on day two and then have nothing to point it at.)

decoding eats weeks. its just calldata. you want who sells what, into which pool, with what min out. every router does it different. universal router hides it in command bytes. your bot "missed" that trade? it probably saw it and couldnt read it lol.

sim everything. fork, run theirs, run yours, check balances. under zero after gas and tip, bin it. anvil works. eth_callBundle works. paper math doesnt, tax tokens will humble you.

bundles, not the public mempool. your tx goes in with the one it backruns, sent to builders. wrong order or a revert just means it doesnt land and you pay nothing. a raw tx in the public pool? congrats, your bot is now someone elses sandwich.

log the misses too, not just wins. which block, what sim said, what you tipped, did it land, who beat you. a week of that and you'll know if its speed or price or the decoder. most people guess wrong.

one more, keys. the bot's key sits on a box, hot, so give it its own wallet and only the gas money it needs. sweep profit out often. lock the contract so only your key can call it, an open executor is free money for whoever spots it first.

can wait: builder deals, colo, assembly gas golf. nice later. useless if the decoder chokes.

want code? we did a long one, [how to create an MEV bot from the mempool to your first bundle](https://mevdao.org/blog/how-to-create-a-mev-bot-from-mempool-to-first-bundle). half these words make no sense yet? fair. [our MEV glossary, 60 terms searchers use](https://mevdao.org/blog/mev-bot-meaning-60-terms-every-searcher-should-know). keep it in a tab.

MEV DAO Engineering. Back to the [field notes](./).
