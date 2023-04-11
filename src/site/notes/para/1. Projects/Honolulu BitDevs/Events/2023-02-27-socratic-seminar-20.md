---
{"dg-publish":true,"permalink":"/para/1-projects/honolulu-bit-devs/events/2023-02-27-socratic-seminar-20/","title":"Socratic 20","tags":["bitdevs, socratic-20, bitcoin, resource"],"noteIcon":"2","created":"2023-02-18T14:14:24.182-10:00","updated":"2023-04-06T10:53:21.223-10:00"}
---


<< [[para/1. Projects/Honolulu BitDevs/Events/2023-01-30-socratic-seminar-19\|2023-01-30-socratic-seminar-19]] | [[para/1. Projects/Honolulu BitDevs/Events/2023-04-10-socratic-seminar-21\|2023-04-10-socratic-seminar-21]] >>

# Announcements

- Respect people’s privacy
- [Chatham House rules](https://www.chathamhouse.org/about-us/chatham-house-rule)
- [Join our telegram group](https://t.me/+Uh9gbHO9EHFkZWJh)
- [Follow us on Twitter (@HonoluluBitcoin)](https://twitter.com/HonoluluBitcoin)
- [Donate sats](http://honolulubitdevs.com/donate)
- Sponsor shoutout
	- Hawaii Technology Development Corporation
	- Entrepreneurs Sandbox

# Geopolitics/Market

- [Mississippi & Missouri lawmakers introduce bills to protect the rights to mine bitcoin and run a node](https://bitcoinmagazine.com/legal/mississippi-missouri-bills-to-protect-bitcoin) ([[para/3. Resources/Highlights/Mississippi, Missouri Lawmakers Introduce Bills To Protect The Rights To Mine Bitcoin And Run A Node\|Obsidian Link]])
	- Lawmakers from the U.S. states of Mississippi and Missouri have introduced bills that seek to **legally protect their citizens’ rights to run a Bitcoin node and to mine BTC**
	- The bills also have language prohibiting:
		* Political subdivisions of the state creating requirements which are not in line with other data center requirements, and changing the zoning of bitcoin miners without proper notice
		* Outlawing of discriminatory energy rates directed at bitcoin miners
		* Sound ordinances directed at mining facilities that are not in-line with other sound ordinances within the community
		* Operating nodes or miners being considered the act of money transmitting
- [Wyoming legislature passes bill protecting bitcoin private keys from courts](https://bitcoinmagazine.com/legal/wyoming-legislature-bill-protecting-private-keys) ([[para/3. Resources/Highlights/Wyoming Legislature Passes Bill Protecting Bitcoin Private Keys From Courts\|Obsidian Link]])
	- The U.S. state of Wyoming has passed a bill that protects its citizens from having to disclose their private keys
	- The bill states that “No person shall be compelled to produce a private key or make a private key known to any other person in any civil, criminal, administrative, legislative or other proceeding in this state that relates to a digital asset, digital identity or other interest or right to which the private key provides access unless a public key is unavailable or unable to disclose the requisite information with respect to the digital asset, digital identity or other interest or right.”
	- The bill has been approved by the state Senate and House of Representatives and now needs to be signed by the Governor in order to take effect

# Technology

- [Bitcoin Core maintainer Marco Falke steps down](https://www.nobsbitcoin.com/marco-falke-steps-down/)
	- **Quality assurance and testing maintainer** for Bitcoin Core for **7 years**
	- Didn't provide a specific reason other than saying "being a maintainer is no longer a good fit for me personally."
	- Several other maintainers have also stepped down over the last few years, **often citing increasing legal risk as a motivating factor**
	- There are only **4 Bitcoin Core maintainers left**: Hennadii Stepanov, Michael Ford, Andrew Chow, and Gloria Zhao
	- Each maintainer specializes in a given area of the code, so it's reasonable to assume a new QA/test maintainer may join soon
	- New maintainers are [generally nominated by someone in one of the weekly IRC meetings and all the attendees vote](https://bitcoin.stackexchange.com/questions/99674/how-do-devs-decide-who-should-have-commit-access-what-is-the-process) - semi-informal, but nominees and most attendees are generally well-known/prominent devs in the space
		- A newcomer likely wouldn't get nominated or accepted
- [Coinkite launches preorders for new bitcoin hardware wallet COLDCARD Q1](https://bitcoinmagazine.com/business/coinkite-new-bitcoin-wallet-coldcard-q1) ([[para/3. Resources/Highlights/Coinkite Launches Its New Flagship Bitcoin Hardware Wallet Coldcard Q1\|Obsidian Link]])
	- Coinkite is launching a higher-end, **battery-powered** COLDCARD, featuring a full **QWERTY keyboard**, a **4x larger LCD screen**, **2 microSD card slots**, and a **QR code scanner**
		- Addition of a AAA battery pack makes it much easier to store in remote/less accessible locations
			- Before this, if you didn't have close access to a power outlet where you store your COLDCARD, you'd have buy a battery adapter + battery to use power it on remotely
		- NVK was hesitant to add QR support until they found an affordable, security-focused way to implement it
			- The Q1’s QR scanner is a specialized module that sits at the top of the unit and is connected to the COLDCARD internally using a basic, 2-wire serial port
			- According to Coinkite, this ensures "there is less danger of scanned data doing more than it seems."
			- It uses an optimized grocery store scanner with an LED flashlight, which theoretically allows users to easily scan QRs under less-optimal lighting conditions (useful for those mountain men storing their COLDCARDs deep in a cave somewhere)
		- The full keyboard is intended to make it much easier to enter BIP39 passphrases on the device
			- Would be worried about wearing down the lettering on individual keys for frequently used passphrases, potentially making it easier to decode if someone accessed the device
	- It borrows some core features included in the Mk4: **same dual multi-vendor secure element setup, NFC compatibility, USB virtual disk mode, USB-C connector**, etc.
	- The new COLDCARD Q1 is available for **pre-sale at $199** with a planned release in **Q4 2023**
		- The Mk4 currently retails for ~$150, so the pre-sale price is a pretty good deal - not sure what the regular price will be post-launch
- [Breez's new SDK enables non-custodial "Lightning as a Service" integration for developers](https://medium.com/breez-technology/lightning-for-everyone-in-any-app-lightning-as-a-service-via-the-breez-sdk-41d899057a1d) ([[para/3. Resources/Highlights/Lightning for Everyone in Any App - Lightning as a Service via the Breez SDK\|Obsidian Link]])
	- Breez wallet in its current form:
		- Breez is a **"swiss army knife"** LN wallet - it does a lot of different things relatively well (regular LN wallet, podcasting 2.0 player, point-of-sale terminal, etc.)
		- It's been in beta since its launch a few years ago - all its functionality has essentially been a **proof-of-concept on what you can do with Lightning**
		- Breez is unique in that it **runs an entire Lightning node on your phone with the keys stored locally** and controlled by the user, but the liquidity **management is done by Breez** as a Lightning Service Provider (LSP)
		- The problem with that model is that **the app has to be open** for the node to stay in sync with the network, so if you don't use it for a few days, you'll have to wait for it to sync when you open the app before you can send/receive payments
	- In the background, Breez has been working on a different model (called **Breez Cloud**) and an entirely separate app leveraging this new model (called "sea breez"?)
		- Breez Cloud uses [Blockstream's Greenlight](https://blockstream.com/lightning/greenlight/) to **offload the node hosting and provisioning to Blockstream**, while the Lightning liquidity management is still handled by Breez
		- This removes the need to run the Lightning node on the mobile device where the app is running - **allowing that computation to be offloaded** to Blockstream's much-more-capable server infrastructure
	- Breez's new SDK takes that concept a step further - **wrapping access the same infrastructure model in a set of API calls that are opened up to any developer** to use in any application
	- The open-source Breez SDK enables developers to integrate Lightning and bitcoin payments into their apps with **zero learning curve or technical expertise**
	- It’s an end-to-end, non-custodial, drop-in solution powered by Blockstream's Greenlight, including a built-in LSP, on-chain interoperability, fiat on-ramps, and other services users and operators need
	- **Key benefits**:
		- It's end-to-end: **no assembly required**
			- Developers can delegate a lot of complexity back to Breez
			- Developers need to add a few abstracted API calls to their apps, and Breez handles all node creation, channel management, etc.
		- It's trustless: **no custody**
			- All peers maintain custody of their own money at all times
			- Breez SDK users get provisioned their own nodes on-demand via Greenlight
			- Users maintain control of private keys and authorize apps to access the Greenlight node when money needs to move
		- It's frictionless: **no KYC/AML**
			- Breez SDK enables P2P payments, so developers never have to touch the users' money directly
			- No KYC/AML, money transmitter licenses, or 3rd-party fiat payment processors required
		- It's interoperable: **no wallets**
			- Users see one balance accessible from any app on any device
			- Various services can be separately authorized to tap into the same Greenlight node
		- It's global: **no borders**
			- Non-custodial lightning wallets circumvent the regulatory hurdles associated with different geopolitical jurisdictions
	- **Tradeoffs**:
		- **Privacy concerns**
			- Blockstream is running the infrastructure, but (I think) all communication with the node happens via E2E encrypted channels
			- Blockstream can still see some metadata 
			- Breez handles liquidity management, so they know balances and payment information
- [Voltage announces Flow 2.0: A new LSP focused on just-in-time liquidity](https://voltage.cloud/blog/voltage-announcements/introducing-flow-v2/) ([[para/3. Resources/Highlights/Introducing Flow v2 - A New LSP Focused on Just In Time Liquidity\|Obsidian Link]])
	- The initial version of Flow was released over a year ago and was created as an easy way to purchase persistent channels of a given size to help users get inbound (and outbound) capacity
	- Flow 2.0 is an upgrade to **provide liquidity at the exact moment it is needed** - a receiver can have zero liquidity and still receive payment via Voltage’s liquidity
	- Flow 2.0 is a noncustodial way to easily receive Lightning payments without thinking about channels
	- By leveraging **zero-confirmation channels and preimage hashes**, they can determine on the fly if a new channel is required, open it instantly if necessary, and send the payment to the receiver without ever taking custody of funds
	- This LSP is **available for use today on testnet with mainnet coming soon**
	- **How it works**:
		* The Receiver generates an invoice on their node.
		* The Receiver sends their invoice to the Voltage LSP.
		* The Voltage LSP returns a new invoice with the same preimage hash but the LSP Pubkey.
		* Receiver gives this new ‘Wrapped Invoice’ to the Sender.
		* The Sender pays the invoice which goes to the LSP.
		* The LSP detects the payment and opens a zero-conf channel to the Receiver.
		* The LSP forwards the payment to the receiver and the payment is completed.
	* **Key benefits**:
		* The Wrapped Invoice uses the same preimage hash as the original invoice, which means the LSP can’t settle the payment without the final Receiver completing the payment
		* The invoice that’s given to the Sender contains the Voltage LSP’s public key meaning an increase in privacy for the Receiver
			* The Voltage LSP knows the Receiver but no one else does
		* This method works even if the Receiver has 0 channels
			* There is no requirement to have any kind of liquidity established, you can start from a brand new node.
	* Think this is **basically how Breez operates** today
		* Instead of hosting a node locally or deferring node management to Blockstream via Greenlight, **Voltage does both the node provisioning/hosting + the Lightning channel liquidity management**
- [Strike's API is now publicly available: Businesses and developers can easily use the lightning network for payments](https://www.nobsbitcoin.com/strike-launches-sending-api/)
	- Strike's Sending API documentation is now public
	- Users can leverage the API to send USD payments over lightning network rails
	- No stablecoins - lightning network is used to move value, which is automatically converted to USD on either end
	- "No need to own/spend bitcoin, stomach volatility, encounter taxable events, handle added accounting, or take on any legal/compliance headaches"
	- List of [example applications](https://docs.strike.me/walkthrough/example-apps/) in the documentation
	- Leveraging this API requires access to Strike and comes with the **typical KYC/AML constraints** (e.g., can't be used in Hawaii)
	- Dollar liquidity has to be managed by Strike in their app, but the bitcoin side connects to the open Lightning network
- [BlueWallet is sunsetting LNDhub.io and is no longer supporting custodial Lightning wallets](https://bluewallet.io/sunsetting-lndhub/) ([[para/3. Resources/Highlights/Sunsetting Lndhub.io\|Obsidian Link]])
	- Lightning wallets in BlueWallet have historically been custodial by default, leveraging their own [LNDhub](https://bluewallet.io/lndhub/) instance to provide separate accounts for individual BlueWallet users
	- BlueWallet is **shutting down their LNDhub instance** on **April 30th**, meaning any users that have sats on BlueWallet's lightning node need to move their funds to a different wallet before that deadline
	- In the interim, BlueWallet LN **users can still withdraw sats, but creating new or refilling existing lightning wallets on their LNDHub node is no longer possible**
	- LNDHub itself is still a [FOSS project](https://github.com/BlueWallet/LndHub) and **users can continue to spin up their own instance as a self-hosted solution**
	- BlueWallet users will always be able to connect to their own LNDHub from BlueWallet or other software that supports the LNDHub API spec (i.e., self-hosted LNDHub users are unaffected by this news)
	- A few **good alternatives**: [Muun](https://muun.com/), [Breez](https://breez.technology/), [Phoenix](https://phoenix.acinq.co/), [Zeus](https://zeusln.app/)

# Mining

- [Fedipool: Fedimint could mitigate bitcoin mining pool concerns](https://www.discreetlog.com/fedipool/) ([[para/3. Resources/Highlights/Fedipool - Fedimint Could Mitigate Bitcoin Mining Pool Concerns\|Obsidian Link]])
	- [More discussion on pros and cons](https://github.com/fedimint/fedimint/discussions/1504)
	- The overwhelming majority of bitcoin mining relies on mining pools
	- Mining pool operators custody bitcoin for their users and choose which transactions are included in the blocks they mine
	- Fedimint is an emerging open source protocol that combines bitcoin, lightning, chaumian ecash, and federated custodians (called Guardians) to create community wallets that are easy to use, have strong privacy, reduced custodial risk, cheap and fast payments within the community, and interoperability with all bitcoin wallets
	- The same tech could be used to **replace major custodial mining pools**:
		- A group of independent miners can choose to create a Fedimint together
		- Rather than a single pool operator constructing blocks and choosing which transactions to include, each Guardian can construct their own blocks, reducing censorship risk
		- Additional miners can join the pool in the future to take advantage of the above, but rather than be a Guardian, they choose which Guardian they want to construct their blocks
	- **Key benefits**:
		- Rewards can't be seized if at least two miners act honestly
		- Miners receive the privacy benefit of chaumian ecash
		* Miners can withdraw mining rewards using bitcoin or lightning at their leisure
		* Regulatory risk is significantly reduced since Guardians can be easily located in different jurisdictions throughout the world
	* Conceptually Fedipool makes sense to distribute risk from a single pool operator managing payouts to a group of operators
	* **Tradeoffs**:
		* The technical implementation of Fedipools could **introduce complexity that adds risk in other ways**, ultimately not accomplishing the kind of risk reduction sought after in the first place (see linked pros & cons discussion)
		* There **may be other ways to reduce miner pool centralization risks** that are ultimately more effective - **e.g. P2Pool** is a decentralized mining pool that hasn't gained much traction
- [Many ~4MB blocks mined this month as Ordinal inscriptions reach 200k milestone](https://blockchair.com/bitcoin/blocks?s=size(desc)#)
	- Fees have been low enough that inscriptions are relatively economical 
	- It's yet to be seen whether inscriptions will maintain popularity over time, especially as fees go up
	- Still a lot of debate on whether or not inscriptions are a good use of block space, but most have accepted that they're inevitable either way

# Optional Topics

- [Kraken to discontinue unregistered offer and sale of crypto asset staking-as-a-service program and pay $30 million to settle SEC charges](https://www.sec.gov/news/press-release/2023-25) ([[para/3. Resources/Highlights/Crypto Exchange Kraken Settles With SEC Over Unregistered Staking Services\|Obsidian Link]])
	- The SEC has charged Kraken with failing to register the offer and sale of their crypto asset staking-as-a-service program
	- The program allowed investors to transfer crypto assets to Kraken for staking in exchange for advertised annual investment returns
	- The SEC's complaint also alleges that Kraken claimed its staking investment program offered easy-to-use benefits and strategies to obtain regular investment returns, but provided investors with zero insight into its financial condition, among other things
	- SEC Chair Gary Gensler commented, "Today’s action should make clear to the marketplace that staking-as-a-service providers must register and provide full, fair, and truthful disclosure and investor protection."
- [James O'Beirne writes formal BIP for OP_VAULT](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2023-February/021465.html)
- [Codex32: Proposed BIP for offline seed-splitting and recovery scheme](https://bitcoinops.org/en/newsletters/2023/02/22/#proposed-bip-for-codex32-seed-encoding-scheme)
- [Handcrank: A drivechain wannabe with no softfork](https://github.com/supertestnet/handcrank)
- [Flyover: A repayment protocol for fast bitcoin transfers over federated pegs](https://eprint.iacr.org/2023/086)
- [Maravedí: A secure and practical protocol to trade risk for instantaneous finality](https://eprint.iacr.org/2023/183)
- [BTCPay Server launches beta release of WabiSabi-based Coinjoin plugin](https://twitter.com/MrKukks/status/1630221270246719489?s=20)
- [Fedimint hackathon winners announced](https://www.fedi.xyz/blog/fedimint-hackaton-winners)
- [How many bitcoin confirmations is enough?](https://blog.lopp.net/how-many-bitcoin-confirmations-is-enough/) ([[para/3. Resources/Highlights/How Many Bitcoin Confirmations is Enough\|Obsidian Link]])
- [Ordisrespector is a mempool filter that rejects ordinal transactions](https://minibolt.info/guide/bonus/bitcoin/ordisrespector.html)
- [Muun wallet submarine swaps are quickly expanding the UTXO set](https://twitter.com/mononautical/status/1621663167582437376?s=20)
- [Should we remove the OP_RETURN size limit?](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2023-February/021438.html)
- [Jeremy Rubin steps away from development on bitcoin-related projects](https://twitter.com/JeremyRubin/status/1618806141903069184)
- [Bitcoin + Nostr could redefine social media](https://bitcoinmagazine.com/culture/nostr-and-bitcoin-can-change-social-media)
- [Bitcoin Search: A search engine for bitcoin technical documentation and discussions](https://bitcoinsearch.xyz)
- [Proposal for a serverless version of the BIP78 payjoin protocol](https://bitcoinops.org/en/newsletters/2023/02/01/#serverless-payjoin-proposal)
- [U.K. details plan to regulate bitcoin/cryptocurrency industry](https://bitcoinmagazine.com/legal/u-k-details-plan-to-regulate-bitcoin) ([[para/3. Resources/Highlights/U.K. Details Plan To Regulate Bitcoin, Cryptocurrency Industry\|Obsidian Link]])
- [UK court rules Craig Wright has no copyright claim on bitcoin](https://bitcoinmagazine.com/legal/court-rules-craig-wright-has-no-bitcoin-copyright)