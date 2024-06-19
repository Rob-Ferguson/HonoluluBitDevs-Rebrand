---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/LND Onion Bomb Denial of Service - Matt Morehouse.md","permalink":"/bit-devs/resources/notes/lnd-onion-bomb-denial-of-service-matt-morehouse/","title":"LND Onion Bomb Denial of Service - Matt Morehouse","tags":["bitcoin","bitdevs","socratic-35","lightning"],"noteIcon":"3","created":"2024-05-17T11:15:07.840-10:00","updated":"2024-06-19T12:30:03.225-10:00"}
---



> [!QUOTE] [DoS: LND Onion Bomb – Matt Morehouse](https://morehouse.github.io/lightning/lnd-onion-bomb/)
> LND versions prior to 0.17.0 are vulnerable to a DoS attack where malicious onion packets cause the node to instantly run out of memory (OOM) and crash. If you are running an LND release older than this, your funds are at risk! Update to at least [0.17.0](https://github.com/lightningnetwork/lnd/releases/tag/v0.17.0-beta) to protect your node.
> # Severity
> It is critical that users update to at least LND 0.17.0 for several reasons.
> - The attack is cheap and easy to carry out and will keep the victim offline for as long as it lasts.
> - The source of the attack is concealed via onion routing. The attacker does not need to connect directly to the victim.
> - Prior to LND 0.17.0, all nodes are vulnerable. The fix was not backported to the LND 0.16.x series or earlier.

# Vulnerability
- **Nature of the Vulnerability:** The Lightning Network uses onion routing for privacy in sending and receiving payments. A flaw in LND’s onion packet decoding process allows an attacker to craft packets that can exhaust a node’s memory.
- **Cause:** The absence of a bounds check on the payload size in the onion packet decoding code. This flaw allows memory allocation up to 4 GB regardless of the actual payload size.
- **Impact:** Nodes running LND versions older than 0.17.0 are vulnerable to this attack, which can cause them to run out of memory (OOM) and crash.

# Details
- **Memory Exhaustion:** An attacker can send a malicious packet with an encoded length of UINT32_MAX (4 GB), causing the victim’s node to crash if it has less than 4 GB of memory.
- **Large Nodes Vulnerable:** Even nodes with more than 4 GB of memory can be overwhelmed if enough malicious packets are sent simultaneously, as they are decoded in parallel.
- **Ease of Attack:** The attack is cheap and easy to execute, and it keeps the victim offline as long as the attack continues.
- **Concealed Source:** The attacker’s identity remains hidden due to the nature of onion routing.

# Fix & Prevention
- **Bounds Check:** A fix was introduced in LND 0.17.0, which includes a bounds check that limits the maximum memory allocation for decoding onion packets to 64 KB.
- **Fuzz Testing:** The vulnerability was discovered through a simple fuzz test for onion packet encoding and decoding, highlighting the importance of fuzz testing for functions that process untrusted inputs. Users are advised to write fuzz tests for all APIs handling untrusted inputs and to update their LND nodes to at least version 0.17.0.

# More Resources
- [DoS: LND Onion Bomb – Matt Morehouse](https://morehouse.github.io/lightning/lnd-onion-bomb/)

