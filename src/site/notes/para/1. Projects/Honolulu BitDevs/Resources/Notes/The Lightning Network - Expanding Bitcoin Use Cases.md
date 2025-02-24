---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/The Lightning Network - Expanding Bitcoin Use Cases.md","permalink":"/bit-devs/resources/notes/the-lightning-network-expanding-bitcoin-use-cases/","title":"The Lightning Network: Expanding Bitcoin Use Cases","tags":["bitcoin","bitdevs","socratic-42","lightning","payments"],"noteIcon":"3","created":"2025-02-21T19:57:36.013-10:00","updated":"2025-02-23T19:32:05.259-10:00"}
---



![BitDevs-42-Fidelity-Voltage-Lightning-Report-Takeaways.png](/img/user/para/artifacts/BitDevs-42-Fidelity-Voltage-Lightning-Report-Takeaways.png)

# [**The Lightning Network: Expanding Bitcoin Use Cases**](https://www.fidelitydigitalassets.com/research-and-insights/lightning-network-expanding-bitcoin-use-cases)
_By Fidelity Digital Assets® in collaboration with Voltage_

## **1. How Lightning Works and Its Unique Role in Bitcoin**

- "The Lightning Network was originally created in 2016 and has been described as a ‘payment scaling layer’ on the Bitcoin network."
- "While the Lightning Network fully launched in 2018 with the intent to enhance transaction speed and reduce costs, it was not until 2024 that its adoption gained momentum. Today, Lightning payments are now integrated into large U.S.-based exchanges such as Kraken and Coinbase."
- "Lightning does not require a unique token as it operates with bitcoin."
- "Channels between parties allow off-chain transactions to happen between a wider array of parties, **avoiding both on-chain block confirmation time and fees associated with traditional Bitcoin transactions**."
- "The Lightning Network permits permissionless unilateral exits as a part of the protocol. In other words, any participant in a Lightning channel may close the channel and reclaim their capital as on-chain bitcoin at any time **without third-party permission**."

Lightning scales Bitcoin by enabling instant, low-cost transactions without requiring changes to the base-layer blockchain. By avoiding block confirmations and allowing seamless off-chain transactions, it provides an efficient, scalable method of transacting while preserving Bitcoin’s decentralized properties.

## **2. Growth in Lightning Network Capital Efficiency**

- "In the early stages of the Lightning Network—during which the community acknowledged its more experimental nature—node runners were quick to open new channels but with a low capacity. This was likely due to the risks associated with losing funds and experimentation around connecting to other nodes across the network."
- "In the years since, **average capacity (in bitcoin) has grown by 118%, while the average channels per node fell 30%**."
- "This shift highlights the network’s growing efficiency, allowing more funds to be transferred using fewer channels."
- "It also reflects users’ increasing trust in the Lightning Network’s stability and a deeper understanding of its potential benefits."

The trend toward fewer but higher-capacity channels indicates that the network is becoming more efficient and better suited for high-volume transactions. This efficiency reduces routing complexity, increases transaction success rates, and reflects a growing trust in Lightning's long-term viability.

![BitDevs-42-Fidelity-Lightning-Report-Capital-Efficiency.png](/img/user/para/artifacts/BitDevs-42-Fidelity-Lightning-Report-Capital-Efficiency.png)

## **3. Increased Channel and Node Capacity**

- "**The average capacity of peer-to-peer Lightning channels has grown by 214% over the last four years**. The 90th percentile sits above this average, increasing 50% since 2020. This rightly skewed data could be alluding to a larger subset of much higher capacity channels, presumably controlled by a few central entities."
- "For example, Voltage, a leading Lightning infrastructure provider for businesses and enterprises, has determined that its clients have an **average channel size of 7.2 million satoshis (0.072 BTC), with some channels being as large as one billion satoshis (10 BTC)**."
- "Large channel capacity ensures a higher success rate for sending and receiving higher value payments. As payments are sent and received, both sides of the channel’s liquidity can be efficiently utilized."

Larger channel sizes make Lightning more effective for high-value transactions and improve liquidity across the network. This shift supports its growing adoption for business payments, remittances, and large transfers.

![BitDevs-42-Fidelity-Lightning-Report-Capacity-Per-Channel.png](/img/user/para/artifacts/BitDevs-42-Fidelity-Lightning-Report-Capacity-Per-Channel.png)

![BitDevs-42-Fidelity-Lightning-Report-Capacity-Per-Node.png](/img/user/para/artifacts/BitDevs-42-Fidelity-Lightning-Report-Capacity-Per-Node.png)

## **4. The Lightning Network’s Total Capacity and Private Channels**

- "Lightning capacity denominated in USD has increased by a substantial 2,767% since 2020—however, bitcoin's price has also increased by 504% during the same period."
- "**Bitcoin-denominated capacity has grown by 384% since 2020**."
- "While not as substantial as the USD-denominated growth, the Lightning Network’s **public capacity stands at 5,358.50 BTC or $509 million** (with a bitcoin price of $95,000), as of January 2025."
- "It is worth noting that this capacity does not include private or unannounced channels, which are estimated to be just as substantial."

While public Lightning capacity has grown significantly, it does not fully account for private channels, which are widely used by exchanges, businesses, and wallet providers. This means the true capacity of the network is likely much higher than reported.

![BitDevs-42-Fidelity-Lightning-Report-Total-Capacity.png](/img/user/para/artifacts/BitDevs-42-Fidelity-Lightning-Report-Total-Capacity.png)

## **5. Transaction Costs, Efficiency, and Reliability**

- "The Lightning Network is a peer-to-peer payment network and not a blockchain, the fee rates experienced in the network can vary drastically between nodes or even between payments."
- "It is possible to **pay no fee whatsoever or under 0.5% fees on payments** on the Lightning Network."
- "The more hops a payment uses, the higher the fee will likely be."
- "Users must be mindful of the channels they open to ensure the fewest number of hops."
- "Through a well-connected self-hosted node, transactions that required an average of one to three hops paid a fee of 0.04%. In other words, **transactions over 1,000,000 satoshis (~$1,000) have cost between $0.39 and $1.27.** This fee-to-transaction settlement ratio is rare within the traditional payment processing sector and across other digital asset networks."
- "The Lightning Network is known for its speed, as **almost all payments below one million sats (0.01 BTC) finalize in less than one second**."
- "A single hop payment averages a completion time of 0.38 seconds, which is notably faster than other digital asset payment mechanisms. This speed is also impacted by the connectivity of nodes, again demonstrating the importance of nodes being well-connected."
- "Additionally, **larger payments do take more time to complete**. This is likely due to time required to find proper routes to send the payment. As payment size increases, fewer and fewer channels could facilitate the payment (in a single transaction)."
- "Our analysis suggests **the biggest impact on the transaction success rate is the number of hops**. The fewer hops, the greater the success rate. Transactions requiring only one hop have the highest success rate of over 99%."
- "**With each hop that is added, the success rate declines by 4-8%.** This becomes particularly problematic with larger payment sizes, as fewer channels across the network can accommodate such payments."

Lightning transactions are highly cost-efficient, particularly for users who optimize their channel management. Compared to traditional payment systems, it provides near-zero fees and instant settlement, making it attractive for both businesses and individual users.

![BitDevs-42-Fidelity-Lightning-Report-Average-Payment-Hop-Fees.png](/img/user/para/artifacts/BitDevs-42-Fidelity-Lightning-Report-Average-Payment-Hop-Fees.png)

![BitDevs-42-Fidelity-Lightning-Report-Average-Payment-Fee.png](/img/user/para/artifacts/BitDevs-42-Fidelity-Lightning-Report-Average-Payment-Fee.png)

![BitDevs-42-Fidelity-Lightning-Report-Average-Payment-Speed.png](/img/user/para/artifacts/BitDevs-42-Fidelity-Lightning-Report-Average-Payment-Speed.png)

![BitDevs-42-Fidelity-Lightning-Report-Average-Payment-Success.png](/img/user/para/artifacts/BitDevs-42-Fidelity-Lightning-Report-Average-Payment-Success.png)

## **6. Expanding Use Cases: Nostr, Podcasting, and AI Payments**

- "Lightning is steadily emerging as **the language (protocol) of multiple layers and services using bitcoin as money**. For example, Fedimint, Cashu, Nostr, and Podcast 2.0 applications all utilize the Lightning Network."
- "Nostr users have sent more than **3.6 million individual zaps in the last six months**."
- "Another popular application born of Lightning is the streaming of bitcoin. Applications such as Fountain - commonly referred to as a Podcast 2.0 application - enable the direct payment to and from podcast creators for time listened."
- "Company payrolls could be automated and earned down to the second worked, enabling employees to realize their paycheck in real time rather than bi-weekly or monthly."
- "Similarly, AI agents perform tasks very frequently and will need a method of transacting between one another."

Beyond person-to-person payments, Lightning is unlocking new use cases, such as automated micropayments for AI, real-time payroll, and tipping mechanisms in decentralized social media platforms.

## **7. The Future of Lightning and Institutional Adoption**

- "The Taproot Assets protocol enables the issuance of digital assets outside the scope of the underlying blockchain (Bitcoin). Assets are created and embedded into bitcoin's existing dataset of UTXOs. **Taproot Assets have the potential to expand Bitcoin's functionality beyond seemingly simple value transfer by enabling the transfer of all assets inscribed to the network.**"
- "Looking ahead, we anticipate continued growth for the Lightning Network, despite bitcoin's perception as a maturing store of value that discourages spending. Stablecoins on Lightning are expected to address this issue. Users will benefit from the speed and low fees that the Lightning Network offers while holding a stable asset."
- "Using the Lightning Network, **banks and institutions could settle debts instantaneously and in real time**, either for themselves or on behalf of clients and users."
- "Further institutional adoption could solidify Bitcoin’s role in the global financial system, enhancing its long-term value proposition and investment potential."

Lightning’s expansion into stablecoins and institutional settlement could make it a major force in financial markets, bridging the gap between Bitcoin’s role as a store of value and its potential as a widely used medium of exchange.

## **8. Conclusion: Lightning Could Strengthen Bitcoin's Overall Investment Thesis**

- "For Lightning to be truly effective, users need Lightning payments to work 100% of the time. Both publicly available data and Voltage’s proprietary data support the thesis that **Lightning is steadily improving in efficiency and growth while also expanding its use cases beyond simple one-to-one payments**."
- "Its network capacity and transaction volume have continued to increase as Lightning continues to scale. Additionally, there is the advantage of not needing to rely on a different blockchain or token. **The ability to use the native bitcoin token for transactions is highly attractive in today’s digital asset ecosystem**, as new protocols with obfuscated tokenomics are constantly emerging."
- "Lastly, we believe the Lightning Network presents a transformative opportunity for both new and existing financial institutions as well as payment service providers to **gain a significant competitive advantage in the global remittance and transaction processing landscape**."
- "This second-layer solution, built on the current most secure digital asset network, offers several key benefits that may warrant consideration from institutional entities. By adopting this technology, banks, exchanges, and payment processors may be able to position themselves at the forefront of financial innovation."
- "Further institutional adoption could solidify Bitcoin’s role in the global financial system, enhancing its long-term value proposition and investment potential."

The Lightning Network has evolved into a fast, low-cost, and scalable payment system that preserves Bitcoin’s decentralization while enabling global transactions. With growing adoption, larger channel capacities, and expanding use cases, it is poised to become the preferred infrastructure for digital payments, institutional settlements, and innovative financial applications.

# More Resources
- [Full Report](https://cdn.prod.website-files.com/66151fa56c7d65f427924664/67b37b4a8d343fbc694778a6_FDA_TheLightningNetwork_ExpandingBitcoinUseCases_1187503.1.0_V5.pdf)
- [My Top 3 Takeaways From Fidelity And Voltage’s Recent Lightning Report](https://bitcoinmagazine.com/takes/my-top-3-takeaways-from-fidelity-and-voltages-recent-lightning-report)

