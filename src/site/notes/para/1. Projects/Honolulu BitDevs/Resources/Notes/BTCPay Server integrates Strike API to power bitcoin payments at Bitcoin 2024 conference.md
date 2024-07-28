---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/BTCPay Server integrates Strike API to power bitcoin payments at Bitcoin 2024 conference.md","permalink":"/bit-devs/resources/notes/btc-pay-server-integrates-strike-api-to-power-bitcoin-payments-at-bitcoin-2024-conference/","title":"BTCPay Server integrates Strike API to power bitcoin payments at Bitcoin 2024 conference","tags":["bitcoin","bitdevs","socratic-36","self-custody","wallet","lightning","payments"],"noteIcon":"3","created":"2024-07-27T14:48:31.374-10:00","updated":"2024-07-28T11:01:22.497-10:00"}
---



![BITCOIN IS THE MEDIUM OF EXCHANGE | BITCOIN 2024 Nashville - YouTube](https://youtu.be/fYndksqimiY)

> [!QUOTE]  [BTCPay Server integrates Strike API to power bitcoin payments at Bitcoin 2024 conference](https://strike.me/blog/btcpay-server-integrates-strike-api-to-power-bitcoin-payments/)
> Today we’re incredibly excited to announce a pilot program to bring local off-ramps to [BTCPay Server](https://btcpayserver.org/) utilizing the Strike API. Now, all BTCPay Server merchants can enjoy open, interoperable, instant, and cheap bitcoin payments with access to local currency settlement wherever Strike supports fiat currency balances. BTCPay Server’s integration with the Strike API allows any BTCPay Server merchant, anywhere Strike is available, to convert any portion of their bitcoin into supported local currency both at the point of transaction or anytime in the future.
> 
> Businesses typically have a unique but consistent challenge when it comes to accepting bitcoin payments. Unfortunately, we are not quite on a Bitcoin standard yet, and much of their overhead, staff, inventory, and supply payouts are still denominated in fiat, which can make accepting bitcoin payments seem like more of a challenge than a benefit. **Every merchant we’ve ever spoken to wants cheaper fees, faster settlement, cash finality, and open network interoperability.** The challenge is integrating bitcoin payments without interrupting their existing business operations. We want Bitcoin to be additive. With BTCPay Server’s utilization of the Strike API, we achieve exactly that.
> 
> Let’s walk through a practical example: Bitcoin 2024 in Nashville. The conference is hosting over 50 merchants, all of which want to interoperate with the bitcoin network and accept instant, cheap, cash final payments from the attendees. However, each merchant has their own needs. Some may accept all BTC and HODL forever, some may need to settle each payment in USD for accounting requirements, others may want to split their bitcoin exposure 50/50 to cover basic fiat denominated costs. The solution? Open source Bitcoin point-of-sale software with optional financial services that allow you to optimize for the experience your business needs.
> 
> That is why, we’re stoked to announce that **Strike will be processing all payments at the Bitcoin 2024 conference in Nashville**. Every merchant at Bitcoin 2024 will be using BTCPay Server with the power to cash out, choose USD settlement, and more. The power of open source software and open networks with the convenience businesses sometimes require.
> 
> [![BitDevs-36-BTCPay-Strike-Plugin.png](/img/user/para/artifacts/BitDevs-36-BTCPay-Strike-Plugin.png)](https://strike.me/blog/btcpay-server-integrates-strike-api-to-power-bitcoin-payments/)
> 
> BTCPay Server’s integration of the Strike API is simple, as it should be. **Any merchant running a BTCPay Server instance can sign up for a Strike Business account, generate an API key for their account from their Strike dashboard, plug it into BTCPay Server, and they’re done. Your business can now accept bitcoin payments in local currency or convert bitcoin into local currency, all settled directly into your account to your bitcoin or supported currency balance.** You can view your fiat or bitcoin balance in your Strike dashboard and do what you want with either of them.

[![BitDevs-36-BTCPay-Strike-Plugin-Announcement-X.png](/img/user/para/artifacts/BitDevs-36-BTCPay-Strike-Plugin-Announcement-X.png)](https://x.com/jackmallers/status/1816198651892355223)

> [!QUOTE]  [GitHub - Marfusios/strike-btcpayserver-plugin: Strike plugin for BTCPayServer](https://github.com/Marfusios/strike-btcpayserver-plugin)
> ### Features
> - Receiving lightning payments directly to Strike Wallet
> - BTC price hedge - settlement into fiat currency
> - Lightning Network liquidity managed by Strike
> 
> ### Usage
> - Visit [Strike Dashboard](https://dashboard.strike.me/login) and obtain API key. Select all scopes under **Account**, **Receiving payments**, **Currency exchange** and **Rates**.
> - Optionally select scopes under **Sending payments** to enable payments triggered by BTCPayServer (payouts, BOLT cards, etc.)
> > [!WARNING]  **Owner of this BTCPayServer instance can access your API key.** Therefore they could spend your Strike balance if **Sending payments** scopes are selected
> 
> ![BitDevs-36-BTCPay-Strike-Plugin-Usage-1.png](/img/user/para/artifacts/BitDevs-36-BTCPay-Strike-Plugin-Usage-1.png)
> 
> - Install Strike plugin from the `Manage Plugins` page (or ask a BTCPayServer admin)
> 
> ![BitDevs-36-BTCPay-Strike-Plugin-Usage-2.png](/img/user/para/artifacts/BitDevs-36-BTCPay-Strike-Plugin-Usage-2.png)
> - Then go to `BTCPayServer > Lightning > Settings > "Change connection" > "Use custom node"` and configure Strike connection. Follow this format: 
> `type=strike;currency=FIAT;api-key=xxx`
> Where xxx is your API key. Select **FIAT** if you want to automatically convert received bitcoins into fiat currency. Otherwise choose **BTC**.
> 
> ![BitDevs-36-BTCPay-Strike-Plugin-Usage-3.png](/img/user/para/artifacts/BitDevs-36-BTCPay-Strike-Plugin-Usage-3.png)

# More Resources
- [BTCPay Server Documentation | BTCPay Server](https://docs.btcpayserver.org/Guide/)
- [What is the Strike API?](https://strike.me/learn/what-is-the-strike-api/)
- [Introduction | Strike API Documentation](https://docs.strike.me/)

