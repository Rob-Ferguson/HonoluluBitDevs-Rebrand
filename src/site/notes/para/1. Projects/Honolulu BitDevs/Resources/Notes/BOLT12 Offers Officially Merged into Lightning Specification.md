---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/BOLT12 Offers Officially Merged into Lightning Specification.md","permalink":"/bit-devs/resources/notes/bolt-12-offers-officially-merged-into-lightning-specification/","title":"BOLT12 Offers Officially Merged into Lightning Specification","tags":["bitcoin","bitdevs","socratic-38","lightning"],"noteIcon":"3","created":"2024-10-26T13:11:28.706-10:00","updated":"2024-10-27T16:04:25.955-10:00"}
---



> [!QUOTE] [BOLT 12 | This is how we bitcoin in the future!](https://bolt12.org/)
> # What is BOLT 12?
> 
> BOLT 12 is a proposed upgrade to the Lightning network. For users, it can enable things like reusable payment requests, increased receiver privacy, and increased censorship resistance.
> 
> **Reusable Payment Requests**
> 
> Now that I can slap a QR code on our tip jar, my band can seamlessly receive tips in bitcoin! No more creating a new QR code for every virtual fan who wants to tip us after a moon colony gig, and no more losing 75% of potential tippers due to the long wait for BOLT 11 invoices.
> 
> > In this scenario, Alice just needs a payment identifier that doesn’t need to be changed or refreshed after each use. Her wallet creates an offer for her. She can then use the share tray and send it to a printer, then affix the printed QR code next to her band, in the same way that one might put a CashApp QR code on their tip jar.
> 
> **Receiver Privacy**
> 
> As a shadowy super coder contributing to Bitcoin Core, I needed a way to accept donations that preserves anonymity while compartmentalizing my 784 digital identities. With BOLT 12’s route blinding, I can now accept payments discreetly and securely!
> 
> > In this scenario, the user needs some extra privacy. By using route blinding, which could be provided as an optional service by the LSP, the user can publish the offer into the world without revealing their node’s pubkey. In theory, the user could create different offers for different sectors of their life, maintaing privacy and separation between these sectors.
> 
> **Social Integration**
> 
> I’m a content creator on Nostr who has always wanted a self-custodial way to accept zaps for my VR artwork. By publishing my bitcoin wallet’s payment code to my Nostr profile, I can receive zaps directly, without custodians or middlemen. Viva la BOLT 12!
> 
> > In this scenario, the user wants to receive self-custodial zaps on Nostr. While the current zaps implementation uses LNURL, there is not reason it could not be done with a BOLT 12 offer as well. For example, a BOLT 12 could be included in a `kind: 0` metadata note, AKA _the user’s profile_. From there, Nostr clients aware of BOLT 12 could attempt to pay using the offer instead of the LNURL data in Charlotte’s profile.
> 
> **Auto-withdrawals**
> 
> After hearing some cyborgs talk about bitcoin on XNBC Squawk Cube, I decided to buy in. Later, I learned that it's better to self-custody bitcoin rather than trust exchanges. So, I set my exchange account to automatically deposit bitcoin into a self-custodial wallet using BOLT 12 offers.
> 
> > Services such as [Swan](https://www.swanbitcoin.com/) allow you to setup automated recurring withdrawals of your bitcoin balance to your own wallet. Currently, this is implemented with a static on-chain address or an xPub. Imagine an exchange adding BOLT 12 offers to the list of accepted formats. Then users could have their balance auto-withdrawn to their own wallet, instantly spendable on lightning and without the onchain fees.
> 
> **Censorship Resistance**
> 
> As an activist living under an authoritarian robot regime, I needed a way to accept donations without payment services blocking my IP address. With onion messaging, my IP address remains hidden, ensuring I can receive support securely. Smash the autonomous patriarchy!
> 
> > Bitcoin payment schemes that rely on HTTP can be censored. One advantage of BOLT 12 offers is that they do not rely on web servers or HTTP requests. Instead, they use onion messaging. Furthermore, the offer can use a [BIP 353 payment identifier](https://github.com/bitcoin/bips/pull/1551), which looks like an email address and is easy to remember and share.

[![BitDevs-38-BOLT12-Dev-Integrations.png](/img/user/para/artifacts/BitDevs-38-BOLT12-Dev-Integrations.png)](https://bolt12.org/)

# Comparing BOLT 11 and BOLT 12
> [!QUOTE] [BOLT 12 | This is how we bitcoin in the future!](https://bolt12.org/)
> ## **BOLT 11: Lightning Invoices**
> 
> BOLT 11 is the first version of the BOLT protocol, and it is currently the most widely used protocol that includes a Lightning invoice and Keysend. A BOLT 11 invoice is a text string that consists of several parts, including the payment amount, the payment hash, and a set of metadata that describes the payment. The invoice is encoded in a way that allows it to be easily read and processed by both humans and machines.
> 
> An example of a lightning invoice is given below:
> ```
>lnbcrt500u1p3luztppp5gaww3eg6ghmtvzp8qr6af2wgx7ndt4mt9kpx4jmtwax77kt7ft6sdqqcqzpgxqyz5vqsp5sl5uprqe0zfu5mkjuypwfykrqt0ka2ap7dq9m6grzyuzflhn8kzs9qyyssqqw4ckhutfyayzc0cgeffhshpf3ln2z8svdt77pkyju7j5c9kjfxrmd68cdq0xdlf3gn6k3m70lx84nt0xsrs0erq400d4t0vtze32pqqeg8reh
>```
>
>One of the key features of BOLT 11 is that it allows for a high degree of flexibility in the way invoices are constructed. For example, it is possible to include additional data in the invoice, such as a description of the payment or a payment memo. This makes BOLT 11 invoices highly customizable, which is useful for merchants who want to provide their customers with a personalized payment experience.
>
>Another advantage of BOLT 11 is that it is backward compatible with older versions of the Lightning Network software. This means that it can be used with a wide range of [Lightning wallets](https://www.whatisbitcoin.com/learn/what-is-a-lightning-wallet) and [nodes](https://www.whatisbitcoin.com/learn/what-is-a-bitcoin-node), which makes it a popular choice for developers who are building Lightning applications.
>
>However, there are some limitations to the BOLT 11 invoice. One key limitation is that, unlike a [Bitcoin address](https://www.whatisbitcoin.com/learn/what-is-a-bitcoin-address), a Lightning invoice can **ONLY BE USED ONCE**. Additionally, an invoice needs to be created by the receiver specifying a fixed amount before funds can be sent – there’s no flexibility for the sender to specify the amount and recipient of a payment.
>
>...
>
>## **BOLT 12: Offers**
>
>BOLT 12 is the latest version of the BOLT protocol, and it was introduced in 2020. It is designed to address some of the limitations of BOLT 11 and provide a more robust and flexible solution for Lightning payments.
>
>BOLT 12 introduced alot of amazing features, one of which is **Offers**.
>
>Offers also involve generating invoices, however Offers are different from lightning invoices in that:
>1. They are reusable and hence can be used to receive payments from as many people as possible
>2. They can be used to receive payment, and they can also be used to request payment.
>
> ### **How Offers Work**
> 
> An “offer” has enough information that enables a user to fetch a real invoice from the vendor through the Lightning Network itself, just like it would send a payment: no web server needed. A wallet that scans an offer can then send a payment or, for a “send invoice” offer, the wallet sends an invoice that the other party pays. This means that offers can be **much smaller** than Lightning invoices and perform dual functions.
> 
> An example of an Offer invoice can be found below:
> ```
> lno1pg257enxv4ezqcneype82um50ynhxgrwdajx283qfwdpl28qqmc78ymlvhmxcsywdk5wrjnj36jryg488qwlrnzyjczlqs85ck65ycmkdk92smwt9zuewdzfe7v4aavvaz5kgv9mkk63v3s0ge0f099kssh3yc95qztx504hu92hnx8ctzhtt08pgk0texz0509tk
> ```
> To create an Offer, the recipient first creates an invoice with the details of the payment request, such as the amount, the recipient’s public key, and any optional metadata. They then sign the invoice using their private key, creating a pre-signed invoice that can be shared with potential payers.

[![BitDevs-38-BOLT-11-12-Comparison.png](/img/user/para/artifacts/BitDevs-38-BOLT-11-12-Comparison.png)](https://www.whatisbitcoin.com/lightning-network/bolt-11-vs-bolt-12)

# More Resources
- [Offers by rustyrussell · Pull Request 798 · lightning/bolts · GitHub](https://github.com/lightning/bolts/pull/798)
- [BOLT12: Offers Officially Merged into Lightning Specification](https://www.nobsbitcoin.com/bolt12-offers-officially-merged-into-lightning-spec/)
- [What Are Lightning Offers (BOLT 12) - The Bitcoin Manual](https://thebitcoinmanual.com/articles/lightning-offers-bolt12/)
- [Understanding BOLT 11 vs BOLT 12](https://www.whatisbitcoin.com/lightning-network/bolt-11-vs-bolt-12)
