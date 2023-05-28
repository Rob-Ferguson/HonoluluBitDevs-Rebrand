---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Ark.md","permalink":"/bit-devs/resources/notes/ark/","title":"Ark","noteIcon":"3","created":"2023-05-25T08:46:04.999-10:00","updated":"2023-05-28T11:16:26.026-10:00"}
---


Created by [@brqgoo](https://twitter.com/brqgoo). It's a second-layer protocol for making cheap, anonymous off-chain Bitcoin payments - a protocol implementation that follows the the [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Enigma Network\|Enigma Network]] framework.

Although it would benefit from [[para/1. Projects/Honolulu BitDevs/Resources/Notes/OP_CTV\|OP_CTV]]-like covenants, Ark can work on bitcoin today with the tradeoff of requiring interactivity.

> [!QUOTE] [Introducing Ark](https://burakkeceli.medium.com/introducing-ark-6f87ae45e272) (narrated on [Bitcoin Audible 734](https://fountain.fm/episode/HwfNHEd6chfAsaAqvtYA))
> - Ark allows recipients to receive payments without acquiring inbound liquidity while preserving their receiver privacy. The protocol is as private as WabiSabi, as convenient as on-chain, and as cheap as Lightning.
> - Ark is a trustless, distinct layer two protocol with unilateral exit.
> - ASPs cannot steal users’ funds or link senders & receivers. Users retain self-custody and can revert their funds to the base layer if something goes wrong on the second layer.
> - Ark has a utxo set that lives off the chain. These utxos are referred to as virtual utxos or vtxos in short.
> - Ark payments settle every 5 seconds and final in every block.
> - Users need to wait for on-chain confirmations to consider a payment ‘final’. However, this doesn’t prevent them from paying invoices with their zero-conf coins.
> - Ark has immediate availability with delayed finality.
> - Ark ensures “absolute atomicity” by using ATLCs instead of HTLCs. Users can receive payments and forward them further without waiting for confirmations. A mempool-level double-spend breaks the atomicity. ASPs cannot redeem senders’ vTXOs if they double-spend recipients’ vTXOs.
> - Ark provides an order of magnitude greater level of privacy compared to Lightning. Every payment on the protocol takes place in a coinjoin round. This obfuscates the trace from the sender to the receiver. The anonymity set is everyone who involves in a payment.
> - Numbers tell us it would take +100 years to onboard the whole population into lightning in a non-custodial way, assuming it takes 4 channels per human and an average channel opening consumes a few hundred vBytes.

Here is how Burak compares Ark's properties to Lightning or on-chain:

![ArkComparisonChart.png](/img/user/para/artifacts/ArkComparisonChart.png)





# More Resources
- [arkpill.me](https://www.arkpill.me/)
- [Ark Community Telegram](https://t.me/ark_network_community)

[![@_arshbot_Tweet_Ark.png](/img/user/para/artifacts/@_arshbot_Tweet_Ark.png)](https://twitter.com/_arshbot/status/1661929814427860997)

