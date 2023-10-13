---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/BitVM - Compute Anything on Bitcoin.md","permalink":"/bit-devs/resources/notes/bit-vm-compute-anything-on-bitcoin/","title":"BitVM - Compute Anything on Bitcoin","tags":["bitdevs","bitcoin","socratic-27","multisig","keys"],"noteIcon":"3","created":"2023-10-11T19:36:25.638-10:00","updated":"2023-10-12T14:28:13.869-10:00"}
---



# What happened?

[Robin Linus](https://twitter.com/robin_linus) (from the [[para/1. Projects/Honolulu BitDevs/Resources/Notes/How ZeroSync hopes to reduce the costs of validating bitcoin nodes\|ZeroSync]] project) dropped the whitepaper for BitVM, a new mechanism to perform essentially any type of computation to happen off-chain and use that computation to control bitcoin on-chain (i.e., Turing-complete smart contracts). This proposal doesn't require any consensus changes to Bitcoin itself.

> [!QUOTE] [BitVM Whitepaper](https://bitvm.org/bitvm.pdf)
> BitVM is a computing paradigm to express Turing-complete Bitcoin contracts. This requires no changes to the network’s consensus rules. Rather than executing computations on Bitcoin, they are merely verified, similarly to optimistic rollups. A prover makes a claim that a given function evaluates for some particular inputs to some specific output. If that claim is false, then the verifier can perform a succinct fraud proof and punish the prover. Using this mechanism, any computable function can be verified on Bitcoin.
> 
> Committing to a large program in a Taproot address requires significant amounts of off-chain computation and communication, however the resulting on-chain footprint is minimal. As long as both parties collaborate, they can perform arbitrarily complex, stateful off-chain computation, without leaving any trace in the chain. On-chain execution is required only in case of a dispute.

[![BitDevs-27-BitVM-SuperTestnet-Tweet.png](/img/user/para/artifacts/BitDevs-27-BitVM-SuperTestnet-Tweet.png)](https://x.com/super_testnet/status/1711395898368856488?s=20)

# How does it work?

BitVM is a proposal that aims to bring arbitrary computation capabilities to Bitcoin without necessitating changes to the core Bitcoin protocol. It leverages logic gates, particularly NAND gates, to enable complex computations while providing a mechanism for on-chain enforcement in case of disputes.

[![BitDevs-27-BitVM-zkchesterton-Tweet.png](/img/user/para/artifacts/BitDevs-27-BitVM-zkchesterton-Tweet.png)](https://x.com/zkchesterton/status/1711421528300982414?s=20)

**Logic Gates and NAND Gates**
   - In digital computing, logic gates are fundamental building blocks that perform specific logical operations. A NAND gate is one such gate.
   - A NAND gate takes two binary inputs (0 or 1) and outputs 0 if both inputs are 1; otherwise, it outputs 1.

**Building NAND Gates in Bitcoin Script**
   - BitVM utilizes Bitcoin script, a simple programming language used for creating smart contracts on the Bitcoin network.
   - To build a NAND gate in Bitcoin script, it uses hashlocks and two lesser-known Bitcoin script opcodes: `OP_BOOLAND` and `OP_NOT`.
   - Hashlocks are used to create branching scripts that can be spent in one of two ways, depending on the preimage revealed. One path corresponds to 1, and the other to 0.

**Implementing NAND Gates**
   - You can implement a NAND gate in Bitcoin script by using `OP_BOOLAND` to simulate the opposite of a NAND gate and `OP_NOT` to reverse the value.
   - This allows you to perform a NAND operation on the scripting stack and verify the result using `OP_EQUALVERIFY`.
   - In this way, a NAND gate is implemented within Bitcoin script, and its operation can be enforced on-chain.

**Creating Complex Computation Structures**
   - Complex computations are achieved by connecting multiple logic gates, just like a computer processor combines logic gates to perform tasks.
   - Hashlocks are used to link these gates together in a series, ensuring that the output of one gate becomes the input for the next.

**Challenge and Response Game**
   - Users, or parties, encode the entire computation, including individual gates, hashlock choices, and outputs, into a tapleaf tree associated with a single Unspent Transaction Output (UTXO).
   - Both the prover (the party asserting correctness) and the verifier (the party checking correctness) pre-sign a series of transactions for a challenge and response game that can be executed on-chain.
   - Ideally, the entire computation is verified off-chain, and the parties cooperatively settle it by spending the funds together based on the outcome.

**Enforcement and Penalties**
   - BitVM's enforcement mechanisms function similarly to the Lightning Network.
   - If the prover stops cooperating or disputes arise, enforcement occurs on-chain.
   - The enforcement process involves locking funds with timelocks, using hashlocks to verify correct execution of specific gates, and challenging the prover to execute specific gates on-chain.
   - Only a few rounds of challenges are required to ensure the contract settles correctly, with various outcomes depending on the situation.

[![BitDevs-27-BitVM-SuperTestnet-Tweet-2.png](/img/user/para/artifacts/BitDevs-27-BitVM-SuperTestnet-Tweet-2.png)](https://x.com/super_testnet/status/1712275722562101367?s=52&t=fR1UfkkV0hfE5yaQW87bRg)

# What are the limitations/challenges?

   - It's **very early** - it will take a long time to create all the building blocks for more complex computation. At this stage, using BitVM basically means programming at the level of circuit design.
   - BitVM **requires a lot of data to be generated and processed**, which incurs an off-chain data management cost - tapleaf trees could theoretically grow to billions of leaves (requiring hundreds of megabytes for a reasonably complex program).
   - In the worst possible case, **you might need ~250 bitcoin transactions to settle an entire challenge/proof series** if the counterparty consistently disputes the computation outcome.
   - BitVM's current proposal is **limited to 2-party interactions**, restricting constructions like sidechains or rollups - multi-party smart contracts are supposedly theoretically possible, but more research is needed.
   - **Contracts are "one-time use"** (related to the 2-party limitation) - every time 2 people engage in one of these contracts, they have to set up an entirely new set of bitcoin transactions.

# More Resources

- [The Big Deal With BitVM: Arbitrary Computation Now Possible On Bitcoin Without A Fork](https://bitcoinmagazine.com/technical/the-big-deal-with-bitvm-arbitrary-computation-now-possible-on-bitcoin-without-a-fork) ([Bitcoin Audible Podcast 🎧](https://fountain.fm/episode/oLduobB1mIVFTA1wS65s))
- [Stephan Livera Podcast 520: What is BitVM? with Robin Linus and Super Testnet](https://stephanlivera.com/episode/520)
- [Super Testnet's "Tapleaf Circuits" BitVM proof of concept for bristol circuits](https://github.com/supertestnet/tapleaf-circuits)
- [@zkchesterton Tweet](https://x.com/zkchesterton/status/1711421528300982414?s=20)
- [@BobBodily Tweet](https://x.com/BobBodily/status/1711581484254192013?s=20)

> [!TIP] [@BTCillustrated Tweet](https://x.com/BTCillustrated/status/1712440417524810227?s=20)
> ![BitDevs-27-BitVM-Illustration-1.png](/img/user/para/artifacts/BitDevs-27-BitVM-Illustration-1.png)
> ![BitDevs-27-BitVM-Illustration-2.png](/img/user/para/artifacts/BitDevs-27-BitVM-Illustration-2.png)
> ![BitDevs-27-BitVM-Illustration-3.png](/img/user/para/artifacts/BitDevs-27-BitVM-Illustration-3.png)
> ![BitDevs-27-BitVM-Illustration-4.png](/img/user/para/artifacts/BitDevs-27-BitVM-Illustration-4.png)