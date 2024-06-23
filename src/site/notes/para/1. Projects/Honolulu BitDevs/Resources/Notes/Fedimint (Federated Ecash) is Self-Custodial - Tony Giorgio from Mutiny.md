---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Fedimint (Federated Ecash) is Self-Custodial - Tony Giorgio from Mutiny.md","permalink":"/bit-devs/resources/notes/fedimint-federated-ecash-is-self-custodial-tony-giorgio-from-mutiny/","title":"Fedimint (Federated Ecash) is Self-Custodial - Tony Giorgio from Mutiny","tags":["bitcoin","bitdevs","socratic-35","lightning"],"noteIcon":"3","created":"2024-06-19T12:11:59.618-10:00","updated":"2024-06-22T23:30:41.264-10:00"}
---



> [!QUOTE] [Fedimint (Federated Ecash) is Self-Custodial](https://tonygiorgio.com/fedimint/) - [Tony Giorgio](https://x.com/tonygiorgio_) from [Mutiny Wallet](https://www.mutinywallet.com/)
> ![BitDevs-35-Ecash-Meme.png](/img/user/para/artifacts/BitDevs-35-Ecash-Meme.png)
> **Fedimint is a scalable self-custodial off-chain programmability layer on top of Bitcoin.** It allows for use cases that are difficult, time-consuming, and unscalable for general users to do on-chain today.
# Understanding Fedimint

**Definition and Functionality**
Fedimint is a "Federated Custody" solution where a group of guardians holds Bitcoin on behalf of users in a multi-signature setup, issuing redeemable notes to mint users. Tony offers an alternative view of its functionality, suggesting that it serves as a scalable self-custodial off-chain programmability layer on top of Bitcoin.

> [!QUOTE] "Fedimint is best understood as a 'Federated Custody' solution where a group of guardians 'custody' Bitcoin on behalf of users in a multi-sig. That's a framing that many of us have understood. Still, as I dig into it more, I have an alternative view of its functionality, especially compared to other technologies."

**Not a Solution for Key Custody Difficulties**
According to Tony, Fedimint is not intended to solve key custody problems for users who find self-custody difficult. Instead, it addresses broader issues and offers unique solutions beyond simple key management.

> [!QUOTE] "I'll repeat that because it's an important distinction that leaves many people with, 'Why would anyone want this or think it's a good thing to let others custody on my behalf?' Fedimint, in my opinion, is not solving key custody for users who 'don't know how' or think it's 'too hard.' Many other things exist to solve that problem."

# Comparison with Existing Custody Solutions

**Existing Solutions**
Tony compares Fedimint with other custody solutions like Unchained, Bitkey, and Onramp. These solutions offer various multi-sig and key recovery mechanisms, but Fedimint stands out for its advanced and expandable role. 

> [!QUOTE] "When it comes to custody, it's a multi-sig like many other solutions that exist out there. There's Unchained, which allows the user to retain one (or more) of the keys, with Unchained holding one as a backup if you lose the other(s). A typical scenario is a 2 of 3 multi-sig solution that doesn't allow Unchained to spend the funds... Fedimint is more advanced and expandable in its role. It does far more than help users custody funds."

**Self-Custodial Nature**
Fedimint uses Ecash, a bearer instrument, allowing for self-custodial operations within each federation's network. This mechanism ensures that users are still responsible for managing their Ecash notes, akin to holding physical cash. Losing a note means the funds are unspendable. 

> [!QUOTE] "You might think I had a typo calling Fedimint a self-custodial network. Let me explain. Fedimint uses Ecash under the hood, which operates as a bearer instrument instead of a 'balance' in a ledger. If you have Ecash within a system, you can freely spend it within that system, much like cash. If you lose or give away (e)cash, you lose the ability to spend it. You must have custody of it in some way. Therefore, each Fedimint federation is its own self-custodial network."

# Unique Functionality of Fedimint

**Federated Model**
Unlike Cashu, where a single member controls each mint, Fedimint involves multiple guardians in a multi-sig setup, ensuring no single party has unilateral control over funds.

> [!QUOTE] "The most crucial difference between Cashu and Fedimint is that each Cashu mint is currently entirely controlled by a single member. Meanwhile, each Fedimint mint can have many members (guardians) who do not have complete individual control... The fact that there is no unilateral control of funds by a single party makes the most significant difference regarding how it technically and legally operates."

**Pricing Mechanism**
The price of Ecash within a Fedimint federation is determined by the free market. Users can swap Bitcoin and Ecash directly with federation guardians or through market mechanisms.

> [!QUOTE] "So if an individual Fedimint federation is its own self-custodial network where users swap Bitcoin and Ecash to enter or leave that network, there's no longer a claim to the Bitcoin that a user traded for Ecash. So then, what determines the price of Ecash? It's determined by the free market... There are two main ways to get into and out of an Ecash federation: Direct Swaps and Market Swaps."

# Risks and Considerations

**Guardian Risks**
Ecash holders face risks if a majority of guardians in a Fedimint federation cease to function or alter the consensus rules. This risk is similar to systemic risks in other decentralized protocols.

> [!QUOTE] "Each holder of Ecash carries a risk that the majority of guardians in a particular Fedimint federation either ceases to function or has hard forked to break the consensus rules. At a certain point, all decentralized protocols face similar risks but have different consequences."

**Expirations and Longevity**
Tony suggests implementing expirations for Ecash notes to manage long-term liabilities and provide clarity on the duration of federation services.

> [!QUOTE] "Expirations reinforce the expectation that Ecash is not a guaranteed claim on the underlying Bitcoin. As soon as a user joins a federation, it can be communicated that their notes will expire at a specific date... This could be extended to another article as well. I believe it's fascinating to think about how the protocol can conceptualize adding 'expirations' onto each mint."

# Conclusion

Thinking of Fedimint as a broader protocol with great potential as a programmability layer helps to put the risk tradeoffs into perspective when we consider building applications that need to leverage BTC-denominated value. Fedimint is not just a Bitcoin custody solution but a new type of distributed ledger network, providing transactional privacy and quasi-self-custody for users. The federated guardian model allows each of these mint networks to distribute risk in very unique ways, catered to specific applications and use cases. 

> [!QUOTE] "Fedimint is not a Bitcoin custody solution but its own protocol and network that can provide financial and non-financial solutions for any user of any mint. A majority of federation guardians enforce the contracts in the protocol, but no single guardian can unilaterally make decisions."

# More Resources
- [Fedimint (Federated Ecash) is Self-Custodial - Tony Giorgio from Mutiny](https://tonygiorgio.com/fedimint/)
- [Bitcoin Audible Read 824 - Ecash is Self-Custodial](https://bitcoin-audible.castos.com/episodes/read-824-ecash-is-self-custodial) 🎧
- [Getting Started | Fedimint](https://fedimint.org/docs/intro)
- [Expanding Bitcoin Custody Models With Fedimint](https://bitcoinmagazine.com/technical/fedimint-adds-new-bitcoin-custody-solutions)
- [Can Fedimints Help Bitcoin Scale To The World?](https://bitcoinmagazine.com/culture/will-fedimints-bring-bitcoin-to-the-world)
- [@fedimint on X](https://x.com/fedimint?lang=en)
- [Fedi Home](https://www.fedi.xyz/)

