---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Validating Lightning Signer Beta Release.md","permalink":"/bit-devs/resources/notes/validating-lightning-signer-beta-release/","title":"Validating Lightning Signer Beta Release","tags":["bitcoin, lightning, custody"],"noteIcon":"3","created":"2023-07-30T20:14:44.759-10:00","updated":"2023-07-30T21:24:46.621-10:00"}
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

VLS is also fully integrated with [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Blockstream Greenlight#^bc7889\|Blockstream's Greenlight service]].

# More Resources
- [[para/1. Projects/Honolulu BitDevs/Events/Socratic Seminar 15#^0467b3\|Socratic Seminar 15]]