---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Make Democracy Great Again with Bitcoin.md","permalink":"/bit-devs/resources/notes/make-democracy-great-again-with-bitcoin/","title":"Make Democracy Great Again with Bitcoin","tags":["bitcoin","bitdevs","socratic-35","politics","democracy","voting"],"noteIcon":"3","created":"2024-07-19T21:35:19.861-10:00","updated":"2024-07-19T21:55:53.982-10:00"}
---



> [!QUOTE] <iframe src='https://6626b866f2af87-36468692.castos.com/player/1783540' width='100%' height='150'></iframe>
> "You eliminate 99% of the attack surface to a single moment in time, which is the beginning. And when you do that, would-be attackers are forced to take risks and make mistakes. You know, when someone is planning on doing election fraud, this doesn't mean that it's impossible for them to do it. But it narrows the window so much that they are likely going to mess up. And when they mess up, you catch them." 
> ~ Carlino

[![BitDevs-36-SimpleProof.png](/img/user/para/artifacts/BitDevs-36-SimpleProof.png)](https://simpleproof.com/)

# Mini-Documentaries

[![BitDevs-36-ImmutableDemocracy-Doc-1.png](/img/user/para/artifacts/BitDevs-36-ImmutableDemocracy-Doc-1.png)](https://youtu.be/g0nnM5_Z90E)

[![BitDevs-36-PaperDemocracy-Doc-2.png](/img/user/para/artifacts/BitDevs-36-PaperDemocracy-Doc-2.png)](https://youtu.be/B6pblkaZMCo)

# OpenTimestamps

> [!QUOTE] [OpenTimestamps: Scalable, Trust-Minimized, Distributed Timestamping with Bitcoin](https://petertodd.org/2016/opentimestamps-announcement)
>I’ve spent the past few weeks working on ([1](https://petertodd.org/2016/opentimestamps-announcement#fn:rewrite)) an old ([2](https://petertodd.org/2016/opentimestamps-announcement#fn:first-commit)) project of mine, [OpenTimestamps](https://opentimestamps.org/), and it’s ready for a [public alpha release](https://github.com/opentimestamps/opentimestamps-client/tree/opentimestamps-client-v0.2.0). It’s timestamping infrastructure with three big advantages over the existing alternatives:
>1. **Trust** — OpenTimestamps uses the decentralized, publicly auditable, Bitcoin blockchain, removing the need for trusted authorities; OpenTimestamps’s architecture is designed to support multiple, cross-checked, notarization methods in the future.
>2. **Cost** — OpenTimestamps scales indefinitely, allowing timestamps to be created for free by combining an unlimited number of timestamps into one Bitcoin transaction.
>3. **Convenience** — OpenTimestamps can create a third-party-verifiable timestamp in about a second; you don’t need to wait for a Bitcoin confirmation.
>
> ---
> 
> ## What Can and Can’t Timestamps Prove?
> 
> A timestamp proves that a message existed prior to some point in time; timestamps are occasionally referred to as “proofs-of-existence”. Being able to prove that data existed prior to a point in time is surprisingly useful. Let’s look at some use-cases to understand why:
> 
> ### Record Integrity
> >Our colocation centre informed us that someone broke into the cage the backend servers are located in last night; the last off-site backups were a week ago. The auditors want to know which records the intruders might have changed after they broke in. What do I tell them?
> 
> If we know when the intrusion happened, and have trustworthy timestamps for all records on the servers, we can use those timestamps to prove records existed prior to the intrusion. This lets post-intrusion auditing and recovery efforts focus on a much smaller set of data.
> 
> However, timestamps can’t help you if you don’t know when the intrusion happened, nor can they help for records created after: the intruder could have just as easily made the timestamp on data they’ve modified. But still, this is an excellent use of timestamping, one that usually helps, and will never make the problem any worse.
> 
> ### Software Signing and PGP
> 
> > I need to install this two-year-old software package to recover old records, but the developer revoked their PGP key six months ago - apparently their laptop got stolen. How do I know I’m getting the real thing?
> 
> PGP revocations have dates on them, so if the revocation is dated after the signature on the software - and there’s a valid timestamp for that signature - you’re good to go ([3](https://petertodd.org/2016/opentimestamps-announcement#fn:pgp-revocation)) Again, this is an excellent timestamping use case.
> 
> ### Evidence Authenticity
> 
> > I found a two-year-old snapshot of the defendant’s website on a public archiving service, but is it authentic?
> 
> A timestamp on a website snapshot doesn’t necessarily mean the snapshot is authentic, but it does greatly limit the scope of who might have tampered with the data. How likely is it that someone hacked into the archiving service, well before they knew there would be a lawsuit?
> 
> > I run a website archiving service, but I don’t have the resources to hire auditors or security consultants. How can I prove our archives haven’t been modified after the fact?
> 
> Simple answer: timestamps only make your problem better, not worse!
> 
> > My colleague said X in an IRC chat last year, but ever since the project failed they’re now claiming they said Y. How do I prove they’re lying?
> 
> A timestamp only proves _a_ message existed, not _the_ message. Last year, would you have known the significance of X and Y? If so, you could have timestamped two conflicting IRC logs.
> 
> > This anonymous crypto-currency ByteCoin looks pretty cool, the technology is legit, and there’s a two-year old community around it. [It can’t be a recently-created pre-mined scam with a fake community, right?](https://bitcointalk.org/index.php?topic=740112.0)
> 
> Timestamps can’t help you here: ByteCoin’s creators wouldn’t have timestamped anything. Additionally, keep in mind that even if they did, creating a crypto-currency from scratch could have very well taken two years - enough time to create perfectly valid timestamps for things that the public never saw.
> 
> ### Ownership
> 
> > I want to secure land titles on the blockchain with timestamps!
> 
> Timestamps do _not_ by themselves solve the doublespend problem; [Bitcoin is a lot more than just a way to timestamp data](http://www.metzdowd.com/pipermail/cryptography/2016-August/029947.html).
> 
> Having said that, timestamps can provide evidence that ownership _records_ are accurate; my client Verisart aims to do exactly that in for art provenance records. While a timestamp on an art provenance record such as a gallery sales receipt doesn’t by itself prove that record is valid, it can limit the scope of potential fraud, allowing provenance investigators to focus their efforts by eliminating many of the possible fraud scenarios they may be dealing with. 

# More Resources
- [OpenTimestamps](https://opentimestamps.org/)
- [Simple Proof](https://simpleproof.com/)
- [@carlostoriello on X](https://twitter.com/carlostoriello)

