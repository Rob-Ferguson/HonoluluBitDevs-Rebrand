---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Privacy concerns from Ledger Live and security concerns from Ledger Connect Kit.md","permalink":"/bit-devs/resources/notes/privacy-concerns-from-ledger-live-and-security-concerns-from-ledger-connect-kit/","title":"Privacy concerns from Ledger Live and security concerns from Ledger Connect Kit","tags":["bitdevs","bitcoin","privacy","security","vulnerability"],"noteIcon":"3","created":"2023-12-14T19:27:12.109-10:00","updated":"2023-12-17T15:18:06.975-10:00"}
---

# What happened?

It's been a rough month for [Ledger](https://www.ledger.com/):
- [Someone noticed that Ledger Live sends a ton of user/device data to an outsourced data harvesting service.](https://www.nobsbitcoin.com/ledger-live-tracks-and-sends-out-all-user-information-by-default/)
- [There was an exploit on the Ledger Connect Kit, a Javascript library that implements a button allowing users to connect their Ledger device to third party DApps.](https://www.ledger.com/blog/a-letter-from-ledger-chairman-ceo-pascal-gauthier-regarding-ledger-connect-kit-exploit)

# Data Harvesting in Ledger Live

[![BitDevs-29-Ledger-Live-X-1.png](/img/user/para/artifacts/BitDevs-29-Ledger-Live-X-1.png)](https://x.com/rektbuildr/status/1732542258698694875?s=20)

From [@rektbuildr](https://twitter.com/rektbuildr)'s investigation, it looks like Ledger Live is hitting a third-party data collection endpoint (operated by [Twilio Segment](https://segment.com/)) to learn as much as possible about user activity - possibly "everything from screen views, to button clicks, error events, installs, uninstalls, etc. It's basically tracking everything. Anything you do on that app gets tracked".

> [!QUOTE] [Ledger Live data collection is more than a little concerning | Crypto.bi Forum](https://crypto.bi/forum/threads/ledger-live-data-collection-is-more-than-a-little-concerning.5/)
> The main question here is **why must hardware wallet vendors track their users?**  
> 
> We should be able to use hardware wallets without being tracked and monitored  
> 
> Hardware wallets should allow incognito operation. The wallet manufacturer does not need to receive an alarm every time you use the thing.  
> 
> **Hardware wallet manufacturers seem to be in the data collection business, not hardware wallet business**  
> 
> That explains why Ledger and Trezor analytics code is built into the core of their apps together with its basic functionality like device installation and update routines?  
> 
> Analytics would then be the business here and selling hardware wallets is secondary.  
> 
> Kinda like inkjet printers, the real profit is in selling cartridges. They might as well give the printers away.  
> 
> I have no idea how anyone thinks it's OK for any of these companies to get an alarm every time you click on a button, open the wallet, access a menu, send a transaction, install a new device and so on. This is crazy!  
> 
> Just so you're a little extra paranoid, if these apps have analytics all over them and you paste your mnemonic in the wrong place, it's gonna leak your mnemonic to an analytics package. Or worse.....it could "accidentally" leak it when pasted in the correct field as well....who knows, it's sending back a tsunami of data. You can't trust it. It has every menu, every text field, everything in the app wired up to view what you're doing.  
> 
> The thing is sending everything you do to the manufacturer. You just can't trust it. There should be ZERO phoning back in any of these hardware wallet apps. ZERO. It should not be sending anything out, only IN. When you REQUEST a device install, it sends you a firmware, that is all it should do. 
> 
> Hardware wallet apps should NEVER send anything OUT.

Unfortunately, Trezor also conducts similar user tracking via Trezor Suite, but it is opt-in, rather than opt-out:

> [!QUOTE] [Trezor Suite Data Analytics README](https://github.com/trezor/trezor-suite/blob/develop/docs/analytics/index.md)
> **Data Analytics**
> 
> [Anonymous](https://github.com/trezor/trezor-suite/blob/develop/docs/analytics/index.md#user-content-fn-1-6dda2c4bc0c9bb92f4f17a1f531a00b2) data volunteered by Trezor users directly contributes to improved performance across all the platforms you use Trezor Suite on.
> 
> Participation is easy and completely optional. Enable or disable usage data sharing with one click at any time in Trezor Suite Settings. With full control over what you contribute, you can safely take part in making Bitcoin more secure.
> 
> **TL;DR**
> 1. Data is only collected with explicit permission.
> 2. Your sensitive data is not collected.
> 3. We use AWS logging for data analytics and Sentry for error tracking.
> 4. We store the data concerning errors for the period of 90 days.
> 5. Only limited amount of users is able to access the data.

# Ledger Connect Kit Exploit

[Ledger Connect Kit](https://developers.ledger.com/docs/connectivity/connect-kit) is a tool that makes it easier for developers to connect DApps to Ledger hardware wallets. These app frontends typically have some sort of a button to connect to the wallet and interact with the smart contract - the Connect Kit is one method of handling that connection.

> [!QUOTE] [Ledger post with final timeline and customer update](https://twitter.com/ledger/status/1735326240658100414)
> - This morning CET, **a former Ledger Employee fell victim to a phishing attack that gained access to their NPMJS account**.
> - The attacker **published a malicious version of the Ledger Connect Kit** (affecting versions 1.1.5, 1.1.6, and 1.1.7). The malicious code used a rogue WalletConnect project to reroute funds to a hacker wallet.
> - Ledger’s technology and security teams were alerted and a fix was deployed within 40 minutes of Ledger becoming aware. The malicious file was live for around 5 hours, however we believe the window where funds were drained was limited to a period of less than two hours.
> - Ledger coordinated with [@WalletConnect](https://twitter.com/WalletConnect) who quickly disabled the the rogue project.
> - The genuine and verified Ledger Connect Kit version 1.1.8 is now propagating and is safe to use.
> - For builders who are developing and interacting with the Ledger Connect Kit code: connect-kit development team on the NPM project are now read-only and can’t directly push the NPM package for safety reasons.
> - We have internally rotated the secrets to publish on Ledger’s GitHub.
> - Developers, please check again that you’re using the latest version, 1.1.8.
> - Ledger, along with [@Walletconnect](https://twitter.com/WalletConnect) and our partners, have reported the bad actor’s wallet address. The address is now visible on [@chainalysis](https://twitter.com/chainalysis). [@Tether_to](https://twitter.com/Tether_to) has frozen the bad actor’s USDT.
> - We remind you to always Clear Sign with your Ledger. What you see on the Ledger screen is what you actually sign. If you still need to blind sign, use an additional Ledger mint wallet or parse your transaction manually.
> - We are actively talking with customers whose funds might have been affected, and working proactively to help those individuals at this time.
> - We are filing a complaint and working with law enforcement on the investigation to find the attacker.
> - We’re studying the exploit in order to avoid further attacks. We believe the attacker’s address where the funds were drained is here: `0x658729879fca881d9526480b82ae00efc54b5c2d`

[![BitDevs-29-Ledger-Connect-Exploit-X-1.png](/img/user/para/artifacts/BitDevs-29-Ledger-Connect-Exploit-X-1.png)](https://x.com/lopp/status/1735353894409052227?s=20)

[![BitDevs-29-Ledger-Connect-Exploit-X-2.png](/img/user/para/artifacts/BitDevs-29-Ledger-Connect-Exploit-X-2.png)](https://x.com/sethforprivacy/status/1735319674303255039?s=20)

In this particular case, Ledger was able to respond quickly to minimize damage. Interestingly, the malicious version that was draining funds added a [class name called `DrainerPopup`](https://x.com/LefterisJP/status/1735280230078509201?s=20), making it fairly obvious to someone watching the code.

# Takeaways

Historically, Ledger has a [bad track record for protecting user data and privacy](https://cointelegraph.com/news/ledger-data-leak-a-simple-mistake-exposed-270k-crypto-wallet-buyers), and the latest exploit also undermines their credibility as security experts. 

If you continue to use a Ledger, at least interact with it via some other wallet software than Ledger Live - e.g., [Sparrow](https://sparrowwallet.com/) is a great alternative. Unfortunately, there's still no way to easily update the firmware on a Ledger device without using Ledger Live. 

Similarly, if you use a Trezor with Trezor Suite, don't opt in to the data analytics (but you should really just use it with Sparrow instead).

For a bitcoiner wishing to protect their wealth, there are simply better options - take the time to research alternative signing devices (preferably bitcoin-only, like a [Coldcard](https://coldcard.com/)) and review [[para/1. Projects/Honolulu BitDevs/Events/Self-Custody Workshop\|self-custody best practices]].