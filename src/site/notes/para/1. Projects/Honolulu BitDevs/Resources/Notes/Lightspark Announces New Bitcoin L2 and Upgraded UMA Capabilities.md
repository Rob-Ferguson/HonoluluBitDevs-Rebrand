---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Lightspark Announces New Bitcoin L2 and Upgraded UMA Capabilities.md","permalink":"/bit-devs/resources/notes/lightspark-announces-new-bitcoin-l2-and-upgraded-uma-capabilities/","title":"Lightspark Announces New Bitcoin L2 and Upgraded UMA Capabilities","tags":["bitcoin","bitdevs","socratic-38","lightning","scaling"],"noteIcon":"3","created":"2024-10-26T13:45:47.781-10:00","updated":"2024-10-26T16:44:23.736-10:00"}
---



> [!QUOTE] [Lightspark Announces New Bitcoin L2 and Upgraded UMA Capabilities](https://bitcoinmagazine.com/business/lightspark-announces-new-bitcoin-l2-and-upgraded-uma-capabilities)
> At Lightspark Sync, Lightspark’s first partner summit on Thursday, the company announced new products and features that will allow users to make global payments with both bitcoin and fiat.
> 
> The company announced that it has launched an alpha version of Spark, a Bitcoin Layer 2 that’s interoperable with Lightning and that makes it cheaper to onboard users to a non-custodial Bitcoin layer.
> 
> The company also announced new capabilities for [UMA](https://www.uma.me/), the company’s open-source and regulatory compliant payment solution that makes sending money as simple as sending an email.
> 
> With UMA Extend, the Lightning Network can serve as a bridge between traditional banks globally, while with UMA Auth and UMA Request, UMA users can tip, pay subscription fees and make payments to merchants within apps.
> 
> [![BitDevs-38-Lightspark-Presentation-Image.png](/img/user/para/artifacts/BitDevs-38-Lightspark-Presentation-Image.png)](https://bitcoinmagazine.com/business/lightspark-announces-new-bitcoin-l2-and-upgraded-uma-capabilities)
> 
> # Spark — Lightspark’s Bitcoin Layer 2
> 
> **[Spark](https://spark.info/) is a Layer 2 protocol for Bitcoin that leverages statechain technology. In short, users can hold fractions of bitcoin off-chain, and transfer these by sending private keys to other users (rather than signing transactions with the keys).**
> 
> Lightspark created Spark to better support the onboarding of users to the Lightning Network, which normally requires an on-chain transaction for each payment channel as well as the locking up of some amount of bitcoin in these channels so users can send and receive transactions.
> 
> **The layer 2 was primarily borne from the frustration that the Lightspark team encountered in trying to create a non-custodial Lightning wallet for users.**
> 
> “Self-custodial Lightning wallets, especially at scale, just aren’t viable,” [Lightspark CTO Kevin Hurley](https://bitcoinmagazine.com/business/lightspark-enables-institutions-to-use-the-bitcoin-lightning-network) told Bitcoin Magazine.
> 
> ...
> 
> So, they built Spark, a Bitcoin Layer 2 that **offers users cheap, instant payments as well as a permissionless, unilateral exit to the Bitcoin base layer. It also enables offline receive, or the ability to receive bitcoin even when your device isn’t connected to the internet**.
> 
> **Besides statechains, Spark also utilizes atomic swap technology**. Its design is similar to that of [Mercury Layer](https://mercurylayer.com/) in that it enables the off-chain transfer of ownership of Bitcoin UTXOs while benefiting from near instant and fee-free transactions, according to Hurley.
> 
> Besides bitcoin, it’s also possible to issue and use stablecoins on Spark. Or you can issue stablecoins via [Taproot assets](https://docs.lightning.engineering/the-lightning-network/taproot-assets/taproot-assets-on-lightning), [LRC-20](https://delvingbitcoin.org/t/lrc-20-scalable-and-fast-tokenization-on-lightning/808) or [RGB](https://rgb.tech/) on the base layer and transfer them to Spark.
> 
> A unique dimension of Spark, though, is that the assets on the layer 2 are all UMA enabled.
> 
> “You can now have non-custodial users sending directly to the bank accounts of UMA Extend users,” said Hurley, mentioning one of the new functionalities of UMA addresses.
> 
> # UMA Extend
> 
> **UMA Extend integrates the Lightning Network with traditional banking systems, allowing users to make international bank transfers in seconds. With this new technology, UMA Extend users can send any other UMA Extend user a near instant cross-border payment from one bank to another over Lightning as easily as sending an email.**
> 
> “It’s designed to facilitate money movement across any currency,” Nicolas Cabrera, VP of Product at Lightspark, told Bitcoin Magazine. “I can be in Brazil sending my local currency, the Brazilian real, to a user based in Europe that wants to receive euros or someone in the US who wants to receive USD.”
> 
> The Brazilian reals leave the sender’s bank account, are converted into sats by the bank (or an entity like [Zero Hash](https://zerohash.com/), if the banks can’t touch crypto), which are then received by the recipient’s bank, which converts it back into euros, USD of whatever currency the recipient holds in their bank account. All of this occurs within 30 seconds or so, a radical shift compared to the two to three days it often takes for international money transfers to settle.
> 
> “This is the first time connecting the Lightning Network to traditional banking routes and bank systems,” Cabrera added.
> 
> UMA Extend utilizes **[Real-Time Payments (RTP)](https://www.theclearinghouse.org/payment-systems/rtp), which enables real-time payments for federally insured depository institutions in the United States**, and comparable services in the other countries in which UMA Extend is available. All banks in the US who use RTP support Extend. Currently, **Lightspark’s partners support on- and off-ramps for 44 fiat currencies in over 100 countries**.
> 
> The traditional financial institutions involved with these transactions will set the fees for the transactions, **which tend to range between 0.25% and 0.5% — significantly cheaper than the [6.35% customers often pay](https://remittanceprices.worldbank.org/sites/default/files/rpw_main_report_and_annex_q124_final.pdf) to make international remittance payments via traditional financial rails**.
> 
>  # UMA Auth
>  
>  At the event, Lightspark also introduced **UMA Auth. The technology leverages OAuth (Open Authentication) technology (the backend tech for when a website gives you the option to sign into a third-party app or website with Google or Facebook), an open-standard authorization protocol that provides users with secure access to a website or application.**
>  
>  UMA Auth was built using [Nostr Wallet Connect (NWC)](https://nwc.dev/), a protocol [developed by the team at Alby](https://remittanceprices.worldbank.org/sites/default/files/rpw_main_report_and_annex_q124_final.pdf). NWC now supports UMA features like cross-currency transactions and client app registration.
>  
>  ...
>  
>  “All you have to do is input your UMA address and then we form a connection to your Lightspark wallet straight from the application. That gives the app access to communicate with your wallet and push money in right from the application.”
>  
>  UMA Auth enables users to do everything from tipping their favorite artists to paying a subscription fee to paying a friend through their preferred messaging app.
>  
>  ...
>
>  # UMA Request
>  
>  **UMA Request is another new dimension of UMA, one that allows any UMA user to request a payment from another UMA user.**
>  
>  Merchants can use UMA Request to request payments via an invoice, which comes in the form of a QR code, for the product sold or service rendered. UMA Request also supports zero-sum invoices, through which invoice recipients can pay whatever amount they’d like.
>  
>  **“Previously with UMA, the sender initiated the payment, but we’ve flipped it around,”** said Vissamsetti.
>  
>  Another standout feature of UMA Request is that it ensures both parties involved in the transaction receive a record of the transaction.
>  
>  UMA Request makes purchasing items online — especially across borders — easier and cheaper than using credit cards.
>  
>  # Moving Forward
>  
>  Lightspark’s CEO David Marcus, the former president of PayPal, believes that it’s only a matter of time until more banks and platforms come to adapt new technologies like UMA Extend, UMA Auth and UMA Request.
>  
>  **“At the end of the day, if you build a more efficient network that enables global money movements to move faster, cheaper, in real time 24/7 with no blackout dates, then that's where money is going to flow and the financial system and the ecosystem players are just going to need to adapt to that,”** Marcus told Bitcoin Magazine.
>  
>  ...
>  
>  “We want to make this completely out in the open, **completely open-source**. Anyone can audit it, spin up their own versions if they want to,” he added.
>  
>  “We want this to be a collaborative thing where the community joins in, where they hopefully submit pull requests and help find things that they want to improve.”

> [!QUOTE] [Spark Docs](https://www.spark.info/)
> # Spark TLDR
> 
> Spark is a Bitcoin L2 that enables instant, dirt-cheap, and unlimited self-custodial transactions of bitcoin and tokens while also enabling users to send and receive natively via Lightning. It's open-sourced and secured by Bitcoin.
> 
> **Spark is purpose-built for payments, and as such enables the following:**
> - Native BTC
> - Full self-custody
> - Instant settlement
> - Extremely low fees
> - Native tokens (e.g. stablecoins)
> - Native Lightning interface without needing to run a Lightning node
> - Ability to scale to billions of users
> - 1/n trust assumptions (or minority/n) with the risk only at the time of transfer, not in perpetuity
> - Unconditional unilateral exits
> - Capital efficiency (no pre-funding, liquidity lockups, etc.)
> - Exists without the need for a new Bitcoin OPcode or any Bitcoin changes (although improves when they're available)
> 
> **What Spark is not:**
> - 100% trustless on day one
> - A new Bitcoin L2 launching a token
> 
> ...
> 
> Stablecoins are now gaining traction as a form of stable, digital money, albeit mostly centralized. They address the core need for stability as a suitable medium of exchange, and for some, serve as a novel form of mostly USD/fiat-denominated “bank accounts”. **While there are signs of promise, the current combination of fragmented networks with a proliferation of new stablecoins entering the market will have a hard time making a real dent at the scale of payment volumes taking place on legacy rails.**  
> 
> Self-custody wallets for payments are gaining solid traction, allowing developers to build novel experiences faster than ever. For end-users, it's becoming less about "crypto" and more about a simple payment or financial service experience. Being able to build and spin up wallets for users with minimal regulatory and compliance overhead is one of crypto's most significant advantages, just as the internet has made the development of non-linear breakthroughs possible.  
> 
> **Bitcoin is the only network that will likely be around on every timeline; it's the natural bedrock for a radically new global payment network. Yet, as it is, it can't scale to meet global demands because it's too slow and expensive. Lightning solves this for custodians, enabling ultra-fast and ultra-cheap BTC transactions. But once you want to onboard millions of users with self-custody wallets, Lightning's design makes scaling economically difficult, if not impossible.** The same is true when introducing stablecoins or any other assets. New protocols have emerged, but they haven't reached escape velocity; it's always too expensive and slow to scale.  
> 
> Spark is built to address Bitcoin and Lightning's remaining challenges, **focusing on scaling self-custody wallets and enabling stablecoins on Bitcoin**. Combining these two features unlocks Bitcoin's fullest potential, helping it become the SMTP for money (Bitcoin, stablecoin, fiat). Spark is simple to implement and use, dirt-cheap, and fully interoperable with the current Bitcoin ecosystem. With it, developers can build novel applications once thought impossible on Bitcoin.
> 
> # How does it work?
> 
> Spark brings together several concepts introduced to the Bitcoin community over the past few years and is **heavily inspired by Statechains**. With a lot of empathy, since we've gone through the same process ourselves, we'll take the time to explain each concept, making it as clear and enjoyable to read as possible. This section is still relatively high-level. For the technically savvy, we invite you to read our [technical overview](https://www.spark.info/#) which gets into the weeds of Spark.
> 
> **The general idea of Spark is that it allows assets on Bitcoin to be spent off-chain instantly. In Spark, the user sends funds into a shared-signature address, where the user retains full control of their funds and the ability to exit without any interaction from any other party. The participants of this address are the user and the Operators of Spark. When a user wants to transfer ownership of these funds, the Spark Operators adjust their keys so the new owner takes control, while the overall signature key remains static. The beauty of this is that at every moment, the current owner remains in full control of their funds and can exit at any time without needing permission from anyone. While users look to SOs to validate transactions by adjusting keys to reflect those transactions, the SOs do not assume control over users funds.**  
> 
> There are several ways to interact with Spark:
> 1. Move funds in and out of Bitcoin
> 2. Move funds within Spark to other users
> 3. Move funds in and out of Lightning
> 
> ...
> 
> # Moving funds into, within, and from Spark
> 
> Now that you're familiar with the key terms, we can dive into Spark and see how everything comes together. As mentioned earlier, there are a few ways to move funds in and out of Spark.
> 
> ## Bitcoin -> Spark
> 
> From your existing wallet, all you have to do is send some BTC to a deposit address shared by both you and the SE.  
> 
> Before you transfer funds into Spark, you and the SE will sign an exit transaction. This is so that if the SE ever goes offline, you can reclaim your funds on L1 to your preferred address. Once your deposit is confirmed on-chain, you're all set—congratulations, you now have funds on Spark!
> 
> ![Spark Diagram](https://www.spark.info/overview/multisig.svg)
> 
> ## Spark <-> Spark
> 
> You can transfer ownership of a leaf to other users within Spark by coordinating with the SE. A transfer is only considered valid when the receiver holds a fully signed Bitcoin transaction they can use to unilaterally exit.
> 
> ![Spark Diagram](https://www.spark.info/overview/receive.svg)
> 
> ## Lightning <-> Spark
> 
> Users within Spark can always send and receive payments directly via existing Lightning Network rails.  
> 
> Importantly, Spark users don't need to run a node, manage Lightning channels, or lock up liquidity themselves. This eliminates almost all the overhead associated with traditional Lightning operations while providing true offline receive, which isn't available in typical Lightning.  
> 
> All Lightning payments are facilitated by SSPs, who accept funds on Spark to send Lightning payments or receive Lightning payments in exchange for funds on Spark. These transactions are executed through atomic swaps, ensuring that neither the SSP nor the user is at risk of losing funds.
> 
> ![Spark Diagram](https://www.spark.info/overview/lightning.svg)
> 
> ## Spark -> Bitcoin
> 
> Spark is designed in a way that ensures users are able to exit to Bitcoin L1 whenever they want, without needing permission from anyone. There are two ways to exit Spark to L1:
> 
> ### The Cooperative Exit
> 
> This is the cheapest and fastest way to exit Spark. Similar to Spark-Lightning transfers, cooperative exits are executed through atomic swaps with an SSP, exchanging Spark funds for on-chain Bitcoin.
> 
> ![Spark Diagram](https://www.spark.info/overview/receive-l1.svg)
> 
> ### The Unilateral Exit
> 
> This represents the most pessimistic scenario and can occur at any time. While there doesn't need to be a specific reason to unilaterally exit, users might choose this option if a set of Spark Operators (SOs) goes offline or if they've lost confidence in the Spark Entity (SE) itself. Unilateral exits are more expensive than cooperative exits because more than one transaction needs to be published to prove ownership of the most recent state.
> 
> ![Spark Diagram](https://www.spark.info/overview/exit-l1.svg)
> 
> This solution requires no cooperation, and can be done by any user at any time. This is core to the design of Spark.

[![BitDevs-38-Spark-Ark-Comparison-X.png](/img/user/para/artifacts/BitDevs-38-Spark-Ark-Comparison-X.png)](https://x.com/_arshbot/status/1849901462991585758)

[![BitDevs-38-Spark-Tradeoffs-X.png](/img/user/para/artifacts/BitDevs-38-Spark-Tradeoffs-X.png)](https://x.com/super_testnet/status/1849868618915631366)

# More Resources
- [Spark Docs](https://www.spark.info/)
- [Lightspark · GitHub](https://github.com/lightsparkdev)

