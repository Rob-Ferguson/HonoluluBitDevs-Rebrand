---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/ACINQ launches Phoenixd and announces Phoenix Wallet withdrawal from US app stores.md","permalink":"/bit-devs/resources/notes/acinq-launches-phoenixd-and-announces-phoenix-wallet-withdrawal-from-us-app-stores/","title":"ACINQ launches Phoenixd and announces Phoenix Wallet withdrawal from US app stores","tags":["bitdevs","bitcoin","socratic-33","lightning","phoenix"],"noteIcon":"3","created":"2024-04-23T21:39:43.414-10:00","updated":"2024-04-28T19:27:42.123-10:00"}
---

# Phoenix stops support for US market

[![BitDevs-33-ACINQ-X1.png](/img/user/para/artifacts/BitDevs-33-ACINQ-X1.png)](https://x.com/acinq_co/status/1783878735168507972)

Citing regulatory uncertainty in the US following [the arrest and money laundering/unlicensed money transmitting charges against Samourai Wallet operators](https://www.justice.gov/usao-sdny/pr/founders-and-ceo-cryptocurrency-mixing-service-arrested-and-charged-money-laundering), ACINQ has announced that they will be removing Phoenix Wallet from US app stores starting **May 3, 2024**.

If you're looking for another non-custodial LN mobile wallet, consider [Mutiny](https://www.mutinywallet.com/) or [Zeus](https://zeusln.com/), who have both stated their intent to continue operations within the US. If you trust Liquid, then [AQUA](https://aquawallet.io/) might be another reasonable alternative.

# Phoenixd specialized LN node

[![BitDevs-33-Phoenix-X1.png](/img/user/para/artifacts/BitDevs-33-Phoenix-X1.png)](https://x.com/PhoenixWallet/status/1771236080680841668)

> [!QUOTE] [Phoenix for server | FAQ](https://phoenix.acinq.co/server/faq)
> ## What is `phoenixd`?
> 
> **`phoenixd` is a minimal, specialized Lightning node designed for sending and receiving Lightning payments.**
> 
> `phoenixd` uses the same software as the popular [Phoenix Wallet](https://phoenix.acinq.co/), but:
> - runs on a server instead of a mobile device
> - offers an [http API](https://phoenix.acinq.co/server/api) instead of a GUI
> - has fully automated liquidity management to facilitate receive-heavy use cases like merchants, crowdfunding, etc.
>  
> **`phoenixd` makes it very easy to develop any application that needs to interact with Lightning, by abstracting away all the complexity, without compromising on self-custody.**
> 
> ## Who is it for?
> 
> `phoenixd` is designed for developers/businesses who want to build on Lightning with minimum hassle and maximum reliability, without compromising on self-custody.
> 
> You can get ready in seconds, with **absolutely zero configuration, no channel management, no peer management, no liquidity management, no firewall configuration**.
> 
> ## What is the difference between `phoenixd` and `eclair`?
> 
> `eclair` is a highly scalable, general-purpose Lightning node designed for routing and managing a huge number of channels.
> 
> `phoenixd` is a minimal, specialized Lightning node designed for sending and receiving payments.

[![BitDevs-33-Phoenixd-Overview.png](/img/user/para/artifacts/BitDevs-33-Phoenixd-Overview.png)](https://phoenix.acinq.co/server)

> [!QUOTE] [Phoenix for server | FAQ](https://phoenix.acinq.co/server/faq)
> ## Auto Liquidity
> 
> **Liquidity management is fully automated.**
> 
> **It is based on the existing on-the-fly channel feature of Phoenix Wallet**, with two additional mechanisms:
> - `auto liquidity`: every time a channel increase is needed, a large amount of liquidity is requested
> - `fee credit`: to facilitate bootstrapping, small payments (too small to pay for a channel creation by themselves) are paid directly to the LSP, instead of being rejected, and will be deducted from future fees. The [fee credit is non-refundable](https://phoenix.acinq.co/server/auto-liquidity?ref=nobsbitcoin.com#important-note-about-the-fee-credit).
> 
> In other words, when receiving a payment, depending on the situation, the funds either:
> - go to your balance (normal scenario)
> - are used to purchase inbound liquidity immediately (once in a while)
> - are set aside to purchase inbound liquidity later (for small payments at bootstrapping).
>  
> From the outside, `phoenixd` is **always** accepting payments, resulting in **seemingly infinite inbound liquidity, with no threshold effect**. You do not have to worry about setting up liquidity, or minimal payment size.
> 
> By requesting liquidity in large chunks, the number of on-chain operations is reduced and mining fees are taken out of the equation, in exchange for higher upfront costs.

# More Resources
- [Phoenix Wallet to Stop Serving US Customers on May 3rd](https://www.nobsbitcoin.com/phoenix-wallet-to-be-removed-from-us-app-stores-on-may-3/)
- [Phoenixd: minimal, specialized Lightning node designed for sending and receiving payments](https://phoenix.acinq.co/server)
- [Phoenixd: Phoenix for Server](https://www.nobsbitcoin.com/phoenixd-released/)
- [GitHub - ACINQ/phoenixd](https://github.com/ACINQ/phoenixd)