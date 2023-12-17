---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Peerswaps - A Lightning channel rebalancing mechanism.md","permalink":"/bit-devs/resources/notes/peerswaps-a-lightning-channel-rebalancing-mechanism/","title":"Peerswaps - A Lightning channel rebalancing mechanism","tags":["bitdevs","bitcoin","lightning","liquid"],"noteIcon":"3","created":"2023-12-10T19:03:08.990-10:00","updated":"2023-12-16T18:46:44.619-10:00"}
---

# What is it?

> [!QUOTE] [GitHub - ElementsProject/peerswap](https://github.com/ElementsProject/peerswap)
> PeerSwap enables Lightning Network nodes to balance their channels by facilitating atomic swaps with direct peers. PeerSwap enhances decentralization of the Lightning Network by enabling all nodes to be their own swap provider. No centralized coordinator, no 3rd party rent collector, and lowest cost channel balancing means small nodes can better compete with large nodes.
# How does it work?

[![BitDevs-29-Peerswap-Diagram.png](/img/user/para/artifacts/BitDevs-29-Peerswap-Diagram.png)](https://strike.me/blog/peerswaps/)

> [!QUOTE] [Peerswaps | Strike blog](https://strike.me/blog/peerswaps/)
> ## Rebalancing Use Bitcoin (BTC) or Liquid Bitcoin (L-BTC)
 Peerswaps supports swapping using both the Bitcoin base chain, and the [Liquid](https://liquid.net/) Bitcoin federated sidechain. Each has their pros and cons, but for the purposes of rebalancing channels, the Liquid Network has a distinct advantage in two important areas - speed, and cost.
>
>### Speed
 > 
 > Blocks on the Liquid network are produced every minute and only 2 confirmations are required to complete a peerswap. So it takes ~2+ minutes to finalize a peerswap.
 >
 >On the Bitcoin network blocks are produced on average every 10 minutes and it will take 3 confirmations to complete a peerswap. So it takes ~30+ minutes to finalize a peerswap.
 >
 >### Cost
 >
 >The average transaction fee on the Liquid network is currently 0.1 sat/vbyte to get into the next block (although this may change over time). Given an average transaction size of ~2000 vbytes it would cost you about 200 sats to perform a swap. That is about $0.025 by today's exchange rates.
 >
 >On the Bitcoin base chain, fees are variable but generally much higher. At the time of writing, it will cost about 50 sat/vbyte to get into the next block. Given an average transaction size of ~300 vbytes it would cost you about 12,000 sats to perform a swap. That is about $5.62 by today's exchange rates. In other words, about 225 times more expensive than L-BTC, and a material consideration if you are a Lightning routing node operator or are running a business in which channels need to be regularly rebalanced.
 >
 >### Other Considerations
 >
 >Of course, cost and speed aren’t the only considerations. To use Peerswaps you will also have some additional overhead.
 >
 >Running peerswaps itself is pretty straightforward. It’s only acting as a coordinator so it doesn’t directly hold funds, although it does need access to your nodes, and it does need to maintain state so you will need to ensure you have robust secrets management and backup solutions in place.
 >
 >If you want to take advantage of Liquid you also need to run the Elements daemon where there is more to consider, as the Elements wallet will be holding an L-BTC balance. And there is also the different [trust model](https://blog.liquid.net/the-truth-about-liquid/) of the Liquid federation itself to consider.

# More Resources

- [PeerSwap - P2P BTC LN Balancing Protocol](https://www.peerswap.dev/)
- [GitHub - ElementsProject/peerswap](https://github.com/ElementsProject/peerswap)
- [Peerswaps | Strike blog](https://strike.me/blog/peerswaps/)