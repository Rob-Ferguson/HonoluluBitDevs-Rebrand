---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Enigma.md","permalink":"/bit-devs/resources/notes/enigma/","title":"Enigma","noteIcon":"3","created":"2023-05-24T21:04:53.112-10:00","updated":"2023-05-28T14:36:04.519-10:00"}
---


Created by [@Polyd_](https://twitter.com/Polyd_). It's a separate scaling layer that leverages [[para/1. Projects/Honolulu BitDevs/Resources/Notes/OP_CTV\|OP_CTV]] covenants. Users send "anchor" bitcoin transactions that commit to a larger set of off-chain transactions by embedding their combined hash into blocks on the base layer. The transactions getting hashed into the blockchain are effectively aggregated together with only a single on-chain transaction.

> [!QUOTE] [Bitcoin and CTV Covenants](https://app.sigle.io/polydeuces.id.stx/bo-iHio5_4iTlvWwXwZ9l)
> - In Bitcoin today, if you need to perform a transaction, you acquire the recipient’s address, create a transaction paying them and then sign it. The Enigma Network will allow you to multi-thread your actions. Instead of sending transactions to be directly mined inside a block, you send an anchor transaction representing all of your transactions.
> - BIP-119 or CheckTemplateVerify (CTV), introduces the capability to pre-commit transactions through pre-signed hashed transactions.
> - To put it in perspective, if Taproot enables signature aggregation, CTV takes it a step further by enabling transaction aggregation. If channels allow you to go up and off-chain, covenants allow you to go down and in-chain.

The Enigma Network is more of a framework that other protocols can fit into. [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Ark\|Ark]] and [Darkpool](https://www.nobsbitcoin.com/darkpool-tarpit/) are examples, according to [@Polyd_](https://twitter.com/Polyd_/status/1661654154962427904?s=20).

Some useful analogies describing Enigma:

[![@OwenKemeys_Tweet_EnigmaAnalogy.png](/img/user/para/artifacts/@OwenKemeys_Tweet_EnigmaAnalogy.png)](https://twitter.com/OwenKemeys/status/1657445153273946119)

[![@z3ke_sk1_Tweet_EnigmaAnalogy.png](/img/user/para/artifacts/@z3ke_sk1_Tweet_EnigmaAnalogy.png)](https://twitter.com/z3ke_sk1/status/1658152242875170818)

# More Resources
- [Stacker News post about the Enigma Network](https://stacker.news/items/178371)