---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/BoardwalkCash - Dollar-based ecash wallet leveraging nostr and Stable Channels.md","permalink":"/bit-devs/resources/notes/boardwalk-cash-dollar-based-ecash-wallet-leveraging-nostr-and-stable-channels/","title":"BoardwalkCash - Dollar-based ecash wallet leveraging nostr and Stable Channels","tags":["bitcoin","bitdevs","socratic-34","chaumian_ecash","lightning","custody","wallet"],"noteIcon":"3","created":"2024-05-16T19:46:14.857-10:00","updated":"2024-11-25T12:06:14.581-10:00"}
---



> [!QUOTE] [GitHub - MakePrisms/boardwalkcash](https://github.com/MakePrisms/boardwalkcash)
> # Boardwalk Cash
> 
> A Lightning / Cashu Ecash wallet designed for fast easy onboarding and use
> 
> ## Features
> - **Lightning Integration**: Send and Receive Lightning payments.
> - **Cashu Ecash Wallet**: Store balance locally as e-cash while at rest.
> - **Lightning Address**: Receive payments using an auto-generated Lightning Address.
> - **Nostr Wallet Connect**: Initiate payments from apps using NWC ([NIP-47](https://github.com/nostr-protocol/nips/blob/master/47.md))
> - **Nostr Wallet Authentication**: Seamlessly create app connections with NWA ([NIP-67](https://github.com/benthecarman/nips/blob/nostr-wallet-connect-connect/67.md))
> - **Prism Payments**: Use NWC to pay multiple invoices at once

[![BitDevs-34-BoardwalkCash-Prism-Announcement-X.png](/img/user/para/artifacts/BitDevs-34-BoardwalkCash-Prism-Announcement-X.png)](https://x.com/makeprisms/status/1790423585888280756)

[![BitDevs-34-BoardwalkCash-Disclaimer.png](/img/user/para/artifacts/BitDevs-34-BoardwalkCash-Disclaimer.png)](https://boardwalkcash.com/setup)

[![BitDevs-34-BoardwalkCash-Tony-X-1.png](/img/user/para/artifacts/BitDevs-34-BoardwalkCash-Tony-X-1.png)](https://x.com/tonklaus/status/1790460672897069527)

[![BitDevs-34-BoardwalkCash-Calle-Masterplan-Diagram.png](/img/user/para/artifacts/BitDevs-34-BoardwalkCash-Calle-Masterplan-Diagram.png)](https://x.com/callebtc/status/1770097016686645642)

# Stable Channels

Stable Channels is an open-source project that aims to bring **bitcoin-backed dollar balances to the Lightning Network**. The main idea is to match up two parties over a Lightning Channel - a "Stable Receiver" who wants less exposure to Bitcoin's price volatility against the US dollar, and a "Stable Provider" who wants more exposure to Bitcoin's price movements.

> [!QUOTE] [Stable Channels - peer-to-peer dollar balances on Lightning | Delving Bitcoin](https://delvingbitcoin.org/t/stable-channels-peer-to-peer-dollar-balances-on-lightning/875)
> **1. Introduction and background**
> 
> Good day, folks. I’d like to present an open-source project that I am working on called Stable Channels. The main goal of this project is to bring bitcoin-backed dollar balances to the Lightning network. Another goal is to bring more bitcoin and interest into Lightning.
> 
> Find this project on Github [here 2](https://github.com/toneloc/stable-channels/) and on Telegram [here](https://t.me/+jvZKrdM6XZFjZGMx).
> 
> **The TL;DR is that Stable Channels matches up BTC shorts (fiat stability seekers) and BTC longs (fiat stability providers) over Lightning Channels. Then, based on the updated BTCUSD price at each checkpoint, we settle sats very frequently so that each side gets what they want. In doing so, we create a bitcoin-backed synthetic dollar balance on the stable side of the channel. The other side is leveraged long.**
> 
> Stable Channels addresses a major impediment to bitcoin adoption: price volatility. In contrast to bitcoin, centralized stablecoins give users a stable store of value, and stablecoins are a huge and growing market. Despite this tremendous success, centralized stablecoins face systemic risks. Centralized stablecoins have external dependencies on centralized banks and bond custodians. They run the risk of hacks, bank runs, asset freezes, asset seizures, and forced closures.
> 

## How They Work

1. The two parties open a dual-funded Lightning Channel with equal Bitcoin amounts.
2. The Stable Channels software continuously monitors the BTC/USD price from multiple exchanges and settles sats between the parties every minute based on price changes.
   - If BTC price goes down, the Stable Provider pays the Stable Receiver to maintain their target stable dollar balance.
   - If BTC price goes up, the Stable Receiver pays the Stable Provider.
3. This continuous settlement creates a synthetic dollar balance on the Stable Receiver's side of the channel, while the Stable Provider gets leveraged Bitcoin exposure.

## Tradeoffs and Risks

- Requires both parties to be online and cooperative; non-cooperative actors can exploit the system.
- If Bitcoin price drops significantly, there may not be enough channel capacity to maintain the stable balance.
- Faces similar UX/operational challenges as regular Bitcoin/Lightning usage (node management, backups, fees, etc.)
- Potential free option problem and need for reputation/trust between counterparties.
- Complex implementation with various risk factors and attack vectors to mitigate.

# More Resources
- [GitHub - MakePrisms/boardwalkcash](https://github.com/MakePrisms/boardwalkcash)
- [uMint.cash](https://umint.cash/how#faq)
- [Stable Channels - peer-to-peer dollar balances on Lightning | Delving Bitcoin](https://delvingbitcoin.org/t/stable-channels-peer-to-peer-dollar-balances-on-lightning/875)
