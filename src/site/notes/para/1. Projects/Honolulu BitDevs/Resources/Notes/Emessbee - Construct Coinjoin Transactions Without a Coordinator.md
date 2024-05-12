---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Emessbee - Construct Coinjoin Transactions Without a Coordinator.md","permalink":"/bit-devs/resources/notes/emessbee-construct-coinjoin-transactions-without-a-coordinator/","title":"Emessbee - Construct Coinjoin Transactions Without a Coordinator","tags":["bitcoin","bitdevs","socratic-34","privacy","coinjoin"],"noteIcon":"3","created":"2024-05-11T20:55:20.546-10:00","updated":"2024-05-11T21:53:05.264-10:00"}
---



[@super_testnet](https://twitter.com/super_testnet) shared a proof-of-concept implementation of the Emessbee protocol - a way to perform coinjoin transactions without a central coordinator.

> [!QUOTE] [Emessbee: Construct Coinjoin Transactions Without a Coordinator](https://www.nobsbitcoin.com/introducing-emessbee/)
> - The Emessbee protocol uses a 3-round serverless flow that can work with any 'public bulletin board' allowing for the sending and reading of messages.
> 
> ![BitDevs-34-Emessbee-Serverless-Flow-Diagram.png](/img/user/para/artifacts/BitDevs-34-Emessbee-Serverless-Flow-Diagram.png)
> 
> - The demo version of the protocol makes use of nostr as a public bulletin board for coordination, although the real version of the protocol would likely communicate over more secure channels.
> 
> [![BitDevs-34-Emessbee-X-1.png](/img/user/para/artifacts/BitDevs-34-Emessbee-X-1.png)](https://twitter.com/super_testnet/status/1787541079945838758?ref=nobsbitcoin.com)
> 
> - "Emessbee also requires users to pay for their own block space. The mining fee is calculated after all change addresses are submitted, then divided up equally among all participants, and deducted from the amount that would otherwise go to users as change," added the developer.
> - [According to the developer](https://twitter.com/super_testnet/status/1787251915446759781?ref=nobsbitcoin.com), the key advantages of the protocol are lack of coordinator and coordinator fees.
> 
> ![BitDevs-34-Emessbee-X-2.png](/img/user/para/artifacts/BitDevs-34-Emessbee-X-2.png)

[![Emessbee-Presentation-Thumbnail.png](/img/user/para/artifacts/Emessbee-Presentation-Thumbnail.png)](https://youtu.be/MT0CfuH7upE)

# More Resources
- [GitHub - supertestnet/coinjoin-workshop: A workshop on constructing coinjoin transactions without a coordinator](https://github.com/supertestnet/coinjoin-workshop)
- [Emessbee Coinjoin Workshop | stacker news](https://stacker.news/items/529905)