---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/BOLT12 Offers Officially Merged into Lightning Specification.md","permalink":"/bit-devs/resources/notes/bolt-12-offers-officially-merged-into-lightning-specification/","title":"BOLT12 Offers Officially Merged into Lightning Specification","tags":["bitcoin","bitdevs","socratic-38","lightning"],"noteIcon":"3","created":"2024-10-26T13:11:28.706-10:00","updated":"2024-10-26T13:42:40.563-10:00"}
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

# More Resources
- [Offers by rustyrussell · Pull Request #798 · lightning/bolts · GitHub](https://github.com/lightning/bolts/pull/798)
- [BOLT12: Offers Officially Merged into Lightning Specification](https://www.nobsbitcoin.com/bolt12-offers-officially-merged-into-lightning-spec/)
- [What Are Lightning Offers (BOLT 12) - The Bitcoin Manual](https://thebitcoinmanual.com/articles/lightning-offers-bolt12/)
