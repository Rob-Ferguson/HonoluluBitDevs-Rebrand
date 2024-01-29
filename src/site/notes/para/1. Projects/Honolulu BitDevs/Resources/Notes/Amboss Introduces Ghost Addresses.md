---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Amboss Introduces Ghost Addresses.md","permalink":"/bit-devs/resources/notes/amboss-introduces-ghost-addresses/","title":"Amboss Introduces Ghost Addresses","tags":["bitdevs","bitcoin","socratic-30","lightning"],"noteIcon":"3","created":"2024-01-28T11:24:48.089-10:00","updated":"2024-01-28T12:16:15.372-10:00"}
---

# Overview

> [!QUOTE] [Introducing Ghost Addresses](https://amboss.tech/blog/ghost-addresses)
> The Ghost Address is Amboss’ latest innovation, which **combines the clever behavior of Phantom Payments with the user experience of the Lightning Address**. In combination, a Ghost Address enables any node to receive payments through invoices created using the Lightning Address protocol.
> 
> Invoices generated from a Ghost Address use Phantom Payments to allow the destination to intercept routed payments.
> 
> The result: a method of invoice creation that enables a lighter-weight solution to receive money. **A Ghost Address functions as a static, reusable endpoint that makes receiving payments into self-custody seamless and straightforward.**
> 
> ---
> 
> When a payer wants to pay to a Ghost Address, they will make a GET request to the ghst.to server, which provides a BOLT 11 lightning invoice.
> 
> **The `destination` in the invoice will be a Phantom Node, which technically does not exist.** Since the invoice destination does not exist in the network graph, Amboss will include a route hint in the invoice, which directs the payer to route the payment to the payee’s node and through a specific phantom channel.
> 
> The phantom channel is a clue to the payee that the payment that they would otherwise route is instead intended for them. This triggers the payee node to request the preimage from the Amboss API. **Using the preimage, the payee node can intercept the payment destined for the phantom node and claim the payment for themselves.**

![BitDevs-30-GhostAddress-Diagram1.png](/img/user/para/artifacts/BitDevs-30-GhostAddress-Diagram1.png)

![BitDevs-30-GhostAddress-Diagram2.png](/img/user/para/artifacts/BitDevs-30-GhostAddress-Diagram2.png)

# Benefits

- **Improved non-custodial LN Address UX**: Node runners can receive to a static LN Address without having to set up their own public-facing LN Address server.

- **Better privacy**: Custodial LN Addresses reveal most payment information to the custodian, allowing them to link much of your metadata together. Ghost Addresses reveal the amount of a payment to Amboss, but it doesn't include proof of that payment being completed. Amboss also can't see any details about subsequent withdrawals/payments.

- **Aligned with routing best practices**: Alternative approaches like [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Zeus v0.8.0 - Embedded LND Node, OLYMPUS, Zeus Pay & More\|Zeus Pay]] leverage Hodl invoices to lock up liquidity until the recipient comes back online - this has been shown to be detrimental to routing efficiency and reliability across connected routes, occasionally resulting in channel force closures. With Ghost Addresses, transaction settlement is immediate, which is a better UX and maintains a higher standard of conduct within the LN community.

# Drawbacks

- **Requires managing a sovereign LN node**: This tech is useful for those users who are running their own nodes and managing their own liquidity. The receiving node still must have enough inbound liquidity to actually receive payments to its Ghost Address. Ghost Addresses are also currently only configurable through [ThunderHub](https://thunderhub.io/).

- **The ecosystem must adapt to Phantom Payments**: Phantom Payments are relatively new and not well understood. Most nodes aren't yet equipped to properly track these types of payments from an accounting perspective, which could cause confusing UX (e.g., a received payment might bump the total balance without recording an explicit payment in the transaction history). Phantom Payments are also incompatible with [Multi-Path Payments (MPP)](https://river.com/learn/terms/m/multi-path-payment-mpp/), which are becoming increasingly common across wallet implementations.

# More Resources
- [Amboss Ghost Address Documentation](https://amboss.tech/docs/ghost)