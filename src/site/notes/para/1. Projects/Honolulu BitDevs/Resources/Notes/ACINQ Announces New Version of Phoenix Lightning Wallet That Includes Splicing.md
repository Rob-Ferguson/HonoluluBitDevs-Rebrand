---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/ACINQ Announces New Version of Phoenix Lightning Wallet That Includes Splicing.md","permalink":"/bit-devs/resources/notes/acinq-announces-new-version-of-phoenix-lightning-wallet-that-includes-splicing/","title":"ACINQ Announces New Version of Phoenix Lightning Wallet That Includes Splicing","tags":["lightning, scaling, splicing, phoenix"],"noteIcon":"3","created":"2023-07-29T16:46:43.746-10:00","updated":"2023-07-29T18:19:35.787-10:00"}
---



[ACINQ](https://acinq.co/about) is the company behind [Phoenix](https://phoenix.acinq.co/) and [eclair](https://github.com/ACINQ/eclair). Eclair is a [full Lightning node implementation](https://acinq.co/blog/eclair-architecture) with a focus on performance and reliability (in contrast to alternatives like [Core Lightning](https://corelightning.org/) and [LND](https://docs.lightning.engineering/lightning-network-tools/lnd)). Phoenix is a non-custodial Lightning wallet that is powered by eclair.

> [!QUOTE] [Introducing the new Phoenix: a 3rd generation self-custodial Lightning wallet](https://acinq.co/blog/phoenix-splicing-update)
> **TL; DR:** Splicing changes the game. Phoenix now manages a single dynamic channel, no more 1% fee on inbound liquidity, better predictability and control, trustless swaps. The new fee schedule is [detailed here](https://acinq.co/blog/phoenix-splicing-update#fee-comparison).
> 
> Only available on Android for now, email phoenix@acinq.co to apply for the beta. ETA for iOS is a few weeks.
> 
> ---
> 
> Leveraging a technology called splicing, the new Phoenix has the possibility to resize channels, making all those issues go away:
> - each user has only one channel
> - there is no more scattered liquidity or splitting issues
> - adding or removing funds to the channel doesn't add future risk and can be priced at current cost: the 1% / 3000 sat fee is replaced by the mining fee for the underlying on-chain transaction.
> 
> Another way to look at it is that we are moving from N UTXOs/user to 1 UTXO/user. It is simply the current optimum for self-custody on Bitcoin. Further reducing the on-chain footprint implies sharing UTXOs amongst users, either in a simplistic trusted way (custodial wallets), or by introducing concepts like virtual UTXOs.
> 
> We believe that the efficiency gains brought by splicing are so phenomenal that all wallets will eventually implement it. That is why this technological improvement marks the beginning of a new generation of self-custodial wallets.

# [[Lightning Channel Splicing \| Splicing]]

<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/bit-devs/resources/notes/lightning-channel-splicing/#description" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



# Description
^321f14

- **Splicing** is the act of transferring funds from onchain outputs into a payment channel, or from a payment channel to independent onchain outputs, without the channel participants having to wait for a confirmation delay to spend the channel’s other funds. ^803539
- **The whole idea behind splicing is to reduce the number of on-chain transactions required to efficiently manage Lightning channel liquidity**
- Splicing comes in two varieties:
	- **Splice in** means adding funds to a channel. 
		- In this case, a cooperative close of the channel is arranged between the involved parties that spends the old channel funds to a new channel along with the new deposit. Because the new channel open is based on the security of the old channel close, the channel participants can safely spend the old funds within the channel while waiting for the close and open transactions to confirm.
	- **Splice out** means removing funds from a channel to an independent onchain output. 
		- Similar to splice-in, the channel is closed and a new channel is opened, with the remaining funds being secured by the old channel’s security until the new channel has fully confirmed.
		- **With a splice out, you can close the channel, pay on-chain, and open a new channel in one single on-chain transaction**
- Splicing enables the resizing of multiple channels in a single on-chain transaction, without any channels being "down" or closed during any part of the process
- Splicing makes it much easier to move funds in and out of Lightning channels dynamically
	- In time, this will enable wallets to implement "one balance" apps that allow users to send lightning & on-chain payments without needing to manage two "bitcoin balances" -- with the lowest fees possible
- Not only can participants add their own resizes, due to compatibility with [@niftynei](https://github.com/niftynei)'s dual funding feature, they can also add channel opens into the same batch. Eventually dual closing will allow all onchain lightning events to be batched into a single bitcoin transaction.



</div></div>


# Benefits in Phoenix Wallet
- [More predictability and more control](https://acinq.co/blog/phoenix-splicing-update#more-predictability-and-more-control)
	- Phoenix today has to periodically create new channels on the fly, which surprises users with a larger fee (1% with a 3000 sat minimum).
	- The new app version seamlessly splices in our out of a single channel as capacity requirements change, and it only requires the user to pay mining fees each time.
	- Users can adjust the maximum fee that they are willing to pay for channel management when receiving payments. If the fee is too high, Phoenix will just wait and retry later (for a swap-in) or reject (for a Lightning payment).
	- This allows the user to validate the fee before making the payment. It also aligns incentives with the wallet provider, which was previously trusted to find the cheapest route. The wallet provider is now incentivized to find the best (reliable, affordable) route within the fee budget.
- [Trustless swaps](https://acinq.co/blog/phoenix-splicing-update#trustless-swaps)
	- Historically, most Lightning wallets have leveraged swap services to offer a way to seamlessly send and receive on-chain bitcoin transactions (aka "swap-out" and "swap-in").
	- **Swap-out** (paying to a bitcoin address)
		- Phoenix's old swap service was very basic, trusted, and didn't let the user choose the feerate for a swap-out.
		- In the new version, a splice-out is used to trustlessly send on-chain payments from a Lightning channel.
	- **Swap-in** (sending an on-chain transaction to Phoenix)
		- In the previous version of Phoenix, the bitcoin address displayed in the Receive tab wasn't controlled by Phoenix but by the swap service, and for every incoming transaction, a new channel was created.
		- With the new Phoenix, funds stay in control of Phoenix during the process. If there is already a channel, the funds will be spliced in and the capacity of the channel will grow by that amount. Otherwise, a new channel will be created using dual-funding.

Phoenix plans to continue expanding on this functionality - the roadmap includes blinded paths, BOLT 12 Offers, and Taproot.