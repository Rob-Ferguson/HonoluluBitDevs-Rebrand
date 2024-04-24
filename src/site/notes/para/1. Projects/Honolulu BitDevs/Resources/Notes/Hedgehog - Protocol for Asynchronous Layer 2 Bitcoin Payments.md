---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Hedgehog - Protocol for Asynchronous Layer 2 Bitcoin Payments.md","permalink":"/bit-devs/resources/notes/hedgehog-protocol-for-asynchronous-layer-2-bitcoin-payments/","title":"Hedgehog - Protocol for Asynchronous Layer 2 Bitcoin Payments","tags":["bitdevs","bitcoin","socratic-33","scaling"],"noteIcon":"3","created":"2024-04-23T21:56:11.623-10:00","updated":"2024-04-23T22:17:28.474-10:00"}
---

# Hedgehog

[![Pasted image 20240423220133.png](/img/user/para/artifacts/Pasted%20image%2020240423220133.png)](https://x.com/callebtc/status/1772650750465691703)

> [!QUOTE] [GitHub - supertestnet/hedgehog: A protocol for improved layer two bitcoin payments](https://github.com/supertestnet/hedgehog)
> Hedgehog is a protocol for two party payment channels. Hedgehog channels are similar to lightning channels but with a few comparative benefits.
> - **Hedgehog channels are simpler than lightning channels**
> - **State updates only require the sender to propose an update and the recipient to accept it**
> - **The recipient can wait to accept a state change til they want to propose another one**
> 
> The properties mentioned above allow for an improved payment experience. **Using hedgehog feels similar to using an ecash protocol like cashu or fedimint, except with no server.** If you have a channel with someone, you can -- without their assistance -- create a payment for them, embed it in a piece of text (think of it like a cheque), and send it to them via email or some other communication method. Then you can go offline. When they get online, they can either accept the state change (the cheque) and update their balance without your further assistance, or they can reject it. If they accept the state change (the cheque) they can even use their new balance to pay you back later by making another state change (another cheque) that builds on the previous state change (i.e. spends the cheque to make a new cheque). And they can send the new state change (the new cheque) to you even if you are still offline. Or, if they reject your state change, they can propose an alternative one and wait for you to accept that.

[![Pasted image 20240423220739.png](/img/user/para/artifacts/Pasted%20image%2020240423220739.png)](https://youtu.be/-JeBDVPH1gA?feature=shared)

[![Pasted image 20240423220403.png](/img/user/para/artifacts/Pasted%20image%2020240423220403.png)](https://x.com/super_testnet/status/1773613481633226911)

[![Pasted image 20240423220301.png](/img/user/para/artifacts/Pasted%20image%2020240423220301.png)](https://x.com/super_testnet/status/1772656384972071243)

# Burrow

[![Pasted image 20240423215948.png](/img/user/para/artifacts/Pasted%20image%2020240423215948.png)](https://x.com/renepickhardt/status/1772886817802539311)

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
- [Burrow: a federated coinpool built on hedgehog channels · GitHub](https://gist.github.com/supertestnet/14addffae669058a9bb9df2e2608ff7f)