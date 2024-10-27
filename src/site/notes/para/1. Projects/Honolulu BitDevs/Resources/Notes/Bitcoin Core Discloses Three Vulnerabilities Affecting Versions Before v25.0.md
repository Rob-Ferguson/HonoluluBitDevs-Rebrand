---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Bitcoin Core Discloses Three Vulnerabilities Affecting Versions Before v25.0.md","permalink":"/bit-devs/resources/notes/bitcoin-core-discloses-three-vulnerabilities-affecting-versions-before-v25-0/","title":"Bitcoin Core Discloses Three Vulnerabilities Affecting Versions Before v25.0","tags":["bitcoin","bitdevs","socratic-38","security","vulnerability"],"noteIcon":"3","created":"2024-10-26T12:59:50.876-10:00","updated":"2024-10-26T13:10:29.335-10:00"}
---



> [!QUOTE] [Email from Niklas Goegge](https://groups.google.com/g/bitcoindev/c/WeSDeV8YOSA?pli=1)
> Today we are releasing three security advisories for the Bitcoin Core project. **These vulnerabilities affect versions of Bitcoin Core before (and not including) 25.0.**  
> 
> ...
> 
> **This is part of the gradual adoption by the project of a new vulnerability disclosure policy.** The policy is available at [https://bitcoincore.org/en/security-advisories/#policy](https://bitcoincore.org/en/security-advisories/#policy).  We will follow up next month with vulnerabilities affecting Bitcoin Core versions before (and not including) 26.0, if any.

> [!QUOTE] [Bitcoin Core Discloses Three Vulnerabilities Affecting Versions Before v25.0](https://www.nobsbitcoin.com/bitcoin-core-discloses-three-vulnerabilities-affecting-versions-up-to-v25-0/) 
> Disclosed vulnerabilities include:
> - [**CVE-2024-35202**](https://bitcoincore.org/en/2024/10/08/disclose-blocktxn-crash/)**.** This is a **high severity** issue that allows attackers to crash Bitcoin Core nodes remotely by triggering an assertion in the blocktxn message handling logic. The vulnerability was discovered by _Niklas Gögge_ and [fixed](https://github.com/bitcoin/bitcoin/pull/26898) in Bitcoin Core v25.0.
> - [**Hindered block propagation due to mutated blocks**](https://bitcoincore.org/en/2024/10/08/disclose-mutated-blocks-hindering-propagation/)**.** This is a **medium severity** issue that allows a peer to clear the block download state of other peers by sending unrequested, mutated blocks. It was fixed in [#27608](https://github.com/bitcoin/bitcoin/pull/27608) by ensuring that a peer can only affect its own block download state, not the download states of other peers.
> - [**DoS due to inv-to-send sets growing too large**](https://bitcoincore.org/en/2024/10/08/disclose-large-inv-to-send/)**.** It's a **medium severity** issue where excessively large `m_tx_inventory_to_send` sets could disrupt node communication by slowing inventory message construction.

# More Resources
- [Bitcoin Core Disclosure of CVE-2024-35202](https://bitcoincore.org/en/2024/10/08/disclose-blocktxn-crash/)
- [No auto-update in Bitcoin Core means 13% of nodes could crash](https://protos.com/no-auto-update-in-bitcoin-core-means-13-of-nodes-could-crash/)
- [Bitcoin Core Security Advisories](https://bitcoincore.org/en/security-advisories/)

