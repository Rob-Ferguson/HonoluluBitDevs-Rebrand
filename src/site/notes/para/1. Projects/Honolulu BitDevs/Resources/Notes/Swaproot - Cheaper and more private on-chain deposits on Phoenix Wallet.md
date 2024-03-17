---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Swaproot - Cheaper and more private on-chain deposits on Phoenix Wallet.md","permalink":"/bit-devs/resources/notes/swaproot-cheaper-and-more-private-on-chain-deposits-on-phoenix-wallet/","title":"Swaproot - Cheaper and more private on-chain deposits on Phoenix Wallet","tags":["socratic-32","bitcoin","lightning","taproot"],"noteIcon":"3","created":"2024-03-16T15:46:22.675-10:00","updated":"2024-03-16T20:07:16.603-10:00"}
---



[Phoenix](https://phoenix.acinq.co/) is one of the most user-friendly self-custodial Lightning wallets in the space. 

A key construction within Phoenix is [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Lightning Channel Splicing\|splicing]], which is a process by which you can transfer funds from onchain outputs into Lightning payment channels (or vice versa) while leaving the channel fully operational during confirmation delays.

A `swap-in` is an on-chain transaction that can be used to add funds to a Lightning channel via splicing. Phoenix uses a trustless, instant swap-in protocol based on [swap-in potentiam](https://lists.linuxfoundation.org/pipermail/lightning-dev/2023-January/003810.html).

**Before Swaproot, swap-in transactions faced several challenges**:

1. "Pay-to-script" transactions were costly, and the cost is paid not when they are published but when they are spent, because the spending transaction must include the complete script that is used.
2. These transactions lacked privacy, as their unique nature made them easily traceable on the blockchain, particularly in the case of Phoenix swap-ins.
3. Developing a universal recovery method, especially for refunds, was complex, leading to the repetitive use of the same address for swap-ins and compromising privacy.

**Phoenix designed the new Swaproot protocol to address these limitations by leveraging a combination of Taproot, MuSig2, and Miniscript descriptors.** 

> [!QUOTE] [Swaproot - Cheaper and more private on-chain deposits on Phoenix Wallet](https://acinq.co/blog/phoenix-swaproot)
> **TL; DR:** Depositing on-chain funds to Phoenix is now **cheaper(\*) and more private**, thanks to a combination of powerful new features added to Bitcoin and Lightning in the last few years.
> 
> (\*) **by 16% if the swap transaction has one input, 23% for 2 inputs, 27% for 3 inputs.**
> 
> Last year, we published a [major upgrade](https://acinq.co/blog/phoenix-splicing-update) to our Phoenix wallet: users now have a single channel that will grow and shrink on-demand.
> 
> One of the key features included in this upgrade was trustless, instant “swap-ins”: you can send funds to your wallet’s on-chain address, and they will be “spliced” into your existing channel.
> 
> But the swap-in protocol that we designed for this upgrade could be improved:
> - the swap-in address displayed by Phoenix was static, which is a privacy issue;
> - swap-in transactions sent to Phoenix had specific features that made them easy to track on-chain, which is also a privacy issue.
> 
> **Using Taproot, MuSig2 and bitcoin descriptors, we designed and implemented a new swap-in protocol: swap-in transactions are now cheaper, harder to track on-chain, and Phoenix will generate a new swap-in address every time you receive a transaction.**
> 
> ---
> 
> ## Conclusion
> 
> Our swap-in protocol is standing on the shoulder of giants:
> - The dual-funding and the interactive transaction protocol that was merged into [the Lightning specifications](https://github.com/lightning/bolts/pull/851);
> - The Taproot upgrade, which makes bitcoin script more powerful and more private;
> - MuSig2, which enables key and signature aggregation;
> - The work on descriptors and miniscript, with extensive support added to Bitcoin Core 26.
> 
> All these features and protocols may seem daunting at first, and it may be difficult to see how they benefit end users. Here it becomes obvious: **they are tools to build better, less expensive, more private protocols that are also easier to use**. Which is what Phoenix is all about!

Among other things, Taproot introduced `key-path` and `script-path` spending, Schnorr signatures, and a new design for `pay-to-script` transactions that can make them indistinguishable from regular transactions on-chain. This allowed Phoenix to redesign their swap-in script to use a single public key created from the aggregation of user and server keys using MuSig2.

MuSig2 is an algorithm for combining public keys and signatures. It's particularly effective with Schnorr signatures and allows the creation of a single public key from multiple keys. With MuSig2, Phoenix aggregates the user key and server key into a single public key that can be used in Taproot `key-path` spends, making the script function like this: `aggregated user + server key OR user key + delay`.

Descriptors, a language for describing wallet patterns, play a crucial role in implementing swap-in address rotation and a recovery procedure. By using descriptors, Phoenix can generate unique swap-in addresses for each transaction while maintaining a single, compact descriptor for recovery. This system not only improves privacy by creating different addresses for each new refund key but also keeps swap-in outputs indistinguishable from regular transactions.

> [!QUOTE] [Swap-in-Potentiam: Moving Onchain Funds "Instantly" To Lightning](https://lists.linuxfoundation.org/pipermail/lightning-dev/2023-January/003810.html)
> In this writeup, we present a novel protocol, **swap-in-potentiam**, that can be used for immediate transfer from the blockchain layer to the Lightning layer, in the above user story.
> 
> ## Advantages And Limitations
> 
> To whet your appetite, here are **the advantages**:
> - Immediate transfer of already-confirmed-received onchain funds to Lightning.
> - Onchain funds can also be transferred to another onchain address (subject to normal onchain confirmation rules).
> - This can be "immediate" if sending to a receiver that accepts the risk of 0-conf onchain transactions.
> - Minimized trust requirement.
>
> **The disadvantages**, to help convince you that yes, this is technology and not magic beans (and to not oversell this tech, Bitcoin media reporting often tend to oversell new technologies because the disadvantages are often hidden away behind technical minutae):
> 
> - Requires a cooperating LSP. If LSP is down or refuses to cooperate, onchain funds are locked for some time. This has a timeout (so if the LSP never comes online again, you just wait out the timeout) and the timeout starts from when the receiving UTXO is confirmed in a block, so it will not cause loss of funds, only loss of opportunity (i.e. "involuntary HODLing").
> - If you have multiple LSPs, when you generate an address you *have to* select one of them at that point, you *cannot* commit to multiple LSPs and select one of them later when your phone wakes up again. This exacerbates the above disadvantage, since you have to select one of your LSPs and hope that when your phone wakes up the LSP you selected is also up and cooperative.
> - The onchain-received funds have to be confirmed first, otherwise we still need to wait for confirmation of the onchain-received funds. This is generally true for many blockchain-only wallets anyway and is thus not a worsening, but is also not an improvement.
> - If the timeout is too near, actions must be performed onchain that require confirmation.
> 
> ---
> 
> **The use-cases** this enables are:
> - If Alice wants to pay to another onchain address, and Bob is also online and cooperative, Alice can ask Bob to help sign the Onchain/channel branch to move the funds in any arbitrary onchain manner.
> - If Alice wants to pay to a Lightning invoice / keysend, and has insufficient Lightning outgoing capacity (but has sufficient *total* capacity), it can swap with Bob, by offerring a transaction that spends via the Onchain/channel  branch and instantiates a fresh onchain HTLC that Bob can then forward over Lightning. As soon as Alice offers its signature of that transaction, Bob can immediately offer an in-Lightning HTLC to Alice on their channel, and then Alice can immediately resolve it (thus immediately getting its funds into Lightning).
> - If Bob is offline or uncooperative, Alice can unilaterally recover its funds after the timeout in the Timelock branch.
> 
> Trust is required only to the extent that Alice trusts Bob to be cooperative so that Alice can dispose of its funds immediately. In case Bob turns out to be non-trustworthy, Alice can recover its funds via the timelock branch after the timeout period. There is no scope for Bob to steal funds (indeed, it is easier for Bob to steal Lightning funds than to steal swap-in-potentiam funds).
> 
> The intent here is that the mobile wallet is Alice, while the LSP is Bob.

