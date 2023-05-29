---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/OP_CTV.md","permalink":"/bit-devs/resources/notes/op-ctv/","title":"OP_CTV","noteIcon":"3","created":"2023-05-24T20:15:13.066-10:00","updated":"2023-05-29T11:11:47.999-10:00"}
---


[BIP-119](https://github.com/bitcoin/bips/blob/master/bip-0119.mediawiki) (OP_CHECKTEMPLATEVERIFY) was pioneered by [Jeremy Rubin](https://rubin.io/). 

> [!QUOTE] [Bitcoin Optech](https://bitcoinops.org/en/topics/op_checktemplateverify/)
> - **OP_CHECKTEMPLATEVERIFY (CTV)** is a proposed new opcode that takes a commitment hash as a parameter and requires any transaction executing the opcode include a set of outputs that match the commitment. This makes it possible to create an address that specifies how any funds received to that address may be spent—a design known in Bitcoin as a _covenant_.

Like most proposed bitcoin soft forks, OP_CTV has been met with extreme skepticism, but the strongest argument against it has been that there simply weren't enough obvious benefits relative to potential risks. Many [covenant proposals](https://bitcoincovenants.com) have circulated over the years, all with varying tradeoffs and degrees of interest/support. Technically, OP_CTV is likely one of the most well-studied and least risky of those alternatives to enable general covenant functionality.

Interest in OP_CTV has renewed recently as more compelling use cases have emerged, particularly around scaling and privacy improvements. It could generally enable more sophisticated smart contracts on bitcoin (e.g., "Merkleize All The Things"/[MATT contracts](https://merkle.fun/)).

By using OP_CTV commitments to form channel-like network constructions, for example, additional [scaling](https://utxos.org/uses/scaling/) solutions like [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Enigma\|Enigma]],  [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Ark\|Ark]], and [Darkpool](https://www.nobsbitcoin.com/darkpool-tarpit/) are enabled.

> [!QUOTE] [A Collection of Resources Related to Covenants](https://www.nobsbitcoin.com/a-collection-of-resources-related-to-covenants/)
> ## CTV Activation - Pros and Cons
> 
> ### Pros
> - "Covenants have been discussed for more than 6 years."
> - "There is strong consensus that Bitcoin should support covenants."
> - "CTV is the most conservative approach to enable covenants."
> - "The BIP was finalized over two years ago."
> - "The code is well tested and reviewed."
> - "People are testing vaults and other covenants live on the CTV signet."
> - "There are no objections against CTV on the code level."
> - "For 5 months there has been a 5.5 BTC bug bounty program funded by community members."
> - "Many community members support the activation of CTV."
> 
> ### Cons
> - "The strongest technical argument against bip119 is: since we have to do some soft fork for covenants let’s activate full-featured covenants right away instead of causing multiple forks with overlapping features."
> - "The most likely alternative seems to be TXHASH + CSFS. It combines Eltoo fans with ctv fans in a way that makes technical sense, it satisfies those who want more complex covenants going forward, the conversational well around it is less poisoned. The main downside is that it uses a few more bytes. The work that needs to be done to get it in safely can be overcome with effort."
> - "However, nobody is working on it. There's no BIP yet. No review. Not even remotely a PR."
> - "The number of bitfields in TXHASH is high, so the limiting factor would be writing a large number of both tests and arguing that any possible permutation of those bitfields does not lead to some resource exhaustion attack on some inputs."
> - "It would take years to activate it."

# More Resources
- [utxos.org](https://utxos.org/)
- [A Collection of Resources Related to Covenants](https://www.nobsbitcoin.com/a-collection-of-resources-related-to-covenants/)
- [Covenants & CTV: What they are, how bitcoin custody might benefit, and risks to consider | Unchained](https://unchained.com/blog/covenants-ctv-bitcoin-custody/)
- [OP_CTV - Summer Softfork Shenanigans | BitMEX](https://blog.bitmex.com/op_ctv-summer-softfork-shenanigans/)
- [Bitcoin Magazine OP_CTV articles](https://bitcoinmagazine.com/tags/op-ctv)
- [What does OP_CTV mean for me?](https://zensored.substack.com/p/what-does-op-ctv-mean-for-me)

[![@giacomozucco_Tweet_CTV.png](/img/user/para/artifacts/@giacomozucco_Tweet_CTV.png)](https://twitter.com/giacomozucco/status/1661716843512381447)

[![BitcoinErrorLog_CTV_Dissent.png](/img/user/para/artifacts/BitcoinErrorLog_CTV_Dissent.png)](https://github.com/JeremyRubin/utxos.org/issues/28)
