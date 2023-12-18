---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Zeus v0.8.0 - Embedded LND Node, OLYMPUS, Zeus Pay & More.md","permalink":"/bit-devs/resources/notes/zeus-v0-8-0-embedded-lnd-node-olympus-zeus-pay-and-more/","title":"Zeus v0.8.0 - Embedded LND Node, OLYMPUS, Zeus Pay & More","tags":["bitdevs","bitcoin","lightning"],"noteIcon":"3","created":"2023-12-16T18:47:53.557-10:00","updated":"2023-12-17T19:38:03.124-10:00"}
---

# What is it?

[ZEUS](https://zeusln.com/) (operated by [@evankaloudis](https://twitter.com/evankaloudis)) announced the public release of v0.8.0 on the [Apple App Store](https://apps.apple.com/us/app/zeus-wallet/id1456038895?ref=blog.zeusln.com) and [Google Play](https://play.google.com/store/apps/details?id=app.zeusln.zeus&ref=blog.zeusln.com). ZEUS is one of several non-custodial Lightning wallets that leverages an [Lightning Service Provider](https://medium.com/breez-technology/introducing-lightning-service-providers-fe9fb1665d5f) (LSP) to abstract away most of the complexities of managing Lightning Network liquidity without sacrificing custody over the funds.

# Why is it cool?

> [!QUOTE] [New release: ZEUS v0.8.0](https://blog.zeusln.com/new-release-zeus-v0-8-0/)
> **Embedded node**
> 
> First and foremost, the new ZEUS features a new embedded LND node. This means that users no longer have to remotely connect to their own pre-configured lightning node back at home or in the cloud. Users simply hit 'Quick Start' on the intro screen and start syncing the blockchain in mere moments.
> 
> This node offers up nearly all the same functionality to users as they would have with a remote node: including lightning + on-chain sending and receiving, and channel management. Only the payment forwarding screens are disabled as mobile nodes are not conducive to routing.
> 
> While we expect most of our users to be using the embedded node moving forward, we remain committed to supporting remote connections for our original users.
> 
> **Our LSP: OLYMPUS by ZEUS**
> 
> Onboarding to lightning can be difficult and overwhelming to new users. So we've lowered the barrier to entry with a channel service from our new lightning service provider (LSP), OLYMPUS by ZEUS.
> 
> Users can generate invoices without having previously set up lightning payment channels, and have them paid and settled, nearly instantly, with our 0-conf channel service.
> 
> The LSP also provides added privacy to our users by providing them with wrapped invoices that conceal their nodes' public keys from payers.
> 
> The LSP is on by default, but users can choose to opt out of it. It is currently only available to use with embedded nodes, but we hope to extend functionality to remote nodes soon.
> 
> [Read more about our LSP here.](https://docs.zeusln.app/lsp/intro?ref=blog.zeusln.com)
> 
> **Self-custodial lightning addresses**
> 
> Here's where we take it up another level. With this release, we offering up a self-custodial lightning address that we're calling ZEUS PAY. This is the _first ever_ offering of a self-custodial lightning address in a mobile app.
> 
> ZEUS PAY leverages user-generated pre-image hashes, hodl invoices, and the [Zaplocker](https://github.com/supertestnet/zaplocker?ref=blog.zeusln.com) Nostr attestation scheme to allow users who may not be online 24/7 to receive payments to a static lightning address. Users just need to log in to their ZEUS wallets within 24 hours to claim the payments, otherwise they will be returned to the sender.
> 
> We hope that more wallets adopt this scheme to improve the UX for their users. But even without any updates, ZEUS PAY can easily receive payments from all lightning-enabled Bitcoin wallets _today._
> 
> We think this is a fantastic solution for service workers, nomads, dissidents, and others to accept tips and donations without sacrificing custody. We eagerly look forward to all the new people that are onboarded to Bitcoin with this new functionality.
> 
> ZEUS PAY is available, not only just to embedded node users, but also remote LND users.

# Controversy

Some controversy has arisen around ZEUS's self-custodial Lightning address implementation. In order to receive Lightning payments to a non-custodial LN address while offline (i.e., if you don't have the app open on your phone), ZEUS PAY leverages hold invoices (aka "hodl" invoices): 

> [!QUOTE] [Understanding Hold Invoices on the Lightning Network - Voltage](https://voltage.cloud/blog/lightning-network-faq/understanding-hold-invoices-on-the-lightning-network/)
> A Hold Invoice is an alternative type of invoice that triggers a different payment flow. **Instead of immediately settling the payment by revealing the payment pre-image to the sender, the Hold Invoice enables the receiver to lock the HTLC and delay (or even cancel) the act of revealing the payment pre-image to complete the payment. This allows recipients to accept Lightning payments at their discretion.** As mentioned previously, there is a finite period within which the recipient can reveal the invoice. If this specific timeframe is exceeded, the possibility of settling the payment is no longer viable.
> ---
> ## Drawbacks Of Hold Invoices
> Unfortunately, this feature doesn’t come without tradeoffs. Here are some of the drawbacks of using Hold Invoices.
> 
> **Liquidity Lock-up**
> Since HODL invoices essentially lock up funds in a transaction, intermediate nodes on the payment route may inadvertently lock their liquidity into payments that could take a long time to settle. This could potentially hinder their ability to route more payments, thereby reducing their operational efficiency and negatively impacting the overall liquidity of the network.
> 
> **Limit On Concurrent HTLC Payments**
> The Lightning protocol allows 483 concurrent HTLCs to conform with the standard transaction size. This implies that Hold Invoices can take up significant transaction space, even those involving small amounts.
> 
> **Trust In The Receiver**
> There’s a level of trust in the receiver to act appropriately by releasing the pre-image or not, based on other physical or virtual conditions. This adds an element of counterparty risk to the transaction, as the sender must trust that the receiver will behave as expected.

[![BitDevs-29-Zeus-Criticism-1.png](/img/user/para/artifacts/BitDevs-29-Zeus-Criticism-1.png)](https://x.com/TheBlueMatt/status/1716848494554595526?s=20)

[![BitDevs-29-Zeus-Criticism-2.png](/img/user/para/artifacts/BitDevs-29-Zeus-Criticism-2.png)](https://primal.net/e/note1h0lqfkm0neywkmsvuyv69gfgfa6pwmj6aay9vau804hrpgvlfkhqszvfj9)

[![BitDevs-29-Zeus-Criticism-3.png](/img/user/para/artifacts/BitDevs-29-Zeus-Criticism-3.png)](https://primal.net/e/note15mgqwjt32hkycxy3tu6738uzm0w9yh3tgmu6zrgv55cw9nqjwrssthazhg)

# More Resources

- [Zeus v0.8.0 - Embedded LND Node, OLYMPUS, Zeus Pay & More](https://www.nobsbitcoin.com/zeus-v0-8-0/)

![BitDevs-29-Self-Custodial-LN-Wallet-Comparison.jpg](/img/user/para/artifacts/BitDevs-29-Self-Custodial-LN-Wallet-Comparison.jpg)