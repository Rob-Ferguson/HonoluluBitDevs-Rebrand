---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/ColdCard NFC Push Tx Feature.md","permalink":"/bit-devs/resources/notes/cold-card-nfc-push-tx-feature/","title":"ColdCard NFC Push Tx Feature","tags":["bitcoin","bitdevs","self-custody","coldcard","socratic-36"],"noteIcon":"3","created":"2024-06-30T17:53:04.979-10:00","updated":"2024-07-19T22:14:50.448-10:00"}
---



[![BitDevs-36-Coldcard-NFC-Push-TX-Example.png](/img/user/para/artifacts/BitDevs-36-Coldcard-NFC-Push-TX-Example.png)](https://pushtx.org/)

> [!QUOTE] [NFC PushTx and More Updates | COINKITE Blog](https://blog.coinkite.com/nfc-pushtx-released/)
> # NFC Push Tx
> 
> Once enabled with a service provider’s URL, you can tap the COLDCARD and your phone will open a webpage which immediately transmits your freshly-signed transaction onto the blockchain.
> 
> See _NFC Push Tx_ under _Settings_ to enable and select a service provider, or your own webpage. Yes, you can provide your own backend for complete transaction privacy!
> 
> As of today, there are two public services supporting this feature: [mempool.space](https://mempool.space/pushtx) and [coldcard.com](https://coldcard.com/pushtx). Both of these options are shown in the settings menu in the COLDCARD firmware.
> 
> Coinkite is operating the _Coldcard.com_ option, but your data does not touch our servers. Instead, your mobile browser is used to push the new transaction to two or more API services: _blockstream.info_ and _mempool.space_ (subject to change). After transmission, we offer links to number of block explorers where you can double-check the transaction is in the mempool and wait for confirmation.
> 
> We’ve published our JS code for this [on github](https://github.com/Coldcard/push-tx), including a [pre-built single-file HTML bundle](https://github.com/Coldcard/push-tx/tree/master/cc-implementation/build-single-file) you can host on any webserver your phone can reach. Mempool’s code is also [open here](https://github.com/mempool/mempool/pull/5132).
> 
> If you want to write your own service handler, the [full specification is public](https://github.com/Coldcard/firmware/blob/master/docs/nfc-pushtx.md) and very simple. It’s just _base64url_ and an SHA-256 checksum.
> 
> We’re happy to add new public service options into the firmware for everyone to use, just reach out to us if you are running a public service.
> 
> # How It Works
> 
> After the new transaction is signed and finalized by the COLDCARD, normally we write it out to a file for your wallet to transmit over the Bitcoin P2P network so that it enters the mempool and ultimately gets into a block.
> 
> With NFC PushTX, instead the complete transaction is encoded into a single long web URL, and COLDCARD pretends to be an NFC tag with just that URL on it. When you tap your NFC-enabled phone on the COLDCARD your phone sees a web URL and will open it—even without any new software.
> 
> The rest of the job is performed by that web page. It looks at the URL (which can be quite long, up to 8000 bytes) and decodes the Bitcoin transaction the COLDCARD put there. Then, the website transmits it to a Bitcoin node, either directly via it’s own infrastructure, or indirectly by making your browser push the transaction to a another existing endpoint (typically via POST).

[![BitDevs-36-Coldcard-NFC-Push-TX-YouTube.png](/img/user/para/artifacts/BitDevs-36-Coldcard-NFC-Push-TX-YouTube.png)](https://youtu.be/Tte7nddBUCI)

[![BitDevs-36-Coldcard-NFC-Push-TX-BTCSessions.png](/img/user/para/artifacts/BitDevs-36-Coldcard-NFC-Push-TX-BTCSessions.png)](https://x.com/BTCsessions/status/1811813191158276251)

