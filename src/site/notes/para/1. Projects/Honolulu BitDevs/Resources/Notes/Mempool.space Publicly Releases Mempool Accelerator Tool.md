---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Mempool.space Publicly Releases Mempool Accelerator Tool.md","permalink":"/bit-devs/resources/notes/mempool-space-publicly-releases-mempool-accelerator-tool/","title":"Mempool.space Publicly Releases Mempool Accelerator Tool","tags":["bitcoin","bitdevs","socratic-36"],"noteIcon":"3","created":"2024-07-19T22:13:20.754-10:00","updated":"2024-07-21T11:49:27.663-10:00"}
---



> [!QUOTE] [Mempool Accelerator™ - mempool](https://mempool.space/accelerator)
> **What is Mempool Accelerator™?**
> 
> Mempool Accelerator™ is a service to get your stuck transactions confirmed by paying an out of band fee.
> 
> **How does Mempool Accelerator™ work?**
> 
> Mempool sends your acceleration request to our mining pool partners. Partners who choose to accept your acceleration request prioritize your transaction based on your new accelerated fee rate.
> 
> For example, if you use Mempool Accelerator™ to accelerate a 1 sat/vB transaction to a 20 sat/vB target fee rate, mining pool partners will treat the transaction as though it has a 20 sat/vB fee rate.
> 
> **What payment methods are accepted?**
> 
> Pay with Lightning or Cash App Pay, or preload your Mempool Accelerator™ Pro account with credit using onchain BTC or Lightning.
> 
> **What is the cost to use Mempool Accelerator™?**
> 
> Acceleration cost includes:
> - The fee to boost to your selected target fee rate.
> - The Mempool Accelerator™ service fee.
> 
> View your transaction on mempool.space to see the cost breakdown (see customize and details).

> [!QUOTE] [Stephan Livera on X](https://x.com/stephanlivera/status/1811386469329637453)
> 
> No accounts, no worries! Just gave the new [@mempool](https://x.com/mempool) accelerator a go. See a random low sat/vB transaction here:
> 
> ![Image](https://pbs.twimg.com/media/GSNVMrnbcAAg81A?format=jpg&name=medium)
> 
> I hit 'accelerate' and it shows me an LN QR:
> 
> ![Image](https://pbs.twimg.com/media/GSNVkPBWQAEb3m7?format=jpg&name=medium)
> 
> Pay, then it's waiting time:
> 
> ![Image](https://pbs.twimg.com/media/GSNVpcwa0AA_A45?format=jpg&name=medium)
> 
> And a few minutes later it has gone through!
> 
> ![Image](https://pbs.twimg.com/media/GSNVx-dW0AAbcTL?format=jpg&name=medium)
> 
> Super useful for stuck transactions!

This tool was originally [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Mempool Space transaction acceleration marketplace\|announced back in 2023]], and sparked some controversy:

<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/bit-devs/resources/notes/mempool-space-transaction-acceleration-marketplace/#concerns" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



# Concerns

[![@1f52b_xyz_Tweet_MempoolFeeAcceleration_Drama.png](/img/user/para/artifacts/@1f52b_xyz_Tweet_MempoolFeeAcceleration_Drama.png)](https://nitter.at/1f52b_xyz/status/1659673323834408962#m)

Because these fee acceleration payments happen entirely out-of-band between Mempool Space and various mining pools, the individual miners within those pools can't audit and confirm that they're receiving the proper cut of those additional fees. Individual miners would have no insight into the acceleration fees that users are paying, so they'd have to trust that the pool operators are honestly divvying out those rewards as blocks are mined.


</div></div>


# More Resources
- [Mempool Accelerator™ - mempool](https://mempool.space/accelerator)
- [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Transaction Fees & The Mempool\|Transaction Fees & The Mempool]]
- [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Surviving a High-Fee Market\|Surviving a High-Fee Market]]

