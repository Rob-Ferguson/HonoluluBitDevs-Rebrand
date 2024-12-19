---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Bitcoin Core's Loss of Focus.md","permalink":"/bit-devs/resources/notes/bitcoin-core-s-loss-of-focus/","title":"Bitcoin Core's Loss of Focus","tags":["bitcoin","bitdevs","consensus","socratic-40","protocol","development"],"noteIcon":"3","created":"2024-12-17T20:44:25.970-10:00","updated":"2024-12-18T20:10:44.271-10:00"}
---



Bitcoin Core contributor James O'Beirne made a controversial post on X criticizing the current maintainer/developer focus and the broader inefficiencies around incorporating new functionality into Bitcoin. He argues that we need to prioritize trustless UTXO ownership and push for changes that enable sovereign scaling methodologies before it's too late, arguing that centralization risk outweighs technical risks that could come from various opcodes.

> [!QUOTE] [@jamesob thread on X](https://x.com/jamesob/status/1860340932706730261)
> # BITCOIN CORE'S LOSS OF FOCUS 
> 
> The legacy technical leadership in bitcoin is becoming increasingly less effective. 
> 
> ---
> 
>  **Almost universally, Core and "graybeard" devs are not focusing on \_the\_ fundamental problem in bitcoin: preserving trustless UTXO ownership.** 
>  
>  **Instead they are distracted with valuable but secondary issues like mempool policy, Core code architecture, and minor IBD performance.** These things are important in their own right, but they fundamentally don't matter if in times of trouble most users can't take possession of their own coins. 
>  
>  Core devs are exceptionally talented people. The brightest engineers. But the priorities of the project are out of whack. 
>  
>  The aggregate focus does not reflect the thing that makes bitcoin a unique asset: trustless custody. 
>  
>  ---
>  
>   **Given the current limits of bitcoin, even upper-middle class Americans will not be able to self-custody, let alone the rest of the world.** 
>   
>   If bitcoin doesn't figure out how to ensure that most users have a trustless way of owning and sometimes moving coins, it will become basically indistinguishable from a gold ETF. A row in some OFAC-compliant database. Another financial widget that is subject to the regulatory dictates of government. 
>   
>   In fact, if bitcoin does not scale UTXO ownership, gold will have the advantage that at least small amounts of it \*can\* be self-custodied and traded peer-to-peer. The same won't be able to be said for bitcoin. **In a world where on-chain fees are in the thousands of dollars and there is not a workable, trustless layer two, most coins will be stuck with custodians.** 
>   
>   Forget payments. I'm talking about savings. I'm talking about less than checking-account volume. 1-2 transactions a month. 
>   
>   **If you think that most people should be able to DCA and withdrawal to self-custody once a month, maybe spend once every few years for big purchases, I've got news for you:** 
>   
>   **Given bitcoin's current limitations, only 18 million users can do that. A little over 5% of Americans.** 
>   
>   --- 
>   
>   Right now, the chain capacity is able to meet demand for self-custody because we are in a time of relative peace. 
>   
>   Most don't feel at risk keeping their bitcoin with a custodian. That can change very rapidly. 
>   
>   As bitcoin grows in value and challenges fiat currency, governments will increasingly want to control it. They won't ban it, which is now obvious, but almost certainly they will impose OFAC-like restrictions and possible wealth taxes. 
>   
>   **When the regulatory hammer comes down, tens of millions will look to withdrawal their coins into self-custody. But they may not be able to.** 
>   
>   --- 
>   
>   Unfortunately this risk does not seem to be top of mind in the current Core culture. 
>   
>   One instance of a tone-deaf Core response to this kind of problem relates to CTV. As [@JeremyRubin](https://x.com/JeremyRubin) has been pointing out for years, **CTV would be the most efficient way to guarantee that people can withdrawal coins from institutions in times of chain-panic and congestion, allowing exit to happen during crises without fully "unrolling" transactions.** I wrote about this at length in 2023, and why it seems there is no more efficient way to do this ([https://delvingbitcoin.org/t/thoughts-on-scaling-and-consensus-changes-2023/32#design-for-exit-5…](https://t.co/U2qqgZJYCt)). 
>   
>   And yet technical figureheads like [@TheBlueMatt](https://x.com/TheBlueMatt) and [@murchandamus](https://x.com/murchandamus) downplay the value of CTV, claiming that it has no compelling uses.
>   
>   CTV is one of the primitive building blocks that we need to figure out UTXO scaling solutions. (Not to mention its use in applications like vaults.) 
>   
>   Some Core devs might argue "well okay, maybe we need that functionality - but CTV isn't the right way to do it. We need to think harder!" 
>   
>   **The problem is that time is running out. As nation-states begin to enter the technical ecosystem, soft forks that promote scaling and self-custody will be more difficult to deploy. Powerful actors will not want bitcoin to change - they're perfectly happy letting regulated custodians act as the L2.** 
>   
>   As the market cap grows, the stakes of change go up, and it will be much harder to get economically relevant actors to run new consensus. 
>   
>   Because Core devs aren't paying close attention to the covenants conversation, they may not realize that CTV is upgradeable, simple, and well-tested. It's good enough. 
>   
>   **This gap in understanding partially reveals that those devs prefer to work on more smaller self-contained puzzle problems that are more tractable.** Maybe this is understandable given the fraught Core development process and historical drama of soft forks, but neither of those are an excuse for abandoning the core challenge of realizing bitcoin. 
>   
>   --- 
>   
>   Segwit and Taproot were massive changes, and I can almost understand why so much drama was spent on them. They both basically reinvented how locking scripts are stored and executed in bitcoin. 
>   
>   **But to make significant headway on finding a scaling solution for self-custody, it may only take a few opcodes - much more narrowly scoped bits of functionality. Changes that are much easier to test and reason about, and don't reinvent the engine of bitcoin.** 
>   
>   --- 
>   
>   As I continue campaigning for a renewed focus on scaling coin ownership, some may compare me to the "big blockers" of the 2017 scaling wars. 
>   
>   The big-blockers camp wanted to raise the blocksize for the sake of housing the world's P2P payments. They resisted the use of Lightning and other second layer solutions. 
>   
>   The reality is that they have been partially vindicated. Lightning has not solved our problems, and given the on-chain footprint that existing channel constructions require, it categorically cannot. Lightning certainly helps reduce on-chain payment volume once someone has opened a channel - but to do that for most people will require a layer 1 innovation. 
>   
>   I don't share the big blockers' objectives. 
>   
>   I don't think that trying to fit the world's P2P payments on the base chain is a reasonable target. 
>   
>   But the ability to resist near complete capture of UTXO custody by third-party financial institutions - \*that\* is intertwined with the core purpose of bitcoin. 
>   
>   In Satoshi's whitepaper, the first sentence claims "A purely peer-to-peer version of electronic cash would allow online payments to be sent directly from one party to another without going through a financial institution." 
>   
>   **If most users become unable to even take possession of their own coins a few times a year, we have failed on the objective.** 
>   
>   --- 
>   
>   I am not writing this out of any sense of antagonism. Yes, I am frustrated that after numerous attempts, Core devs are not engaging more productively with the few people trying to translate scaling strategies to the base layer. 
>   
>   **But I'm hoping that by calling attention to this issue, we can get some of these great minds to refocus on bitcoin's critical mission, and to realize that ossification will come sooner than we thought.** 
>   
>   The existing (and well-funded) power structures \*want\* stasis. 
>   
>   The recent show of rapid institutional affinity should make you suspicious that bitcoin in its current form isn't a threat to the fiat order. 
>   
>   The lack of "ivory tower" attendance in the recent OP\_NEXT and the broader covenants discourse demonstrates that, like many of America's elite institutions, there has been mission drift in bitcoin's technical elite. I hope this changes. 
>   
>   --- 
>   
>   **The risk of merging many of the opcodes proposed during the last few years is limited.** 
>   
>   OP\_CAT, OP\_CTV, lnhance, probably OP\_CCV, some others; they're all fine. If sufficiently tested, great additions to bitcoin. 
>   
>   **We can pretty easily mitigate what risk there is with comprehensive testing and analysis, provided the focus is there.** 
>   
>   The upside is almost infinite: a reasonable attempt to continue the preservation of bitcoin's unique function - trustless self-custody that is practically available to most.

[![BitDevs-40-Core-Focus-Lopp-X.png](/img/user/para/artifacts/BitDevs-40-Core-Focus-Lopp-X.png)](https://x.com/lopp/status/1860361355594789363)

[![BitDevs-40-Core-Focus-Peter-X.png](/img/user/para/artifacts/BitDevs-40-Core-Focus-Peter-X.png)](https://x.com/peterktodd/status/1860396809836753219)

[![BitDevs-40-Core-Focus-John-X.png](/img/user/para/artifacts/BitDevs-40-Core-Focus-John-X.png)](https://x.com/BitcoinErrorLog/status/1860550508076839067)

# More Resources
- [The Consensus Conundrum](https://bitcoinmagazine.com/culture/the-consensus-conundrum)

