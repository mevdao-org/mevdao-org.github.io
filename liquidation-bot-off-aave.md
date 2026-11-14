---
layout: default
title: Moving a liquidation bot off Aave? Compound III and Morpho work differently
description: What breaks when you point an Aave liquidation bot at Compound III or Morpho Blue, and what to change before you send a single transaction.
---

# Moving a liquidation bot off Aave? Compound III and Morpho work differently

the Aave market is crowded, so people look at Compound III and Morpho next. fair. but the bot doesnt port by swapping an address. the liquidation call itself is different on both, and so is how you get paid.

compound III. no liquidationCall at all, which trips everyone up the first time. you call absorb() with the underwater accounts and the protocol eats the position itself, debt and collateral both. what do you get for that? liquidator points. thats it, unless governance pays out for them. the discount comes later, from buyCollateral(), and anyone can call that one. heres the gotcha. once reserves are at target, buyCollateral just reverts (NotForSale). so read the reserves before you get excited about a price gap. a fork pinned to an older block can pass on this and mainnet wont.

morpho blue is weirder. anyone can spin up a market with whatever oracle and LLTV they want, and no reserve list exists to loop over. we read markets off the CreateMarket events. most of them? tiny, or dead, we skip those. oh and higher LLTV means a smaller bonus. biggest market, not always the best paying one.

the nice part on morpho. liquidate() sends you the seized collateral before it pulls the loan token, and calls you back in between. so you can swap the collateral inside the callback and repay out of that. no flash loan needed for most cases. if you do need one, morpho flash loans dont charge a fee.

spark? its an aave v3 fork, your code mostly runs. read the reserve configs anyway, we wouldnt assume theyre the same numbers.

and same as aave, youre still racing everyone else on the oracle update, and a thin collateral token can still eat the bonus on the way out.

we went through all three protocols in more depth in [liquidation bot development on Compound, Morpho and Spark](https://mevdao.org/blog/liquidation-bot-development-compound-morpho-spark). still deciding between a callback and a borrowed float? [how flash loans let a bot borrow inside one transaction](https://mevdao.org/blog/what-is-a-flash-loan-how-mev-bots-borrow-millions-in-one-transaction) covers that part.

MEV DAO Engineering. More in the [field notes](./).
