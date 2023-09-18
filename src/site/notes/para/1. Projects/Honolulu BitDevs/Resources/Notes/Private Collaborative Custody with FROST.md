---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Private Collaborative Custody with FROST.md","permalink":"/bit-devs/resources/notes/private-collaborative-custody-with-frost/","title":"Private Collaborative Custody with FROST","tags":["bitdevs","bitcoin","socratic-26","privacy","custody","mpc","frost","multisig"],"noteIcon":"3","created":"2023-09-17T14:25:48.468-10:00","updated":"2023-09-17T21:07:53.322-10:00"}
---



# What happened?

> [!QUOTE] [TFTC Issue 1379: Using FROST to Increase Privacy in Collaborative Bitcoin Custody Models](https://tftc.io/martys-bent/issue-1379-using-frost-to-increase-privacy-in-collaborative-bitcoin-custody-models/)
> Nick Farrow took to the bitcoin-dev mailing list earlier this week to lay out his idea for a private collaborative custody solution using FROST.
> 
> For those who are unaware, **FROST** stands for **Flexible Round-Optimized Schnorr Threshold Signatures** and it leverages Schnorr signatures and Taproot addresses to allows individuals to create multi-sig quorums that look like a single sig output on-chain. FROST achieves this by enabling each quorum to produce a joint FROST key that is used to sign a transaction after a threshold of members sign their key shares. This is a **massive privacy benefit** as it makes it impossible to tell whether or not an input was produced by a multi-sig spend or a single-sig spend. If implemented into popular wallet softwares individuals and businesses would be able to have peace of mind knowing that it is impossible for people to determine the type of key set up they are using.
> 
> Nick's mailing list post from earlier this week is exploring **the possibility of creating a collaborative custody service that enables third parties who are participating in a FROST multi-sig quorum to sign without knowing exactly what transaction they're signing**. Adding a solid layer of privacy to those using FROST multi-sig quorums while engaging with a third party signing service. Again, an incredibly cypherpunk application that is made possible via bitcoin.
> 
> It should be noted that FROST isn't exactly the same as the on-chain multisig mechanics that you are probably familiar with. **FROST is a [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Multi-Party Computation (MPC)\|multiparty computation (MPC)]] multisig, which means the multisig quorum is coordinated off chain.** Once the necessary threshold signers coordindate and sign off chain, an on chain key can then be signed. There are tradeoffs that come with MPC, mainly revolving around nonce generation that, **if not done properly, can erode the security of a private key**. However, the team at [BitGo recently came up with a unique solution](https://bitcoinops.org/en/newsletters/2023/08/16/?ref=tftc.io) to the nonce generation tradeoff by leveraging the data field space in PSBTs to ensure randomness before signing. It will be interesting to see if MPC becomes more popular across the industry. From what I understand, the ability to leverage Schnorr signatures allows for the creation of more secure MPC set ups.

# How does it work?

> [!QUOTE] [Private Collaborative Custody with FROST](https://gist.github.com/nickfarrow/4be776782bce0c12cca523cbc203fb9d/)
> ## Enrolling a Private Collaborative Custodian
> 
> Each signer in a FROST multisig controls a point belonging to a joint polynomial at some participant index.
> 
> Participants in an existing multisig can collaborate in an enrollment protocol to securely generate a new point on this shared polynomial and verifiably communicate it to a new participant, in this case a collaborative custodian.
> 
> ---
>  
>  ## Blind Collaborative Signing
>  
>  Once the collaborative custodian controls a point belonging to this FROST key, we can now get their help to sign messages.
>  
>  ...
>  
>  As an overview, we give a 3rd party a secret share belonging to our FROST key. When we need their help to sign something, we ask them to send us (FROST coordinator) a public nonce, then we create a challenge for them to sign with a blind Schnorr scheme. They sign this challenge, send it back, and we then combine it with the other partial signatures from FROST to form a complete Schnorr signature that is valid under the multisignature's public key.
>  
>  During this process the collaborative custodian has been unknowing of our public key, and unknowing as to the contents of the challenge which we have requested them to sign. The collaborative signer doesn't even need to know that they are participating in FROST whatsoever.

# More Context

> [!QUOTE] [Bitcoin Optech Newsletter 267](https://bitcoinops.org/en/newsletters/2023/09/06/#privacy-enhanced-co-signing)
> **Privacy enhanced co-signing:** Nick Farrow [posts](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2023-August/021917.html) to the Bitcoin-Dev mailing list about how a [scriptless threshold signature scheme](https://bitcoinops.org/en/topics/threshold-signature/) like [FROST](https://eprint.iacr.org/2020/852) could improve the privacy of people who use co-signing services. A typical user of a co-signing service has multiple signing keys that are stored separately for security; but, to simplify normal spending, they also allow their outputs to be spent by a combination of some of their keys plus one or more keys held by one or more service providers who only sign after authenticating the user in some way. The user can bypass the service provider if needed, but the service provider makes operations easier in most cases.
> 
> With scripted threshold signature schemes like 2-of-3 `OP_CHECKMULTISIG`, the service’s public key must be associated with the output being spent, so any service will be able to find the transactions it signed by looking at onchain data, allowing it accumulate data about its users. Worse, all currently used protocols we’re aware of directly reveal user transactions to the service provider before signing, allowing the service to refuse to sign certain transactions.
> 
> As Farrow describes, **FROST allows hiding the signed transaction from the service at every step of the process, from generation of an output script, to signing, to publication of the fully signed transaction. All the service will know is when it signed and any data the user provided to authenticate themselves with the service.**
> 
> The idea received some discussion on the mailing list. [🎧](https://bitcoinops.org/en/podcast/2023/09/07/#privacy-enhanced-co-signing)

[![BitDevs-26-frost-1.png](/img/user/para/artifacts/BitDevs-26-frost-1.png)](https://x.com/utxoclub/status/1696717492213657775?s=20)

[![BitDevs-26-frost-2.png](/img/user/para/artifacts/BitDevs-26-frost-2.png)](https://x.com/utxoclub/status/1696458577743897032?s=20)
# More Resources
- [Blind Schnorr Signature Interactive Demo](https://blindsigs.utxo.club/)
- [Taproot and FROST improve Bitcoin privacy](https://bitcoinmagazine.com/technical/taproot-and-frost-improve-bitcoin-privacy)
- [Stephan Livera's 476th podcast episode](https://stephanlivera.com/episode/476/) 
- [FROST: Flexible Round-Optimized Schnorr Threshold Signatures research paper](https://eprint.iacr.org/2020/852.pdf)
- [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Multi-Party Computation (MPC)\|Multi-Party Computation (MPC)]]