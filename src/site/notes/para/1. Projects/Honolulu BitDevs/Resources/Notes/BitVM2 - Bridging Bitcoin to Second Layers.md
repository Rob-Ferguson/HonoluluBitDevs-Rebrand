---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/BitVM2 - Bridging Bitcoin to Second Layers.md","permalink":"/bit-devs/resources/notes/bit-vm-2-bridging-bitcoin-to-second-layers/","title":"BitVM2 - Bridging Bitcoin to Second Layers","tags":["bitcoin","bitdevs","socratic-37","scaling","sidechain"],"noteIcon":"3","created":"2024-08-17T13:45:19.068-10:00","updated":"2024-08-19T07:51:04.502-10:00"}
---



[![BitDevs-37-BitVM2-PDF.png](/img/user/para/artifacts/BitDevs-37-BitVM2-PDF.png)](https://bitvm.org/bitvm_bridge.pdf)

# Overview
BitVM2 is the second iteration of the [[para/1. Projects/Honolulu BitDevs/Resources/Notes/BitVM - Compute Anything on Bitcoin\|original BitVM design]].

> [!QUOTE] [Bitcoin's Programmability Draws Closer to Reality as Robin Linus Delivers 'BitVM2'](https://www.coindesk.com/tech/2024/08/15/bitcoins-programmability-draws-closer-to-reality-as-robin-linus-delivers-bitvm2/)
> Robin Linus, the Bitcoin developer who shook up the crypto tech landscape last year with a theoretical method of making the oldest and original blockchain [more programmable](https://www.coindesk.com/tech/2023/10/11/bitcoin-might-get-ethereum-style-smart-contracts-under-bitvm-plan/), is out with a second iteration called "BitVM2" – boasting dramatic improvements that could bring the concept closer to real-world implementation.
> 
> **The basic setup involves using cryptography to compress programs into sub-programs that can then be executed within Bitcoin transactions**, according to a [white paper](https://bitvm.org/bitvm_bridge.pdf) published Thursday by Linus along with five co-authors.
> 
> The programs are then "verified" – basically making sure nobody is trying to cheat or steal – in three on-chain transactions. In the previous version, the verification could take upwards of 70 transactions, according to one of the co-authors, Alexei Zamyatin, who separately works for a project called BOB, short for Build on Bitcoin.
> 
> A key improvement of the new version is that anyone can call into question a suspicious transaction, in a feature known as "permissionless challenging." In the original BitVM, which was published last October but never really put into any practical implementation, only a fixed set of operators could initiate challenges.
> 
> ---
> 
> **"Our new bridge design is simpler and more capital efficient," Linus told CoinDesk in a Telegram message. "The previous design caused liquidity issues both in terms of how much and for how long bridge operators had to lock collateral. Now, it requires less capital, which is locked for a shorter duration."**

> [!QUOTE] [@alexeiZamyatin on X](https://x.com/alexeiZamyatin/status/1824034904516051335)
> BitVM2 and BitVM Bridge: TLDR Today we released the BitVM2 tech and bridge paper! Huge thanks to brilliant [@robin_linus](https://twitter.com/robin_linus) [@lukas_aumayr](https://twitter.com/lukas_aumayr) Andrea Pelosi [@zetavar1](https://twitter.com/zetavar1)[@matteo_maffei](https://twitter.com/matteo_maffei)
> 
> **TLDR:**
> - BitVM2 is a major improvement over previous BitVM versions.
> - BitVM Bridge is now the most secure BTC bridge design.
> - The paper is the more comprehensive write-up of the BitVM2 design so far. 
> 
> **BitVM2 is:**
> - Secure: optimistic computation secured by Bitcoin
> - Practical: only 3 tx to complete a challenge
> - Permissionless: anyone can challenge BitVM Bridge is the most secure BTC bridge to date.
> - BTC Bridges so far: t-of-n multisigs, honest majority assumption.
> - BitVM Bridge: 1-of-n security model, where anyone can challenge and prevent theft.
>  
> **Tech TLDR**
> - Idea: BitVM2 enables arbitrary computation secured by Bitcoin.
> - How? Optimistic off-chain execution, on-chain fraud-proofs.
> - Why? Any bigger program implemented in Bitcoin Script does not fit into a Bitcoin block. So we run them off-chain. If there is a dispute, we challenge on-chain only the part of the computation that was incorrect. 
> 
> **BitVM2 Protocol ELI5**
> 1. Compress a program into a SNARK verifier, implemented in Bitcoin Script. Groth16 is approx 3GB in size.
> 2. Split the verifier into sub-program chunks, max 4MB each (can be run in a Bitcoin tx!)
> 3. Operator commits to the program during setup
> 4. When attempting to withdraw funds from BitVM2, the Operator can be challenged by anyone (e.g. if the peg-out was wrong).
> 5. If challenged, the Operator must reveal all intermediary program results.
> 6. If the Operator is cheating, one of the sub-program results will be fake. Anyone can disprove the Operator by executing that specific sub-program in a Bitcoin transaction, showing that the Operator claimed a fake computation.
> 7. Done! Bad Operator is kicked out and cannot access the BitVM funds (invalidated spend transaction).

# Key Features and Improvements

1. **Arbitrary Program Execution**: BitVM2 enables the execution of arbitrary programs on Bitcoin, combining Turing-complete expressiveness with Bitcoin's robust consensus security.
2. **Optimistic Computation**: The protocol assumes operators are honest unless proven otherwise through fraud proofs submitted by challengers.
3. **Permissionless Challenging**: Unlike its predecessor, BitVM2 allows any user with a Bitcoin full node to challenge faulty operators, enhancing the system's security and decentralization.
4. **Reduced On-Chain Transactions**: BitVM2 significantly reduces the number of on-chain transactions required to resolve disputes from up to 70 in the original design to just 3, executable within 1-2 weeks.
5. **No Consensus Changes**: Importantly, BitVM2 requires no changes to Bitcoin's consensus rules, making it easier to implement.

# BitVM Bridge
One of the most promising applications of BitVM2 is the BitVM Bridge protocol, which enhances Bitcoin bridges by:

- Reducing trust assumptions from an honest majority to existential honesty during setup
- Requiring only one active rational operator for liveness
- Enabling permissionless verification

> [!QUOTE] [@alexeiZamyatin on X](https://x.com/alexeiZamyatin/status/1824034904516051335)
> **BitVM Bridge ELI5**
> 
> The BitVM Bridge makes use of BitVM2 to implement a light-client bridge on Bitcoin! The most interesting part is the peg out.
> 1. Operators send BTC to withdrawing users and then reclaim the BTC from BitVM.
> 2. BitVM then checks that for a burn transaction on the L2, there is a correct peg-out on Bitcoin.
> 3. If all is correct, the Operator gets the BTC refunded.

> [!QUOTE] [@BobBodily on X](https://x.com/BobBodily/status/1824143355472908638)
> **Technical Deep Dive Example**
> 1. Compress a program into a SNARK verifier, implemented in Bitcoin Script. Groth16 is approx 3GB in size (this is all offchain). 
> 2. Split the verifier into sub-program chunks, max 4MB each so they can be run in a Bitcoin txn (all offchain) 
> 3. Operator commits to the program during setup (along with the signing committee signatures) 
> 4. Users deposit funds into the bridge and can mint a wrapped token on the L2. 
> 5. Users can then initiate a withdrawal of funds from the bridge with appropriate proof of burn from the L2. 
> 6. The Operator checks the validity of their request and fronts their withdrawal. 
> 7. The Operator then initiates a request to withdraw funds from the bridge as a reimbursement. 
> 8. When attempting to withdraw funds from BitVM2, the Operator can be challenged by anyone. 
> 9. To prevent spam challenges on the operator, users must lock up collateral to cover the operator challenge/response transaction cost. 
> 10. If challenged, the Operator must reveal all intermediary program results (this is expensive) 
> 11. If the Operator is cheating, one of the sub-program results will be fake. Anyone can disprove the Operator by executing that specific sub-program in a Bitcoin transaction, showing that the Operator claimed a fake computation. 
> 12. Then the bad Operator is kicked out and cannot access the BitVM funds (invalidated spend transaction).

[![BitDevs-37-BitVM2-Bridge-Diagram.png](/img/user/para/artifacts/BitDevs-37-BitVM2-Bridge-Diagram.png)](https://bitvm.org/bitvm_bridge.pdf)

# Bridge Limitations
> [!QUOTE] [@BobBodily on X](https://x.com/BobBodily/status/1824143355472908638)
> **Limitations**
> 
> **Active Signer Committee**
> Requires an active signer committee to all come together in the initial bridge setup phase. They have to pre-sign transactions since we don’t have covenants on Bitcoin yet. This has a 1-of-N trust assumption (at least one signer will be honest). Covenants (aka OP_CAT) removes this trust assumption.
> 
> **Operator Fronts Withdrawals**
> Operator has to front withdrawals (with a 1-2 week challenge period on their reimbursement from the bridge) so in the worst case, a bank run on the bridge would mean users would have to wait 1-2 weeks for a withdrawal.
> 
> **Expensive Challenge/Response**
> Challenge response transactions (in the event of a challenge) are large and expensive. This disincentivizes users from challenging malicious withdrawals. On the bright side, users can crowdsource funds to challenge a withdrawal. But for now, this limits BitVM applications to larger liquidity providers, and means you won’t be using BitVM bridging for BRC-20s, Runes, or Ordinals anytime soon.
> 
> **Pre-Signing to Emulate Covenants**
> We don’t have covenants yet, so you have to emulate covenants with pre-signed transactions. This means it is much more practical to use a fixed amount of Bitcoin in the BitVM bridge. You can always spin up multiple bridges for different amounts (0.5 BTC, 1 BTC, 10 BTC), but again, because the challenge / response process is expensive, this static amount will likely be too high for normal users. So expect large LPs to do the bridging, and users to do crosschain bridging to get in.

# More Resources
- [[para/1. Projects/Honolulu BitDevs/Resources/Notes/BitVM - Compute Anything on Bitcoin\|BitVM - Compute Anything on Bitcoin]] (original implementation)
- [BitVM 2: Permissionless Verification on Bitcoin](https://bitvm.org/bitvm2)
- [SNARK Verifier in Bitcoin Script | BitVM](https://bitvm.org/snark)
- [Bitcoin sidechain creators tout new ‘permissionless’ version BitVM2](https://cointelegraph.com/news/bitcoin-sidechain-creators-tout-new-permissionless-version-bitvm2)
- [Bitcoin's Programmability Draws Closer to Reality as Robin Linus Delivers 'BitVM2'](https://www.coindesk.com/tech/2024/08/15/bitcoins-programmability-draws-closer-to-reality-as-robin-linus-delivers-bitvm2/)
- [@delken_ on X](https://x.com/delken_/status/1824035558970274035)

