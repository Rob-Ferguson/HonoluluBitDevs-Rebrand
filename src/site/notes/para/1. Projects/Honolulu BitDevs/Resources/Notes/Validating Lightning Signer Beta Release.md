---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Validating Lightning Signer Beta Release.md","permalink":"/bit-devs/resources/notes/validating-lightning-signer-beta-release/","title":"Validating Lightning Signer Beta Release","tags":["bitcoin","lightning","custody"],"noteIcon":"3","created":"2023-07-30T20:14:44.759-10:00","updated":"2023-07-31T15:06:29.358-10:00"}
---



> [!QUOTE] [Validating Lightning Signer Beta Release](https://vls.tech/posts/vls-beta/)
> The Bitcoin Lightning Network has grown significantly in recent years, but this growth leads to increased security concerns. Lightning Network private keys are currently stored on the node; if the node is compromised, the attacker can steal the user's funds.
> 
> VLS (the Validating Lightning Signer), is an open-source Rust library and reference implementation of software that **separates a user's private keys from their Lightning node, ensuring that if the node is compromised, the attacker cannot steal the user's funds**. There are currently no other solutions in the ecosystem that provide the same level of security as VLS. Unlike VLS, [Blind signers](https://gitlab.com/lightning-signer/docs/-/wikis/Blind%20Signing%20Considered%20Harmful), for example, accept any transaction request the node sends them, and actually reduce security if deployed in production.
> 
> VLS also opens up the possibility of multi-signature Lightning network setups, similar to Bitcoin layer 1 multi-signature wallets (multi-sig).
> 
> We're thrilled to announce the [VLS beta release](https://gitlab.com/lightning-signer/validating-lightning-signer/-/releases/v0.9.1), **a major step forward for Lightning network security**, and we're excited to share it with developers and companies in the Bitcoin ecosystem.
> 
> ---
> 
> We propose to sequester the private keys and secrets in hardened policy signing devices. We have a reference [Validating Lightning Signer implementation](https://gitlab.com/lightning-signer/validating-lightning-signer) in Rust.
> 
> When run with VLS, the Lightning node uses an alternate signing module, replacing internal signing with proxy calls to the signing device.
> 
> The signing device applies a complete set of validation rules to ensure that the proposed transaction is safe to sign. Having a complete set of validation rules protects the funds even in the case of a complete compromise of the node software.
> 
> ---
> 
> Users and merchants who do not want to maintain their own lightning node can also work with a Lightning Service Provider to host and manage their node, while maintaining custody of their funds by securing their Lightning private keys on a consumer device.
> Some of the validation rules that VLS implements include:
> - Don't sign a revoked commitment transaction
> - Don't revoke a signed commitment transaction
> - Don't close a channel to an unapproved destination
> - Routed payments must have at least as much input as output value
> - Payments must claim at least as much from the input as was claimed from us on the output
> - And [many more](https://gitlab.com/lightning-signer/validating-lightning-signer/-/blob/main/docs/policy-controls.md) ...

VLS is also fully integrated with [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Blockstream Greenlight#^bc7889\|Blockstream's Greenlight service]], which we discussed at [[para/1. Projects/Honolulu BitDevs/Events/Socratic Seminar 23#^ee6080\|Socratic Seminar 23]]:

<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/bit-devs/resources/notes/blockstream-greenlight/#bc7889" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



On a related note, in mid-June 2023, [Build on L2 (BOL2) announced support](https://community.corelightning.org/c/start-here/build-on-l2-supports-vls-integration-into-greenlight-with-150-000-grant) for the [Validating Lightning Signer project](https://vls.tech/?ref=nobsbitcoin.com) (VLS) with a $150,000 grant. BOL2 is a community initiative spearheaded by Blockstream to connect developers building on technology related to Core Lightning and Liquid. VLS is an open source project that includes the ability to operate on hardware security modules HSMs. This will improve enterprise-level Lightning node security by helping to keep private keys segregated from the node itself. Users can define rules for the types of transactions that the VLS module will automatically sign (e.g., channel opens, routing forwards, etc.), which will enable more sophisticated and programatic node management without necessarily requiring direct human interaction or relinquishing full signing access. VLS is fully integrated with Blockstream's Greenlight, which means that developers can easily access this signer without custom modifications. 

</div></div>


# More Resources
- [[para/1. Projects/Honolulu BitDevs/Events/Socratic Seminar 15#^0467b3\|Socratic Seminar 15]]