---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Silentium - Progressive Web App with Silent Payments.md","permalink":"/bit-devs/resources/notes/silentium-progressive-web-app-with-silent-payments/","title":"Silentium - Progressive Web App with Silent Payments","tags":["bitcoin","bitdevs","socratic-34","privacy","wallet"],"noteIcon":"3","created":"2024-05-18T12:41:34.067-10:00","updated":"2024-05-20T13:36:53.272-10:00"}
---



# Silentium

[Silentium](https://app.silentium.dev/) is a new PWA that leverages [BIP 352](https://bips.dev/352/) (also known as [Silent Payments](https://silentpayments.xyz/)). Silent Payments have relatively little adoption so far, with [Cake Wallet](https://cakewallet.com/) having the only other known implementation at the time of writing.

[![BitDevs-34-Silentium-Louis-X-Thread.png](/img/user/para/artifacts/BitDevs-34-Silentium-Louis-X-Thread.png)](https://x.com/TheSingerLouis/status/1790824126472667227)

# Silent Payments

> [!QUOTE] [SilentPayments.xyz Docs](https://silentpayments.xyz/docs/)
> **Silent Payments tl;dr**
> 
> **Silent Payments allow you to create a single, static address to share with friends, use for donations, or post for tips _without sacrificing privacy_**. When someone wants to send you a payment, they use the unique public key that is a part of your Silent Payment address, combine it with the public keys of the outputs they want to send and generate a unique, one-time address that looks on-chain just like any other Taproot address. The main advantages of Silent Payments are:
> -  **Simpler user experience**: users just need to worry about a single, static address instead of the hurdles of generating new addresses for every receive.
> -  **Better receiver privacy**: address re-use with Silent Payments is impossible, as no two senders can generate the same on-chain address.
> -  **Better sender privacy**: receivers have no way of connecting sends from the same receiver together, providing better privacy for even the sender.
> -  **No server required**: anyone with a wallet supporting Silent Payments can receive funds without address reuse, without communication, and without running complex infrastructure.

[![BitDevs-34-Silent-Payments-Benefits.png](/img/user/para/artifacts/BitDevs-34-Silent-Payments-Benefits.png)](https://silentpayments.xyz/)

> [!QUOTE] [SilentPayments.xyz Docs](https://silentpayments.xyz/docs/)
> In March of 2022 Ruben Somsen proposed “[Silent Payments](https://gist.github.com/RubenSomsen/c43b79517e7cb701ebf77eec6dbb46b8),” a new approach to reusable payment codes that **removes the need for a notification transaction (the major drawback of [BIP 47 payment codes](https://silentpayments.xyz/docs/comparing-proposals/bip47)) by entirely leveraging information that was already in the transaction to signal to the recipient when funds are intended for them.** Silent Payments makes use of advances in Bitcoin scanning to remove the need for a notification transaction, thereby improving scaling and privacy associated with reusable payment codes (with a key trade-off we’ll address later).
> 
> ## How they work
> 
> When Alice goes to send funds to Bob, **she takes three keys and creates a unique one-time address that only Bob controls the keys to**. These three keys are the **(1)** public key of the output(s) Alice wants to send to Bob, **(2)** Bob’s public key in his reusable payment code, and **(3)** a shared secret (generated using the Silent Payment public key and the user’s UTXO private key using [ECDH](https://en.wikipedia.org/wiki/Elliptic-curve_Diffie%E2%80%93Hellman)) that only Alice and Bob can know. **These three keys combine into a unique one-time Taproot address that Bob can then validate and spend from**, allowing Alice to generate practically infinite addresses without any communication with Bob. **The resulting unique, one-time Taproot address makes the payment appear exactly like any other Taproot payment on-chain, thereby preventing an outside observer from even knowing Silent Payments were used at all, much less link payments to a specific Silent Payment address.**
> 
> **When Bob wants to check for received funds, he looks on chain for a potential Silent Payments transaction, builds an aggregated key of all its inputs, and combines it with the private scanning key of his payment code. If the combination matches an output of that transaction, he can spend it.** If not, he can ignore that transaction and move on to the next, until he has scanned the entire set of potential Silent Payment UTXOs.
> 
> ---
> 
> ## Tradeoffs
> 
> **Because Bob cannot pre-generate addresses with silent payments, he needs to keep checking to find new payments from the point he generated the payment code. Because this scanning is relatively costly, Silent Payments require more compute and bandwidth when scanning than a standard Electrum-style server.** The average Bitcoin wallet today will have to connect to a new type of server that serves the necessary “tweak” data for a wallet to check each potential transaction for themselves.
> 
> The key difference with Silent Payment scanning is that instead of pre-generating a large amount of addresses up front like with a standard BIP 32 light client, **Silent Payments requires the wallet to download 33 bytes of data per potential output and then perform an ECDH calculation to check if it is owned by the user**. The major benefit to this approach is that it provides excellent privacy (even for light wallets) as the wallet back-end does not know what outputs belong to any light client.
> 
> Even though this may sound like a major hit to user experience, thankfully we can already drastically improve sync performance by ruling out potential outputs like:
> 1. Non-Taproot outputs
> 2. Taproot dust outputs <=1000sats (~85% of Taproot outputs right now)
> 3. All potential Silent Payments outputs spent since you last scanned
> 
> Additionally, there are many brilliant people working on reducing the impact of this tradeoff through things like transaction cut-through, [Silent Payments-specific indexes in Bitcoin Core](https://github.com/bitcoin/bitcoin/pull/28241#), and much more.

[![BitDevs-34-Silent-Payments-Multisig-X.png](/img/user/para/artifacts/BitDevs-34-Silent-Payments-Multisig-X.png)](https://x.com/_benma_/status/1792420181517750278)

# More Resources
- [BIP 352: Silent Payments](https://bips.dev/352/)
- [SilentPayments.xyz Docs](https://silentpayments.xyz/)