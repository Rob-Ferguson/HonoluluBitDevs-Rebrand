---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Mercury Layer - Bitcoin MPC layer 2 protocol using blinded signatures.md","permalink":"/bit-devs/resources/notes/mercury-layer-bitcoin-mpc-layer-2-protocol-using-blinded-signatures/","title":"Mercury Layer - Bitcoin MPC layer 2 protocol using blinded signatures","tags":["bitdevs","bitcoin","socratic-30","statechain"],"noteIcon":"3","created":"2024-01-20T22:32:15.564-10:00","updated":"2024-01-28T14:50:02.884-10:00"}
---

# Overview

[![BitDevs-30-Statechains-Youtube-Thumbnail.png](/img/user/para/artifacts/BitDevs-30-Statechains-Youtube-Thumbnail.png)](https://youtu.be/FNHPI10af4g?feature=shared)

Mercury Layer is a layer-2 protocol designed to leverage [statechains](https://bitcoinops.org/en/topics/statechains/), enabling the off-chain transfer of entire bitcoin UTXOs such that they remain under full custody of the rightful owner at all times, are instantly settled, and cost zero transaction fees. These transfers can happen without requiring any on-chain blocks to be mined.

The simplest way to think about a statechain is as a virtual [opendime](https://opendime.com/). You can load funds onto an opendime and physically give it to someone else, effectively transferring ownership of those UTXOs without ever having to transact on chain. Statechains are a similar process but conducted via digital means - you're transferring control of entire UTXOs without ever making a transaction on the base layer (i.e., like exchanging private keys with someone else but removing your own ability to spend after the exchange is done).

> [!QUOTE] [Mercury Layer: A Massive Improvement On Statechains](https://bitcoinmagazine.com/technical/mercury-layer-a-massive-improvement-on-statechains)
> Statechains are essentially analogous to payment channels in many ways, i.e. they are a collaboratively shared UTXO with a pre-signed transaction as a mechanism of last resort for people to enforce their ownership. The major difference between a Lightning channel and a statechain is the parties involved in collaboratively sharing the UTXO, and how ownership of an enforceable claim against it is transferred to other parties.
> 
> Unlike a Lightning channel, which is created and shared between two static participants, a statechain is opened with a facilitator/operator, and can be freely transferred in its entirety between any two participants who are willing to trust the operator to be honest, completely off-chain. Someone wishing to load a statechain collaborates with the operator to create a single public key that the creator and operator both hold a share of the corresponding private key, with neither having a complete copy of the key. From here they pre-sign a transaction allowing the creator to claim their coins back after a timelock unilaterally.

# How does it work?

> [!QUOTE] [Mercury Layer: Bitcoin MPC layer 2 protocol using blinded signatures](https://mercurylayer.com/)
> The simplest function of the Mercury layer system is to enable the transfer of the ownership of individual UTXOs controlled by a single public key `P` from one party to another without an on-chain (Bitcoin) transaction (or change in the spending condition). The SE facilitates this change of ownership, but has no way to seize, confiscate or freeze the output. To enable this, the private key (`s`) for `P` (where `P = s.G`) is shared between the SE and the owner, such that neither party ever has knowledge of the full private key (which is `s = s1 + o1` where `s1` is the SE private key share, and `o1` is the owner key share) and so cooperation of the owner and SE is required to spend the UTXO. However, by sharing the secret key in this way, the SE can modify its key share (`s1 -> s2`) so that it combines with a new owner key share (`o2`) with the cooperation of the original owner, but without changing the full shared key (i.e. `s1 + o1 = s2 + o2`) all without any party revealing their key shares or learning the full key. The exclusive control of the UTXO then passes to the new owner without an on-chain transaction, and the SE only needs to be trusted to delete/overwrite the key share corresponding to the previous owner.
> 
> This key update/transfer mechanism is additionally combined with a system of _backup_ transactions which can be used to claim the value of the UTXO by the current owner in the case the SE does not cooperate or has disappeared. The backup transaction is cooperatively signed by the current owner and the SE at the point of transfer, paying to an address controlled by the new owner. To prevent a previous owner (i.e. not the current owner) from broadcasting their backup transaction and stealing the deposit, the `nLocktime` value of the transaction is set to a future specified block height. Each time the ownership of the UTXO is transferred, the `nLocktime` is decremented by a specified value, therefore enabling the current owner to claim the coin before any of the previous owners.
> 
> ---
> 
> The life-cycle of a coin in the statechain, key reassignment and closure is summarised as follows:
> 
> 1. The first owner initiates a UTXO statechain with the SE by paying BTC to an address where Owner 1 and the SE each have private key shares, both of which are required to spend the UTXO. Additionally, the SE and the initiator cooperate to sign a backup transaction spending the UTXO to a timelocked transaction spending to an address fully controlled by Owner 1 which can be confirmed after the `nLocktime` block height in case the SE stops cooperating.
> 2. Owner 1 can verifiably transfer ownership of the UTXO to a new party (Owner 2) via a key update procedure that overwrites the private key share of SE that invalidates the Owner 1 private key and _activates_ the Owner 2 private key share. Additionally, the transfer incorporates the cooperative signing of a new backup transaction paying to an address controlled by Owner 2 which can be confirmed after a new `nLocktime` block height, which is reduced (by an accepted confirmation interval) from the previous owners backup transaction `nLocktime`.
> 3. This transfer can be repeated multiple times to new owners as required (up until the most recent recovery `nLocktime` reaches a lower limit determined by the current Bitcoin block height).
> 4. At any time the most recent owner and SE can cooperate to sign a transaction spending the UTXO to an address of the most recent owner's choice (i.e. closure).
> 
> ---
> 
> **Statechains**
> 
> The essential function of the Mercury layer system is that it enables 'ownership' (and control) of a UTXO to be transferred between two parties (who don't need to trust each other) via the SE without an on-chain transaction. The SE only needs to be trusted to not store any information about previous key shares and then the transfer of ownership is completely secure, even if the SE was to later get compromised or hacked. At any time the SE can prove that they have the key share for the current owner (and only to the current owner). The current owner is required to sign a _statechain transaction_ (`SCTx`) with an owner key to transfer ownership to a new owner (i.e. a new owner key). This means that any theft of the UTXO by the collusion of a corrupt SE and old owner can be independently and conclusively proven.
> 
> **Blinding**
> 
> The Mercury layer server is _blind_ - that is the server _does not_ and _cannot_ know anything that would enable it to identify the coin (UTXO) that it is co-signing for. This prevents any censorship and storage of any identifying data in the server - the server itself is not aware of bitcoin, and does not perform any verifcation of transactions.
> 
> To achieve this the server cannot know or be able to derive in any way the following values:
> - The TxID:vout of the statecoin UTXO
> - The address (i.e. public key) of the UTXO
> - Any signatures added to the bitcoin blockchain for the coin public key.
>  
> This means that the server cannot:
> - Learn of the shared public key it is co-signing for.
> - Learn of the final (unblinded) form of any signatures it co-generates.
> - Verify ANY details of backup or closure transactions (as this would reveal the statecoin TxID).

# More Resources
- [Mercury Layer - Bitcoin MPC layer 2 protocol using blinded signatures](https://mercurylayer.com/)
- [Statechains: Non-custodial Off-chain Bitcoin Transfer | by Ruben Somsen | Medium](https://medium.com/@RubenSomsen/statechains-non-custodial-off-chain-bitcoin-transfer-1ae4845a4a39)
- [What Are Bitcoin State Chains? - The Bitcoin Manual](https://thebitcoinmanual.com/blockchain/state-chain/)
- [Mercury Layer is Now Code Complete and Available For Testing](https://www.nobsbitcoin.com/mercury-layer-available-for-testing/)
- [This Tool Can Protect Your Privacy When Using Bitcoin](https://bitcoinmagazine.com/technical/a-new-privacy-tool-for-bitcoin)