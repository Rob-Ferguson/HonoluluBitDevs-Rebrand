---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Blockstream Greenlight.md","permalink":"/bit-devs/resources/notes/blockstream-greenlight/","title":"Blockstream Greenlight","noteIcon":"3","created":"2023-06-10T23:15:26.237-10:00","updated":"2023-06-10T23:48:59.391-10:00"}
---



# Description

[Greenlight](https://blockstream.com/lightning/greenlight/) is a Lightning Network service powered by [Core Lightning](https://blockstream.com/lightning/) and operated by [Blockstream](https://blockstream.com/). The basic idea is that users can spin up a Lightning node on-demand in Blockstream's cloud infrastructure and interact with it as needed without ever having to relinquish custody of the private keys used to operate the node.

> [!QUOTE] [Greenlight by Blockstream: Lightning Made Easy](https://blog.blockstream.com/en-greenlight-by-blockstream-lightning-made-easy/)
> The key differences from other setups can be summed up by the following:
> - **Security**: Greenlight is non-custodial. While the nodes run on our infrastructure, our operations team never has access to your funds since keys are managed on the user’s device. Operations proposed by the node are verified on the user device before signing off on them.
> - **Low cost**: c-lightning’s low resource footprint and the fact that nodes run on-demand means running a node using Greenlight is very inexpensive compared to other providers. During the initial testing phases of the service, users won’t be charged at all.
> - **One user, one node**: Unlike bundling the node with the front-end app, Greenlight allows sharing a single node among any number of front-ends. This saves a lot of on-chain fees for the user, and reduces fragmentation of user funds. No more moving funds from your home node to your phone because you ran out of capacity.
> - **Simple recovery**: Losing your phone at sea won’t mean losing your bitcoin. Since we manage the database and the backups, recovering the funds is as simple as initiating a new front-end with your seed phrase.
> - **On-board to off-board**: Our main goal is to provide new users with a great first experience and a suitable starting point into the Bitcoin space. Conversely, we want users to eventually become knowledgeable enough to begin taking more control over their infrastructure. For that reason, we will offer users the option of exporting their node and loading it onto a platform of their choice.

# More Resources
- [[para/1. Projects/Honolulu BitDevs/Events/Socratic Seminar 20#^13b467\|Socratic Seminar 20 discussion]]
- [Lightning for Everyone in Any App: Lightning as a Service via the Breez SDK](https://medium.com/breez-technology/lightning-for-everyone-in-any-app-lightning-as-a-service-via-the-breez-sdk-41d899057a1d)