---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Trezor Announces Safe 5 Signing Device.md","permalink":"/bit-devs/resources/notes/trezor-announces-safe-5-signing-device/","title":"Trezor Announces Safe 5 Signing Device","tags":["bitcoin","bitdevs","socratic-35","custody","self-custody","hardware","wallet"],"noteIcon":"3","created":"2024-06-22T14:11:18.949-10:00","updated":"2024-06-23T21:11:00.124-10:00"}
---



At the [BTC Prague](https://btcprague.com/#) 2024 conference, [Satoshi Labs](https://satoshilabs.com/) announced its new flagship product: the [Trezor Safe 5](https://trezor.io/trezor-safe-5). The new signing device costs $169, incorporates several new features over its predecessors, and comes with either Bitcoin-only firmware or multi-coin support. The company also introduced new service called [Trezor Expert Session](https://trezor.io/trezor-expert-session?ref=nobsbitcoin.com), which is intended to be a "concierge" service to help onboard new users to self-custody.

> [!QUOTE] [Trezor Safe 5 | Secure Crypto Hardware Wallet](https://trezor.io/trezor-safe-5)
> # Trezor Safe 5
> 
> Trezor Safe 5 is designed to be the ultimate hardware wallet for cryptocurrency users who prioritize both security and user-friendliness. With its **vibrant color touchscreen and tactile feedback features** from the Trezor Touch haptic engine, it offers an intuitive experience that’s easy to navigate.  
> 
> **Based on a decade of open-source security and privacy development**, the Trezor Safe 5 provides a reliable foundation for safeguarding your cryptocurrency assets. It employs the **NDA-free EAL 6+ Secure Element along with PIN and passphrase protection**, ensuring strong defense against both online and offline threats. The **addition of an enhanced 20-word wallet backup standard** allows for a seamless transition from a Standard Single-share Backup to an Advanced Multi-share Backup, enhancing wallet recovery protection with added security measures.
> 
> The Trezor Safe 5 seamlessly integrates with the complete Trezor ecosystem, which includes user-friendly desktop and mobile apps. This integration simplifies tasks such as buying, selling, and exchanging cryptocurrencies. Additionally, users have access to a wide array of third-party services, enabling them to tailor their cryptocurrency experience to their individual preferences and requirements.
> 
> Whether you’re new to hardware wallets or an experienced cryptocurrency user, Trezor Safe 5 offers unparalleled security and convenience for storing, managing, and using your crypto.

![BitDevs-35-Trezor-Safe-5-Overview.png](/img/user/para/artifacts/BitDevs-35-Trezor-Safe-5-Overview.png)

![BitDevs-35-Trezor-Safe-3-5-Comparison.png](/img/user/para/artifacts/BitDevs-35-Trezor-Safe-3-5-Comparison.png)

[![BitDevs-35-Trezor-Safe-5-Video.png](/img/user/para/artifacts/BitDevs-35-Trezor-Safe-5-Video.png)](https://youtu.be/1EVzbNPn6bc)

# Secure Element

> [!QUOTE] [Secure Element in Trezor Safe Devices](https://trezor.io/learn/a/secure-element-in-trezor-safe-devices)
> **Secure Element in Trezor Safe Devices**
> 
> A significant advancement in the Trezor hardware wallet series is the integration of a dedicated Secure Element, **first introduced in the Trezor Safe 3 and now also incorporated into the new Trezor Safe 5**. This feature highlights our commitment to bolstering security without compromising the foundational open-source philosophy that Trezor is known for.
> 
> **What is a Secure Element and what does it (not) do?**
> 
> The Secure Element serves as a robust shield for sensitive data. **First, it enhances the physical security of the Trezor by adding a layer of safety to the PIN protection mechanism. Second, it plays an important role in [verifying the authenticity of your device](https://trezor.io/learn/a/trezor-safe-device-authentication-check).**
> 
> The Secure Element used in the Trezor Safe 3 and Safe 5 is the OPTIGA™ Trust M (V3). In effect, it is a chip designed to protect highly sensitive information from software and hardware attacks. In the context of hardware wallets, what you really need to protect is your [recovery seed](https://trezor.io/learn/a/keeping-your-recovery-seed-safe). The trick is to design a mechanism in which the Secure Element doesn’t learn your wallet backup (recovery seed) - and that’s what we’ve implemented here.
> 
> The Secure Element used in the Trezor Safe family of devices protects your [PIN](https://trezor.io/learn/a/pin-protection-on-trezor-devices) (without learning it), which releases a secret (stored on the Secure Element), which in turn protects your recovery seed (stored only on the Trezor general purpose chip, encrypted by both the device PIN and the secret stored on the Secure Element).
> 
> > [!NOTE] We do not run code on the chip itself. The Secure Element simply stores a secret that can be used to decrypt the recovery seed, i.e., **it never actually knows what your recovery seed is**.

# 20-Word Seed Phrase

With the Safe 5, Trezor is incorporating a new 20-word seed phrase standard, which is intended to make it easier to split a seed via [Shamir backups](https://blog.trezor.io/https-blog-trezor-io-dev-corner-shamir-backup-guide-5f9957ff1008). Although useful in some circumstances, [Shamir backups have their own tradeoffs](https://unchained.com/features/mpc-vs-multisig-vs-sss) to consider relative to other multi-key custody schemes.

This 20-word seed phrase is not a widely adopted standard, which means seeds generated in this way would probably be difficult to import into another wallet outside of the Trezor ecosystem.

# More Resources
- [Trezor Safe 5 | Secure Crypto Hardware Wallet](https://trezor.io/trezor-safe-5)
- [Trezor Introduced Safe 5 Signing Device](https://www.nobsbitcoin.com/trezor-introduces-safe-5-signing-device/)

