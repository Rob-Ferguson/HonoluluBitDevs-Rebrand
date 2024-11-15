---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/\"Unlocking Mass-Market Self-Custody\" paper from Block - novel design for smartphone-based bitcoin wallets.md","permalink":"/bit-devs/resources/notes/unlocking-mass-market-self-custody-paper-from-block-novel-design-for-smartphone-based-bitcoin-wallets/","title":"\"Unlocking Mass-Market Self-Custody\" paper from Block - novel design for smartphone-based bitcoin wallets","tags":["bitcoin","bitdevs","socratic-39","self-custody","multisig"],"noteIcon":"3","created":"2024-11-12T20:42:37.719-10:00","updated":"2024-11-12T21:07:33.718-10:00"}
---



> [!QUOTE] [Building in the open: a novel design for smartphone-based bitcoin wallets](https://bitkey.build/building-in-the-open/) 
> # Design challenge: How could we turn smartphones into secure wallets?
> 
> Smartphones are ubiquitous and integral to daily life, making them a compelling platform for bitcoin wallets. The “holy grail” is to transform these devices into secure wallets that approach the security properties of specialized hardware setups. But let’s be honest—this is no small feat. Phones are general-purpose computing devices, always connected to the internet, and constantly carried around—conditions that expose them to risks like malware, remote exploits, and physical theft.
> 
> So, how could we leverage the convenience of smartphones while still providing strong protections against common attacks?
> 
> # A collaborative custody model for security and simplicity
> 
> In line with the philosophy behind our hardware wallet, we believe that [seed phrases are sharp edges](https://bitkey.build/seed-phrases-are-sharp-edges/) that can lead to user errors and loss of funds. Iterating from Bitkey’s 2-of-3 setup used by our hardware wallet—where the hardware, phone, and server each hold a key—we’ve designed a method for a software wallet to operate on a 2-of-2 model. This means both the phone and the server must collaborate to authorize a transaction.
> 
> But here’s the twist: to maintain true self-custody, the user is provided with an encrypted copy of the server’s key share. With control over both keys, you can move funds unilaterally if needed. It might sound counterintuitive to create a 2-of-2 wallet and then give both keys to the user. However, the server key is provided in a very particular way—designed to be used only when a user wants to exercise self-sovereignty and “escape” the wallet. We refer to this as the “Self-Sovereign Backup,” which we’ll delve into shortly, but first,  we need to touch on FROST.
> 
> # What is FROST, and how can it be leveraged?
> 
> To enhance flexibility in our collaborative custody model, we utilize FROST (Flexible Round-Optimized Schnorr Threshold Signatures). FROST enables off-chain key management, enabling adding or removing key shares without the need for an on-chain transaction or a wallet “sweep.”  Avoiding wallet sweeps is crucial for cost efficiency and avoiding linking previously unconnected UTXOs.
> 
> By managing keys off-chain with FROST, we can seamlessly handle practical scenarios like repairing a lost key, periodically rotating keys for enhanced security, or adding new hardware to an existing software wallet under this design—all without moving funds or compromising privacy.  The FROST protocol is detailed in the [whitepaper](https://assets.ctfassets.net/mtmp6hzjjvnd/6Qjcs8zgMiyffC0Uk8cx4V/380f331f5b4156622c8f5a376c352c96/Self-Custody_without_Hardware_-10-30-24-.pdf?ref=bitkey.build).
> 
> # Designed for security
> 
> We know that securing mobile devices is crucial, given their susceptibility to attacks. To mitigate these risks, we’ve incorporated several security features into our wallet design:
> 
> **Self-sovereign backup**  
> The Self-Sovereign Backup is the most critical element to protect, as it provides full unilateral control over a wallet. This backup is encrypted to a user’s phone’s secure enclave, meaning access is limited to the physical phone it was created on and the Bitkey-signed application. The app secures this key behind a time delay (e.g., 3 days) and a biometric scan after the delay. This multi-layered approach ensures that even if someone gains physical access to a phone, accessing funds won’t be easy.
> 
> **Delay and notify**  
> Delay and Notify is a core security system we currently use to protect sensitive actions in the Bitkey hardware wallet. When a protected action is initiated—like changing a sensitive setting or starting a recovery process—the server imposes a mandatory delay, usually several days, before executing the action. During this period, a user receives notifications via multiple channels (email, SMS, push notifications). This gives them time to notice any unauthorized activities and veto them before they take effect.  Even if an attacker gains control of a phone, they’d need to maintain control over all communication channels for the entire delay period—a challenging feat. It’s likely that the targeted individual will regain access to at least one channel, allowing them to cancel any unauthorized actions.
> 
> **Vaults**  
> Vaults offer an additional safeguard by allowing you to designate a portion of one’s funds to be stored with extra protection. Funds in the vault can’t be moved without going through the Delay and Notify process. This means that even if someone accesses an unlocked phone, they can’t instantly drain significant funds held in a Vault. Only a limited amount outside the vault is immediately accessible, mitigating the risk of substantial loss.
> 
> # Designed for Recovery
> 
> We understand that losing access to your funds is a nightmare scenario. That’s why we’ve built multiple layers of recovery options.  We’ll reference some cryptographic techniques below, if you want to learn more, please check out the [whitepaper](https://assets.ctfassets.net/mtmp6hzjjvnd/6Qjcs8zgMiyffC0Uk8cx4V/380f331f5b4156622c8f5a376c352c96/Self-Custody_without_Hardware_-10-30-24-.pdf?ref=bitkey.build).
> 
> **Loss of the application**  
> If a user loses access to the Bitkey app on their phone, they can restore their wallet using a backup stored in their cloud account. This backup is protected by a combination of a user-defined PIN and an Oblivious Pseudo-Random Function (OPRF). OPRF combines a server-side process with a PIN to create a robust encryption key that resists brute-force attacks. This allows the user to easily restore their wallet on a new phone while making it challenging for attackers who might have gained cloud access.
> 
> **Loss of the cloud backup**  
> If a user’s cloud backup is lost or deleted, the app will detect that fact and re-encrypt the wallet data using the same PIN encryption process before securely re-uploading it to the cloud. This automatic detection and re-encryption helps ensure that users remain protected, even if a cloud backup is inadvertently removed.
> 
> **Loss of both app and cloud backup**  
> In the worst-case scenario where both the app and the cloud backup are lost, we leverage a feature also used in the Bitkey hardware product called “Social Recovery.” This approach would allow you to enlist trusted individuals from a user’s personal network to assist in recovery. Through a protocol based on Portable Blind Cloud Storage and OPRF, each trusted contact securely stores the user’s app key. Even then, trusted contacts don’t gain any access to a user’s funds or sensitive information.
> 
> # Designed for privacy
> 
> One common concern with collaborative custody solutions is the potential loss of privacy since the server might need visibility into one’s wallet to function properly. However, we’ve implemented advanced cryptographic techniques to mitigate these concerns.
> 
> **Descriptor privacy**  
> A wallet descriptor reveals its entire transaction history. To protect a user’s privacy, the server must not learn this information while still being able to sign transactions. We achieve this by: (1) assigning the mobile application the sole responsibility for generating and interacting with the chain code; and (2) using predicate blind signing to allow the server to sign transactions without learning which child key it’s signing for or recognizing the final signature.
> 
> **Signing privacy**  
> Predicate blind signing combines blind Schnorr signatures with zero-knowledge proofs that make assertions about transaction attributes. This allows the server to enforce signing policies without learning any identifying information about the transaction itself.
> 
> **Vault privacy**  
> For transactions involving funds stored in the vault, the server only signs for the funds outside the vault, adding an extra layer of protection. To preserve privacy while proving funds exist, we use a zero-knowledge proof system similar to the proof-of-solvency approach utilized by exchanges. This method allows the app to prove to the server that sufficient funds exist for a transaction without revealing any specific details about wallet balances or transaction history.

>[!QUOTE]  ["Unlocking Mass-Market Self-Custody" paper from Block](https://assets.ctfassets.net/mtmp6hzjjvnd/6Qjcs8zgMiyffC0Uk8cx4V/f4be3237365ab7302915ec96d80f74d2/Unlocking_Mass_Market_Self_Custody.pdf)
> # Abstract 
> 
> This paper proposes a smartphone-based Bitcoin wallet design that aims to make self-custody safe and accessible to the mass market, recognizing that requiring specialized hardware to safely own bitcoin limits self-custody adoption. We address many of the security, availability, and privacy challenges inherent with mobile platforms by leveraging a variety of cryptographic techniques such as FROST-based multi-party computation (MPC), secure key backups, Oblivious Pseudorandom Functions (OPRF) for PINs, and zero-knowledge proofs, alongside protective procedures like server signing policies and time-delayed security mechanisms. We detail the key management architecture, backup and recovery mechanisms, and security features designed to protect against unauthorized access and actions. Building upon the widespread ownership of smartphones, our approach aims to demonstrate a practical pathway toward widespread self-custodial adoption
> 
> # Introduction 
> 
> The pursuit of widespread self-custodial adoption in Bitcoin faces a fundamental challenge: balancing security with usability. Today, the benchmark for secure Bitcoin storage is often considered to be a multisignature setup utilizing specialized hardware wallets. While this approach offers formidable protection against a range of attack vectors, it can present significant barriers to entry for the average customer. Expecting the mass market to invest in and manage specialized hardware is impractical and hinders the broader adoption of self-custody solutions. 
> 
> Mobile phones, ubiquitous and integral to daily life, represent a compelling platform for Bitcoin wallets. The “holy grail” is to transform these devices into secure wallets that approach the security properties of specialized hardware setups. However, this is no small feat. Phones are general-purpose computation devices, perpetually connected to the internet, and constantly carried on one’s person—conditions that inherently expose them to increased security risks such as malware, remote exploits, and physical theft. To address these challenges, we start by identifying key properties that Bitcoin wallets should embody.
> - **Usability**: Familiar user experience on familiar devices without creating operational security burdens.
> - **Security**: Safeguard against both remote and physical threats.
> - **Availability**: Provide wallet recovery mechanisms after loss of devices, cloud accounts, or both
> - **Privacy**: Protect identity and transaction details even in collaborative custody configurations.
> 
> In this paper, we introduce a smartphone-based wallet design that addresses these challenges. By leveraging a combination of cryptographic techniques and security features, we demonstrate how to significantly improve upon existing software wallet designs while approaching some of the desirable security properties of hardware wallets. Recognizing that all wallet designs involve a series of trade-off decisions, we believe the combination presented herein offers a practical path toward bringing self-custody to the mass market.
> 
> ---
> 
> # Key Management
> 
> Effective key management is the cornerstone of a secure and user-friendly Bitcoin wallet. Traditional single-signature (1-of-1) solutions present significant risks due to their reliance on a single point of failure. Customers are often required to export mnemonic seed phrases and store them securely—a process that is both cumbersome and fraught with potential for loss or theft. In many cases, customers are not even aware of the sensitivity and responsibility they are undertaking. 
> 
> To mitigate these risks, we explore a two-of-two (2-of-2) multi-party computation (MPC) approach. In this setup, both the customer’s mobile device and the server each hold a distinct key share, and both are required to authorize transactions. Notably, Coinbase has made significant contributions in this area with their 2-of-2 MPC wallet architecture, where normal spending requires collaboration between the customer’s device and Coinbase’s servers, while the customer retains a self-custodial backup of the server’s key share. 
> 
> We propose enhancements to the 2-of-2 MPC architecture by optimizing it for Bitcoin and addressing practical considerations unique to mobile wallets. We recognize that involving more keys in a k-of-n setup, without introducing additional devices, adds complexity with.
> 
> ---
> 
> # Key Backups
> 
> In the previous sections, we defined the key arrangements of our wallet, detailing how they are generated, stored, and utilized within our 2-of-2 spending paths. We also discussed how these keys are secured, and the use of FROST to move key management operations off-chain, enhancing both privacy and security. Having established the operational keys of the wallet, we now turn our attention to the crucial aspect of key backup, which ensures both self-sovereignty and recovery from loss. This section is anchored on two main considerations:
> - **Loss of the Server**: This scenario encompasses situations where the server becomes inaccessible, becomes uncooperative, attempts to censor transactions, or when the customer simply wishes to exercise full self-sovereignty without relying on the server’s participation. To facilitate unilateral control over their funds, we provide customers with a Self-Sovereign Backup (SSB). The SSP contains the necessary key material to assemble the Self-Sovereign Backup, allowing customers to independently access and transfer their funds to any destination of their choosing.
> - **Loss of the App**: In cases where the customer loses their mobile device, the app key share stored on the phone is no longer accessible. To address this, we securely back up the app key share in the customer’s cloud account. Importantly, this key share is encrypted in a manner that does not rely on the phone, nor is the secret revealed to the server.
> 
> ---
> 
> # Recovery
> 
> In the preceding sections, we detailed the architecture of our wallet, covering key management, backup mechanisms, and security features designed to protect against unauthorized actions. This section examines situations where the customer loses access to parts of their wallet—such as the mobile application, the cloud backup, or both. We address these scenarios by explaining how customers can recover wallet access, the mitigations used to prevent the recovery tools being useful for attackers.
> 
> ---
> 
> # Privileged Actions
> 
> To enhance the security of our wallet, we introduce mechanisms to protect certain privileged actions. These mechanisms leverage time delays as a defensive strategy, making it significantly more difficult for attackers to execute unauthorized operations—especially if they have only momentary or partial access to the customer’s device or credentials. By incorporating these time-based defenses, we increase the likelihood that only the true owner can perform sensitive operations.
> 
> ---
> 
> # Privacy
> 
> Maintaining customer privacy is a critical challenge in collaborative custody arrangements, where the server actively participates in wallet security. The key issue lies in leveraging the server’s capabilities without compromising sensitive information about the customer’s wallet and transactions. In our proposed design, we demonstrate how privacy can be preserved even when the server is involved in critical operations. We address this by focusing on descriptor privacy, signing privacy, and vault privacy.
> 
> ---
> 
> # Summary
> 
> The landscape of Bitcoin self-custody has often faced a balance between security and usability. Our wallet design brings together cryptographic techniques like FROST-based MPC, secure key backups, OPRFbased PINs, and zero-knowledge proofs into a cohesive solution tailored for the mass market. Our goal is to maximize security, privacy, and availability, without compromising on the user experience provided by a smartphone-based solution.

# More Resources
- [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Bitkey\|Bitkey]]

