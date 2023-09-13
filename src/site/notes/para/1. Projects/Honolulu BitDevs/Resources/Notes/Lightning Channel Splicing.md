---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Lightning Channel Splicing.md","permalink":"/bit-devs/resources/notes/lightning-channel-splicing/","title":"Lightning Channel Splicing","tags":["bitcoin","lightning","scaling","splicing"],"noteIcon":"3","created":"2023-04-09T14:48:09.984-10:00","updated":"2023-07-30T23:19:51.467-10:00"}
---


# Description

- **Splicing** is the act of transferring funds from onchain outputs into a payment channel, or from a payment channel to independent onchain outputs, without the channel participants having to wait for a confirmation delay to spend the channel’s other funds.
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


# More Resources
- [Splicing pull request by ddustin: Adds the features needed to enable collaborative splicing & resizing of active channels](https://github.com/ElementsProject/lightning/pull/5675)
- [Splices and Liquidity in the Lightning Network](https://blog.muun.com/splices-and-liquidity-in-the-lightning-network/)
- [What Is Splicing On The Lightning Network? - The Bitcoin Manual](https://thebitcoinmanual.com/articles/splicing-lightning-network/)
- [Splicing - Bitcoin Optech](https://bitcoinops.org/en/topics/splicing/)

