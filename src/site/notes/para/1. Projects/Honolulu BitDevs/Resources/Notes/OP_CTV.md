---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/OP_CTV.md","permalink":"/bit-devs/resources/notes/op-ctv/","title":"OP_CTV","noteIcon":"3","created":"2023-05-24T20:15:13.066-10:00","updated":"2023-05-25T08:38:05.892-10:00"}
---


[BIP-119](https://github.com/bitcoin/bips/blob/master/bip-0119.mediawiki) (OP_CHECKTEMPLATEVERIFY) was pioneered by [Jeremy Rubin](https://rubin.io/). 

> [!QUOTE] [Bitcoin Optech](https://bitcoinops.org/en/topics/op_checktemplateverify/)
> - **OP_CHECKTEMPLATEVERIFY (CTV)** is a proposed new opcode that takes a commitment hash as a parameter and requires any transaction executing the opcode include a set of outputs that match the commitment. This makes it possible to create an address that specifies how any funds received to that address may be spent—a design known in Bitcoin as a _covenant_.

Like most proposed bitcoin soft forks, OP_CTV has been met with extreme skepticism, but the most compelling argument against it has been that there simply weren't enough obvious benefits relative to potential risks. Many [covenant proposals](https://bitcoincovenants.com) have circulated over the years, all with varying tradeoffs and degrees of interest/support. Technically, OP_CTV is likely one of the most well-studied and least risky of those alternatives to enable general covenant functionality.

Interest in OP_CTV has renewed recently as more compelling use cases have emerged, particularly around scaling and privacy improvements.

By using OP_CTV commitments to form channel-like network constructions, for example, additional [scaling](https://utxos.org/uses/scaling/) solutions like [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Enigma Network\|Enigma Network]] and [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Ark\|Ark]] are enabled.

# More Resources
- [utxos.org](https://utxos.org/)
- [Covenants & CTV: What they are, how bitcoin custody might benefit, and risks to consider | Unchained](https://unchained.com/blog/covenants-ctv-bitcoin-custody/)
- [OP_CTV - Summer Softfork Shenanigans | BitMEX](https://blog.bitmex.com/op_ctv-summer-softfork-shenanigans/)
- [Bitcoin Magazine OP_CTV articles](https://bitcoinmagazine.com/tags/op-ctv)
- [What does OP_CTV mean for me?](https://zensored.substack.com/p/what-does-op-ctv-mean-for-me)