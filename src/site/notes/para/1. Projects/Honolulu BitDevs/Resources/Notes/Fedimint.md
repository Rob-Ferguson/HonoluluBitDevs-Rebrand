---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Fedimint.md","permalink":"/bit-devs/resources/notes/fedimint/","title":"Fedimint","tags":["bitcoin","chaumian_ecash","multisig"],"noteIcon":"3","created":"2024-06-05T19:48:39.088-10:00","updated":"2024-06-05T19:56:11.947-10:00"}
---

-

> [!QUOTE] [Fedimint (Federated Ecash) is Self-Custodial — Tony Giorgio](https://arc.net/l/quote/leavmbhp)
> **Fedimint is a scalable self-custodial off-chain programmability layer on top of Bitcoin.** It allows for use cases that are difficult, time-consuming, and unscalable for general users to do on-chain today.
> 
> **Self-Custodial**
> 
> You might think I had a typo calling Fedimint a self-custodial network. Let me explain.
> 
> Fedimint uses Ecash under the hood, which operates as a bearer instrument instead of a "balance" in a ledger. If you have Ecash within a system, you can freely spend it within that system, much like cash. If you lose or give away (e)cash, you lose the ability to spend it. You must have custody of it in some way. Therefore, each Fedimint federation is its own self-custodial network.
> 
> A real-world example of this is looking at cash. If you have USD cash in your pocket, that is considered custody of the dollars. Still, it is not inherently interoperable with EUR cash in someone else's pocket. Each Fedimint federation operates in this way as well. Ecash from one federation is not inherently interoperable with the federation of another. To move between federations or between networks such as Bitcoin or Lightning, you must partake in an atomic swap. The transaction either is completed or is refunded. This can be done with the federation guardians (for on-chain Bitcoin) or through non-trusted entities that operate as liquidity swap providers (such as Lightning).
> 
> **Federated**
> 
> Some of what I describe can be true for Ecash on both Cashu and Fedimint. However, I will be focusing specifically on Fedimint. The most crucial difference between Cashu and Fedimint is that each Cashu mint is currently entirely controlled by a single member. Meanwhile, each Fedimint mint can have many members (guardians) who do not have complete individual control. Fedimint can be arranged as a 3 of 4 multisig, 5 of 7, etc. The more guardians you have, the slower they achieve consensus. More research is being made into its practical limitations as you extend beyond 40. Eventually, it should be able to dynamically swap out guardians if most of them agree.
> 
> The fact that there is no unilateral control of funds by a single party makes the most significant difference regarding how it technically and legally operates.
> 
> Custody is typically defined as a single party having clear control over the funds or establishing a contract or legal claim to the funds. If there are none of these things and there was ever a dispute of the funds, it may be considered unowned or abandoned property.
> 
> I believe there is no guarantee or cryptographic claim of the Bitcoin sent to a federation in exchange for Ecash. Many people who worry about using Fedimint as a custody solution would agree with me. So, let's call it what it is, not a claim to the "underlying" Bitcoin. I believe it behaves more like Wrapped Bitcoin on other chains where it's a smart contract of federation members (such as the one Bitgo was a proponent of on Ethereum).
> 
> ---
> 
> **Conclusion**
> 
> Fedimint is not a Bitcoin custody solution but its own protocol and network that can provide financial and non-financial solutions for any user of any mint. A majority of federation guardians enforce the contracts in the protocol, but no single guardian can unilaterally make decisions. Users have fantastic privacy inside the system to transact without censorship concerns. Users must have custody of their Ecash and back them up to spend them later. It's a new type of distributed ledger network without a ledger at all.
> 
> I welcome constructive comments and opinions around these ideas. If anyone has conflicting thoughts, you should be looking at this in comparison to other things that exist. Consider how it compares to Bitcoin's trust model or other currency networks. How does it compare to Wrapped Bitcoin on ETH, to ZK-Rollups, to state chains on secure enclaves that are technically considered non-custodial, to other cryptocurrencies without their scammy pricing mechanisms (at least as far as they are legally allowed to exist as self-custodial networks)? Some of it sounds cringe to compare it to, and I don't endorse any of them. But evaluate how they operate technically and legally if you'd like to challenge some of my thoughts around Fedimint being its own decentralized network with its own stable, but dynamic pricing structure.

# More Resources
- [Fedimint](https://fedimint.org/)
- [Bitcoin Audible Read 824 - Ecash is Self-Custodial](https://bitcoin-audible.castos.com/episodes/read-824-ecash-is-self-custodial)
- [Expanding Bitcoin Custody Models With Fedimint](https://bitcoinmagazine.com/technical/fedimint-adds-new-bitcoin-custody-solutions)
- [Can Fedimints Help Bitcoin Scale To The World?](https://bitcoinmagazine.com/culture/will-fedimints-bring-bitcoin-to-the-world)
- [@fedimint on X](https://x.com/fedimint?lang=en)
- [Fedi Home](https://www.fedi.xyz/)