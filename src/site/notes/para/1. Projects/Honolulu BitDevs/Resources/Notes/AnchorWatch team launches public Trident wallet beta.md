---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/AnchorWatch team launches public Trident wallet beta.md","permalink":"/bit-devs/resources/notes/anchor-watch-team-launches-public-trident-wallet-beta/","title":"AnchorWatch team launches public Trident wallet beta","tags":["bitdevs","bitcoin","socratic-26","custody","miniscript","multisig"],"noteIcon":"3","created":"2023-09-24T20:25:11.093-10:00","updated":"2023-09-24T21:50:06.659-10:00"}
---



[![BitDevs-27-RobHamilton-TridentBeta-1.png](/img/user/para/artifacts/BitDevs-27-RobHamilton-TridentBeta-1.png)](https://x.com/Rob1Ham/status/1704917235305746439?s=20)

# What happened?

Rob Hamilton, CEO of AnchorWatch, announced the public testnet beta for their forthcoming [Trident Vault](https://www.tridentvault.com) wallet coordinator.

Trident is interesting because it is one of the first wallets to leverage miniscript, which the AnchorWatch team believes can redefine best practices around bitcoin custody.


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