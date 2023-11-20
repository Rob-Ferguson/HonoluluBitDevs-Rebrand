---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Lightning Replacement Cycling Attack.md","permalink":"/bit-devs/resources/notes/lightning-replacement-cycling-attack/","title":"Lightning Replacement Cycling Attack","tags":["bitdevs","bitcoin","socratic-28","lightning","vulnerability","exploit"],"noteIcon":"3","created":"2023-11-16T19:35:10.427-10:00","updated":"2023-11-20T12:01:42.280-10:00"}
---



# Context

> [!QUOTE] [Postmortem On The Lightning Replacement Cycling Attack](https://bitcoinmagazine.com/technical/postmortem-on-the-lightning-replacement-cycling-attack)
> When a Lightning payment is routed across the network, **one thing that is key to understand is how the timelocks for refunding a failed payment work.** The hop closest to the receiver has a timelock of 'x', and every hop going back to the sender has one of 'x+1', 'x+2', and so on. **The timelocks get progressively longer as you go each hop from the receiver back towards the sender.** The reason for this is that if a payment reaches the receiver, but some problem stops the preimage from propagating all the way back to the sender, the hop where it stopped has time to enforce it on-chain, and put the preimage there that all preceding hops need to confirm the payment. **Otherwise someone in the middle, where the failure happens, could have their outgoing hop claim the funds with the preimage, and the hop that forwarded it to them claim it with their refund path, and leave that person in the middle shit out of luck having lost funds.**
> 
> The Replacement Cycling Attack is a complicated way to try and accomplish exactly that undesired outcome, the target node losing money by having the outgoing hop claim the funds with a success transaction, and the incoming hop claiming funds through the refund transaction. **This necessitates stalling out the victim node, and preventing them from seeing the preimage in the success transaction on one side until after the timelock expires on the other side, so they can claim the refund there.**

# High-Level Breakdown

**Exploit Prerequisites**

- **Two-way channel connectivity:** The attackers must establish Lightning channels with the victim node on both sides of the payment path. This allows them to control the flow of the payment and manipulate the timelocks.
- **Payment routing:** The attackers must initiate a payment that routes through the victim node's channels. This creates the opportunity to withhold the preimage and exploit the timelock differences.

**Attack Mechanism**

1. Bob, the victim, opens channels with Alice and Carol, the attackers.
2. Alice and Carol route a payment through Bob's node.
3. When Alice receives the payment, she refuses to provide Bob with the preimage needed to complete the transaction.
4. Bob waits for the timelock to expire and broadcasts a transaction to reclaim his funds.
5. Alice and Carol repeatedly broadcast transactions to prevent Bob's transaction from being confirmed.
6. Eventually, Bob gives up and abandons his funds.
7. Alice and Carol spend Bob's funds.

# Technical Breakdown

One of the best resources to understand how this attack works and its implications is [Guy Swann's "Lightning Is Dead, Long Live Lightning" episode of the Bitcoin Audible podcast](https://open.getmatter.com/q/rXfwQq0mU2OL?content_id=43545698).

This Tweet thread also provides a great illustrated explanation:

> [!QUOTE] [@mononautical Illustrative Thread](https://x.com/mononautical/status/1715736832950825224?s=52&t=fR1UfkkV0hfE5yaQW87bRg)
![BitDevs-28-Mononaut-Tweet-1.png](/img/user/para/artifacts/BitDevs-28-Mononaut-Tweet-1.png)
![BitDevs-28-Mononaut-Tweet-2.png](/img/user/para/artifacts/BitDevs-28-Mononaut-Tweet-2.png)
![BitDevs-28-Mononaut-Tweet-3.png](/img/user/para/artifacts/BitDevs-28-Mononaut-Tweet-3.png)
![BitDevs-28-Mononaut-Tweet-4.png](/img/user/para/artifacts/BitDevs-28-Mononaut-Tweet-4.png)
![BitDevs-28-Mononaut-Tweet-5.png](/img/user/para/artifacts/BitDevs-28-Mononaut-Tweet-5.png)
![BitDevs-28-Mononaut-Tweet-6.png](/img/user/para/artifacts/BitDevs-28-Mononaut-Tweet-6.png)
![BitDevs-28-Mononaut-Tweet-7.png](/img/user/para/artifacts/BitDevs-28-Mononaut-Tweet-7.png)
![BitDevs-28-Mononaut-Tweet-8.png](/img/user/para/artifacts/BitDevs-28-Mononaut-Tweet-8.png)
![BitDevs-28-Mononaut-Tweet-9.png](/img/user/para/artifacts/BitDevs-28-Mononaut-Tweet-9.png)
![BitDevs-28-Mononaut-Tweet-10.png](/img/user/para/artifacts/BitDevs-28-Mononaut-Tweet-10.png)
![BitDevs-28-Mononaut-Tweet-11.png](/img/user/para/artifacts/BitDevs-28-Mononaut-Tweet-11.png)
![BitDevs-28-Mononaut-Tweet-12.png](/img/user/para/artifacts/BitDevs-28-Mononaut-Tweet-12.png)
![BitDevs-28-Mononaut-Tweet-13.png](/img/user/para/artifacts/BitDevs-28-Mononaut-Tweet-13.png)
![BitDevs-28-Mononaut-Tweet-14.png](/img/user/para/artifacts/BitDevs-28-Mononaut-Tweet-14.png)

# Mitigation Strategies/Considerations

1. **Fee bumping:** Regularly rebroadcasting the refund transaction with a higher fee can make the attack economically infeasible for the attackers.
2. **Trusted channel partners:** Restricting channel openings to trusted parties and implementing efficient channel management practices can reduce the risk of falling victim to the attack.
3. **Target selection:** The attack is more likely to be successful against large routing nodes that handle a significant amount of payment volume. Routing nodes that fall into this category should be more careful and prepared generally (i.e., LSPs and other large routers require more sophisticated/secure operations because they are high-value targets).
4. **Transaction structure changes:** Changes to the HTLC transaction structure could prevent the attack altogether by using the `SIGHASH_ALL` flag, which ensures that the transaction signature is invalidated if any minor changes are made. This could prevent double-spending these Lightning channel transactions but would also limit opportunities for more efficient fee optimization via transaction batching.
5. **Reverse timelocks:** Peter Todd suggested an alternative method to prevent the attack by introducing a reverse timelock mechanism, where a transaction becomes invalid after a certain time or block height (instead of being spendable after a certain amount of time).

While the Lightning Replacement Cycling attack could be a real concern, the Lightning Network is not dying because of it. Mitigation strategies and ongoing network improvements can significantly reduce the risk and impact of the attack. Future development and community efforts will continue to identify and address potential issues like this.

# More Resources

- [Postmortem On The Lightning Replacement Cycling Attack](https://bitcoinmagazine.com/technical/postmortem-on-the-lightning-replacement-cycling-attack) 
- [Bitcoin Optech Newsletter 274: Replacement Cycling Vulnerability Against HTLCs](https://bitcoinops.org/en/newsletters/2023/10/25/?ref=nobsbitcoin.com#replacement-cycling-vulnerability-against-htlcs) 
- [New Class of Replacement Cycling Attacks Might Put Lightning Network in Perilous Position](https://www.nobsbitcoin.com/major-lightning-vulnerability-concern-leaves-the-network-in-hard-dillema/)