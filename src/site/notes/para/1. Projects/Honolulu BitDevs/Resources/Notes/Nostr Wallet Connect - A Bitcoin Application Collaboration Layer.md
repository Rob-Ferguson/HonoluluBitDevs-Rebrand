---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Nostr Wallet Connect - A Bitcoin Application Collaboration Layer.md","permalink":"/bit-devs/resources/notes/nostr-wallet-connect-a-bitcoin-application-collaboration-layer/","title":"Nostr Wallet Connect: A Bitcoin Application Collaboration Layer","tags":["bitdevs","bitcoin","socratic-31","nostr","zap","lightning"],"noteIcon":"3","created":"2024-02-17T19:57:28.023-10:00","updated":"2024-02-19T13:34:12.665-10:00"}
---

# What is it?

> [!QUOTE] [Nostr Wallet Connect: A Bitcoin Application Collaboration Layer](https://bitcoinmagazine.com/technical/nostr-wallet-connect-a-bitcoin-application-collaboration-layer)
> The team behind Amethyst, a Nostr client, and Alby, the web based Lightning wallet, **created NWC in order to solve the problem of Nostr users wishing to integrate Lightning into their Nostr experience without having to use a special purpose wallet**. The application/protocol is based on Nostr’s identity architecture where every message (event) sent over Nostr is signed by a cryptographic keypair functioning as your identity on Nostr. This allows an application to simply generate a Nostr keypair, and from that alone have a cryptographic authentication mechanism to use in communicating with an external Bitcoin wallet to fulfill the functionality of the app.
> 
> ![BitDevs-31-NWC-Diagram.png](/img/user/para/artifacts/BitDevs-31-NWC-Diagram.png)
> 
> **Using the keypair to register the external application with the Lightning wallet, the application can now ping your wallet to initiate a payment.** The specification currently supports paying BOLT 11 invoices, making keysend payments (invoiceless payments made to a node’s public key), paying multiple invoices simultaneously, generating an invoice to present to someone else to pay you, and a few other functionalities to allow payment history and wallet balance queries from the external application.
> 
> **All of this is coordinated over Nostr**, allowing for a very redundant means of communication not dependent on a single centralized messaging mechanism or the user needing to depend on complicated software such as Tor or other protocols to facilitate the network connection between an application and wallet software or infrastructure running on their home network. Nostr also supports encrypted direct messages, meaning the communication between the wallet and the application is entirely private, revealing no details about payments being coordinated to the Nostr relays used to communicate.

> [!QUOTE] [NIP-47: Nostr Wallet Connect](https://github.com/getAlby/nips/blob/master/47.md#theory-of-operation)
> ## Theory of Operation
> 1. **Users** who which to use this NIP to send lightning payments to other nostr users must first acquire a special "connection" URI from their NIP-47 compliant wallet application. The wallet application may provide this URI using a QR screen, or a pasteable string, or some other means.
> 2. The **user** should then copy this URI into their **client(s)** by pasting, or scanning the QR, etc. The **client(s)** should save this URI and use it later whenever the **user** makes a payment. The **client** should then request an `info` (13194) event from the relay(s) specified in the URI. The **wallet service** will have sent that event to those relays earlier, and the relays will hold it as a replaceable event.
> 3. When the **user** initiates a payment their nostr **client** create a `pay_invoice` request, encrypts it using a token from the URI, and sends it (kind 23194) to the relay(s) specified in the connection URI. The **wallet service** will be listening on those relays and will decrypt the request and then contact the **user's** wallet application to send the payment. The **wallet service** will know how to talk to the wallet application because the connection URI specified relay(s) that have access to the wallet app API.
> 4. Once the payment is complete the **wallet service** will send an encrypted `response` (kind 23195) to the **user** over the relay(s) in the URI.

# Why is it cool?

Nostr Wallet Connect is a fully open source protocol that makes it much easier for developers to integrate Lightning payments into their applications without having to understand the intricate and complicated details typically associated with such integrations. It relies on the (semi-)decentralized network of nostr relays to handle all of the communication between an application and a user's wallet.

Although NWC focuses on Lightning wallet connections currently, its scope could easily be expanded to handle many other types of communication between multiple parties in any interactive protocol. For example, key holders in a multisig quorum could eventually pass around transaction data and PSBTs via NWC when performing signing ceremonies, or Discreet Log Contract (DLC) participants could receive signatures from an oracle directly over NWC in a consistent/standardized way. Ultimately, NWC is a mechanism that could replace many centralized coordinators by using nostr as a distributed communication layer instead of some centralized platform.

# More Resources
- [Alby Nostr Wallet Connect FAQ](https://nwc.getalby.com/about)
- [Introducing Nostr Wallet Connect](https://blog.getalby.com/introducing-nostr-wallet-connect/)