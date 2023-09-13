---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Milk Sad - Wallet Theft Enabled By Weak Entropy.md","permalink":"/bit-devs/resources/notes/milk-sad-wallet-theft-enabled-by-weak-entropy/","title":"Milk Sad - Wallet Theft Enabled By Weak Entropy","tags":["bitdevs","socratic-25","bitcoin","vulnerability","hack","security"],"noteIcon":"3","created":"2023-08-20T09:56:05.217-10:00","updated":"2023-08-20T11:19:43.458-10:00"}
---



> [!QUOTE] [Milk Sad Technical Write-Up](https://milksad.info/disclosure.html)
> **This is the story of a wallet theft enabled by bad cryptography**. It covers our research on problems with Libbitcoin Explorer 3.x (CVE-2023-39910), outlines how it is related to the Trust Wallet vulnerability (CVE-2023-31290), and shows some of the real-world impact that we were able to confirm.
>
> ### Tracing the Issue to the Source
> 
> Our story starts on Friday, 21 July 2023. Upon attempting to use a well-protected cryptocurrency wallet, the wallet owner realizes that all of their funds stored in their wallet are gone. This was no accident – **they were the victim of a sophisticated theft**. The funds were sent to the attacker’s addresses on July 12th, at a time when the hardware wallet wasn’t in use for several days.
> 
> The generation and use of the affected wallet was unusually strict:
> - Generated on an [air-gapped](https://en.wikipedia.org/wiki/Air_gap_(networking)) Linux laptop with self-compiled software
> - Use of BIP39 24 mnemonic word phrase
> - Mnemonic securely entered into Ledger & Trezor hardware wallets
> - Good PIN and physical security on the hardware wallets
> - Mnemonic seed phrase never touched a non-air-gapped computer
> - Mnemonic seed backup well-protected
> 
> The victim reached out to their network of friends with similar key generation and management protocols, and **a second victim was identified**! The second victim also had the contents of their cryptocurrency wallet stolen during the same period of time – **both victims Bitcoin (BTC) was stolen in the same _minute_ on-chain**. The victims realized this was no accident. They had fallen victim to a some type of hack.
> 
> The victims discovered their Bitcoin (BTC) holdings were not the only things stolen. The attackers had also taken Ethereum and other distinct cryptocurrency types from the same wallets. **The victims realized this could only happen with an underlying leak of their main wallet private keys**. Tricking their hardware wallets into authorizing incorrect transfers or breaking individual private keys of sub-accounts would manifest with a more limited impact.
> 
> ---
> 
> ### Our Cryptocurrency is Gone, But How!?!?
> 
> **An essential tool that was involved in the wallet creation in both cases was the [Libbitcoin Explorer](https://github.com/libbitcoin/libbitcoin-explorer/tree/version3) in a 3.x version, via its `bx` binary**. The Libbitcoin project has been around for a very long time (2011 !), is Open Source, and `bx` brings everything needed for an offline wallet generation in one self-contained binary.
> 
> Despite being a specialized tool that most wallet users won’t have heard of, **`bx` has some popularity and is dedicated an [appendix section](https://github.com/bitcoinbook/bitcoinbook/blob/97df56f77c06813b1e028b5b1f2dbc036f27b1fc/appdx-bx.asciidoc) in the “Mastering Bitcoin” book**. In other words, it appeared to be a reasonable tool to use.
> 
> ---
> 
> ### Given Enough Eyes, All Bugs are Shallow?
> 
> Digging deeper, the team confirmed that the code uses the standard MT19937 Mersenne Twister PRNG variant which only operates on 32 bits of initial seeding input by design, and not the MT19937-64 extended variant with 64 bits of seeding. So the PRNG can at most have 2^32 starting positions as an upper bound, regardless if it’s seeded by `/dev/random` or time.
> 
> To put this in different words: **when running `bx seed -b 256` to request 256 bits of non-guessable entropy, the result is 32 bits of high-precision clock time that was put through a blender (or rather: twister 🌪️) and expanded to 256 bit *without adding new information***. The number of possible key variations would grow exponentially with the size if this were _real_ entropy data, so the difference from the safe expected result (256 bits) and the actual result (32 bits) is of astronomical proportions.
> 
> **Anyone can re-compute and find a victim’s originally used entropy after a maximum of about 4.29 billion attempts if they have specific characteristics to look for to see if they successfully found a cryptocurrency wallet**. In this case, by checking derived wallet addresses that were seen receiving funds on a public blockchain in the past. To put this number into perspective: **brute-forcing this key space takes a few days of computation on the average gaming PC, at most**. And unfortunately, anyone with sufficient programming skills could do it.
> 
> In terms of cryptocurrency wallet security, this is a pretty **catastrophic situation**.
> 
> ---
> 
> ### Codename “Milk Sad”
> 
> Faced with the unexpected task of handling an urgent disclosure, we were in need of a project name that was relevant yet told outsiders nothing about the technical issue. The suggestion was made to use the first two words of first BIP39 mnemonic secret generated by `bx` on time zero - `milk sad wage cup reward [...]` -> **Milk Sad**. We found our project name.
> 
> ---
> 
> ### Libbitcoin Team Response and Context
> 
> During our accelerated coordinated disclosure to the Libbitcoin team, **the Libbitcoin team quickly disputed the relevancy of our findings and the CVE assignment**. By our understanding, they consider `bx seed` a command that should never be used productively by any `bx` user since it is sufficiently documented as unsuited for safe wallet generation.
> 
> We do not agree with this assessment.
> 
> ---
> 
> ### Basic Lessons Learned
> 
> - **Use BIP39 passphrases for your wallets**, ideally with a complex passphrase based on entropy from a separate source.
> - **Trust only heavily audited software** to be in your wallet generation path.
> - **Document every wallet generation setup for your future self**, this may be very important.
> 
> ### Summary
> 
> In this article, we presented technical information of a weak entropy generation function in Libbitcoin Explorer, confirmed the practical use of the weak function for over 2600 cryptocurrency wallets on the Bitcoin Mainnet, and connected it to a recent large theft of cryptocurrency funds on multiple popular blockchains that amounts to an **estimated $900k of damages**. Additionally, we described the close similarities with another actively exploited vulnerability in Trust Wallet, and provided some background on the Libbitcoin Explorer context and overall timeline.

[![MilkSadTheft_DisclosureTimeline.png](/img/user/para/artifacts/MilkSadTheft_DisclosureTimeline.png)](https://milksad.info/disclosure.html#basic-timeline-of-thefts-and-our-disclosure)

[![Voskuil_MilkSad_Response.png](/img/user/para/artifacts/Voskuil_MilkSad_Response.png)](https://twitter.com/evoskuil/status/1688657656620167169?s=20)

[![AdamBack_MilkSad_Response.png](/img/user/para/artifacts/AdamBack_MilkSad_Response.png)](https://twitter.com/adam3us/status/1689051705504153600?s=20)

# More Resources
- [Milk Sad: Wallet Theft Enabled By Weak Entropy](https://www.nobsbitcoin.com/milk-sad-vulnerability-disclosure/)
- [X Space recording with Eric Voskuil, Bitcoin core developer and lead maintainer of libbitcoin](https://twitter.com/i/spaces/1vOxwMrpXDdGB)
- [Funds of every wallet created with the Trust Wallet browser extension could have been stolen without any user interaction](https://blog.ledger.com/Funds-of-every-wallet-created-with-the-Trust-Wallet-browser-extension-could-have-been-stolen/)