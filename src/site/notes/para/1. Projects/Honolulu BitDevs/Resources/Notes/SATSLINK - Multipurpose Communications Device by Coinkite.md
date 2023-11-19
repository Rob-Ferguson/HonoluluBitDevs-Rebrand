---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/SATSLINK - Multipurpose Communications Device by Coinkite.md","permalink":"/bit-devs/resources/notes/satslink-multipurpose-communications-device-by-coinkite/","title":"SATSLINK - Multipurpose Communications Device by Coinkite","tags":["bitdevs","bitcoin","socratic-28","communication","hardware"],"noteIcon":"3","created":"2023-11-17T19:09:19.844-10:00","updated":"2023-11-19T10:24:37.785-10:00"}
---



# What is it?


> [!QUOTE] [Satslink specs (not final)](https://satslink.com/specs)
> - ESP32-S3 main CPU running at 240Mhz with 512k of SRAM, 8M of PSRAM, and 32M of flash ([datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-s3_datasheet_en.pdf))
> - Wifi (2.4Ghz) and Bluetooth support
> - ESP-Now protocol for device-to-device radio, Internet access via your 2.4Ghz Wifi access point
> - 320x240 colour LCD (IPS with wide viewing angle)
> - Full QWERTY keyboard
> - NFC tag emulation (NFC-V radio protocol)
> - QR scanner module (with light, dedicated co-processor for image processing)
> - RGB light for "message waiting" feature (top left corner)
> - Secure element for private key storage (part number, vendor TBD)
> - Powered by 3 x AAA cells, or USB-C port
> - Dedicated keyboard scanning chip to reduce CPU load
> - MicroSD slot for data transfer
> - Expansion GPIO and serial port for hacking/debug (includes all ESP32 programming connections)
> - Typically programmed in Micropython, all source fully-available; completely field upgradable with no locked-down ROM areas
> - Rugged plastic enclosure

# Why does it matter?

[![BitDevs-28-Satslink-Diagram.png](/img/user/para/artifacts/BitDevs-28-Satslink-Diagram.png)](https://bitcoinmagazine.com/business/coinkites-newest-bitcoin-device-can-serve-as-a-lightning-wallet-and-nostr-client)

> [!QUOTE] [SATSLINK: A Fusion of Technologies for Bitcoin and Lightning Network Applications - LightningNetwork+](https://lightningnetwork.plus/posts/462)
> ## How SATSLINK Augments the Bitcoin Lightning Network Ecosystem
> 
> SATSLINK, brimming with features, is poised to bolster the Lightning Network's prowess. It presents the potential to remotely connect with bitcoin nodes, be it at one's home, office, or even the cloud. Key highlights include:  
> - **Security:** The Infineon Trust-M secure element stands as a bastion for private key storage pertaining to your Bitcoin node.
> - **Remote Node Management:** Harnessing SATSLINK's multifaceted communication mechanisms will help Lightning Network node management, especially in regions with limited internet access.
> - **QR Payments:** The embedded QR scanner in SATSLINK paves the way for streamlined Lightning Network transactions and instantaneous payments.
> - **NFC-Enabled Payments:** Transact with ease, courtesy of SATSLINK's NFC tag emulation, which propels contactless Lightning Network payments
> 
> ## Beyond Bitcoin
> - **Decentralized Communication:** Leveraging the ESP-Now protocol, SATSLINK can relay decentralized messages, mitigating reliance on centralized ISPs.
> - **Open-Source Potential:** SATSLINK’s open-source Micropython infrastructure invites custom applications, catering to a diverse range of communication needs.
> - **Portable Convenience:** The device's pocket-friendly design, combined with a range of communication tools, makes it a must-have for tech aficionados on the move.


# More Resources

- [Coinkite's Newest Bitcoin Device Can Serve As A Lightning Wallet And Nostr Client](https://bitcoinmagazine.com/business/coinkites-newest-bitcoin-device-can-serve-as-a-lightning-wallet-and-nostr-client)
- [SATSLINK Presentation - Nostrasia 2023 - YouTube](https://youtu.be/aN5HkQNXGGk?si=BkNhhJ25Ae_dG91p)