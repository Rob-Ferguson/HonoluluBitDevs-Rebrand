---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Ledger Recover.md","permalink":"/bit-devs/resources/notes/ledger-recover/","title":"Ledger Recover","noteIcon":"3","created":"2023-05-26T21:45:08.476-10:00","updated":"2023-05-27T00:22:21.719-10:00"}
---


# Description

Ledger Recover is an opt-in, ~$10/month service that uses Shamir Secret Sharing to split a seed phrase into 3 encrypted shards and distributes them to 3 custodians:
- [Ledger](https://www.ledger.com/)
- Crypto custody firm [Coincover](https://www.coincover.com/)
- Code escrow company [EscrowTech](https://www.escrowtech.com/) 
  

If a private key is lost, 2 of the 3 shards can be combined to reproduce the key. Ledger Recover requires the user to submit KYC identification because the custodians will check against this ID before reproducing the key.

At the time of writing (for [[para/1. Projects/Honolulu BitDevs/Events/Socratic Seminar 22\|Socratic Seminar 22]]), this service is not yet available, but will be compatible with Ledger Nano X at launch.

> [!QUOTE] [FTX-ed Crypto Investors Are Moving Back to Hardware Wallets | WIRED UK](https://www.wired.co.uk/article/ftx-crypto-investors-hardware-wallets)
> - Essentially, Ledger Recover is an additional safety net; for the price of $9.99 a month, it takes the jeopardy out of crypto’s version of stuffing dollars under the mattress. It’ll be available in the UK, EU, US, and Canada and come to other territories later in the year.
> - Ledger Recover is a service, he says, not a feature - one that provides all the niceties and safety mechanisms regular people are looking for.
> - The fragments of the recovery phase are encrypted and stored by each custodian on specially secured servers, and the balance of the user’s wallet is covered up to a value of €50,000 ($55,000) if something goes awry, a little like deposit insurance at a bank. It’s also being designed with a less technical user in mind.
> - “A lot of people say they cannot enter crypto because they can’t manage the recovery phrase. It’s _the_ industry problem. Making that pain point go away will trigger a lot more people to join the space,” Gaunthier was quoted as saying.
> - "Ledger Recover is a service, he says, not a feature - one that provides all the niceties and safety mechanisms regular people are looking for."

Due to a marketing mistake, the Ledger Recover service was [announced prematurely and quickly retracted](https://www.nobsbitcoin.com/ledger-to-launch-kyc-cloud-based-recovery-service/), which was met with speculation and skepticism from the community. Ledger has since had to respond to severe social backlash to the announcement.

> [!QUOTE] [Ledger Recover: A Message From Pascal Gauthier, Chairman & CEO at Ledger | Ledger](https://www.ledger.com/blog/ledger-recover-a-message-from-pascal-gauthier-chairman-ceo-at-ledger)
> - Ledger Recover is a much needed product in the market to help existing and future crypto users to be able to get to the security of self-custody, and either offload assets from less secure environments, exchanges or soft wallets, & for newcomers to onboard self-custody securely.
> - The main concerns that you expressed are around transparency, censorship resistance, and security. I think we’ve done a good job to address all of your concerns, but again, it’s for you to tell us, so please don’t hesitate to like, comment, share our clarified service.
> - Ledger Recover will be launched as soon as the source code is auditable. We believe in these amendments to the project and will continue to build the industry together.

# Risks

- Because this is a KYC'ed service, users lose privacy, and the 3rd-party KYC service provider becomes a honeypot of identity data potentially tied to crypto balances and transaction history ([Citadel Dispatch 51](https://www.podpage.com/citadeldispatch/cd51-bitcoin-companies-keeping-lists-of-bitcoiners-and-our-transaction-history-with-btcxzelko-laserhodl-diverter_nokyc-and-stephanlivera/))
- 2 of the 3 shard custodians could collude to steal funds or be coerced to reproduce a key and hand it over to authorities.
- In the [What Bitcoin Did 661](https://www.whatbitcoindid.com/podcast/ledger-recover) interview (with Pascal Gauthier, NVK, Matt Odell & Harry Sudock), Pascal confirmed that if the custodians were subpoenaed, they would have to hand over private key shards.
	- He downplayed the regulatory risk by claiming the shard custodians were in different jurisdictions and that the likelihood of such a subpoena was very low.
	- He countered the collusion risk by noting that the shard custodians are all regulated businesses with legal obligations to operate honestly. The reputation hit of such a collusion attempt would also be against their best interest financially. 
- There are technical implementation risks introduced when the key is being sharded and transferred to the custodians. It expands the attack surface where private key data might be leaked.
- Many parts of the Ledger software stack are closed source, so users can't independently verify that the device is operating how Ledger developers claim.

# Opinion

The most important takeaway is that current Ledger users **should not panic** - that's how mistakes are made and funds get lost. 

The Recover service will only be available for Ledger Nano X users initially, so users of older Ledger Nano S models are at no additional risk. Even Nano X users have to explicitly opt in to the service to initiate the process, so if you don't want to use it, don't opt in (you could also try keep an older firmware version on the device). There's always some risk that Ledger developers could push malicious code that sends private key data involuntarily, but that concern exists to some degree with every wallet - the main difference is that closed source code can't be openly audited to help confirm that isn't happening.

Because only private key data is being sent to the shard custodians, users that add an additional [[para/1. Projects/Honolulu BitDevs/Events/Self-Custody Workshop#BIP39 passphrases\|BIP39 passphrase]] on top of their seed are completely safe even if the custodians collude to reproduce the private key itself. In that case, they would still need the secret passphrase to actually access funds.

In response to the community backlash, Ledger announced [they are fast-tracking their open source roadmap](https://www.nobsbitcoin.com/ledger-accelerates-open-source-roadmap/) to make more of the software stack publicly auditable:

![LedgerOpenSourceRoadmap.png](/img/user/para/artifacts/LedgerOpenSourceRoadmap.png)

Any increase in transparency is a good thing - the more code open sourced, the better. The roadmap also includes more educational material about the service itself and hints at the ability to implement your own shard backup provider, which might better distribute risk.

Overall, Ledger Recover will probably be a useful service for very non-technical bitcoin users who aren't ready to take on the personal responsibility of proper key management. For people who are much more concerned with the potential for user error than they are with regulatory/collusion risk, Ledger Recover might offer acceptable tradeoffs.

That being said, I personally wouldn't use Ledger's Recover service and wouldn't secure a meaningful amount of my own savings with a single Ledger device (especially not without a BIP39 passphrase). There are other hardware wallets with arguably better tradeoffs ([Coldcard Mk4](https://youtu.be/FAYmE5-40PQ), [Foundation Passport](https://foundationdevices.com/), [BitBox02](https://shiftcrypto.ch/bitbox02/), [SeedSigner](https://seedsigner.com/), etc) for single-signature setups.

However, I think the risk tradeoffs shift if a Ledger device is being used as part of a larger [[para/1. Projects/Honolulu BitDevs/Events/Self-Custody Workshop#Multisignature\|multisignature quorum]], e.g., in a 2-of-3 setup. In that case, compromising a single key doesn't inherently risk loss of funds, so it is probably worth it to over-optimize for redundancy on one of the key backups. Enabling Ledger Recover for a Ledger used in a 2-of-3 quorum would make that particular seed phrase very resilient against loss, and if the shard custodians ever did collude, they still wouldn't have the other 2 keys or even know about the multisignature wallet's existence.

# More Resources
- [Twitter thread from @sethforprivacy](https://twitter.com/sethforprivacy/status/1659888128486699008?s=20)