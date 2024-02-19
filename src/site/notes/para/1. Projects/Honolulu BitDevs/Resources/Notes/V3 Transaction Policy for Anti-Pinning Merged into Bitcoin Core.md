---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/V3 Transaction Policy for Anti-Pinning Merged into Bitcoin Core.md","permalink":"/bit-devs/resources/notes/v3-transaction-policy-for-anti-pinning-merged-into-bitcoin-core/","title":"V3 Transaction Policy for Anti-Pinning Merged into Bitcoin Core","tags":["bitdevs","bitcoin","socratic-31"],"noteIcon":"3","created":"2024-02-17T22:21:12.451-10:00","updated":"2024-02-19T10:37:40.613-10:00"}
---

# What happened?

> [!QUOTE] [Bitcoin Optech Newsletter 289](https://bitcoinops.org/en/newsletters/2024/02/14/#bitcoin-core-28948)
> [Bitcoin Core PR 28948](https://github.com/bitcoin/bitcoin/issues/28948) adds support for (but does not enable) [version 3 transaction relay](https://bitcoinops.org/en/topics/version-3-transaction-relay/), allowing any v3 transaction that has no unconfirmed parent to enter the mempool according to the normal transaction acceptance rules. The v3 transaction can be [CPFP fee-bumped](https://bitcoinops.org/en/topics/cpfp/) but only if the child is 1,000 vbytes or less. Each v3 parent may only have one unconfirmed child transaction in the mempool and each child may only have one unconfirmed parent. Either the parent or child transaction can always be [replaced by fee](https://bitcoinops.org/en/topics/replace-by-fee/). The rules only apply to Bitcoin Core’s relay policy; at the consensus layer, v3 transactions are validated the same as version 2 transactions defined in [BIP68](https://github.com/bitcoin/bips/blob/master/bip-0068.mediawiki). The new rules are intended to help contract protocols such as LN ensure their precommitted transactions can always be confirmed quickly with minimal extra fees needed to escape [transaction pinning attacks](https://bitcoinops.org/en/topics/transaction-pinning/). [🎧](https://bitcoinops.org/en/podcast/2024/02/15/#bitcoin-core-28948)

# What is V3 TX Relay?

[![BitDevs-31-V3TxRelay-SLP-Thumbnail.png](/img/user/para/artifacts/BitDevs-31-V3TxRelay-SLP-Thumbnail.png)](https://www.youtube.com/watch?v=H1o7TgTCMjk)

> [!QUOTE] [Version 3 Transaction Relay | Bitcoin Optech](https://bitcoinops.org/en/topics/version-3-transaction-relay/)
> **Version 3 transaction relay** is a proposal to allow transactions to opt-in to a modified set of transaction relay policies designed to prevent pinning attacks. Combined with package relay, these policies help enable the use of dynamic feerates with LN onchain transactions.
> 
> V3 transaction relay is a superset of standard transaction policy. That is, v3 transactions follow all rules for standard transactions (e.g. minimum and maximum transaction weights) while also adding some additional rules designed to allow [transaction replacement](https://bitcoinops.org/en/topics/replace-by-fee/) while precluding transaction-pinning attacks. v3 transactions also require minor changes to the [package RBF](https://bitcoinops.org/en/topics/package-relay/) policy in order to maintain incentive compatibility with miners.
> 
> V3 transaction relay solves rule 3 [transaction pinning](https://bitcoinops.org/en/topics/transaction-pinning/) and may allow the removal of the [CPFP carve-out](https://bitcoinops.org/en/topics/cpfp-carve-out/).
> 
> Version 3 transactions are used by [ephemeral anchors](https://bitcoinops.org/en/topics/ephemeral-anchors/).

> [!QUOTE] [v3 transaction policy for anti-pinning by glozow · Pull Request 28948 · bitcoin/bitcoin · GitHub](https://github.com/bitcoin/bitcoin/pull/28948)
> Rationale:
> - There are various pinning problems with RBF and our general ancestor/descendant limits. These policies help mitigate many pinning attacks and make package RBF feasible (see [Cluster size 2 package rbf 28984](https://github.com/bitcoin/bitcoin/pull/28984) which implements package RBF on top of this). I would focus the most here on Rule 3 pinning. [1][2]
> - Switching to a cluster-based mempool (see [Proposal for a new mempool design 27677](https://github.com/bitcoin/bitcoin/issues/27677) and [[WIP] Cluster mempool implementation 28676](https://github.com/bitcoin/bitcoin/pull/28676)) requires the removal of CPFP carve out, which applications depend on. V3 + package RBF + ephemeral anchors + 1-parent-1-child package relay provides an intermediate solution.
> 
> V3 policy is for "Priority Transactions." [3][4] **It allows users to opt in to more restrictive topological limits for shared transactions, in exchange for the more robust fee-bumping abilities that offers.** Even though we don't have cluster limits, we are able to treat these transactions as having as having a maximum cluster size of 2.
> 
> **Immediate benefits:**
> **- You can presign a transaction with 0 fees (not just 1sat/vB!) and add a fee-bump later.**
> **- Rule 3 pinning is reduced by a significant amount, since the attacker can only attach a maximum of 1000vB to your shared transaction.**
>  
> This also enables some other cool things (again see [27463](https://github.com/bitcoin/bitcoin/issues/27463) for overall roadmap):
> - Ephemeral Anchors
> - Package RBF for these 1-parent-1-child packages. That means e.g. a commitment tx + child can replace another commitment tx using the child's fees.
> - We can transition to a "single anchor" universe without worrying about package limit pinning. So current users of CPFP carve out would have something else to use.
> - We can switch to a cluster-based mempool [5] ([Proposal for a new mempool design 27677](https://github.com/bitcoin/bitcoin/issues/27677) [[WIP] Cluster mempool implementation 28676](https://github.com/bitcoin/bitcoin/pull/28676)), which removes CPFP carve out [6].

# More Resources
- [v3 transaction policy for anti-pinning by glozow · Pull Request 28948 · bitcoin/bitcoin · GitHub](https://github.com/bitcoin/bitcoin/pull/28948)
- [V3 transaction policy for anti-pinning - Protocol Design - Delving Bitcoin](https://delvingbitcoin.org/t/v3-transaction-policy-for-anti-pinning/340)
- [Peter Todd's V3 Transactions Review/Criticisms](https://petertodd.org/2023/v3-transactions-review)
- [Rebuttal to Peter Todd's V3 Criticisms](https://github.com/bitcoin/bitcoin/pull/28948#issuecomment-1873490509)
- [Transaction pinning | Bitcoin Optech](https://bitcoinops.org/en/topics/transaction-pinning/)