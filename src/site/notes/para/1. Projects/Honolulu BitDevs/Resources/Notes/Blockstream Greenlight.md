---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Blockstream Greenlight.md","permalink":"/bit-devs/resources/notes/blockstream-greenlight/","title":"Blockstream Greenlight","noteIcon":"3","created":"2023-06-10T23:15:26.237-10:00","updated":"2023-06-14T22:32:52.586-10:00"}
---



# Description

[Greenlight](https://blockstream.com/lightning/greenlight/) is a Lightning Network service powered by [Core Lightning](https://blockstream.com/lightning/) and operated by [Blockstream](https://blockstream.com/). The basic idea is that users can spin up a Lightning node on-demand in Blockstream's cloud infrastructure and interact with it as needed without ever having to relinquish custody of the private keys used to operate the node. Christian Decker explains the 5-minute overview of Greenlight and its intended purpose in this [YouTube video](https://youtu.be/u4ovmbDFJcY).

> [!QUOTE] [Greenlight by Blockstream: Lightning Made Easy](https://blog.blockstream.com/en-greenlight-by-blockstream-lightning-made-easy/)
> The key differences from other setups can be summed up by the following:
> - **Security**: Greenlight is non-custodial. While the nodes run on our infrastructure, our operations team never has access to your funds since keys are managed on the user’s device. Operations proposed by the node are verified on the user device before signing off on them.
> - **Low cost**: c-lightning’s low resource footprint and the fact that nodes run on-demand means running a node using Greenlight is very inexpensive compared to other providers. During the initial testing phases of the service, users won’t be charged at all.
> - **One user, one node**: Unlike bundling the node with the front-end app, Greenlight allows sharing a single node among any number of front-ends. This saves a lot of on-chain fees for the user, and reduces fragmentation of user funds. No more moving funds from your home node to your phone because you ran out of capacity.
> - **Simple recovery**: Losing your phone at sea won’t mean losing your bitcoin. Since we manage the database and the backups, recovering the funds is as simple as initiating a new front-end with your seed phrase.
> - **On-board to off-board**: Our main goal is to provide new users with a great first experience and a suitable starting point into the Bitcoin space. Conversely, we want users to eventually become knowledgeable enough to begin taking more control over their infrastructure. For that reason, we will offer users the option of exporting their node and loading it onto a platform of their choice.

At the time of writing (for [[para/1. Projects/Honolulu BitDevs/Events/Socratic Seminar 23\|Socratic Seminar 23]]), Blockstream has announced that Greenlight is now available for developers to start experimenting with: 

> [!QUOTE] [Greenlight by Blockstream: Scalable, Non-Custodial Lightning Infrastructure Now Open to Developers](https://blog.blockstream.com/greenlight-by-blockstream-scalable-non-custodial-lightning-infrastructure-now-open-to-developers/)
> ### What’s Available Today?
> While we are still actively developing Greenlight, the public interfaces are stable and ready for you to explore.
> 
> The client repository contains several components:
> - `gl-client` and its language bindings provide a simple API to interact with Greenlight and user nodes. The built-in signer takes care of managing your seed, and keeps it hidden from the node, and by extension us, the service operators. The _end-to-end_-verification (still under active development, not complete in this preview) in the signer ensures that any state change was authorized by an authenticated client, such that a potential node host compromise does not result in funds being lost.
> - `gl-testing` provides a complete mock environment to test your code against, rather than the real Greenlight service. To learn more, see our [tutorial](https://blockstream.github.io/greenlight/tutorials/testing/?ref=blog.blockstream.com) on how `gl-testing` can be used in a Python project using the Python bindings in `gl-client-py`, with more tutorials in the pipeline.
> - `gl-plugin` and `gl-signerproxy` allow anybody to replicate the interface exposed by Greenlight nodes, including the ability to use a remote signer, rather than keeping the seed on an exposed server.
> 
> The last two are the basis for our off-boarding plans: **if you outgrow Greenlight, or want more control, we enable you to off-board into your own infrastructure and all of your applications will keep working. This means that if you develop your application against the Greenlight API, you will automatically have support for Core Lightning out of the box.**

The last part of the snippet above is particularly interesting and speaks to Blockstream's intentions when funneling users into their ecosystem of products and services. They're following a 3-phase approach:
1. **Onboarding**: Pull forward a good onboarding UX for users new to Lightning by offloading all of the technical complexities associated with node provisioning and management - without sacrificing self-custody.
2. **Educating**: Provide the resources to teach users how Lightning node management works and build the tools that help streamline that knowledge transfer.
3. **Offboarding**: When users are ready, enable a seamless offboarding mechanism to switch to self-hosted, fully-sovereign infrastructure at home.

On a related note, in mid-June 2023, [Build on L2 (BOL2) announced support](https://community.corelightning.org/c/start-here/build-on-l2-supports-vls-integration-into-greenlight-with-150-000-grant) for the [Validating Lightning Signer project](https://vls.tech/?ref=nobsbitcoin.com) (VLS) with a $150,000 grant. BOL2 is a community initiative spearheaded by Blockstream to connect developers building on technology related to Core Lightning and Liquid. VLS is an open source project that includes the ability to operate on hardware security modules HSMs). This will improve enterprise-level Lightning node security by helping to keep private keys segregated from the node itself. Users can define rules for the types of transactions that the VLS module will automatically sign (e.g., channel opens, routing forwards, etc.), which will enable more sophisticated and programatic node management without necessarily requiring direct human interaction or relinquishing full signing access. VLS signer is fully integrated with Blockstream's Greenlight, which means that developers can easily access this signer without custom modifications.

# More Resources
- [[para/1. Projects/Honolulu BitDevs/Events/Socratic Seminar 20#^13b467\|Socratic Seminar 20 discussion]]
- [What Is Greenlight By Blockstream - The Bitcoin Manual](https://thebitcoinmanual.com/articles/greenlight-blockstream/)
- [Lightning for Everyone in Any App: Lightning as a Service via the Breez SDK](https://medium.com/breez-technology/lightning-for-everyone-in-any-app-lightning-as-a-service-via-the-breez-sdk-41d899057a1d)