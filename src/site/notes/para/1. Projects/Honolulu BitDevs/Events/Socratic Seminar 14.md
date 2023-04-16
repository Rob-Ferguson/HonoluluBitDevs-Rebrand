---
{"dg-publish":true,"permalink":"/para/1-projects/honolulu-bit-devs/events/socratic-seminar-14/","title":"Socratic Seminar 14","tags":["bitdevs, socratic-14, bitcoin, resource"],"noteIcon":"3","created":"2022-11-21T22:26:28.383-10:00","updated":"2023-04-15T13:44:21.948-10:00"}
---



<button class="obsidian-button previous-seminar">[[para/1. Projects/Honolulu BitDevs/Events/Socratic Seminar 13\|Previous Seminar]]</button> <button class="obsidian-button next-seminar">[[para/1. Projects/Honolulu BitDevs/Events/Socratic Seminar 15\|Next Seminar]]</button> 

# Announcements

- Respect people’s privacy
- Interaction and asking questions are encouraged
- [Chatham House rules](https://www.chathamhouse.org/about-us/chatham-house-rule)
- [Apply for a bitcoin job](https://bitcoinerjobs.com/)
- [Join our telegram group](https://t.me/+Uh9gbHO9EHFkZWJh)
- [Follow us on Twitter (@HonoluluBitcoin)](https://twitter.com/HonoluluBitcoin)
- [Donate sats](https://honolulubitdevs.com/donate)
- Entrepreneur's Sandbox sponsorship + venue change


# Bitcoin KPIs

- [Clark Moody's Bitcoin Dashboard](https://bitcoin.clarkmoody.com/dashboard/)


# Geopolitics
- [US Treasury adds Tornado Cash to OFAC sanctions list](https://www.coincenter.org/u-s-treasury-sanction-of-privacy-tools-places-sweeping-restrictions-on-all-americans/)
	- What happened?
		- Tornado Cash smart contract on Ethereum was specifically targeted (alongside known connected addresses, Tornado Cash entity, etc.)
		- Tornado Cash is a mixer deployed as a smart contract on the Ethereum blockchain
			- More akin to a robot than an entity –– it can be thought of as an automated version of a typical cryptocurrency mixer
			- It still works like a regular mixer. Users deposit cryptocurrency into the Tornado Cash contract, which pools the funds and enables withdrawals unlinked to the deposits
			- Still non-custodial as users can trustlessly withdraw mixed funds by using zero-knowledge proofs to certify ownership over previously deposited funds
		- The sanctioning of Tornado Cash represents OFAC’s **second-ever sanction on a cryptocurrency mixer**. The first, on Blender, happened in May 2022.
		- This is still the **first time an open source protocol has been sanctioned**.
		- OFAC said in a statement that Tornado Cash “**has been used to launder more than $7 billion worth of virtual currency since its creation in 2019**,” highlighting the alleged funneling of over $455 million stolen by the Democratic People’s Republic of Korea (DPRK)-sponsored Lazarus hacking group, which was sanctioned by the U.S. in 2019
		- Tornado Cash smart contract is still running but requires someone run their own Ethereum node to interact - other known frontends have been shut down
		- Tornado Cash GitHub repository taken down and certain developers who contributed to the Tornado Cash protocol had their GitHub accounts deleted - affecting unrelated work on other projects
		- [A suspected Tornado Cash developer was arrested in Amsterdam](https://www.fiod.nl/arrest-of-suspected-developer-of-tornado-cash/)
	- What are the implications?
		- [Coin Center Analysis: What is and what is not a sanctionable entity in the Tornado Cash case](https://www.coincenter.org/analysis-what-is-and-what-is-not-a-sanctionable-entity-in-the-tornado-cash-case/)
		- [BTC Policy Institute statement on Tornado Cash](https://www.btcpolicy.org/articles/criminal-code)
		- Code is speech - banning open source software is unconstitutional and practically infeasible
		- Blacklisting Tornado Cash funds impacts the complex network of DeFi protocols and connected companies leveraging that money (e.g., DAI, USDC, etc.)
		- Ethereum's account based system (vs Bitcoin's UTXO system) makes it more difficult to separate "tainted" funds that have gone through Tornado Cash
			- People sending tainted ETH to celebrities and other prominent figures who can't reject or easily isolate that money
		- How does this affect Ethereum's transition to proof of stake (supposedly) next month?
			- Majority of stakers will be OFAC-compliant entities
			- Is this [Ethereum's UASF moment](https://twitter.com/pourteaux/status/1559879293810774017)?
	- [Is Bitcoin next after Tornado Cash?](https://bitcoinmagazine.com/technical/is-bitcoin-next-after-tornado-cash)
		- Ethereum smart contract mixers vs Bitcoin coinjoins
			- Account-based structure forces ETH privacy tools to act more like mixers (deposit, then withdraw), while Bitcoin's UTXO system enables coinjoins, which are just collaborative bitcoin transactions where input ownership is obfuscated
				- Bitcoin UTXO ownership isn't as clearcut - chain analysis is all based on probabilities
			- In a 2020 report on Wasabi coinjoin software, Europol stated that “users who download the wallet store all bitcoins locally,” which “means that the AML legislation... does not apply to this service.”
			- Ethereum smart contracts have fixed addresses that users interact with, making it a trivial target for sanctioning
				- Coinjoin coordinators rotate deposit addresses with each new round
			- Centralized coinjoin coordinators can be targeted (except Joinmarket), but new coordinators can easily pop up and gain liquidity (also applies to spinning up new mixing smart contracts on Ethereum)
			- In general, centralized tools play a bigger role in Ethereum infrastructure versus Bitcoin - ETH has more regulatory chokepoints, and Bitcoin is more prepared to withstand nation-state attacks 
		- Ultimately, Bitcoin can't rely on good-faith regulation because regulators tend to be stupid
		- We need to design systems and tools that are robust against bad regulation, such that regulatory enforcement is infeasible in practice

- [FDIC issues cease and desist letters to five crypto companies about false/misleading claims about deposit insurance](https://content.govdelivery.com/accounts/USFDIC/bulletins/328cfe1)
	- These companies suggested that certain crypto-related products are FDIC-insured
	- List includes FTX exchange (others aren't notable)
	- "FTX US is not insured by the FDIC, and the regulator does not insure brokerage accounts or cover stocks and cryptocurrencies" according to FDIC Assistant General Counsel Seth Rosebrock
	- [In a tweet](https://web.archive.org/web/20220720201025/https://twitter.com/brett_ftx/status/1549773584922333184) that has since been deleted, FTX US President Brett Harrison said that any direct deposits from employers to FTX US would be stored in FDIC-insured bank accounts.
	- Sam Bankman-Fried, CEO of FTX tweeted: “FTX does not have FDIC insurance … banks we work with do. We never meant otherwise, and apologize if anyone misinterpreted it.”
	- Other letter recipients claimed certain crypto exchanges (Coinbase, Gemini, eToro) were FDIC-insured, which isn't accurate
	- Similar claims made against Voyager in July for falsely claiming FDIC insurance status

- [Defending BTC telethon fundraiser on 8/26 for hodlonaut's legal defense](https://www.defendingbtc.com/)
	- [Timeline of the legal battle between hodlonaut and Faketoshi](https://bitcoinmagazine.com/culture/timeline-of-hodlonaut-craig-wright-case)
	- [Greg Maxwell's response/context](https://www.reddit.com/r/Bitcoin/comments/ws8wfd/starting_september_12th_in_oslo_norway_hodlonaut/ikxqxoo)
		- Faketoshi doesn't deserve any more airtime, but this is an important case
		- Hodlonaut and many Bitcoin Core developers are racking up legal bills, even though Faketoshi has repeatedly lied and falsified evidence in the past
		- [OpenSats introduces Legal Defense Fund to defend open source Bitcoin contributors](https://opensats.org/projects/opensats_legal_defense) 
			- Initial round of donations will fund hodlonaut's legal bills, but future donations will go toward defending other open source Bitcoin contributors in similar situations
			- Currently raised over 50 bitcoin + ~$30k
			- Fiat donations can be tax deductible (and BTC donations can be anonymous)
			- You can set up your paycheck split to automatically donate a portion of USD to OpenSats

- [Victorian police to get ‘greater power’ to seize crypto assets from criminals](https://cointelegraph.com/news/victorian-police-to-get-greater-power-to-seize-crypto-assets-from-criminals)
	- Authorities in the Australian state are being granted the power to "**seize digital wallets**” under the new laws
	- Convictions for possessing a **trafficable quantity of firearms/drugs** or **sexual offenses** will automatically trigger the forfeiture of assets (including cryptocurrency)
	- Cryptocurrency platforms will also be forced to hand over information about suspects to law enforcement


# Market/Adoption
- Blackrock wants your sats
	- [BlackRock to offer Bitcoin trading/custody in new Coinbase partnership](https://bitcoinmagazine.com/markets/blackrock-to-offer-bitcoin-in-coinbase-partnership)
		- BlackRock will begin offering bitcoin trading and custody services for its institutional clients by partnering with Coinbase.
		* Coinbase Prime (Coinbase's institutional brokerage platform) will be integrated into BlackRock's investment platform Aladdin as part of existing portfolio management/trading workflows
		* Bitcoin will be held by Coinbase Custody
		* Funds can be transferred between wallets internally but not withdrawn outside of the Coinbase Prime platform
	- [BlackRock launches spot Bitcoin private trust](https://bitcoinmagazine.com/markets/blackrock-launches-spot-bitcoin-private-trust)
		- BlackRock’s institutional bitcoin trust will not support the custodial transfer of bitcoin
		- The value of the trust will be derived from bitcoin’s spot price
	- Just last year, BlackRock stated they were **not aware of any institutional interest in Bitcoin**, and now they've launched 2 Bitcoin-focused products for their clients

- [U.S. inflation only 8.5% in July](https://bitcoinmagazine.com/markets/u-s-inflation-slowed-to-8-5-in-july-bitcoin-jumps)
	- Slightly under market expectations, but still high
	- "0% inflation" is a lie - maybe not as bad as last month, but inflation is not 0%

- [Motiv launches 16 Bitcoin economies in Peru](https://bitcoinmagazine.com/business/motiv-launches-16-bitcoin-economies-in-peru)
	- Motiv is a non-governmental organization (NGO) dedicated to creating bitcoin circular economies
	- The NGO announced **16 circular bitcoin economies are operational in Peru** after providing the communities with the educational materials and tools needed to get started
	- Many communities in Peru are separated from central banking, but **the region has 80% smartphone penetration** - perfect catalyst for Bitcoin adoption

- [Vinteum non-profit launches to fund Bitcoin developers in Brazil/Latin America](https://bitcoinmagazine.com/business/vinteum-to-fund-bitcoin-developers-in-brazil)
	- Vinteum is a non-profit dedicated to decentralizing the open-source development of Bitcoin in Brazil (with the intent to expand to all of Latin America and then worldwide)
	- Vinteum executive director Lucas Ferreira: "The development ecosystem will be **more robust and resistant if we have different entities funding developers from all over the world**."
	- Bruno Garcia will be the first Bitcoin Core developer to be funded through Vinteum
		- He will also be joining the Vinteum team as the third founding member

- [River introduces zero-fee recurring Bitcoin purchases](https://blog.river.com/announcing-zero-fee-recurring-orders-2/)
	- Not newsworthy itself, but useful info for local sat stackers
	- River is a great bitcoin-only exchange that actually operates in Hawaii
	- **DCA is the way** - set it and forget it 


# Technology
- [Bitcoin Independence Day on 8/1](https://bitcoinmagazine.com/culture/luke-dashjr-segwit-bitcoin-independence-day)
	- ["The History Of Bitcoin Independence Day" video by Bitcoin Magazine](https://youtu.be/ui9JwnB1d-k)
	- Segregated Witness (SegWit) was introduced in a Bitcoin Core upgrade in October 2016
		- It repaired a transaction malleability bug (paving the way for secondary networks like Lightning) and slightly increased the amount of data that could fit in each block
	- SegWit was merged but would not activate until enough miners signaled their support for the upgrade and began mining SegWit-compatible blocks
		- Once one miner or pool made the signal, 95% of the network’s miners would have the span of two weeks (2,016 blocks; aka a difficulty period) to begin mining SegWit blocks
		- If 95% of hashing power generated blocks under the new SegWit rules within this timeframe, then the soft fork’s rules would be “locked in” to the network and would be fully activated after another difficulty period
	- In mid-2017, a cabal of influential companies in the Bitcoin space met and forged what came to be known as the New York Agreement.
		- This group of the largest miners/stakeholders didn't like the original plan for the SegWit soft fork - they demanded a hard fork to further increase the block size to 4 MB as a prerequisite to SegWit activation
		- The controversial initiative was branded SegWit2x
		- The hard fork meant the new protocol rules, unlike the SegWit soft fork, would be incompatible with non-upgraded versions — and the agreement’s version of SegWit was incompatible with Core’s version
		- What was assumed to be a seamless soft fork with SegWit had spiraled into a scaling war between big businesses and individual users
	- Originally introduced in February 2017, the **idea of a user-activated soft fork resurfaced via BIP148** as a way to implement SegWit without expanding the block size to 4 MB (i.e., a way for node runners to reject the SegWit2x hard fork)
		- BIP148 allowed users to move forward with the SegWit upgrade without the need for 95% of miners to signal their support
	- By activating the UASF on their wallets and nodes, users would be giving miners an ultimatum: signal SegWit or we will reject your blocks
		- In effect, this would incentivize miners into flipping the switch on SegWit, an opportunity for the community to exercise its control over the Bitcoin network.
		- In this case, if the miners don’t play by the UASF rules, then they lose out on profit by having their mined blocks be orphaned by the network
	- 8/1/2017 was set as BIP148 flag day - the specific day that node runners would start enforcing the SegWit update via a UASF
	- Ultimately, the threat of the UASF was enough to get miners to activate SegWit without the SegWit2x hard fork
	- While it’s unclear how many people implemented BIP148 on August 1, SegWit would [lock into the network on August 9](https://bitcoinmagazine.com/articles/point-no-return-segregated-witness-will-lock-bitcoin), and after a two-week grace period, the upgrade would be set in stone — and without splitting the chain in two.
	- 8/1 is now recognized as Bitcoin Independence Day because it's the day that proved individual node runners are the ones that define the network's consensus rules - not the miners

- [Bitcoin without internet: SMS service allows sending BTC with a text](https://cointelegraph.com/news/bitcoin-without-internet-sms-service-allows-sending-btc-with-a-text)
	- Using the GSM cellular network could help onboard millions of Bitcoin users without direct/easy internet access (but who do have mobile phones)
	- A South African developer has created Machankura (local slang word for 'money'), a new SMS-based service that enables sending/receiving Bitcoin over the Lightning Network to the phone's number
	- Similar experience to topping up a phone with minutes, which is very common in Africa
	- How it works: Users dial a number and are then introduced to a menu where they can learn more about Bitcoin or register an account. "All you need to register an account is a 5-digit pin, and from there on, you are presented with a different menu: Send and receive Bitcoin"
	- The service is custodial, so the team is looking for a way to use SIM cards as private keys
	- Not censorship resistant or sovereign, but a good first step to introduce a lot of people to Bitcoin who couldn't otherwise access it

- [Galoy brings synthetic USD to Bitcoin](https://bitcoinmagazine.com/technical/galoy-brings-us-dollars-to-bitcoin)
	- [Stablesats](https://stablesats.com/) is able to offer a stable dollar balance backed by bitcoin through [inverse perpetual swaps](https://www.bitmex.com/app/inversePerpetualsGuide).
	- Users are exposed to full custodial risk in order to minimize dollar-denominated volatility
	- Useful for people who want to leverage Bitcoin payment rails without volatility risk (similar to Strike)
	- Allows easy interoperability with the Lightning Network (e.g., spend synthetic USD when scanning an invoice or automatically converting BTC received into synthetic USD)
	- Interesting way to access stable value in USD without requiring access to the traditional banking system or creating another token
	- The derivatives contracts placed to create Stablesats are fully collateralized with BTC – for every dollar liability, there is an equivalent dollar worth of value in bitcoin
	- Currently in beta for the Bitcoin Beach Wallet popularized in El Salvador
![Stablesats_Trust_Comparison.png](/img/user/para/artifacts/Stablesats_Trust_Comparison.png)

# Mining
- [Foundry Makes BTC Donation to Open Source Stratum V2 Protocol Developer to Improve Bitcoin's Proof-of-Work Mining Layer](https://www.prnewswire.com/news-releases/foundry-makes-btc-donation-to-open-source-stratum-v2-protocol-developer-to-improve-bitcoins-proof-of-work-mining-layer-301598747.html)
	- 1 BTC grant to 4ss0, a pseudonymous developer working on Stratum V2
	- Stratum V2 is an open-source protocol that defines how bitcoin miners and mining pools communicate to contribute hashrate to the bitcoin network
	- Increases efficiency, security, and decentralization by improving the POW coordination layer that connects the miner and the pool
	- The developer will use the funds to focus on the **implementation of the Job Negotiation Protocol** in Stratum V2
		- Job Negotiation is a Stratum sub-protocol that **allows miners to construct their own block templates** and will further improve the censorship resistance of Bitcoin by decentralizing block template creation
		- The protocol will allow individual miners to negotiate a block template (including the set of transactions to be mined) with a pool, making it more difficult for mining pools to censor specific transactions. 


# Optional Topics
- Last month's missed topics
	- TAPSIGNER Integration Is Live Within Nunchuk Mobile App ([[para/1. Projects/Honolulu BitDevs/Events/Socratic Seminar 13#^e3e3b7\|Socratic Seminar 13#^e3e3b7]])
	- Blockstream Draft BIP For Non-Interactive Schnorr Signature Half-Aggregation ([[para/1. Projects/Honolulu BitDevs/Events/Socratic Seminar 13#^1f4081\|Socratic Seminar 13#^1f4081]])
	- Controversy Around BlueWallet's Push Notifications Feature Allowing Addresses/TXIDs To Be Leaked ([[para/1. Projects/Honolulu BitDevs/Events/Socratic Seminar 13#^04cb9a\|Socratic Seminar 13#^04cb9a]])
- [Bitcoin Infinity Day on 8/21](https://bitcoinmagazine.com/culture/the-bitcoin-infinity-day-public-private-keys)
- Bitcoin Policy Institute submitted a [letter](https://uploads-ssl.webflow.com/627aa615676bdd1d47ec97d4/62f1737c38e3e4ea452021b9_Bitcoin%20Policy%20Institute%20-%20US%20Department%20of%20Treasury%20RFC.pdf) responding to the US Treasury's request for comment on responsible digital asset development
- [Beautyon's thoughts on the Lummis-Gillibrand Responsible Financial Innovation Act](https://bitcoinmagazine.com/legal/unpacking-and-analyzing-the-lummis-gillibrand-bill)
- [Bitmain, Antpool, Antalpha Offer Bitcoin Mining Industry Lifeline](https://bitcoinmagazine.com/business/bitmain-antpool-antalpha-offer-bitcoin-mining-industry-lifeline)
- [Widespread malware attack on Github (> 35k repositories affected)](https://twitter.com/stephenlacy/status/1554697077430505473)
- [Block releases blog post about their approach to multisig key management](https://wallet.build/losing-your-keys-without-losing-your-coins/)
- Lyn Alden's ["A Look At the Lightning Network"](https://www.swanbitcoin.com/a-look-at-the-lightning-network/)
- [LATAM’s Largest Investment Bank BTG Pactual Launches Bitcoin, Crypto Exchange](https://bitcoinmagazine.com/business/btg-pactual-launches-bitcoin-crypto-exchange-in-brazil)
- [Tropic Square Launches Open-Source Chip Prototype For Bitcoin Hardware](https://bitcoinmagazine.com/business/tropic-square-launches-open-source-chip-prototype-for-bitcoin-hardware)
- ["Log in with ZBD" product for authenticated identity across Lightning-enabled applications](https://blog.zebedee.io/introducing-log-in-with-zbd/)
	- The monetary equivalent of "log in with Google" widgets
	- Log in with ZBD to connect apps together and move LN funds seamlessly between them (bi-directionally - user can get paid by connected apps)
	- Uses the [OAuth 2.0](https://oauth.net/2/) protocol for authentication/authorization and allows users to connect ZBD gamer info to different apps (Gamertag, Lightning Address, profile pictures, etc.)
- [Effortless Inbound Channel Opening for Voltage Nodes](https://voltage.cloud/blog/feature-updates/effortless-inbound-channel-opening-for-voltage-nodes/)


# Obsidian Note Links
- [[para/3. Resources/Highlights/A Look At the Lightning Network\|A Look At the Lightning Network]]
- [[para/3. Resources/Highlights/Bitcoin Independence Day - Luke Dashjr On The Lessons From SegWit That We’re Forgetting\|Bitcoin Independence Day - Luke Dashjr On The Lessons From SegWit That We’re Forgetting]]
- [[para/3. Resources/Highlights/Bitcoin without internet- SMS service allows sending BTC with a text\|Bitcoin without internet- SMS service allows sending BTC with a text]]
- [[para/3. Resources/Highlights/Bitmain, Antpool Offer Bitcoin Mining Industry Lifeline Amid Miner Capitulation\|Bitmain, Antpool Offer Bitcoin Mining Industry Lifeline Amid Miner Capitulation]]
- [[para/3. Resources/Highlights/BlackRock To Offer Bitcoin Trading, Custody In Coinbase Partnership\|BlackRock To Offer Bitcoin Trading, Custody In Coinbase Partnership]]
- [[para/3. Resources/Highlights/World’s Largest Asset Manager BlackRock Launches Spot Bitcoin Private Trust\|World’s Largest Asset Manager BlackRock Launches Spot Bitcoin Private Trust]]
- [[para/3. Resources/Highlights/Foundry Makes BTC Donation to Open Source Stratum V2 Protocol Developer to Improve Bitcoin's Proof-of-Work Mining Layer\|Foundry Makes BTC Donation to Open Source Stratum V2 Protocol Developer to Improve Bitcoin's Proof-of-Work Mining Layer]]
- [[para/3. Resources/Highlights/LATAM’s Largest Investment Bank BTG Pactual Launches Bitcoin, Crypto Exchange\|LATAM’s Largest Investment Bank BTG Pactual Launches Bitcoin, Crypto Exchange]]
- [[para/3. Resources/Highlights/Losing your keys without losing your coins\|Losing your keys without losing your coins]]
- [[para/3. Resources/Highlights/Motiv Inc. Launches 16 Circular Bitcoin Economies In Peru\|Motiv Inc. Launches 16 Circular Bitcoin Economies In Peru]]
- [[para/3. Resources/Highlights/Police to get sweeping new asset seizure powers\|Police to get sweeping new asset seizure powers]]
- [[para/3. Resources/Highlights/Tropic Square To Launch Prototype For Open-Source Chips Used In Bitcoin Hardware\|Tropic Square To Launch Prototype For Open-Source Chips Used In Bitcoin Hardware]]
- [[para/3. Resources/Highlights/U.S. Inflation Slowed To 8.5 In July. Bitcoin Claims $24,000\|U.S. Inflation Slowed To 8.5 In July. Bitcoin Claims $24,000]]
- [[para/3. Resources/Highlights/Vinteum Launches Funding Bitcoin Developers In Brazil, Latin America\|Vinteum Launches Funding Bitcoin Developers In Brazil, Latin America]]
- [[para/3. Resources/Highlights/Criminal Code\|Criminal Code]]
- [[para/3. Resources/Highlights/Now That Authorities Have Shut Down Tornado Cash, Is Bitcoin Next\|Now That Authorities Have Shut Down Tornado Cash, Is Bitcoin Next]]
- [[para/3. Resources/Highlights/Unpacking the “Lummis-Gillibrand Responsible Financial Innovation Act”\|Unpacking the “Lummis-Gillibrand Responsible Financial Innovation Act”]]