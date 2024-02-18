---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Dual Funding Officially Merged into Lightning Network Specifications.md","permalink":"/bit-devs/resources/notes/dual-funding-officially-merged-into-lightning-network-specifications/","title":"Dual Funding Officially Merged into Lightning Network Specifications","tags":["bitdevs","bitcoin","socratic-31","lightning"],"noteIcon":"3","created":"2024-02-17T21:51:31.015-10:00","updated":"2024-02-17T22:20:13.426-10:00"}
---

[![BitDevs-31-DualFunding-Nifty-1.png](/img/user/para/artifacts/BitDevs-31-DualFunding-Nifty-1.png)](https://njump.me/nevent1qqsv49qx632j2tfhcf05ppcyltdppl9e7lyvw9jkhpycnngmll4gs8cpz3mhxue69uhhyetvv9ujumn0wd68ytnzvupzpj79aa4srj73l73vh9df2ncycwz6jdkp4phphwwvmuk0pa8tatxt94j75e)

# What is dual funding?

The "version 2 channel establishment protocol" is the underlying protocol that enables dual funding, which **allows for the creation of Lightning channels where both participants can contribute funds**. This means participants can immediately spend in either direction once the channel is opened, potentially balancing liquidity and splitting the channel opening costs. V2 channel establishment protocol may also be used for negotiating the opening of single-funded channels, but dual funding is the primary use case.

[![BitDevs-31-DualFunding-YT-Thumbnail.png](/img/user/para/artifacts/BitDevs-31-DualFunding-YT-Thumbnail.png)](https://youtu.be/i_GxmNZjwhk)

Dual funding is already supported in some Lightning Network implementations, like LND and Core Lightning, but without a formal [BOLT](https://github.com/lightning/bolts/blob/master/00-introduction.md) (Basis of Lightning Technology), implementations might not adhere to any specific standard. Now that Lisa's PR has been merged, implementations have clear guidelines on how to support this functionality in a consistent way.

Overall, dual funding in the Lightning Network allows for more flexible and balanced payment channels by enabling both parties to contribute funds, potentially improving the overall efficiency and functionality of the network.

# More Resources
- [interactive-tx: Add dual-funding flow, using the interactive tx protocol (feature 28/29) by niftynei · Pull Request #851 · lightning/bolts · GitHub](https://github.com/lightning/bolts/pull/851)
- [Dual funding | Bitcoin Optech](https://bitcoinops.org/en/topics/dual-funding/)
- [Breakdown: Dual Funded Lightning Channels | Voltage](https://voltage.cloud/blog/lightning-network-faq/what-are-dual-funded-lightning-channels/)