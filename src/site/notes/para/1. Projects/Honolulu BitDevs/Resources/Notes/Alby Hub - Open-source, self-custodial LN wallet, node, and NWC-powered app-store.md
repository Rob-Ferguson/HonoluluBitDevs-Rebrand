---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Alby Hub - Open-source, self-custodial LN wallet, node, and NWC-powered app-store.md","permalink":"/bit-devs/resources/notes/alby-hub-open-source-self-custodial-ln-wallet-node-and-nwc-powered-app-store/","title":"Alby Hub - Open-source, self-custodial LN wallet, node, and NWC-powered app-store","tags":["bitcoin","bitdevs","socratic-36","self-custody","wallet","lightning","nwc","nostr"],"noteIcon":"3","created":"2024-07-26T21:01:17.316-10:00","updated":"2024-07-26T21:22:46.462-10:00"}
---




> [!QUOTE]  [Alby Hub: Open-source, self-custodial LN wallet, node, and NWC-powered app-store](https://blog.getalby.com/what-is-alby-hub/)
> # What exactly is Alby Hub?
> 
> Alby Hub is a Lightning Network node app that lets you take full control of your bitcoin. **With a one-click setup, an intuitive interface, and the seamless integrations of dozens of Bitcoin apps, Alby Hub makes Lightning Network self-custody accessible to everyone.**
> 
> At its core, Alby Hub is a full fledged lightning node (LDK by default, supporting other backends), with a friendly web platform to manage it. Moreover, it’s **open-source and fully self-custodial** - only its owner knows the keys. The Hub **comes also with a Nostr Wallet Connect service**, which enables remote, easy and secure use of funds by various apps, whether Nostr social media clients or wallet interfaces. The Hub actually has embedded marketplace of suggested applications, that can be linked directly to **your** node.
> 
> Its software can be run by you on a desktop or a server or even on a Raspberry Pi for free, or in the **Alby Cloud for 21,000 sats per month**. This approach combines the security of self-custody with the convenience of a self-custodial Lightning wallet ready to be adopted by masses.
> 
> A node to be run anywhere, accessed from everywhere.
> 
> # Key Features and Benefits of Alby Hub
> 
>  - **Your Own Lightning Node:** a convenient app on top of popular lightning instances.
>  - **Self-Custody:** Alby Hub provides users complete ownership of their funds, secured by a 12-word seed phrase known only to the user.
>  - **Open-Source**: All Alby Hub code is available for review, ensuring transparency and allowing users to experiment or self-host for free if desired.
>  - **One-click install**: For those choosing the cloud hosting option, setting up your own Lightning node is as simple as a single click.
>  - **Easy access**: Access your Hub from anywhere within your browser, or use its wallet in the Alby Extension, the desktop or mobile app.
>  - **Simple channel management**: Integrated LSPs, a friendly interface and notifications give you full and smooth control over your channels in the network
>  - **Card top-ups**: Buy Bitcoin directly within the app using debit/credit cards and SEPA transfers to top-up your channels.
>  - **Flexibility**: Users can choose to self-host their Alby Hub at home, in a datacenter, or opt for Alby's cloud hosting service for convenience and reliability.
>  - **Always Online**: The Alby Cloud hosting option makes your node online 24/7, ensuring you never miss a transaction.
>  - **App Marketplace**: Connect your Hub to a diverse range of Bitcoin and Lightning apps, all while maintaining control over your funds.
>  - **Permission Management**: Control exactly what access each connected app has to your node, ensuring security and privacy.
>  - **Isolated balances:** Share your node liquidity with friends, create NWC app permissions with isolated balances
>  - **Developer-Friendly**: With API access, webhook support and NWC integration, Alby Hub encourages innovation and custom solutions for programmatic use of lightning.

# [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Nostr Wallet Connect - A Bitcoin Application Collaboration Layer\|Nostr Wallet Connect (NWC)]]

<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/bit-devs/resources/notes/nostr-wallet-connect-a-bitcoin-application-collaboration-layer/#why-is-it-cool" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



# Why is it cool?

Nostr Wallet Connect is a fully open source protocol that makes it much easier for developers to integrate Lightning payments into their applications without having to understand the intricate and complicated details typically associated with such integrations. It relies on the (semi-)decentralized network of nostr relays to handle all of the communication between an application and a user's wallet.

Although NWC focuses on Lightning wallet connections currently, its scope could easily be expanded to handle many other types of communication between multiple parties in any interactive protocol. For example, key holders in a multisig quorum could eventually pass around transaction data and PSBTs via NWC when performing signing ceremonies, or Discreet Log Contract (DLC) participants could receive signatures from an oracle directly over NWC in a consistent/standardized way. Ultimately, NWC is a mechanism that could replace many centralized coordinators by using nostr as a distributed communication layer instead of some centralized platform.


</div></div>


# More Resources
- [GitHub - getAlby/hub: Alby Hub - Your own lightning node connected to every app. Run anywhere. Become self-sovereign.](https://github.com/getAlby/hub)
- [Alby Hub: A One-Click Lightning Node Connected To All Your Bitcoin Apps](https://www.nobsbitcoin.com/alby-hub-intro/)
- [@getAlby on X](https://x.com/getAlby/status/1816106846832173379)
- [nwc.dev](https://t.co/a9gBWzMX0R)

