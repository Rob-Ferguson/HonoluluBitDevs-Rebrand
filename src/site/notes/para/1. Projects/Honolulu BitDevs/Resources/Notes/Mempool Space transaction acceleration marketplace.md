---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Mempool Space transaction acceleration marketplace.md","permalink":"/bit-devs/resources/notes/mempool-space-transaction-acceleration-marketplace/","title":"Mempool Space transaction acceleration marketplace","noteIcon":"3","created":"2023-05-28T15:27:12.235-10:00","updated":"2023-05-29T15:54:44.361-10:00"}
---



# Description

The [Mempool open source project](https://mempool.space/about) is an extremely popular [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Transaction Fees & The Mempool\|mempool]] and block explorer that can be self-hosted and connected to any bitcoin node. Mempool Space is a company that maintains the project and operates the commonly referenced [mempool.space](https://mempool.space/) instance. Because the Mempool Space team is so well-connected across the network, the primary mempool.space instance is often considered the de facto snapshot of bitcoin's global mempool state by many enterprises and individuals. 

At Bitcoin 2023, the [Mempool Space team announced a transaction acceleration marketplace](https://youtu.be/ebLpn_d133Y), which is set to officially launch later in the year. At the time of writing (for [[para/1. Projects/Honolulu BitDevs/Events/Socratic Seminar 22\|Socratic Seminar 22]]), the specific details of how this program works have not been released yet.

Generally, Mempool Space will establish business relationships with mining pools interested in participating in this service. Users will be able to top up their Mempool Space account with funds ahead of time, and if they come across a transaction they wish to accelerate, they can initiate it from the mempool.space interface. The transaction doesn't necessarily need to be your own - opening the possibility for others to accelerate transactions on your behalf through Mempool Space.

Users pay an additional fee using their existing balance on the platform, and Mempool Space then sends that transaction out-of-band to participating mining pools who will attempt to include that transaction in the next block. The acceleration fee paid by the user will be split in some way between Mempool Space and the mining pool who successfully mines the transaction into a block.

Transaction acceleration is not new and has been supported by some 3rd-party services for years (e.g., [ViaBTC](https://www.viabtc.com/tools/txaccelerator)). It can also be done natively on the bitcoin protocol with techniques like [replace-by-fee (RBF)](https://river.com/learn/terms/r/replace-by-fee-rbf) and [child-pays-for-parent (CPFP)](https://river.com/learn/terms/c/child-pays-for-parent-cpfp/). 

It seems that this service would target less-technical end users who may not be familiar with RBF/CPFP or users who were caught off guard by fee market fluctuations and want a quick and simple way to accelerate a transaction confirmation.

# Concerns

[![@1f52b_xyz_Tweet_MempoolFeeAcceleration_Drama.png](/img/user/para/artifacts/@1f52b_xyz_Tweet_MempoolFeeAcceleration_Drama.png)](https://nitter.at/1f52b_xyz/status/1659673323834408962#m)

Because these fee acceleration payments happen entirely out-of-band between Mempool Space and various mining pools, the individual miners within those pools can't audit and confirm that they're receiving the proper cut of those additional fees. Individual miners would have no insight into the acceleration fees that users are paying, so they'd have to trust that the pool operators are honestly divvying out those rewards as blocks are mined.

# More Resources
- [Mempool.Space Announces Transaction Acceleration Marketplace](https://www.nobsbitcoin.com/mempool-acceleration-marketplace-upcoming/)
- [Mempool Transaction Accelerator Reactions w/ Jeremy Rubin, Antoine Poinset (darosior) + niftynei](https://youtu.be/kndOXJn6AK8)
- [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Transaction Fees & The Mempool\|Transaction Fees & The Mempool]]