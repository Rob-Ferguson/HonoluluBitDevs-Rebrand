---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Dark Skippy Disclosure - A Powerful Method For Key Exfil Attacks.md","permalink":"/bit-devs/resources/notes/dark-skippy-disclosure-a-powerful-method-for-key-exfil-attacks/","title":"Dark Skippy Disclosure - A Powerful Method For Key Exfil Attacks","tags":["bitcoin","bitdevs","socratic-37","security","self-custody","hack"],"noteIcon":"3","created":"2024-08-16T22:02:03.893-10:00","updated":"2024-08-18T13:11:04.056-10:00"}
---



[![BitDevs-37-DarkSkippy-SLP-Podcast.png](/img/user/para/artifacts/BitDevs-37-DarkSkippy-SLP-Podcast.png)](https://overcast.fm/+AAOBZm65JN4)

> [!QUOTE] [Dark Skippy Disclosure - A Powerful Method For Key Exfil Attacks](https://darkskippy.com/)
> **With Dark Skippy, a malicious signer can use a modified signing function to efficiently and covertly exfiltrate their master secret seed by embedding it within transaction signatures.**
> 
> This attack was discovered and discussed within the context of Bitcoin signing devices and hardware wallets, though it may be applicable to contexts outside of Bitcoin.
> 
> Dark Skippy requires a signer to be corrupted via malicious firmware. Dark Skippy has not yet been seen in the wild.
> 
> [![BitDevs-37-Dark-Skippy-Demo-Thumbnail.png](/img/user/para/artifacts/BitDevs-37-Dark-Skippy-Demo-Thumbnail.png)](https://youtu.be/U2u5bqZNQWA)
> 
> # TL;DR
> 
> Previously it was thought to take _[dozens](https://bitbox.swiss/blog/anti-klepto-explained-protection-against-leaking-private-keys/)_ of signatures/transactions for a malicious signing device to leak a secret seed to an attacker by covertly embedding it inside transaction signatures. We have shown it can be done in just two signatures. **A single use of a malicious hardware wallet is enough to lose everything.**
> 
> # Is hardware wallet X affected?
> 
> Dark Skippy is not an attack against any particular hardware wallet/signing device and has not been seen in the wild; but rather is is a general method that a malicious signing device could use to steal your funds.
> 
> **As long you are using a genuine device with honest firmware then it should not be carrying out this attack.** Ideally verifying open source firmware against your vendor's public keys, many devices verify firmware signatures automatically. You should ensure no one has the opportunity to tamper with your device's firmware in-between uses.
> 
> [See FAQ for more details](https://darkskippy.com/faq.html).
> 
> # How It Works
> 
> It might be useful to refresh your knowledge of malicious signing attacks with our [Taxonomy of Malicious Signer Attacks](https://darkskippy.com/taxonomy.html) which includes a refresher on Schnorr signatures.
> 
> First, an attacker needs to corrupt a signing device:
> - A signing device could be tampered with to have malicious firmware loaded onto it.
> - The user could be tricked into installing malicious firmware onto their device.
> - The attacker could build malicious devices to sell or infiltrate supply chains.
> 
> The malicious signing firmware uses a signing function that differs from regular Schnorr signing:
> - Instead of sampling secret nonces randomly from 32 bytes, the malicious signer deliberately uses a weak & low entropy secret nonce that is a chunk of the secret seed that is being exfiltrated.
> - The malicious signer uses the first 8 bytes of a 12-word seed (totaling 16 bytes) for the first input signature's nonce, and uses the remaining 8 bytes for the nonce of second input signature.
> 
> The attacker scans the mempool for transactions with affected signatures produced by the malicious signer.
> 
> Upon detecting an affected transaction, the attacker runs an algorithm like [Pollard's Kangaroo algorithm](https://en.wikipedia.org/wiki/Pollard%27s_kangaroo_algorithm) (hence the name Dark Skippy) on the signature's public nonces to solve for the secret nonces.  
> 
> Once solved, the attacker concatenates the results to reconstruct the full 16 bytes of entropy that the malicious signer was trying to exfiltrate.
> 
> ---
> 
> This is the most rudimentary version of the attack but a sophisticated attacker is likely to enhance it so that only they can extract the seed. This can be done by blinding the nonce with an attacker controlled key embedded in the malicious device. Additionally, affected transactions can be watermarked so that the attacker can easily identify them on-chain.
> 
> An attacker who corrupts a signing device watches on-chain until they spot a watermarked transaction, unblind and invert the low entropy nonces to learn the master secret seed, then wait and steal the funds whenever they decide best. For the user, the attack is impractical to detect and difficult to forensically determine what has occurred.
> 
> # Attack Advantages
> 1. **Covert** - the attack is impractical to detect.
> 2. **No additional communication channels** - data is exfiltrated within signatures broadcasted to the Bitcoin network.
> 3. **Works against stateless devices** - the attack can be executed in a single transaction with only a few inputs.
> 4. **Exfiltrates the master secret** - the attack exposes the entire wallet by exfiltrating the seed words.
> 5. **Affects every user of a malicious device** - including users who provide their own secure seed.


> [!QUOTE] ["Dark Skippy" Vulnerability | Nunchuk](https://nunchuk.io/blog/dark-skippy)
> Recently, a group of Bitcoin researchers (Nick Farrow, Lloyd Fournier, and Robin Linus) disclosed a [security vulnerability](https://x.com/utxoclub/status/1820520960476561825) — called “Dark Skippy” — that potentially impacts Bitcoin hardware signing devices.
> 
> Here’s what you need to know about Dark Skippy:
> 1. Hardware signing devices insert random values called “nonces” every time they sign Bitcoin transactions.
> 2. Weak nonces (values that are not sufficiently random) can allow an attacker to mathematically brute-force the private key from the signatures alone, just by analyzing transactions on the public blockchain.
> 
> This is a well-known class of attack. Dark Skippy is a new technique which makes it easier to grind the private key from weak nonces.
> 
> **What are the conditions required for the attack?**
> 
> The attack requires either:
> 1. Loading malicious firmware onto the device, which generates weak nonces.
> 2. A bug in the vendor’s official firmware that produces weak nonces.
> 
> ---
> 
> **How do I protect myself from this type of attack?**
> 
> 1. Order hardware signing devices straight from the vendors, if possible. The more direct, the lower the likelihood of tampering.
> 2. Use hardware vendors that have tamper-resistant mechanisms in place, such as tamper-evident sealed bags, firmware attestation, etc.
> 3. Use hardware that employs a secure bootloader and enables you to easily verify the integrity of the source firmware and its updates.
> 4. Use hardware that follows security standards in generating nonces. One such standard is [RFC6979](https://datatracker.ietf.org/doc/html/rfc6979) (deterministic nonces).
> 5. Verify the authenticity of the firmware every time you upgrade. (Tip: bookmark the vendor website to avoid phishing).
> 6. Avoid upgrading firmware unless you absolutely have to. Use another device if you want to experiment with firmware features that you don’t actually need for your main wallet.
> 7. Use multisig, preferably multi-vendor multisig. This alone significantly increases the difficulty of executing the attack.
> 
> **Multisig versus Anti-exfil**
> 
> You might have heard that “anti-exfil” is a way to prevent the above attack. In short, anti-exfil describes a security technique which combines entropy from the hardware signing device with entropy from a _second device_ (typically the host of the companion software wallet) to generate the nonces.
> 
> However, there are two downsides to this approach. First, there is currently no anti-exfil standard, so you’d have to trust that the vendors implement anti-exfil securely. Secondly, since anti-exfil changes the way a signature is generated, i.e., asking for entropy from a second device for every single transaction, it is not compatible with the way most Bitcoin wallets work today, and therefore introduces a UI/UX challenge.
> 
> Until anti-exfil has a well-defined standard and wider wallet compatibility, we recommend multisig as the more practical approach. Fundamentally, multisig achieves the same goal as anti-exfil: it also requires entropy from a second device to authorize each Bitcoin transaction. Multisig can also add entropy from more than just 2 devices, if you so choose (3-of-5 multisig, for example). Last but not least, multisig has been widely used for over a decade in Bitcoin, battle-tested (securing hundreds of billions worth of Bitcoin), and at this point has been very well standardized ([PSBT](https://github.com/bitcoin/bips/blob/master/bip-0174.mediawiki), [BSMS](https://github.com/bitcoin/bips/blob/master/bip-0129.mediawiki), [Output Descriptors](https://github.com/bitcoin/bips/blob/master/bip-0380.mediawiki), to name a few standards).
> 
> Hence, **use multisig if you are concerned about Dark Skippy** or potentially malicious firmware.
> 
> In conclusion, **while the Dark Skippy vulnerability highlights potential risks in hardware signing devices, users can significantly mitigate these risks by following best practices in device procurement and usage, and by implementing multisig setups**. Stay informed, verify your devices and firmware, and consider multisig for enhanced security of your Bitcoin holdings.

# More Resources
- [@utxoclub on X](https://x.com/utxoclub/status/1820520960476561825)
- [Dark Skippy - Mitigations](https://darkskippy.com/mitigations.html)

