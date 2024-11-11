---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Pubky - Infrastructure for decentralized identity management, data routing, and hosting.md","permalink":"/bit-devs/resources/notes/pubky-infrastructure-for-decentralized-identity-management-data-routing-and-hosting/","title":"Pubky - Infrastructure for decentralized identity management, data routing, and hosting","tags":["bitcoin","bitdevs","socratic-39"],"noteIcon":"3","created":"2024-11-10T15:05:10.910-10:00","updated":"2024-11-10T16:03:33.026-10:00"}
---


# Reason for Pubky
> [!QUOTE] [Pubky - Infrastructure for decentralized identity management, data routing, and hosting](https://medium.com/pubky/pubky-the-next-web-3287b35408f1) 
> [Pubky](https://pubky.org/) is designed to redefine the web by creating a self-sovereign system where users have full control over their data and interactions. This document is the master reference for all things Pubky, encompassing the scientific, economic, and network/system design aspects of the project. Pubky uses foundational technologies like Public Key Addressable Resource Records ([PKARR](https://pkarr.org/)), Mainline Distributed Hash Table (DHT), homeservers, and indexers to create a decentralized, user-owned internet.
> - **The State of the Web**: The current web is dominated by centralized control, leading to issues such as censorship, algorithmic manipulation, and lack of user privacy. Big Tech algorithms are described as ‘poisoned algorithms’ that prioritize corporate and state interests while compromising user control. Platforms also lock users into walled gardens, limiting freedom and commodifying data.
> - **The Vision of Pubky**: Pubky represents a new paradigm for the web — one where **_you are the algorithm_**. Individuals have full control over their data, identity, and social interactions, breaking free from Big Tech platforms. **_Your public key is your self-sovereign domain name_**, signifying ownership over your digital presence.
> 
> ---
> ## How Pubky Fixes the Web
> **Poisoned Algorithms?**  
> - **You Are the Algorithm.** Pubky empowers users through **social tagging** and personalized feeds, effectively eliminating the control that Big Tech algorithms have over what content is presented.
> 
> **Censorship?**
> - **Cancel Cancel Culture.** With **PKARR identities** and decentralized homeservers, censorship becomes ineffective. Users can maintain their data, contacts, and followers even if a server tries to block or ban them. By commoditizing hosting services, Pubky ensures there is no financial or control incentive for hosts to censor users — if your homeserver bans you, you simply move to a new one, taking everything with you. This **credible exit** removes power from gatekeepers and puts it back in the hands of users.
> 
> **Walled Gardens?**
> - **Unlock the Web.** Pubky enables true portability of identity, social graphs, and content. Users are no longer locked into any single platform’s ecosystem. With Pubky, your data, identity, and social relationships are entirely yours — they move with you, not with the platform. It’s time to unlock the web and reclaim your digital autonomy.
> 
> ![Image](https://miro.medium.com/v2/resize:fit:1260/0*Q6kKLJCL9cSRq1Ae)
> 
> **Semantic Social Graph for Personalized Discovery:**
> - **Pubky’s Semantic Social Graph (SSG)** revolutionizes the way we discover and interact with content online. By leveraging a decentralized web of contextually rich tags and user-defined relationships, Pubky offers an experience that is genuinely tailored to individual interests and values. Users define how they interact with content and build a personalized, context-rich internet that serves them.

# How Pubky Works

> [!QUOTE] [Pubky - Infrastructure for decentralized identity management, data routing, and hosting](https://medium.com/pubky/pubky-the-next-web-3287b35408f1) 
> Pubky is a key-oriented, user-controlled web where individuals own their data, identity, and content, breaking free from Big Tech platforms. It’s not just another app or platform; it’s a paradigm shift — a new kind of web that puts you at the center. You are no longer a passive participant; you are the algorithm. Pubky is made of two major aspects:
> - [**Pubky Core**](https://pubky.org/):  The decentralized protocol infrastructure that powers identity management, data routing, and hosting.
> - [**Pubky App**](https://pubky.app/):  A flagship web application for interfacing with, and publishing to, the Pubky web, enabling personalized content feeds, social tagging, and web-of-trust-based curation.
> 
> ## Pubky Core
> 
> ![Image](https://miro.medium.com/v2/resize:fit:1260/0*ACCUq6Q_RXQcoUIR)
> 
> Pubky Core comprises the foundational protocols and technologies that power the decentralized Pubky ecosystem.
> 
> ![Image](https://miro.medium.com/v2/resize:fit:1260/0*1deMI94ghnu8VWxe)
> 
> - **PKARR (Public Key Addressable Resource Records)**: PKARR enables users to associate content, identities, and resources with cryptographic keys, ensuring verifiable ownership. PKARR handles key revocation through a distributed update mechanism, where changes are signed and propagated via Mainline DHT. Master keys are kept in cold storage, and access is delegated through revokable homeserver sessions, minimizing exposure and maximizing security.
> - Your **public key** is your **self-sovereign domain name**, representing your ownership of identity, data, and content in a censorship-resistant manner. Imagine having an online identity that is entirely yours — one that no platform can take away.
> 
> ![Image](https://miro.medium.com/v2/resize:fit:1260/0*pK4saGHU9PhwV4gV)
> 
> - [**Mainline DHT Integration**](https://github.com/pubky/mainline): Pubky uses Mainline DHT as its backbone for distributing and locating user data. This technology, which powers the BitTorrent network, enables decentralized data discovery, scalability, and fault tolerance, ensuring that Pubky’s network remains resilient and efficient under any conditions.
> - Decentralized peer discovery ensures that the network scales seamlessly, supporting millions of nodes globally.
> 
> ![Image](https://miro.medium.com/v2/resize:fit:1260/0*nJ8-vbWpTQnmxKHN)
> 
> - **Signed DNS Records for Self-Sovereign Domains**: Pubky leverages signed DNS records to create self-sovereign domain names linked directly to user public keys. Unlike traditional DNS systems, Pubky eliminates reliance on certificate authorities, mitigating risks such as cache poisoning and registrar hijacking.
> 
> ![Image](https://miro.medium.com/v2/resize:fit:1260/0*xOWcv9yxZ1C4P59-)
> 
> - **Homeservers**: Homeservers are web servers that store and serve user data based on the rules set by the user. Anyone can host a homeserver, and there is no network-effect moat favoring a particular provider. This guarantees users **a credible exit** by providing full portability of identity and data.
> - Users can seamlessly migrate their data, social graph, and identity to a new homeserver if needed, ensuring resilience and availability. If one server goes offline or bans you, your digital life doesn’t miss a beat.
> 
> ![Image](https://miro.medium.com/v2/resize:fit:1260/0*k6BSgPkRBEmvAvRd)
> 
> ## Pubky App: Your Portal to the Pubky Web
> Pubky App provides the interface through which users interact with the Pubky ecosystem, manage content, and curate their online experience.
> 
> ![Image](https://miro.medium.com/v2/resize:fit:1260/0*GlJE8Nr1VxGDMfK5)
> 
> - **Progressive Web App**: The Pubky App is a browser-based or locally installed tool that allows users to interact with the Pubky ecosystem. It offers **publishing**, **social tagging**, and **curation** features, letting users control every aspect of their web experience.
> - **You Are the Key**: Users represent themselves as public keys, removing the need for email or phone numbers and creating a self-sovereign identity that is consistent across the entire network.
> 
> ![Image](https://miro.medium.com/v2/resize:fit:1260/0*QLh2YtNT1vpovsv3)
> 
> - **Posts & Post Types**: Users can publish content in various formats: short notes, articles, images, videos, or links. The tagging system allows for enhanced curation and discoverability.
> - **The Taggable Web**: Forget the black-box algorithms of traditional platforms. With Pubky, users engage in **social tagging**, building a network based on their own values and preferences. Tags allow users to curate content and relationships, effectively making users “the algorithm” by deciding what content is relevant and how it is presented.
> 
> ![Image](https://miro.medium.com/v2/resize:fit:1260/0*LoRiGWsnEonaptUu)
> 
> - **Tagging Posts and Users**: Tagging is central to the Pubky experience. Users can tag content or other users, enhancing discoverability and establishing trust within the network. **“You Are the Algorithm”** means that user-created tags influence what content appears and how it is prioritized.
> 
> ![Image](https://miro.medium.com/v2/resize:fit:1260/0*6PnxcVC-QtDcdrFd)
> 
> - **Nexus Indexers**: The Pubky App integrates with Nexus Indexers to enhance the Semantic Social Graph, improving data discovery and content curation. Users create and save **custom content feeds**, filtering content based on their preferences. The Nexus Indexer acts like your “personal librarian,” crawling the pubkyverse and querying the Semantic Social Graph to help users find content, connections, and data relevant to their interests. Unlike centralized search engines, indexers can be run by anyone, democratizing the process of content discovery.
> 
> ![Image](https://miro.medium.com/v2/resize:fit:1260/0*kxWklnr3cLZULy4A)
> 
> - **Custom Feeds and Curation**: Users have the ability to create and save custom feeds, building their own **lens into the web**, shaped by the people they trust and the content they value.
> 
> ## Semantic Social Graph (SSG) and Contextual Web of Trust
> 
> ![Image](https://miro.medium.com/v2/resize:fit:1260/0*h-jCe5SJaGDuicZS)
> 
> The Semantic Social Graph (SSG) lies at the core of Pubky’s social infrastructure, allowing users to curate and manage their online interactions based on shared context and trust relationships.
> - **Tags and Relationships**:  Users categorize content, label relationships, and establish connections using cryptographically signed tags. Tags serve as filters that let users create custom perspectives, defining how they view the web. Users can establish **weighted relationships** that reflect trust and personal relevance, making Pubky a **semantic social graph** driven by user intent.
> - **Contextual Web of Trust (WoT)**:  Pubky allows users to establish a Contextual Web of Trust through tagging and direct interactions. Trust relationships are updated dynamically based on ongoing interactions and can be retracted as needed, ensuring that the trust graph remains current, meaningful, and secure.
> - **Graph Dynamics and Social Incentives**:  The SSG structure encourages engagement through **social tagging**, transforming content discovery into a collaborative experience. Users curate content that matters to them and establish their own networks of trust, putting the power of “the algorithm” directly into the hands of the community.

# More Resources
- [Pubky Core | Build The Next Web](https://pubky.org/#intro)
- [Overview - Pubky](https://pubky.github.io/pubky-core/overview.html)
- [Pubky · GitHub](https://github.com/pubky)
- [awesome-pubky: A curated list of awesome Pubky resources, libraries, tools and applications](https://pubky.tech/)
- [Pubky AI Bot: Automating Content with AI and Lightning | by Synonym | Oct, 2024 | Medium](https://medium.com/@synonym_to/pubky-ai-bot-62ebf7348c2a)
- [John Carvalho on nostr](https://primal.net/e/note18q09zjjnku60n3zsrf543jrkftf2ykrku83hvepfrzc3dfp8ce5q3zk9ny)

