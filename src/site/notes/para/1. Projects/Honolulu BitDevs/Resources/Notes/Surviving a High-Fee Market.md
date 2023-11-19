---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Surviving a High-Fee Market.md","permalink":"/bit-devs/resources/notes/surviving-a-high-fee-market/","title":"Surviving a High-Fee Market","tags":["bitdevs","bitcoin","socratic-28","utxo","fees"],"noteIcon":"3","created":"2023-11-19T10:18:53.022-10:00","updated":"2023-11-19T11:02:46.913-10:00"}
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


# UTXO Management

![What is a bitcoin UTXO? - YouTube](https://youtu.be/0_5wb5agLqE?si=vs7P-ukJ1dXt05L-)

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

**Balancing future costs and privacy:**
- 



# Fee-Saving Techniques & Strategies

**Reach a stacking threshold before withdrawing to cold storage**

Dollar cost averaging (DCA) straight to cold storage is probably a bad idea. Consistent sat stackers generally buy small amounts of bitcoin on semi-frequent intervals. Immediately withdrawing those sats to an on-chain wallet means that, over time, your balance will consist of a large number of small UTXOs. When you then go to spend them later, you will likely need to use many different UTXOs for any reasonably large purchase, which means your transactions will be larger overall (more data = higher total fees).



**Leverage an intermediary layer to accumulate UTXOs and transact day-to-day**


**Use software wallets that allow for coin control**



**Proactively manage UTXOs when fees are low**

The most cost-effective time to clean up your UTXOs is when transaction fees are low. Everyone has a unique definition of what a "low"-fee market looks like depending on their own situation and preferences. Still, you can use explorers like [mempool.space](https://mempool.space/) for priority-based fee estimations and to [easily visualize trends over time](https://mempool.space/graphs/mining/block-fee-rates#1w).

If you don't want to actively watch the fee market for an opportune time to transact, use a tool like [txfee.watch](https://txfee.watch/) to setup email alerts whenever fees are currently high or low. You can even use that tool to set up more customizable automations that respond to the current fee market (e.g., flash your smart lights when fees drop).


# More Resources

- [High Fees? Bitcoin is Working As Designed](https://www.discreetlog.com/high-fees/)