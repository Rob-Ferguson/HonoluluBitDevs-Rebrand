---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Boltz BTCPay Plugin - Accept Lightning Payments Without Running a Node.md","permalink":"/bit-devs/resources/notes/boltz-btc-pay-plugin-accept-lightning-payments-without-running-a-node/","title":"Boltz BTCPay Plugin - Accept Lightning Payments Without Running a Node","tags":["bitcoin","bitdevs","socratic-38","scaling","lightning","liquid"],"noteIcon":"3","created":"2024-10-26T22:39:56.045-10:00","updated":"2024-10-26T23:56:02.281-10:00"}
---



> [!QUOTE] [⚡ Launching the Boltz BTCPay Plugin: Accept Lightning Payments Without Running a Node](https://blog.boltz.exchange/p/launching-the-boltz-btcpay-plugin)
> For those short on time, here is a rundown of the key features:
> - ⚡ “Nodeless” mode: any merchant using BTCPay Server (even on a shared BTCPay instance) can now accept Lightning - powered by [Liquid Swaps](https://blog.boltz.exchange/p/launching-liquid-swaps-unfairly-cheap) 🌊
> - 🤖 Autoswap to mainchain: when using Liquid Swaps, the BTCPay Plugin allows for triggering swaps back to the mainchain based on a set of preferences
> - 👛 Integrated wallet system: create or import Liquid/mainchain wallets
> - 🥕 Built on [Taproot](https://bitcoinops.org/en/topics/taproot/): fully leveraging the power of [Taproot Swaps](https://blog.boltz.exchange/p/introducing-taproot-swaps-putting)
> - 🙅‍♂️ Non-custodial: as with all Boltz products, all mentioned features are powered by Boltz Atomic Swaps, allowing merchants to stay in control of their money
> 
> ![Image](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fbe009e1c-4171-4f9c-91d5-18f6f5f7fe04_2552x1432.png)
> 
> # 🤔 The Problem
> 
> Running and managing a Lightning node is _no easy feat_. Or, as our CTO Michael [recently put it](https://x.com/Boltzhq/status/1838137180914364752): “Channel management is complex and inbound liquidity can be such an alien concept”. As an industry, we have slowly but surely come to accept that the Lightning Network may scale Bitcoin [differently than originally anticipated](https://blog.bitfinex.com/education/is-lightning-scaling-bitcoin-in-a-way-nobody-predicted/). “Running your own Lightning node” is not a realistic nor a recommended goal for many individuals and even for professionals like merchants alike.
> 
> As a consequence, most applications and use cases nowadays revolve around the concept of using someone else’s professionally managed Lightning node to send and receive payments on the Lightning Network. Unfortunately, this all too often means relinquishing custody of funds. For merchants using BTCPay, choices of accepting Lightning payments that do not require operating a Lightning node, are historically limited. [Various bugs](https://d11n.net/lnbank-vulnerability-recap) of custodial solutions in the past showed that custodial risk goes both ways: the custodian can be at risk of losing funds too.
> 
> Albeit being great products, today most solutions for merchants remain custodial and require setting up accounts with the service providers, some of which are only available in [specific countries](https://strike.me/faq/where-is-strike-available-wr/).
> 
> # 👇 What is the Boltz BTCPay Plugin?
> 
> The [Boltz BTCPay Plugin](https://github.com/BoltzExchange/boltz-btcpay-plugin) is set to change this by allowing any merchant using BTCPay Server to accept Lightning payments without operating a Lightning node. This is especially powerful for merchants using a shared BTCPay server, as the choice of decent non-custodial options for accepting Lightning payments is very limited.
> 
> From a technical perspective, the Boltz BTCPay Plugin acts as an advanced UI to control and monitor [Boltz Client](https://github.com/BoltzExchange/boltz-client), our [proven swap client](https://blog.boltz.exchange/p/launching-boltz-client), which it uses under the hood.
> 
> After installation, the plugin offers users two modi operandi:
> 
> ![Image](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F539adb0d-35c2-4b05-9213-f66f6798046e_1417x925.png)
> 
> “Rebalance”, the first mode of Boltz BTCPay plugin, is currently still in _closed_ beta ([message us](https://t.me/+YdK0sV1OaVJmZjM1) if you are interested in participating) and only available to merchants running their own BTCPay instance with their own Lightning node connected to it. It walks you through setting up Boltz Client’s [Autoswap](https://blog.boltz.exchange/p/guide-how-to-use-boltz-clients-autoswap) in a visual setup flow and finally takes over managing your Lightning node’s liquidity based on your configuration. Next to regular mainchain Submarine Swaps, users have the option to use [Liquid Swaps](https://blog.boltz.exchange/p/launching-liquid-swaps-unfairly-cheap) combined with [Chain Swaps](https://blog.boltz.exchange/p/dispatching-chain-swaps) for increased cost efficiency.
> 
> ![Image](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc1c0e2fc-3c67-45c9-90f2-4e6210ce0c86_1445x967.png)
> 
> “Rebalance” mode using Autoswap in action
> 
> “Nodeless”, the second mode of the plugin and the flagship feature of today’s launch, uses Boltz’s well connected Lightning nodes for processing incoming Lightning payments and swaps the funds to a Liquid wallet controlled by the merchant. It offers great cost planning security as swap fees rarely change and network fees on the Liquid network are reliably low (usually around 40 sats per swap). Finally, it avoids typical Lightning channel management issues like running out of inbound liquidity or unforeseen channel force closes or even potentially catastrophic events like corrupted channel state.
> 
> ![Image](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F897cdb6f-4b75-437e-ba5e-e40e94dee867_1493x978.png)
> 
> “Nodeless” mode in action, using Autoswap to move from Liquid back to the mainchain
> 
> We don’t want to draw any preliminary conclusions today as only time will tell, but we strongly believe that, from a cost-perspective, “nodeless” mode can be very competitive compared to the total costs of operating a Lightning node.
> 
> # 🚧 WIP
> 
> We labeled today’s launch “Open _**Beta”**_. Even though we tested meticulously and disabled features that were either known to have issues or not well-tested enough, we can’t guarantee absence of bugs. Do _**not**_ install and run the plugin if you expect things to be perfect. As a cautious approach, we recommend starting off by only enabling the plugin to take over Lightning payments while the behavior can be monitored and only enable it permanently once a certain confidence level is reached. You can find an overview of known limitations [here](https://docs.boltz.exchange/v/boltz-btcpay-plugin/limitations).

# More Resources
- [GitHub - BoltzExchange/boltz-btcpay-plugin: Boltz BTCPay Plugin](https://github.com/BoltzExchange/boltz-btcpay-plugin)
- [Boltz Docs](https://docs.boltz.exchange/boltz-btcpay-plugin)
- [BTCPay Boltz Plugin Beta Telegram group](https://t.me/+YdK0sV1OaVJmZjM1)

