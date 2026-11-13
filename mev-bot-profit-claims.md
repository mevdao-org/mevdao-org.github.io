---
layout: default
title: Three questions before you believe an MEV bot is profitable
description: Someone says their MEV bot prints money. Ask these three things before you send anything.
---

# Three questions before you believe an MEV bot is profitable

We get forwarded these a lot. Some Telegram account claims their bot did "3 ETH last week" and wants 0.5 ETH for a copy. Before you pay, ask them three things.

**1. Which address?** Ask for the bot contract. Then open it on Etherscan and look at internal txs and the coinbase transfers to builders. If they won't give one, you're looking at a screenshot of a dashboard, which anybody can fake in Figma.

**2. Gross or net?** Ask for net. Reverts still burn gas, the builder wants its tip, the node isn't free. On mainnet the tip usually takes most of an arb, so a long list of wins can still add up to a loss.

**3. Why sell?** If I had a backrun that still cleared, I'd shut up and run it. Selling copies means every buyer bids against the others for the same txs, and the edge goes to the builder. People do sell decent code, fine, but then you're buying a codebase and hours of setup. Not an income.

Oh, and if the setup is paste this into Remix, deploy, send it ETH: that's [the YouTube scam](https://mevdao.org/blog/the-youtube-mev-bot-scam-how-the-remix-contract-drains-your-eth). The ETH leaves and doesn't come back.

If you want the long version, it's in [are MEV bots legit, and what real profits look like](https://mevdao.org/blog/are-mev-bots-legal-legit-real-profits-vs-scams-2026). And [is MEV bot arbitrage still profitable in 2026](https://mevdao.org/blog/is-mev-bot-arbitrage-still-profitable-in-2026) is about the arb side. Other notes: [field notes index](index.html).

MEV DAO Engineering
