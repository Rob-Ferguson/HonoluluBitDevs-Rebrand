---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/The Great Script Restoration - A Path Forward For Bitcoin.md","permalink":"/bit-devs/resources/notes/the-great-script-restoration-a-path-forward-for-bitcoin/","title":"The Great Script Restoration - A Path Forward For Bitcoin","tags":["bitcoin","bitdevs","socratic-34"],"noteIcon":"3","created":"2024-05-17T11:15:07.840-10:00","updated":"2024-05-17T12:22:17.715-10:00"}
---



> [!QUOTE] [Bitcoin Script | River](https://river.com/learn/terms/s/script-bitcoin/)
> # Bitcoin Script
> 
> Bitcoin’s scripting language is simply called Script. All Bitcoin scripts are written in Script. It is a simple language that is not Turing complete, meaning it lacks several logical functions, including loops. **This is done to ensure that no Bitcoin script can consume inordinate computing power and harm nodes on the network.**
> 
> Script is used almost exclusively to lock and unlock bitcoin, not to build applications or run programs. Script’s simplicity also gives Bitcoin security and makes it easier for developers to avoid losing money while designing wallets or applications on top of Bitcoin.

> [!QUOTE] [Opcode | River](https://river.com/learn/terms/o/opcode/)
> # Opcode
> 
> An operation code, or opcode, is a basic command of some computer languages. Bitcoin’s scripting language, called [Script](https://river.com/learn/terms/s/script-bitcoin/), has its own set of opcodes. **Each opcode is numbered and performs a limited, predefined function.** The combination of these opcodes and additional data such as addresses, public keys, and signatures can produce Bitcoin scripts.
> 
> For example, the most common Bitcoin script is P2PKH, which is composed of 4 opcodes and a public key hash. This script is a type of ScriptPubKey, which is used to lock bitcoin such that only someone capable of producing the public key and a valid signature can spend it.

# Great Script Restoration

Before Satoshi disappeared, **he removed 15 opcodes from Bitcoin Script**, disabling them entirely. He also imposed a size limit (520 bytes) for data being manipulated on the scripting engine stack. This was necessary because those now-removed opcodes enabled complicated scripts that could be used to denial-of-service attack the network overall, potentially crashing nodes due to the resulting validation cost. **The lack of resource constraints around these opcodes was the real problem** - not that they were inherently dangerous functionally.

> [!QUOTE] [The Great Script Restoration - A Path Forward For Bitcoin](https://bitcoinmagazine.com/technical/the-great-script-restoration-a-path-forward-for-bitcoin)
> At Bitcoin++ in Austin at the start of May, Core Lightning developer Rusty Russell made a pretty radical proposal during the first presentation of the conference. He essentially pitched the idea of [turning back on most of the opcodes](https://github.com/bitcoin/bips/blob/c2f268e83031b9b67e798c5c72a1171bfc463d1f/bip-unknown-var-budget-script.mediawiki) that Satoshi disabled in 2010 before he disappeared.
> 
> For the last few years since Taproot activated in 2021, the development space has been frankly kind of aimless. We all know that Bitcoin is not scalable enough to really service any sizeable chunk of the world’s population in a self sovereign way, and likely not even in a trust minimized or custodial way that can scale beyond very large custodians and service providers incapable of really escaping the long arm of the government.
> 
> Anyone who understands Bitcoin on a technological level understands this, it’s not a matter of debate. What is a matter of debate, and a very contentious one, is how to go about addressing this shortcoming. Since Taproot, everyone has been putting forward very narrow proposals intended to address only very particular use cases that could be enabled.
> ...
> **Rather than attempting to comprehensively address the expressivity and programmability needed to scale Bitcoin in a fundamental way, each of the proposals over the last few years was designed to either give a small increase in scalability or improve a single narrow functionality deemed desirable.** This I think is the source of why none of these conversations is going anywhere. No one is happy with any other proposal because it doesn’t cater to the use case they want to see built.
> 
> Nothing is comprehensive enough for anyone to think, outside of the proposal originator, that it is the sensible next move forward.
> 
> That is the logic behind the Great Script Restoration. **By pushing through and analyzing a comprehensive restoration of script as Satoshi initially designed it, we can actually try to explore the entire space of what functionality we need, rather than bickering and infighting over what small extension of functionality is good enough for now.**
> 
> ---
> 
> ## How To Make This Safe: varops
> 
> As I said above, the reason all of these opcodes were disabled was to remove risks of denial of service attacks that could quite literally crash the nodes comprising the network. There is a way to solve this, constrain the amount of resources any of these opcodes can use.
> 
> We already have such a solution when it comes to signature verification, the most expensive part of verifying Bitcoin scripts. It's called the sigops budget. Each use of a signature check opcode consumes a certain ‘budget’ of allowed signature operations per block. This places a hard limit on the cost that transactions can impose on users to verify an individual block.
> 
> Taproot shifted the way this works, instead of using a single global block limit, each transaction has its own sigops limit proportional to the size of the transaction. This works out essentially to the same global limit, but makes it easier to reason about in terms of how many sigops an individual transaction has available.
> 
> The shift in how Taproot handles sigops limits relative to each transaction offers a way to generalize this, which is what Rusty proposes with a varops limit. **The idea is to assign a cost for each of the reactivated opcodes to take into account the worst case, i.e. most expensive computational cost to validate, that each opcode could create. With this, every one of these opcodes would have its own “sigops” limit of sorts to restrain how many resources it could consume in verification.** It would also be based on the size of any transaction using them, so maintain the ease of reasoning about it, while still adding up to an implicit global limit per block.
> 
> **This would solve the denial of service risks that caused Satoshi to disable all of these opcodes in the first place.**
> 
> ---
> 
> ## Forward Momentum
> 
> I’m sure many of you are thinking “that is way too big of a change.” I can empathize with that, but I think an important aspect of this project as a proposal to understand is _we don’t have to do all of it_. **The value of this proposal isn’t necessarily actually turning all of this back on as a whole, it’s the fact that we would actually be comprehensively looking at a massive suite of primitives and asking ourselves what we really want out of this in terms of functionality.**
> 
> It would be a complete about face from the past three years of bickering and arguing over tiny narrow changes that only help certain functionalities. It’s a tent that could bring everyone together under one roof to really comprehensively assess where to go from here. Maybe we do wind up turning all of this back on, maybe we wind up just activating a few things because the consensus is that is all we need to enable functionality everyone agrees we need.
> 
> Regardless of what the end result actually is, it can be a productive change in the entire conversation around where we go from here. **We can actually map out and get a comprehensive lay of the land, rather than bumbling around arguing over what murky and half lit path to go down next.**

[![BitDevs-34-Script-Restoration-Rusty-BM-Interview-Thumbnail.png](/img/user/para/artifacts/BitDevs-34-Script-Restoration-Rusty-BM-Interview-Thumbnail.png)](https://youtu.be/GOzMYoIBJlc)

# More Resources
- [Rusty Russel's "Great Script Restoration" proposal for a segwit v2 upgrade](https://github.com/rustyrussell/bips/blob/c2f268e83031b9b67e798c5c72a1171bfc463d1f/bip-unknown-var-budget-script.mediawiki)
- [Rusty Russell -- The Great Script Restoration Project | bitcoin++ presentation](https://youtu.be/rSp8918HLnA?feature=shared)
- [Script - Bitcoin Wiki](https://en.bitcoin.it/wiki/Script)

