---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Transaction Fees & The Mempool.md","permalink":"/bit-devs/resources/notes/transaction-fees-and-the-mempool/","title":"Transaction Fees & The Mempool","noteIcon":"3","created":"2023-05-26T23:38:14.650-10:00","updated":"2023-05-29T15:54:14.896-10:00"}
---



# Limited Block Space

Bitcoin block space is scarce (theoretical limit of 4 megabytes). The size of each block is kept relatively small to make it easier to run a bitcoin full node - decreased bandwidth and storage costs means a bitcoin full node can run on less powerful hardware in more remote locations around the world.

There is a limit to how many transactions can fit in each new block, and because of that, a queue forms of transactions waiting to get confirmed on chain. 

# Mempools

Each bitcoin node keeps track of unconfirmed transactions in a local database called the mempool. People generally refer to this constantly changing set of unconfirmed transactions as "*the* mempool", even though, technically, each node has its own version. 

As new transactions are discovered, nodes gossip with one another to share updates on the latest state of known, unconfirmed transactions. Every node has its own snapshot of these unconfirmed transactions, but they aren't necessarily the same because it takes time for updates to propagate through the network.

Miner nodes also have a mempool, and miners pull from that local database when constructing each new block. In other words, it doesn't matter much if a transaction is sitting in *your* mempool - it won't get mined unless it eventually propagates into a miner's mempool, either via normal P2P gossip or out-of-band communication directly to a miner.

> [!QUOTE] [Why do we have a mempool? | Bitcoin Optech 251](https://bitcoinops.org/en/newsletters/2023/05/17/#waiting-for-confirmation-1-why-do-we-have-a-mempool)
> - Many nodes on the Bitcoin network store unconfirmed transactions in an in-memory pool, or mempool. This cache is an important resource for each node and enables the peer-to-peer transaction relay network. 
> - Nodes that participate in transaction relay download and validate blocks gradually rather than in spikes. Every ~10 minutes when a block is found, nodes without a mempool experience a bandwidth spike, followed by a computation-intensive period validating each transaction. On the other hand, nodes with a mempool have typically already seen all of the block’s transactions and store them in their mempools. 
> - Mempools can also be used to build an independent fee estimator. The market for block space is a fee-based auction, and keeping a mempool allows users to have a better sense of what others are bidding and what bids have been successful in the past. 
> - However, there is no such thing as “the mempool”—each node may receive different transactions. Submitting a transaction to one node does not necessarily mean that it has made its way to miners. 
> - Some users find this uncertainty frustrating, and wonder, “why don’t we just submit transactions directly to miners?” Consider a Bitcoin network in which all transactions are sent directly from users to miners. One could censor and surveil financial activity by requiring the small number of entities to log the IP addresses corresponding to each transaction, and refuse to accept any transactions matching a particular pattern. 
> - This type of Bitcoin may be more convenient at times, but would be missing a few of Bitcoin’s most valued properties. Bitcoin’s censorship-resistance and privacy come from its peer-to-peer network. In order to relay a transaction, each node may connect to some anonymous set of peers, each of which could be a miner or somebody connected to a miner. This method helps obfuscate which node a transaction originates from as well as which node may be responsible for confirming it. Someone wishing to censor particular entities may target miners, popular exchanges, or other centralized submission services, but it would be difficult to block anything completely. 
> - The general availability of unconfirmed transactions also helps minimize the entrance cost of becoming a block producer—someone who is dissatisfied with the transactions being selected (or excluded) may start mining immediately. Treating each node as an equal candidate for transaction broadcast avoids giving any miner privileged access to transactions and their fees. 
> - In summary, a mempool is an extremely useful cache that allows nodes to distribute the costs of block download and validation over time, and gives users access to better fee estimation. At a network level, mempools support a distributed transaction and block relay network. All of these benefits are most pronounced when everybody sees all transactions before miners include them in blocks - just like any cache, a mempool is most useful when it is “hot” and must be limited in size to fit in memory.

# Fee Market

Because of the scarce nature of bitcoin block space and the fact that miners must perform work to construct new blocks, a fee market develops where users bid to get their transactions confirmed into upcoming blocks. Bitcoin transactions include a fee output which goes toward miner revenue. Miners generally search through their mempools and choose the transactions that provide the largest amount of fee revenue with a total data footprint that is under the bitcoin block size limit.

When authoring a new transaction, node runners can check their own mempool to see a snapshot of unconfirmed transactions (and associated fees) and then estimate a fee for their own transactions based on the relative priority of the payment and the overall mempool congestion - i.e., if there are a lot of unconfirmed transactions, users must attach a higher fee to increase the likelihood that time-sensitive transactions get confirmed more quickly. You have to outbid everyone else vying for block space at the same time. However, lower priority transactions can include a smaller fee with the assumption that it may take longer for a miner to eventually include it in a block.

In this way, a dynamic fee market emerges where people can pay higher fees to get their transactions confirmed more quickly, all via a free market mechanism without a central coordinator.

> [!QUOTE] [Bitcoin Transaction Fees and UTXO Management](https://www.discreetlog.com/utxos/)
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

# Fee Bumping

There are times where mempools become congested very quickly, and unconfirmed transactions get stuck with a too-low fee (potentially getting purged from mempools and never getting picked up by a miner). There are bitcoin-native mechanisms for dynamically adjusting fees for unconfirmed transactions (like [replace-by-fee (RBF)](https://river.com/learn/terms/r/replace-by-fee-rbf) and [child-pays-for-parent (CPFP)](https://river.com/learn/terms/c/child-pays-for-parent-cpfp/)), and there are [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Mempool Space transaction acceleration marketplace\|3rd-party transaction acceleration services]] that can pay miners out-of-band to get transactions confirmed sooner.

# More Resources
- [mempool.space FAQ](https://mempool.space/docs/faq#what-is-a-mempool)
- [High Fees? Bitcoin is Working As Designed](https://www.discreetlog.com/high-fees/)
- [Citadel Dispatch 101: Mempools and Transaction Fees with the Mempool Space Team - Wiz, Simon, and Steve](https://www.podpage.com/citadeldispatch/cd101-mempools-and-transaction-fees-with-the-mempool-space-team-wiz-simon-and-steve/)