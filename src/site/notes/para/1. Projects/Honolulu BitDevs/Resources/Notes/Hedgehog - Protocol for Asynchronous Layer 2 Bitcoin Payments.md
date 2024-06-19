---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Hedgehog - Protocol for Asynchronous Layer 2 Bitcoin Payments.md","permalink":"/bit-devs/resources/notes/hedgehog-protocol-for-asynchronous-layer-2-bitcoin-payments/","title":"Hedgehog - Protocol for Asynchronous Layer 2 Bitcoin Payments","tags":["bitdevs","bitcoin","socratic-33","scaling"],"noteIcon":"3","created":"2024-04-23T21:56:11.623-10:00","updated":"2024-06-18T18:56:10.836-10:00"}
---

# Hedgehog

[![BitDevs-33-Calle-X-Hedgehod.png](/img/user/para/artifacts/BitDevs-33-Calle-X-Hedgehod.png)](https://x.com/callebtc/status/1772650750465691703)

> [!QUOTE] [GitHub - supertestnet/hedgehog: A protocol for improved layer two bitcoin payments](https://github.com/supertestnet/hedgehog)
> Hedgehog is a protocol for two party payment channels. Hedgehog channels are similar to lightning channels but with a few comparative benefits.
> - **Hedgehog channels are simpler than lightning channels**
> - **State updates only require the sender to propose an update and the recipient to accept it**
> - **The recipient can wait to accept a state change til they want to propose another one**
> 
> The properties mentioned above allow for an improved payment experience. **Using hedgehog feels similar to using an ecash protocol like cashu or fedimint, except with no server.** If you have a channel with someone, you can -- without their assistance -- create a payment for them, embed it in a piece of text (think of it like a cheque), and send it to them via email or some other communication method. Then you can go offline. When they get online, they can either accept the state change (the cheque) and update their balance without your further assistance, or they can reject it. If they accept the state change (the cheque) they can even use their new balance to pay you back later by making another state change (another cheque) that builds on the previous state change (i.e. spends the cheque to make a new cheque). And they can send the new state change (the new cheque) to you even if you are still offline. Or, if they reject your state change, they can propose an alternative one and wait for you to accept that.

Hedgehog is a protocol for two-party payment channels that works by combining two primitives: **revocable scripts and connector outputs**. Revocable scripts allow one party to revoke their ability to spend funds in an address after a certain number of blocks. Connector outputs allow one party to create a signature that sends funds from a multisig address to another party, but only if a specific UTXO (the "connector") is also spent.
1. Alice opens a channel with Bob by funding a 2-of-2 multisig address.
2. To send Bob some bitcoin off-chain, Alice creates two transactions:
   a. One that creates a revocable "dust" output spendable by Bob after a timelock.
   b. Another that sends funds to Bob, but requires spending the revocable dust output as an input (acting as a "connector").
3. Alice sends the signatures for these transactions to Bob. Bob can either accept the new state by broadcasting the transactions after the timelock expires, or reject it.
4. If Bob wants to send funds back to Alice, he revokes the previous revocable output and creates new transactions following the same pattern, sending the new state back to Alice.
5. This process can continue indefinitely, with Alice and Bob taking turns updating the latest state off-chain.

## Comparison to Lightning Network
- Hedgehog aims to be simpler than Lightning by only requiring the sender to propose a state update and the recipient to accept it, without complex revocation processes.
- Hedgehog allows **asynchronous payments**, where the sender can create a "cheque" (payment) and send it to the recipient, who can accept it later without the sender being online (similar to an ecash system).
- Lightning requires more interactive setup and revocation processes between the parties for each payment.
- Hedgehog is designed specifically for **direct two-party payment channels** (unlike the Lightning Network, which allows routing payments across multiple nodes/channels). This simplifies the protocol but limits its ability to facilitate payments across a broader network.
- Hedgehog has **unique edge cases**:
	- Inability to force channel closure after sending: once a party sends a payment, they cannot force the closure of the channel without the recipient's cooperation. Conditional revocation scripts might fix this.
	- Stuck funds if counterparty disappears: If one party broadcasts an old channel state after sending a payment, the funds could potentially get stuck in the multisig output if their counterparty disappears before broadcasting the final state. The proposed solution involves time-locked emergency keypaths to allow eventual withdrawal.

[![BitDevs-33-Hedgehog-Video-Thumbnail.png](/img/user/para/artifacts/BitDevs-33-Hedgehog-Video-Thumbnail.png)](https://youtu.be/-JeBDVPH1gA?feature=shared)

[![BitDevs-33-Hedgehog-Supertestnet-X.png](/img/user/para/artifacts/BitDevs-33-Hedgehog-Supertestnet-X.png)](https://x.com/super_testnet/status/1773613481633226911)

[![BitDevs-33-Hedgehod-X-Thread-1.png](/img/user/para/artifacts/BitDevs-33-Hedgehod-X-Thread-1.png)](https://x.com/super_testnet/status/1772656384972071243)

# Burrow

[![BitDevs-33-Rene-X-1.png](/img/user/para/artifacts/BitDevs-33-Rene-X-1.png)](https://x.com/renepickhardt/status/1772886817802539311)

> [!QUOTE] [Burrow: a federated coinpool built on hedgehog channels · GitHub](https://gist.github.com/supertestnet/14addffae669058a9bb9df2e2608ff7f)
> Burrow is a proposal for a **federated coinpool on top of [hedgehog channels](https://github.com/supertestnet/hedgehog)**. The coinpool can have a bunch of cool properties:
> - a single-honest-party assumption, so the federation can't rug any user unless the keyholders in the federation are all scoundrels
> - users can onboard into the pool without an on-chain transaction (e.g. maybe you send in coins via lightning, or maybe another user gives you your first coins from within the pool)
> - every onboarded user gets their own wallet interface with their own personal balance and Send/Receive buttons
> - no transfer fees within the pool, and internal transactions happen faster than lightning (due to no need for pathfinding, and no liveness assumption about the recipient -- only the server must be online)
> - users can issue off-chain "cheques" which are essentially vtxos that you give someone else the right to spend. The recipient does not need to be in the coinpool, they can be literally anyone. The cheque issuer can send the cheque to the recipient e.g. via email, and the recipient can redeem it off-chain even if the issuer is offline (but the server has to be online for this part, and can censor, though the issuer can override censorship via a force closure)
> - a lightning gateway can allow transferring sats into or out of the pool, e.g. for users who want to withdraw to a fully self custodial wallet (mining fees would apply there if you send to a base layer wallet, and routing fees if you send to a lightning wallet)

# More Resources
- [Hedgehog: Protocol for Asynchronous Layer 2 Bitcoin Payments](https://www.nobsbitcoin.com/introducing-hedgehog/)
- [GitHub - supertestnet/hedgehog: A protocol for improved layer two bitcoin payments](https://github.com/supertestnet/hedgehog)
- [Hedgehog Slideshow and Demo - YouTube](https://www.youtube.com/watch?v=eGz-54y31r8) ([link to slides](https://t.co/OfnvaniAc0))
- [Hedgehog Protocol - CoinCorner YouTube](https://youtu.be/tB2EAbJtLRU?feature=shared)
- [@super_testnet Thread on X describing interactivity between Hedgehog and Lightning Network](https://x.com/super_testnet/status/1800515195124748503)
- [Burrow: a federated coinpool built on hedgehog channels · GitHub](https://gist.github.com/supertestnet/14addffae669058a9bb9df2e2608ff7f)