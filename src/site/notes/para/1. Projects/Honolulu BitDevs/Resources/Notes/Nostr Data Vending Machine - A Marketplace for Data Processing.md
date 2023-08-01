---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Nostr Data Vending Machine - A Marketplace for Data Processing.md","permalink":"/bit-devs/resources/notes/nostr-data-vending-machine-a-marketplace-for-data-processing/","title":"Nostr Data Vending Machine - A Marketplace for Data Processing","tags":["nostr, lightning, zap, ai, llm, agent, micropayment"],"noteIcon":"3","created":"2023-07-30T00:53:31.852-10:00","updated":"2023-07-31T14:52:10.627-10:00"}
---



> [!QUOTE] [Nostr Data Vending Machine NIP](https://github.com/nostr-protocol/nips/blob/67e950a2009e81df1b8c91b0a2ade0596e83f168/vending-machine.md) (nostr improvement proposal)
> # Rationale
> Nostr can act as a marketplace for data processing, where users request jobs to be processed in certain ways (e.g. "speech-to-text", "summarization"), but where they don't necessarily care about "who" processes the data.
> 
> This NIP is not to be confused with a 1:1 marketplace; but rather, a flow where user announces a desired output, willigness to pay, and service providers compete to fulfill the job requirement in the best way possible.
> 
> There are **two actors** to the workflow described in this NIP:
> - Customers (npubs who request a job)
> - Service providers (npubs who fulfill jobs)
> 
> # User flow
> - User publishes a job request `{ "kind": 68001, "tags": [ [ "j", "speech-to-text" ], ... ] }`
> - Service providers listen for the type of jobs they can perform `{"kinds":[68001], "#j": ["speech-to-text", "image-generation", ... ]}`
> - When a job comes in, the service providers who opt to attempt to fulfill the request begin processing it
> - Upon completion, the service provider publishes the result of the job with a `job-result` event.
> - Upon acceptance, the user zaps the service provider, tagging the job request

 
The [Nostr Data Vending Machine (DVM) NIP](https://github.com/nostr-protocol/nips/blob/67e950a2009e81df1b8c91b0a2ade0596e83f168/vending-machine.md) was created by [PABLOF7z](https://primal.net/p/npub1l2vyh47mk2p0qlsku7hg0vn29faehy9hy34ygaclpn66ukqp3afqutajft). He has since [open sourced an implementation of the NIP](https://github.com/pablof7z/nostr-data-vending-machine).

The general idea is that nostr can be used as an open communication protocol for broadcasting and coordinating data processing job requests. By following the standard defined in the DVM NIP, automated AI agents (and humans) can watch nostr relays for job requests, complete the task, broadcast the result, and get [zapped as payment](https://nostr.how/en/zaps) for their work. 

You could imagine competitive markets develop where AI agents are creating and completing various DVM jobs by autonomously coordinating with each other over nostr. As they complete those tasks, agents will probably be utilizing large sets of [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Lightning Labs Releases Developer Tools for Powering APIs and Large Language Models#L402 ⚡ + AI 🤖\|L402-enabled public APIs]] to collect and process data at each step.

# More Resources
- [Nostr Data Vending Machine: A Marketplace for Data Processing](https://www.nobsbitcoin.com/data-vending-machine-implementation-open-sourced/)
- [Highlighting from an AI through nostr - YouTube](https://youtu.be/OJx6ExVTS7c)
- [AI4ALL: Nostr Data Vending Machine Clients and Services Tutorial - YouTube](https://www.youtube.com/watch?v=dAuLnNxU0Yg)
- [Tutorial for AI Nostr DVM Client and Service Bounties - Replit](https://replit.com/@kody/Tutorial-for-AI-Nostr-DVM-Client-and-Service-Bounties#.tutorial/00-intro.md)