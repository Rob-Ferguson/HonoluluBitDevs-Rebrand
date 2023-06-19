---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Bitkey.md","permalink":"/bit-devs/resources/notes/bitkey/","title":"Bitkey","noteIcon":"3","created":"2023-06-17T14:24:52.611-10:00","updated":"2023-06-18T15:59:23.213-10:00"}
---



# Description

[Block](https://block.xyz/), formerly known as Square, announced in 2022 that they'd be developing a new self-custody solution, which has since been named the [Bitkey](https://bitkey.build/). This solution leverages a 2-of-3 multisignature quorum where each component is built in-house and structured to work in tandem with one another:

> [!QUOTE] [How the wallet we're building works](https://bitkey.build/how-the-wallet-works/)
> With broad adoption in mind, the wallet we’re building has 3 valuable elements that together provide flexibility, security, and peace of mind. The 3 parts of the customer’s wallet have different permissions and optionality built-in to allow the customer to use these self-serve tools in a way that fits with their needs, which we realize will vary greatly for different people in different geographic settings. The wallet is composed of 3 things:
> 1. **A mobile app** that’s easy to use and allows customers to safely own and manage their bitcoin, while finding partners where they can buy/sell/convert between fiat and bitcoin
> 2. **A hardware device** that adds additional layers of security when moving money and acts as a self-serve recovery kit when a customer loses their mobile wallet
> 3. **Recovery tools** that help customers recover from losing part or all of their wallets, and that have a clear, defined set of rules to provide customers with reasonable support and peace of mind
> 
>  ![Bitkey Quorum Structure.png](/img/user/para/artifacts/Bitkey%20Quorum%20Structure.png)
>  
>  ---
>  
>  **How do I move money?**
>  
>  You can always move money without interacting with our servers by using the mobile key stored in the mobile app on your phone and the key stored in your hardware device – but we don’t expect you to do this for every transaction as you might want some more flexibility while still maintaining a high level of security.
>  
>  For smaller transactions, you only need your mobile key stored in your phone, and we will provide the second key in response to you when you move your money with your mobile app. This lets you keep your hardware device tucked away somewhere safe and reserved for larger-sized transactions - or for the recovery capabilities it holds, which we discuss in a few questions below. We don’t expect you to bring the hardware device with you for daily usage - in fact, it’s safer to keep your mobile phone separate from the hardware device on a regular basis as both of those things (the mobile app and the hardware device) are needed together to move larger amounts of money.
>  
>  ---
>  
>  **Does the company that makes this wallet have control over my funds?**
>  
>  No, we do not have control over your funds. You have true ownership: we cannot move your money for you, and you can move your money at any time without us. You have two of the three keys in your possession - on your mobile phone and on your hardware device. We only have one key, and because two keys are required to make a transaction, we cannot access, move, or take your money, or grant anyone else access to your money. Our key only serves two purposes: (1) only with your explicit permission, cooperate in recovering your wallet in case you’ve lost your phone or hardware, and (2) sign, in response to you moving your money with the mobile key for transactions you’ve allowed that do not additionally require your hardware device.

At the time of writing (for [[para/1. Projects/Honolulu BitDevs/Events/Socratic Seminar 23\|Socratic Seminar 23]]), Block recently began accepting applications for an [external beta program](https://bitkey.build/beta-launch/) though the end of June 2023 and would reach out to those chosen to participate by the end of the following month.

# Engineering & Design Principles

> [!QUOTE] [Product Principles & Jobs To Be Done: Our Compass for the Journey Ahead](https://bitkey.build/product-principles/)
>  **Two Jobs To Be Done**
>  
>  Our opportunity is to build a safe and easy way for people from all around the world with different experiences with technology and financial services to own bitcoin and manage their money with confidence – on their own terms.
>  
>  That means we want to serve **two** [**Jobs To Be Done**](https://jobs-to-be-done.com/the-history-of-jobs-to-be-done-and-outcome-driven-innovation-a2fdfd0c7a9a?ref=bitkey.build) for our customers:
>  1. **Help me _own_ bitcoin easily and safely**. Ownership of your keys means ownership of your money. We are building a wallet that prioritizes security and great customer experiences equally.
>  2. **Help me _manage_ my bitcoin by making it easy to send and receive money anywhere in the world quickly, easily, and cost-effectively**. Bitcoin, especially with its layer 2 innovation, Lightning, can help people send and receive money between friends, families, and businesses – both internationally and domestically. This decentralized payments network has the potential to create a more inclusive financial system for those who have traditionally been underserved.
>  
> ---
> 
> **Our Product Principles**
> 1. Simple and safe financial tools will empower people to access and benefit from bitcoin.
> 2. A customer should own their money with confidence and peace of mind.
> 3. A customer should be able to manage their money quickly, easily, and cost-effectively on their own terms.
> 4. We build transparently together with partners.
> 5. Global-first always.


> [!QUOTE] [Losing your keys without losing your coins](https://bitkey.build/losing-your-keys-without-losing-your-coins/)
>  **Who we’re building for**
>  
>  As we laid out in [our product principles](https://bitkey.build/product-principles/), we are trying to build a better tool for a global, mainstream audience to _safely_ self-custody and manage their digital assets, starting with bitcoin. Safety, in the context of a wallet, breaks out into two equally essential jobs:
>  - Ensure you do have access (**availability**)
>  - Ensure unauthorized people don’t have access (**security**)
>  
>  **These two jobs are almost always in tension**. Any added protection to keep a bad actor out adds a risk that it may also trip up the owner, and any new backup or alternative way to access creates a new potential security hole. From our global research, we've learned that most people holding coins on custodial platforms are hesitant to move to self-custody wallets because they are nervous about making mistakes using them - and not because they think self-custody solutions are less secure. They feel stuck: worried about the lack of control they might experience in a custodial platform, yet also anxious about the unforgiving product experiences that exist in today's relatively technical self-custody wallets.
>  
>  To make self-custody accessible to this kind of audience, we need to **optimize not just for security, but for safety**. That means building tools that balance the desire for perfect protection against practical realities - accidents happen, and people won’t always perform security procedures perfectly, especially ones that require new behaviors and deep understanding. We need to create forgiving recovery experiences that prioritize easier paths to get customers back on their feet when something goes wrong, with more tolerance for simple mistakes, and without a steep learning curve.
>  
> ---
> 
> **Recovery experiences and tools to enable them**
> 
> 1. **Enabling your App on a new phone with Cloud Backups and your Hardware**
> 	- Cloud Backups allows two encrypted copies of the App Key to be exported to customer-owned cloud storage during Wallet creation, one then decrypted by the Hardware Key, and the second decrypted by a secret held by Server and made available to App in rare emergencies (see 3.) below). The first backup is helpful for quick and easy setup of Wallet on new mobile devices, while the second copy protected by Social Recovery creates a path to recover from loss of both customer-owned hardware devices and their keys.
> 2. **Replacing your lost Hardware with Key Rotation with Delay and Notify**
> 	- A permanently lost key (either Hardware or App) can be replaced by ‘rotating in’ a new one by using the remaining customer-controlled key + Server’s key to move funds to the control of a new 2-of-3 address. Because Wallet won’t require a login/password elsewhere and identifies customers through key possession, there is a risk of theft by any would-be attackers temporarily compromising a single customer-owned device/key. To mitigate this risk without relying on things like formal identity verification, this recovery flow is time-gated to allow a rightful owner time to be made aware of and cancel any fraudulently-triggered recovery attempts by a bad actor. Notifications of recovery countdowns are broadcast persistently to any online App part of a Wallet undergoing recovery, and periodically to any other customer-provided communication channels such as email or via SMS. If that delay completes without anyone canceling by proving control of the key being replaced, then Server can more safely treat that key as lost and proceed to cooperate in replacing it.
> 3. **Recovering from losing *both* your App and Hardware with Social Recovery**
> 	- We plan to offer Social Recovery as an additional opt-in layer of protection that provides another alternative to identifying you as the real owner during a recovery event. This can be used to expedite Delay+Notify Key Rotation, and even unlocks a recovery path in a (more rare) scenario where something goes wrong with both your keys at once. Instead of relying on passwords and/or government-issued IDs to authorize yourself, Wallet can let you rely on people you trust to confirm you are who you say you are, so that Server can safely help you restore your Wallet even with one or both your keys missing or unavailable.


> [!QUOTE] [Staying Safe with Self-Custody](https://bitkey.build/staying-safe-with-self-custody/)
>  **How Bitkey Can Help**
>  
>   We're building Bitkey with a focus on security, resilience, and simple user experiences for a broad audience. Our system security choices mean Bitkey:
>   - **Uses three keys instead of one, by default.** Unlike in a single-signature setup, an attacker must be able to compromise more than one key in order to steal funds - compromising one key is not enough.
>   - **Incorporates secure hardware to keep one key stored offline.** Storing one of the keys in a device that is not persistently connected to the internet helps reduce the attack surface available to malicious parties looking to steal keys - and thus your money.
>   - **Doesn't require customers to hold onto seed phrases,** which are hard to hold onto and easy to get stolen.
>   - **Incorporates important platform security features,** the details of which we'll cover in depth in future posts. We’re designing for considerations including, but not limited to:
> 	  - Safe key generation, storage, and management on each of the three platforms that store a key (mobile app and secure hardware - which hold 2 keys controlled by the customer; and Block servers, which hold only one key, not enough to move money in this 2-of-3 model)
> 	  - Secure authentication on each of the three platforms
> 	  - Features that enable customers to ensure they're using the legitimate Bitkey mobile app and hardware
> 	  - Finding and fixing security issues by inviting scrutiny in the open and investing in security patching and hardening


> [!QUOTE] [Seed Phrases are Sharp Edges](https://bitkey.build/seed-phrases-are-sharp-edges/)
> - A seed phrase consists of 12 or 24 words representing your bitcoin ownership - it’s a human-readable version of the secret that can unlock your bitcoin on the blockchain. Lose track of it, and you’ve lost access to your money – potentially forever. Let someone else see it, and you’ve given them all they need to take your money. Keeping them safe is a lot of responsibility! It’s a sharp edge of self-custody that we are aiming to smooth out.
> - To prevent attackers from stealing people’s keys, we want to make it hard to accidentally leave the keys in an unsafe state or even to accidentally hand the keys over.
> - More fundamentally, beyond safe storage of these seed phrases, a newcomer to bitcoin might not fully understand that the seed phrases are all they - or an attacker - needs to move their money.
> - And there are so many ways for people to get tricked with seed phrases, from social engineering to [phishing](https://usa.kaspersky.com/blog/cryptocurrency-giveaway-scam/26492/?ref=bitkey.build) to schemes that trick people into using an [attacker-provided seed phrase](https://medium.com/metamask/rotten-seed-phrases-a-new-scam-targeting-crypto-users-b414f9ef292e?ref=bitkey.build) during wallet setup. **We don’t want our customers subject to these types of attacks, so we aren’t burdening them with seed phrases in the first place.**
> - Even customers who use hardware wallets and don't hand over their seed phrase to scammers can still be subject to remote theft. When customers have to figure out how to back up a sensitive seed themselves, some end up with a copy in their cloud storage that is either completely unencrypted or secured with a password weak enough to be brute-forced by an attacker who steals the file.
> - **So if seed phrases have so many sharp edges, why does anyone use them?**
> 	- **The first reason is to have a backup**: people use seed phrases to back up keys without needing to worry about file formats or other ways to protect digital information. After all, seed phrases are easy to write on post-it notes, or take a picture of and put in cloud storage. Bitkey is a multisignature wallet that uses three keys instead of one, so our [approach to recovery](https://bitkey.build/losing-your-keys-without-losing-your-coins/) allows customers to recover from losing either or both of their devices, but without having to rely on unencrypted seed phrases left accessible to prying eyes.
> 	- **A second reason people use seed phrases lies in ‘key portability’**: the ability to freely move your keys and money to and from different wallets, often by importing a seed phrase. If the provider of your software or hardware wallet goes out of business, or otherwise stops providing services to you for any reason, you can take your seed phrase - and your money - elsewhere. **We think this property is essential to self-custody, and are working on a feature that will allow customers to export their keys and take them to another wallet if they so choose**, but without asking people to hold onto seed phrases until they need them.  


> [!QUOTE] [Screens are not a Panacea](https://bitkey.build/screens-are-not-a-panacea/)
> **Easier to Use Means More Self-Custody Owners**
> 
> In earlier sections, we covered how a screen can be useful in several cases:
> 1. For providing receive addresses to a sender either in person or via multiple platforms/channels that the sender can compare against
> 2. For verifying outgoing transaction details, specifically on a device that was _**not**_ used to supply the hardware wallet with the transaction details in the first place
>  
> We think the above aren’t likely to happen for a broad audience - **it's hard to know how to verify correctly and very easy to do a naive comparison between screens that doesn't mitigate most threats**. We also think that reducing the complexity involved in hardware wallet management is one of the biggest levers we can use to bring more people to self-custody and put them in control of their money. Here's why:
> - Small screens are hard to use, and often accompanied by user input mechanisms that are hard to use, too. We want to make self-custody more accessible -- and enabling customers to use their familiar phone screen as much as possible is a key enabler.
> - Screens add cost and complexity to hardware wallets, including introducing more ways for the hardware to fail. We want to drive the cost of self-custody down, and the reliability up.
> - Using a screen correctly in order to provide protection is hard – customers have to know to compare their hardware wallet screen to an independent source on outgoing transfers, and to share receive addresses through multiple channels. When many customers don’t do this in practice, they incur a user experience cost that doesn’t come with the benefits they were hoping for. And the user experience cost also means that it’s more likely the feature will be misused, or won’t be used at all. We want large security benefits for low user experience cost – not the other way around.
> - Correctly verifying properties of transactions is likely to become more technical, not less (e.g. as the community builds on top of Bitcoin over time, for example to provide functionality over the Lightning network). We want to build solutions that hide this complexity from people where we can, while still giving them a set of options that allow them to add more verification friction where they really want it.

# Opinion

Block recognized some of the common pitfalls of single-signature security setups and how multisignature can help reduce some of those pain points (at the cost of increased complexity). In order to abstract away some of challenges of multisignature (and custody in general), they decided to build a full-stack solution that focuses on a cohesive user experience, rather than interoperability with other vendors.

This setup **will probably serve as a really simple and robust self-custody option to onboard a lot of new people into Bitcoin** without overwhelming them. 

Bitkey differs from typical collaborative custody setups (like [Unchained](https://unchained.com/) or [Nunchuk](https://nunchuk.io/)) in that more trust must be put in Block specifically, even though the user still maintains control of the majority of keys in the optimistic case. So far, it doesn't sound like the mobile app or backend server will be open sourced, so users will have to trust that the code does what it says and that Block will not act maliciously (e.g., pushing a bad update to the mobile app, the backend infrastructure gets compromised, etc.). Because there are 3 separate keys with different risk/security considerations, the odds of a user losing funds are still much lower than they would be with a typical custodial setup, even if Block were compromised in some way. 

Vendor lock-in is also somewhat of a concern - each component of this multisignature structure is designed to work as a complementary unit, so users would not be able to rotate to a different vendor's hardware device (e.g., ColdCard) or use a different "backend server" key custodian without setting up an entirely different multisignature quorum completely separate from Block's solution. The current design doesn't seem to accommodate swapping out vendors for any of the 3 keys without migrating away from the  Bitkey product family entirely.

You could also argue against some of the Bitkey team's claims about seed phrases and screens on hardware devices:
- Properly safeguarded seed phrases are a new concept for people and doing so properly takes research and practice. However, **it's still the foundation of true self-custody** - if you don't maintain a copy of each seed phrase and public key in the multisignature quorum, you can't unilaterally exit Block's infrastructure. Although Block says they'll allow users to access seed phrases if requested, you still have to trust that they actually will and that the software hasn't been compromised in some way to prevent it. **Abstracting away the seed phrases enables a more convenient UX at the cost of reduced individual sovereignty**. It adds friction in the worst-case scenario where the user needs to move money without Block's cooperation.
- On validating transaction information on hardware device screens, I generally agree with the Bitkey team's assessment of the pitfalls and false sense of security. Currently, **it isn't easy to properly validate and protect each piece of data in transit at each touchpoint in the transaction signing process**. Standardization around best practices is still ongoing in the industry (and the technology is constantly evolving). Because of that, work still needs to be done to designing a truly secure transaction signing experience across the full stack that's interoperable with different vendors (where different different combinations of hardware and software wallets can still be used together). **Block got around that issue by designing their Bitkey product suite without interoperability in mind**. Their server, mobile app, and hardware wallet specifically work as a unit and (presumably) no other vendors, so risk/responsibilities can be more effectively distributed across the stack (since each signing device in the Bitkey quorum serves a distinct purpose). The setup is less generalized to build a more cohesive experience, which is why the screenless Bitkey hardware wallet can defer a lot of the transaction verification to the server - that doesn't work with a typical multisignature quorum of 3 random hardware wallets because there is no server to do the same validation. If you're comfortable with this level of vendor lock-in and reliance on Block's infrastructure, then the screen on the actual device isn't very important (since you're just trusting the server to verify transaction data instead).

**Still, for the majority of relative newcomers (and even some more experienced Bitcoiners), this set of tradeoffs is likely a good balance of security and convenience. For more paranoid Bitcoiners (or those who just want more optionality), there are other custody options that provide more privacy, security, and sovereignty, depending on the tradeoffs they're willing to accept.** Either way, Bitkey's approach to custody is fairly novel, and the rest of the industry will gain useful insights from the user feedback. 

# More Resources
- HNL BitDevs [[para/1. Projects/Honolulu BitDevs/Events/Self-Custody Workshop\|Self-Custody Workshop]] reference material