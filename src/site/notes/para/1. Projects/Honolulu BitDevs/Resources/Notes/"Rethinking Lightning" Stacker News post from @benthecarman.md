---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/\"Rethinking Lightning\" Stacker News post from @benthecarman.md","permalink":"/bit-devs/resources/notes/rethinking-lightning-stacker-news-post-from-benthecarman/","title":"\"Rethinking Lightning\" Stacker News post from @benthecarman","tags":["bitdevs","bitcoin","lightning","socratic-30"],"noteIcon":"3","created":"2024-01-20T21:36:40.968-10:00","updated":"2024-01-20T22:35:54.528-10:00"}
---

> [!QUOTE] [Rethinking Lightning](https://stacker.news/items/379225) - Ben Carman
> Over the last few months it feels the bitcoin community has gotten more and more jaded on lightning. To be honest, this is for good reason, back in 2017 we were promised a decentralized payment network that would always have cheap payments and everyone would be able to run their own node. Nowadays, the average lightning user actually isn't using lightning, they are just using a custodial wallet and the few of that do run lightning nodes often find it a burdensome task. For us at Mutiny Wallet, we are trying to make this better by creating a lightweight self-custodial wallet and in my opinion we have been executing on that dream fairly well.

# Overview

[@benthecarman](https://twitter.com/benthecarman) recently made an [insightful post on Stacker News](https://stacker.news/items/379225) acknowledging that Bitcoin's Lightning network has fallen short of many end users' expectations. His post critically examines the current state of the Lightning Network, discussing its limitations and proposing a mix of technical and strategic solutions to improve its scalability and user experience.

1. **Jaded Bitcoin Community on Lightning**: There's a growing disillusionment within the Bitcoin community regarding the Lightning Network. Initially promised as a decentralized network with cheap payments, many users now rely on custodial wallets instead of running their own Lightning nodes, which is often seen as too burdensome.

2. **Channel Liquidity Challenge**: One of the primary user experience (UX) issues with Lightning is channel liquidity. This unique requirement often confuses users, and there are no simple workarounds. While solutions like just-in-time (JIT) liquidity and splicing exist, they don't fully resolve the problem, leading to confusion over fee variations in day-to-day use.

3. **Offline Receive Problem**: Another major issue is the need to be online to receive payments, a requirement that contrasts sharply with the typical on-chain payment flow (and how most people think about payments generally). Attempts to address this, like Zeus Pay lightning addresses, have led to other problems.

4. **On-Chain Fees Impacting Liquidity**: Available liquidity doesn't always equate to the ability to receive payments. Even with sufficient liquidity, high on-chain fees can make receiving payments impractical, undermining the fundamental goal of avoiding on-chain fees with Lightning. As fees increase over, this problem will likely worsen.

5. **Potential Solutions**: The post discusses solutions like anchor channels, package relay, and ephemeral anchors, but notes these only mask underlying issues. They require users to have on-chain funds for fee bumps, complicating the UX for self-custodial users.

6. **Large Scale Nodes vs. Self-Custodial Nodes**: Carman suggests that while Lightning is an excellent payment protocol, its limitations become more apparent without scale. Most users prefer custodial wallets for their efficiency with small-scale retail payments. If we want to enable more sovereign commerce, we need to re-evaluate Lightning's role and accept that some tradeoffs may be necessary for less-technical users.

7. **Combining Large Scale Infrastructure with Self-Custodial Solutions**: Current solutions like Muun Wallet and Aqua Wallet offer partial fixes but don't address the root problem. Atomic swaps can improve UX but just offload these challenges to someone else.

8. **Scaling Ownership in Bitcoin**: The post explores the need for scaling UTXO (Unspent Transaction Output) ownership in Bitcoin, arguing that scaling ownership is as crucial as scaling payments. It discusses the potential of covenants via soft forks, like OP_CTV and OP_VAULT, which can scale ownership by restricting how UTXOs are spent - allowing for more flexible management of Bitcoin addresses and their spending conditions

9. **Fedimint as a Scaling Solution**: Carman is particularly optimistic about leveraging Fedimint (and Chaumian Ecash generally) as a reasonable way to offload some of these Lightning complexities. Fedimints allow for dynamic shared ownership over a group of UTXOs and can interoperate with Lightning - at the cost of requiring trust in a particular mint.

Despite these challenges, the Lightning Network is a useful tool for scaling bitcoin - users just need to manage their expectations and critically evaluate the tradeoffs available. 

# More Resources
- [@niftynei's comparison of Bitcoin layer 2 alternatives](https://gist.github.com/niftynei/5f9373568e2cf6d15db6c7546a43f763)