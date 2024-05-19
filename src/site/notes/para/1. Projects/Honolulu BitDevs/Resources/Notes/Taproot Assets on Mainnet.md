---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Taproot Assets on Mainnet.md","permalink":"/bit-devs/resources/notes/taproot-assets-on-mainnet/","title":"Taproot Assets on Mainnet","tags":["bitcoin","bitdevs","socratic-34","lightning","tokenization","taproot"],"noteIcon":"3","created":"2024-05-18T15:45:11.916-10:00","updated":"2024-05-18T17:07:28.513-10:00"}
---



> [!QUOTE] [Taproot Assets | Builder's Guide](https://docs.lightning.engineering/the-lightning-network/taproot-assets)
> # Taproot Assets
> 
> **A Taproot-powered protocol for issuing assets on bitcoin that can be transferred over the Lightning Network for instant, high-volume, low-fee transactions.**
> 
> Taproot Assets (formerly Taro) is a new Taproot-powered protocol for issuing assets on the bitcoin blockchain that can be transferred over the Lightning Network for instant, high volume, low fee transactions. At its core, Taproot Assets taps into the security and stability of the bitcoin network and the speed, scalability, and low fees of Lightning.
> 
> Taproot Assets relies on Taproot, bitcoin’s most recent upgrade, for a new tree structure that allows developers to embed arbitrary asset metadata within an existing output. It uses Schnorr signatures for improved simplicity and scalability, and, importantly, works with multi-hop transactions over Lightning.
> 
> Throughout Bitcoin's history, there have been a number of proposals with regard to bringing assets to the Bitcoin blockchain. Taproot Assets advances those ideas by focusing on what Taproot enables in that realm. **With a Taproot-centered design, Taproot Assets can deliver assets on Bitcoin and Lightning in a more private and scalable manner. Assets issued on Taproot Assets can be deposited into Lightning Network channels, where nodes can offer atomic conversions from Bitcoin to Taproot Assets. This allows Taproot Assets to be interoperable with the broader Lightning Network, benefiting from its reach and strengthening its network effects.**
> 
> ---
> 
> Summary:
> 1. Allows assets to be issued on the bitcoin blockchain
> 2. Leverages taproot for privacy and scalability
> 3. Assets can be deposited into Lightning channels
> 4. Assets can be transferred over the existing Lightning Network

[![BitDevs-34-Taproot-Assets-Roasbeef-X-1.png](/img/user/para/artifacts/BitDevs-34-Taproot-Assets-Roasbeef-X-1.png)](https://x.com/roasbeef/status/1786043468164337951)

[![BitDevs-34-Taproot-Assets-Roasbeef-X-2.png](/img/user/para/artifacts/BitDevs-34-Taproot-Assets-Roasbeef-X-2.png)](https://x.com/roasbeef/status/1788624974728790471)

[![BitDevs-34-Taproot-Assets-Roasbeef-X-3.png](/img/user/para/artifacts/BitDevs-34-Taproot-Assets-Roasbeef-X-3.png)](https://x.com/roasbeef/status/1791171395336192174)

# How It Works

[![BitDevs-34-Taproot-Assets-Overview-Thumbnail.png](/img/user/para/artifacts/BitDevs-34-Taproot-Assets-Overview-Thumbnail.png)](https://youtu.be/-yiTtO_p3Cw?feature=shared)

> [!QUOTE] [Taproot Assets: Issuing Assets on Bitcoin - Voltage](https://voltage.cloud/blog/lightning-network-use-cases/taproot-assets-on-bitcoin-and-lightning-network/)
> ## WHAT IS TAPROOT ASSETS?
> 
> Taproot Assets relies on Bitcoin’s most recent upgrade, Schnoor-Taproot, to issue assets on top of Bitcoin. **It leverages Taproot to create a new tree-like structure that allows developers to embed asset data into a UTXO. It also uses Schnorr signatures to make the protocol simpler, scalable, and Lightning compatible.** This means that assets issued with this protocol can be deposited into Lightning Network channels, allowing Lightning nodes to offer atomic conversions from Bitcoin to Taproot Assets, benefiting from its network effects and instant, high-volume, low-fee transactions.
> 
> ![BitDevs-34-Taproot-Assets-Voltage-1.png](/img/user/para/artifacts/BitDevs-34-Taproot-Assets-Voltage-1.png)
> 
> Taproot Assets uses a special digital tree structure to quickly and privately access and update transaction information. It also uses another kind of tree to confirm that no extra assets are being created out of thin air. **People who use Taproot Assets must take care of the verification and storage costs by keeping the transaction information, or “witness data,” either on their personal storage devices or with external storage services called “Universes.”**
> 
> ![BitDevs-34-Taproot-Assets-Voltage-2.png](/img/user/para/artifacts/BitDevs-34-Taproot-Assets-Voltage-2.png)
> 
> **To ensure an asset is legitimate, they trace its entire history to its creation.** This is done by receiving a file containing all the transaction information through a communication system called the “gossip layer”. Users can compare this information with their copy of the transaction history and update it with their proofs when they transfer the asset.
> 
> **The main difference between Taproot transactions and usual Bitcoin transactions is the difference between a secret diary and a public billboard. With Bitcoin, all the instructions (or scripts) that control the coins are fully revealed on the public billboard (the blockchain) for everyone to see. With Taproot, these instructions are kept in a special private structure, like hidden notes in a secret diary, called the ‘tapScript branch’, which is only shown to specific parties in a transaction.**
> 
> These hidden instructions don’t need to be shown if you use a special spending mechanism called the ‘KeySpend’ to move the coins. It’s like having a secret key to a safe – if you have the key, you don’t need to know or show the safe’s combination. If the KeySpend path is not an option, only the part of the instructions used is shown on the blockchain, while all other possible instructions stay private.
> 
> This allows for more complex instructions without the extra burden of putting more data on the public billboard when using the KeySpend path. It also enables easier checking of the pruned instruction data. In the context of Taproot Assets, it’s like being able to attach extra secret notes to a transaction without showing these notes to the public.
> 
> ## TAPROOT ASSETS ON LIGHTNING
> 
> As discussed, Taproot Assets can be deposited and transacted in the Lightning Network. **This means that LN users can hold, send and receive payments using other assets besides BTC, such as a stablecoin. These payments can be routed over the Lightning Network without intermediary nodes needing to upgrade or opt-in.**
> 
> Taproot Assets-enabled channels can be created similarly to how Bitcoin channels are currently created. HTLCs for these Taproot Assets-aware payment channels are nested HTLCs that can be claimed by the recipient by revealing a preimage or by the sender after a timeout, just like a regular HTLC works.
> 
> **Usually, payment networks face a “chicken and egg” problem. Each time a new asset is created a new payment network is needed. It’s like building a new road system to accommodate a specific type of car. Taproot Assets presents a solution: It allows the Lightning Network to accommodate all types of assets in its channels, even finding routes across different assets. In the case of the Lightning Network and Taproot Assets, if all parties along a route are connected regarding liquidity, they can charge transaction fees in BTC or in the respective Taproot Assets being transferred.**
> 
> Interestingly, even if there’s no direct Taproot Assets route, a BTC route can substitute if the first node agrees to forward the Taproot Assets value in satoshis. This allows the LN to function as a platform for exchange between Bitcoin and Taproot Assets over the Lightning Network. 
> 
> **This feature enables one to receive a Taproot Asset but issue the corresponding invoice to any other Lightning wallet – even to those wallets that have not adopted the Taproot Assets Protocol – which could settle the invoice using BTC. This preserves the Lightning invoice as the universal standard for invoice schemes. An invoice-settled Taproot Assets could be paid by BTC or any other asset, enabling anyone with a Taproot Assets balance to settle any Lightning invoice.**
> 
> ![BitDevs-34-Taproot-Assets-Voltage-3.gif](/img/user/para/artifacts/BitDevs-34-Taproot-Assets-Voltage-3.gif)

# More Resources
- [Taro Explainer Video From Lightning Labs - YouTube](https://youtu.be/-yiTtO_p3Cw)
- [Taproot Assets on Lightning - YouTube](https://youtu.be/2h2MabzCN7M?feature=shared)
- [Tapping into Taproot Assets - YouTube Playlist](https://youtube.com/playlist?list=PL-3jjRT_28Sh3u_9CPVJkm8BLomh23QGk&feature=shared)
- [Taro: A New Protocol for Multi-Asset Bitcoin and Lightning](https://lightning.engineering/posts/2022-4-5-taro-launch/)
- [How Taro Brings Assets To Bitcoin Through Taproot And Lightning](https://bitcoinmagazine.com/technical/how-bitcoin-taro-protocol-works)
- ["Emergence of Token Layers on Bitcoin: Overview of Client-Side Validation, RGB, and Taro" slideshow from the Diamond Hands community](https://docsend.com/view/he8x9erkjmphphvn)
- [Exploring the Multi-Asset Issuance Mechanism of Taproot Assets](https://wublock.substack.com/p/exploring-the-multi-asset-issuance)

