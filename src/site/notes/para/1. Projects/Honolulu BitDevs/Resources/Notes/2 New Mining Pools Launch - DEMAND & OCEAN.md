---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/2 New Mining Pools Launch - DEMAND & OCEAN.md","permalink":"/bit-devs/resources/notes/2-new-mining-pools-launch-demand-and-ocean/","title":"2 New Mining Pools Launch - DEMAND & OCEAN","tags":["bitdevs","bitcoin","mining","pool"],"noteIcon":"3","created":"2023-12-07T18:48:34.007-10:00","updated":"2023-12-17T19:41:24.954-10:00"}
---

# [DEMAND](https://dmnd.work/)

Bitcoin mining company DEMAND has launched the world's first Stratum V2 mining pool, built on open-source Stratum Reference Implementation (SRI). 

**Key benefits of Stratum V2:**
- Enhanced security, flexibility and performance for mining
- Empowers individual miners to construct their own block templates and select transactions for inclusion, decentralizing this process from pool operators
- Makes Bitcoin more resistant to mining censorship and regulatory pressure

DEMAND currently focuses on **solo mining, allowing miners to keep full block rewards**. The company also runs a hash power resale marketplace.  

The new pool aims to drive adoption of Stratum V2 and make home mining more viable to promote a more decentralized Bitcoin mining ecosystem. Miners will need to run translator proxy, job declaration client, and Bitcoin node to utilize Stratum V2 capabilities. 

> [!QUOTE] [DEMAND FAQ](https://dmnd.work/#faq)
> **What is Solo Mining?**
> Solo mining is the process of mining Bitcoin independently, with the help of DEMAND. We provide the infrastructure you need to mine efficiently. This means you receive the entire block reward if you are successful.
> 
> **How Does Solo Mining Differ from Pool Mining?**
> In solo mining, you compete against the entire Bitcoin network to find a block, whereas in pool mining, you collaborate with other miners. In a pool, rewards are shared among participants, but in solo mining, you receive the full reward for any block you find.
> 
> **What is hashrate DEMAND?**
> An option to maximize your earnings via our hashrate marketplace. You can now earn with just one miner.
> 
> **What is StratumV2?**
> Stratum V2 is the next generation protocol for pooled mining. It increases security, makes data transfers more efficient, and reduces mining infrastructure requirements. It also introduces three new sub-protocols that let miners select transaction sets and improve decentralization. More info here
> 
> **Is Solo Mining Profitable?**
> We make it profitable by giving our miners an option to sell their hashrate on various hashrate marketplaces. If you hit a block, you earn 6.25 BTC plus the transaction fees.
> 
> **What Are the Chances of Successfully Mining a Block Solo?**
> The probability of successfully mining a block solo depends on your mining power compared to the total network hash rate.
> 
> **How Does Solo Mining Affect Network Security?**
> Solo mining contributes to the decentralization of the Bitcoin network, which is beneficial for the health of the bitcoin mining network.

[![BitDevs-29-DEMAND-Youtube-Thumbnail.png](/img/user/para/artifacts/BitDevs-29-DEMAND-Youtube-Thumbnail.png)](https://youtu.be/hFtI2dPgDdc)

# [OCEAN](https://ocean.xyz/)

OCEAN Pool is a new Bitcoin mining pool launched by long-time Bitcoin developer [@LukeDashjr](https://twitter.com/lukedashjr). It's technically a relaunch of Eligius, a mining pool created and operated by Luke back in 2011. 

OCEAN has received $6.2 million in seed funding led by Jack Dorsey's Block Inc. among others. It aims to address centralization issues in Bitcoin mining related to transparency, custodianship of funds, and control over transaction selection. 

**Unique features include:**
- Non-custodial operation, giving miners direct control of bitcoin payouts rather than through a custodial pool operator.
- The TIDES reward system for precise, equitable payouts based on hashrate contribution 
- Support for Stratum V2 to further decentralize mining and improve efficiency
- Future Lightning Network integration for instant, low-cost payouts  
- Planned upgrades focused on decentralization like distributed block template creation
- Runs [Bitcoin Knots](https://bitcoinknots.org/) under the hood (Luke's own Bitcoin node/wallet implementation)

By tackling centralization, opacity, and exclusivity issues in mining, OCEAN Pool aims to realign the sector with Bitcoin's founding principles - setting a new standard for transparency, inclusiveness, security, and permissionless participation.

> [!QUOTE] [Message from OCEAN founder Luke Dashjr](https://ocean.xyz/about)
> As we stand today, Bitcoin is not a censorship resistant network, rather it just happens to be a network that is not currently being censored. As with other forms of centralization (hardware, firmware, ...), the role of mining pools must change for Bitcoin to exist as a truly decentralized currency.
> 
> To that end, I am relaunching Eligius as OCEAN, a new type of pool that enables miners to be truly miners again. At the start, we are already the most transparent pool giving you full visibility into block templates, generation payouts, miner stats, etc. As miners, you should have the ability to know what transactions you are mining with your hashrate. We are also the only non-custodial pool, making you, the miners, recipients of new block rewards directly from Bitcoin.
> 
> Over the next year, I will be redesigning the process of block template construction, leveraging and improving Stratum V2 where possible, to truly decentralize mining. We also plan to incorporate Lightning payouts which will solve the dust problem for small miners. This will also serve the dual benefit of bringing more liquidity to Lightning.
> 
> To make it worth everyone's effort to switch, OCEAN will be at 0% for the first 2 months of operation. After that we will need to introduce fees, but they will be kept reasonable and fair for all sizes of miners.
> 
> ~ Luke Dashjr, 2023

# OCEAN Controversy

Although the stated mission of OCEAN is noble, they've made several operational blunders and decisions that have stirred up a lot of controversy and debate. 

[@brian_trollz](https://twitter.com/Brian_trollz) outlined several of these issues in his Bitcoin Magazine article "[An Ocean Launch Post-mortem](https://bitcoinmagazine.com/technical/an-ocean-launch-post-mortem)":
- **Launch Issues**
	- Launch was chaotic due to unclear communication about filtering inscription transactions.
	- First block was invalid due to a test server issue.
	- Payout system initially had problems but has been fixed.
- **Censorship Debate**
	- Because OCEAN uses Bitcoin Knots to construct their block templates, it  filters inscriptions and Whirlpool-based coinjoin transactions, sparking censorship concerns.
	- Censorship opponents argue miners have the right to choose what transactions to include.
	- Stratum v2 can allow miners to construct their own templates, including inscriptions, but this is not yet implemented at OCEAN (although is on the roadmap).
- **Addressing Incentive Problems**
	- OCEAN is trying to address issues like miner censorship and the "dying mempool" (where the majority of transactions start to circumvent typical mempool propagation by relaying directly to mining pools).
	- Stratum v2 could revive the mempool and make MEV strategies more transparent.
	- OCEAN's non-custodial payouts and Lightning integration are steps towards solving pool centralization issues.
- **Overall**
	- OCEAN launch was rocky, but they're actively working on addressing problems.
	- They're not perfect, but they're taking action while others complain.
	- The future of Bitcoin mining incentives is complex and evolving, but Stratum v2 has potential to further decentralize the Bitcoin mining ecosystem.

More information about OCEAN's role in renewing the miner censorship debate can be found in this D-Central article "[The Debate Over OCEAN Pool's OP_RETURN Size Limit](https://d-central.tech/the-debate-over-ocean-pools-op_return-size-limit/)."


[![BitDevs-GrassFedBitcoin-X-Ocean-1.png](/img/user/para/artifacts/BitDevs-GrassFedBitcoin-X-Ocean-1.png)](https://x.com/GrassFedBitcoin/status/1734463368361394564?s=20)

[![BitDevs-29-Luke-Nostr-1.png](/img/user/para/artifacts/BitDevs-29-Luke-Nostr-1.png)](https://primal.net/e/note1z03wsa48vwgm3m4vpckgq40yy68mchfzztwvdyndq9a6jkvke40qeux255)

[![BitDevs-29-GuySwann-Ocean-X-1.png](/img/user/para/artifacts/BitDevs-29-GuySwann-Ocean-X-1.png)](https://x.com/TheGuySwann/status/1733522148377887137?s=20)

> [!TIP]
> If you are a miner and aren't satisfied with the current pool options available, you can also [run your own mining pool](https://www.nobsbitcoin.com/how-to-run-your-own-bitcoin-mining-pool/).

# More Resources

- [Stratum V2: The next-gen protocol for pooled mining](https://stratumprotocol.org/)
- [DEMAND launches world’s first Stratum V2 bitcoin mining pool](https://bitcoinmagazine.com/business/demand-launches-worlds-first-stratum-v2-bitcoin-mining-pool)
- [Jack Dorsey Leads Seed Round in Support of OCEAN'S Mission to Decentralize Bitcoin Mining Globally - Announces Launch at Future of Bitcoin Mining Conference](https://www.prnewswire.com/news-releases/jack-dorsey-leads-seed-round-in-support-of-oceans-mission-to-decentralize-bitcoin-mining-globally---announces-launch-at-future-of-bitcoin-mining-conference-301999073.html)
- [Ocean Pool: A New Wave in Bitcoin Mining Decentralization](https://d-central.tech/ocean-pool-a-new-wave-in-bitcoin-mining-decentralization/)
- [Defending The Undefendable: The Censoring Miner](https://bitcoinmagazine.com/markets/defending-the-undefendable-the-censoring-miner)
- [Inscriptions: The Cure Is Worse Than The Disease](https://bitcoinmagazine.com/technical/inscriptions-the-cure-is-worse-than-the-disease)
- [@sethforprivacy Thread](https://x.com/sethforprivacy/status/1729949544035557702?s=20)
- [@WilsonMining Tweet](https://x.com/WilsonMining/status/1735446340618891641?s=20)
- [@SamouraiWallet Thread](https://x.com/SamouraiWallet/status/1732584009442443336?s=20)
- [@TheGuySwann Tweet](https://x.com/TheGuySwann/status/1733544435537875371?s=20)
- [@pippellia Thread](https://twitter.com/pippellia/status/1730595998215327917)