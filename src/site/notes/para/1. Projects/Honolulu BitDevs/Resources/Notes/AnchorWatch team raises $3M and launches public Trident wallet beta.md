---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/AnchorWatch team raises $3M and launches public Trident wallet beta.md","permalink":"/bit-devs/resources/notes/anchor-watch-team-raises-3-m-and-launches-public-trident-wallet-beta/","title":"AnchorWatch team raises $3M and launches public Trident wallet beta","tags":["bitdevs","bitcoin","custody","miniscript","multisig","socratic-27"],"noteIcon":"3","created":"2023-09-24T20:25:11.093-10:00","updated":"2023-10-11T16:31:43.969-10:00"}
---



[![BitDevs-27-RobHamilton-TridentBeta-1.png](/img/user/para/artifacts/BitDevs-27-RobHamilton-TridentBeta-1.png)](https://x.com/Rob1Ham/status/1704917235305746439?s=20)

# What happened?

Rob Hamilton, CEO of AnchorWatch, announced the public testnet beta for their forthcoming [Trident Vault](https://www.tridentvault.com) wallet coordinator.

Trident is interesting because it is one of the first enterprise-grade wallets to leverage **miniscript**, which the AnchorWatch team believes can redefine best practices around bitcoin custody.

Soon after introducing the public beta, AnchorWatch also [announced a $3M funding round led by Ten31](https://www.nobsbitcoin.com/anchorwatch-raises-3m-funding-round-led-by-ten31/).

> [!QUOTE] [AnchorWatch Raises $3M to Solidify Bitcoin Custody and Insurance Platform](https://www.prnewswire.com/news-releases/anchorwatch-raises-3m-to-solidify-bitcoin-custody-and-insurance-platform-301938468.html)
> AnchorWatch's proprietary Trident Vault software provides a protocol native custody solution to owners of bitcoin, backed by regulated high-quality insurance.
> 
> With this latest investment, AnchorWatch will be in position to complete all regulatory and capital requirements needed to deliver Trident Vault to customers and start selling policies. Additionally, AnchorWatch will undergo security audits by a number of credentialed firms to further solidify Trident Vault as a sound and viable custody solution for enterprise use.
> 
> ---
> 
> AnchorWatch achieves its superior collaborative custody in two ways. First, their Trident Vault enables supported custody by holding a minority of keys and employing protocol-level governance and compliance. With layered security, Trident Vault allows bitcoin to be custodied in a method that suits its technology by dispersing custody physically and among unrelated entities, reducing risks of loss from catastrophic events like fires and floods, but also from theft by internal and external bad actors.
> 
> Secondly, AnchorWatch embeds regulated property insurance on the bitcoin in a Trident Vault itself. This guarantees that assets are insured in the case of catastrophe via regulated and collateralized property insurance. Because Trident enables superior security during custody, AnchorWatch is able to offer insurance at affordable rates.

# What is miniscript?

> [!QUOTE] [What Is Bitcoin Miniscript? - The Bitcoin Manual](https://thebitcoinmanual.com/articles/btc-miniscript/)
> Miniscript was designed and implemented by Pieter Wuille, Andrew Poelstra, and Sanket Kanjalkar at Blockstream Research as a result of working on [multi-sig](https://thebitcoinmanual.com/security/multi-sig/) implementations but is the conclusion of discussions with several other people who have had to deal with bitcoin scripting in the past and found it difficult or time-consuming to work with and compile.
> 
> **Miniscript is a standardisation of bitcoin scripts; think of it as turning each script into a building block that any bitcoin wallet could use as a method of compiling transactions on the back end based on what the user would like to achieve.**
> 
> Minscript allows the software to automatically analyse a script, including determining what witness data must be generated to spend bitcoins protected by that script. It saves wallet developers time as they don’t need to write new code when they switch from one script template to another and would provide better interoperability for users switching between wallets.
> 
> The structured representation of Bitcoin scripts provided by miniscript allows wallets to be much more dynamic about the scripts they use while also being efficient in compiling transactions and slightly reducing the footprint of a transaction on-chain.
> 
> In support of that dynamism, miniscripts can be created using an easily-written policy language. Policies are composable, allowing any valid sub-expression to be replaced by another valid sub-expression (within certain limits imposed by the Bitcoin system).
> 
> **This brings the promise of more complex [smart contracts](https://thebitcoinmanual.com/articles/what-is-a-bitcoin-smart-contract/) directly on the base chain and offers users more flexible solutions for self-custody that can make it easier and safer to hold your own keys.**


# How does AnchorWatch use miniscript?

## Social recovery

[![BitDevs-27-Trident-ui-social-recovery.png](/img/user/para/artifacts/BitDevs-27-Trident-ui-social-recovery.png)](https://x.com/Rob1Ham/status/1704917244734566856?s=20)

## Multi-institutional custody

[![BitDevs-27-Trident-ui-multi-institutional.png](/img/user/para/artifacts/BitDevs-27-Trident-ui-multi-institutional.png)](https://x.com/Rob1Ham/status/1704917250736574744?s=20)

# More Resources
- [AnchorWatch - Trident Wallet](https://www.tridentvault.com/)
- [Rob Hamilton Trident beta announcement Tweet](https://x.com/Rob1Ham/status/1704917235305746439?s=20)
- [TFTC 441: Miniscript and Bitcoin Risk Products with Rob Hamilton](https://tftc.io/tftc-podcast/441/)
- [What Is Bitcoin Miniscript? - The Bitcoin Manual](https://thebitcoinmanual.com/articles/btc-miniscript/)
- [BitBox blog: Understanding Bitcoin Miniscript (Part 1) - How does Bitcoin Script work, and why is it so difficult?](https://bitbox.swiss/blog/understanding-bitcoin-miniscript-part-1/)
- [BitBox blog: Understanding Bitcoin Miniscript (Part 2) - What's Miniscript, and how does it make Bitcoin scripting easier?](https://bitbox.swiss/blog/understanding-bitcoin-miniscript-part-2/)