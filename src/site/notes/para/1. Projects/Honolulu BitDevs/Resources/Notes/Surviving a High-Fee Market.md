---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Surviving a High-Fee Market.md","permalink":"/bit-devs/resources/notes/surviving-a-high-fee-market/","title":"Surviving a High-Fee Market","tags":["bitdevs","bitcoin","socratic-28","utxo","fees"],"noteIcon":"3","created":"2023-11-19T10:18:53.022-10:00","updated":"2023-11-19T14:47:33.550-10:00"}
---

# Bitcoin Transaction Fees

> [!QUOTE] [How Bitcoin Fees Work - River's Learning Center](https://river.com/learn/how-bitcoin-fees-work/)
> ## What Are Bitcoin Transaction Fees?
> 
> A Bitcoin transaction fee is what a user pays to miners to get their transaction included in the blockchain. The more a user pays, the higher the chance their transaction will be picked up immediately as there is only a limited amount of space in each block.
> 
> Bitcoin transaction fees are an important income stream for miners alongside the [block subsidy](https://river.com/learn/terms/b/block-subsidy/). Users who pay transaction fees are contributing to the security of the bitcoin network.
> 
> ---
> 
> ## How are Transaction Fees Determined?
> Transaction fees on Bitcoin are mostly determined by two factors:
> - The **“size,”** or data volume of the transaction.
> - Users’ **demand for block space**. The faster a user wants their transaction confirmed, the more fees they will be willing to pay (generally).
> 
> A block can contain a maximum of 4 MB of data, so there is a limit to how many transactions can be processed in one block. A larger transaction will take up more block data. Thus, larger transactions typically pay higher fees on a per-byte basis.
> 
> If you are sending a transaction with the help of a Bitcoin wallet, the wallet should display an option for you to select your fee rate. This fee rate will be calculated in [satoshis](https://river.com/learn/terms/s/satoshi/) per unit of data your transaction will consume on the blockchain, abbreviated as sats/[vByte](https://river.com/learn/terms/v/vByte/). The total fee paid by your transaction will then be this rate multiplied by the size of your transaction.

![BitDevs-28-Tx-Fee-Equation.png](/img/user/para/artifacts/BitDevs-28-Tx-Fee-Equation.png)
# UTXO Management

[![BitDevs-28-UTXO-Video-Thumbnail.png](/img/user/para/artifacts/BitDevs-28-UTXO-Video-Thumbnail.png)](https://youtu.be/0_5wb5agLqE?si=vs7P-ukJ1dXt05L-)

> [!QUOTE] [Matt Odell's UTXO Management Guide](https://werunbtc.com/utxos)
> - bitcoin transaction fees limit network abuse by making usage expensive
> - there is a cost to every transaction, set by a dynamic free market based on demand
> - it is an incredibly robust way to prevent spam without relying on centralized entities that can be corrupted or pressured
> - when bitcoin blocks are full, highest fee transactions are confirmed first
> - pending transactions sit in node mempools awaiting confirmation: can conceptualize mempools as a line to enter a restaurant sorted by who is willing to pay the most
> - if you are willing to wait for your transaction to confirm you can pay significantly lower fees
> - your bitcoin wallet may show a single balance but the reality is that it is made of many different unspent transaction outputs (UTXOs)
> - when you make a bitcoin transaction your wallet will select as many UTXOs as necessary to reach the amount of bitcoin you wish to send
> - onchain transaction fees are calculated based on size in bytes not the amount of sats sent
> - the more UTXOs required on the input side the higher the fee paid
> - from a cost perspective you want to consolidate UTXOs, fewer UTXOs with larger amounts
> - consolidation has privacy tradeoffs though: you link any UTXOs you consolidate as owned by the same person + larger UTXOs mean you will dox more of your stack to anyone you pay in the future

Consider reading this series of [Unchained blog posts](https://unchained.com/blog/) about UTXO management:
- [What is a bitcoin UTXO and why do they matter?](https://unchained.com/blog/what-is-a-utxo-bitcoin/)
- [More UTXOs, more problems: High fees, signing failures, and how to avoid them](https://unchained.com/blog/too-many-bitcoin-utxos/)
- [UTXOs, addresses, and CoinJoins: Preserving privacy in a bitcoin economy](https://unchained.com/blog/bitcoin-utxo-privacy/)

# Fee-Saving Techniques & Strategies

**Avoid bitcoin dust**

> [!QUOTE] [How to prevent small UTXOs from becoming bitcoin dust - Unchained](https://unchained.com/blog/small-utxo-bitcoin-dust/)
> In the world of bitcoin, dust colloquially refers to a UTXO with a value smaller than the transaction fees the owner would have to pay in order to spend it. In other words, if someone has a UTXO worth 5k sats, but it would cost 6k sats in transaction fees to be spent, they are disincentivized from spending it. Why would you ever choose to pay a fee that grants you access to a smaller amount of money than what you just paid? This describes the nature of dust—bitcoin that is effectively stuck where it is, useless to the owner.
> 
> A common and more precise definition of dust as it relates to mempool policy (what I might call “technical dust”) [can be found here](https://bitcoin.stackexchange.com/questions/10986/what-is-meant-by-bitcoin-dust/41082#41082).
> 
> Naturally, the UTXOs categorized as dust will typically have very tiny values. However, the transaction fee required to spend any given UTXO is partially dependent on the current market demand to move bitcoin. This means that if the market demand increases, and fee rates increase as a result, larger-sized UTXOs can enter the dust category. Then, if demand were to subside, some of those bigger UTXOs could lose their dust status.
> 
> If we suppose that global bitcoin adoption has a lot of room to grow, it is reasonable to speculate that the average market demand for transferring bitcoin on the blockchain might also grow substantially, and with permanence. The implication would be that the general size of a UTXO qualifying as dust becomes different than it has been historically.

**Reach a stacking threshold before withdrawing to cold storage**

Dollar cost averaging (DCA) straight to cold storage is probably a bad idea. Consistent sat stackers generally buy small amounts of bitcoin on semi-frequent intervals. Immediately withdrawing those sats to an on-chain wallet means that, over time, your balance will consist of a large number of small UTXOs. When you then go to spend them later, you will likely need to use many different UTXOs for any reasonably large purchase, which means your transactions will be larger overall (more data = higher total fees).

**Use software wallets that allow for coin control**

Some wallets abstract away coin control such that users don't actually know which UTXOs are selected when they send a given transaction. In many cases, the wallet will optimize this for you in some way, but if you don't choose UTXOs yourself, you have to trust the wallet to do it properly (and you can't control your privacy by selecting UTXOs based on their prior history).

You don't always need to choose your own UTXOs, but having the option is usually preferable. 

**Proactively manage UTXOs when fees are low**

The most cost-effective time to clean up your UTXOs is when transaction fees are low. Everyone has a unique definition of what a "low"-fee market looks like depending on their own situation and preferences. Still, you can use explorers like [mempool.space](https://mempool.space/) for priority-based fee estimations and to [easily visualize trends over time](https://mempool.space/graphs/mining/block-fee-rates#1w).

If you don't want to actively watch the fee market for an opportune time to transact, use a tool like [txfee.watch](https://txfee.watch/) to setup email alerts whenever fees are currently high or low. You can even use that tool to set up more customizable automations that respond to the current fee market (e.g., flash your smart lights when fees drop).

**Consider how base layer fees impact Lightning**

For cheaper day-to-day transacting, the Lightning Network is the best option without compromising sovereignty (if done properly). Every LN transaction is one that didn't have to occur on-chain (and incur base layer fees).

However, Lightning channel management is heavily dependent on the base layer fee market. On-chain transactions are required to open, close, or resize channels (via [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Lightning Channel Splicing\|splicing]]). That means cost effective channel management should be done when fees are lower - if you don't have enough liquidity on one side of a channel when fees spike, you might not actually be able to transact without paying high mining fees first.

**Leverage an intermediary layer to accumulate UTXOs**

Rather than accumulating sats with a custodian and withdrawing to self-custody after some large-enough threshold, you can find an intermediary step where fees are less of a concern and the custody tradeoffs are reasonable - somewhere between trusting a single custodian and self-custodial cold storage.

For example, you could withdraw from an exchange straight to a Lightning wallet if that exchange supports LN withdrawals (like [River](https://river.com/signup?r=IRL4B44B)). Unfortunately, self-custodial Lightning still requires a hot wallet. You could do something similar with [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Expanding Transparency by Open-Sourcing Liquid's Functionary Code\|Liquid]] or Chaumian e-cash (like [Fedimint](https://fedimint.org/) or [Cashu](https://blog.bitfinex.com/education/cashu-chaumian-e-cash-mints-over-lightning/)) for different security/UX tradeoffs. 

For example, you can use a non-custodial swap service like [Boltz](https://boltz.exchange/) to easily switch between on-chain bitcoin, Lightning bitcoin, or L-BTC without KYC. Liquid is particularly interesting for this type of intermediary stacking layer because you can actually use [Blockstream's Jade](https://blockstream.com/jade/) to store L-BTC in cold storage. 

You could set up a flow where you accumulate smaller UTXOs as L-BTC (by receiving on Lightning and swapping directly to Liquid), and then you can periodically swap/peg-out of L-BTC to regular, on-chain sats whenever you've reached a reasonable stacking threshold. Liquid could act as a "staging area" for sats that you eventually either send to long-term cold storage or top up a Lightning wallet for day-to-day payments. A setup like that could potentially save a lot of money in a high-fee environment and provide fairly strong security.

[![BitDevs-28-Francis-Liquid-Tweet.png](/img/user/para/artifacts/BitDevs-28-Francis-Liquid-Tweet.png)](https://x.com/francispouliot_/status/1726253329418756192?s=20)

# More Resources

- [High Fees? Bitcoin is Working As Designed](https://www.discreetlog.com/high-fees/)
- [What Is Coin Control? - The Bitcoin Manual](https://thebitcoinmanual.com/articles/what-is-coin-control/)
- [Coin Selection | Bitcoin Design](https://bitcoin.design/guide/how-it-works/coin-selection/)
- [Bitcoin Privacy Guide](https://bitcoiner.guide/privacy/segregate/)