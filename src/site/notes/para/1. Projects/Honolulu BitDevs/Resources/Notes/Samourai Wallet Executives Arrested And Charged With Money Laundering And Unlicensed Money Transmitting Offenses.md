---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Samourai Wallet Executives Arrested And Charged With Money Laundering And Unlicensed Money Transmitting Offenses.md","permalink":"/bit-devs/resources/notes/samourai-wallet-executives-arrested-and-charged-with-money-laundering-and-unlicensed-money-transmitting-offenses/","title":"Samourai Wallet Executives Arrested And Charged With Money Laundering And Unlicensed Money Transmitting Offenses","tags":["bitdevs","bitcoin","socratic-33","regulation","privacy","coinjoin"],"noteIcon":"3","created":"2024-04-27T14:30:19.751-10:00","updated":"2024-04-28T01:35:10.499-10:00"}
---

![BitDevs-33-Samourai-Website-Seizure.png](/img/user/para/artifacts/BitDevs-33-Samourai-Website-Seizure.png)
# The State vs Samourai Wallet

> [!QUOTE] [Southern District of New York | Founders And CEO Of Cryptocurrency Mixing Service Arrested And Charged With Money Laundering And Unlicensed Money Transmitting Offenses | United States Department of Justice](https://www.justice.gov/usao-sdny/pr/founders-and-ceo-cryptocurrency-mixing-service-arrested-and-charged-money-laundering)
> **Keonne Rodriguez and William Lonergan Hill Are Charged with Operating Samourai Wallet, an Unlicensed Money Transmitting Business That Executed Over $2 Billion in Unlawful Transactions and Laundered Over $100 Million in Criminal Proceeds**
> 
> Damian Williams, the United States Attorney for the Southern District of New York; Thomas Fattorusso, the Special Agent in Charge of the New York Field Office of the Internal Revenue Service, Criminal Investigation (“IRS-CI”); and James Smith, the Assistant Director in Charge of the New York Field Office of the Federal Bureau of Investigation (“FBI”), announced today the unsealing of an Indictment charging KEONNE RODRIGUEZ, the Chief Executive Officer and a co-founder of Samourai Wallet (“Samourai”), and WILLIAM LONERGAN HILL, the Chief Technology Officer and also a co-founder of Samourai, with conspiracy to commit money laundering and conspiracy to operate an unlicensed money transmitting business.  **These charges arise from the defendants’ development, marketing, and operation of a cryptocurrency mixer that executed over $2 billion in unlawful transactions and facilitated more than $100 million in money laundering transactions from illegal dark web markets**, such as Silk Road and Hydra Market; a web-server intrusion; a spearphishing scheme; and schemes to defraud multiple decentralized finance protocols.  RODRIGUEZ was arrested this morning and is expected to be presented today or tomorrow before a U.S. Magistrate Judge in the Western District of Pennsylvania.  HILL was arrested this morning in Portugal based on the U.S. criminal charges.  The United States will seek HILL’s extradition to stand trial in the United States.  The case is assigned to U.S. District Judge Richard M. Berman.
> 
> In coordination with law enforcement authorities in Iceland, **Samourai’s web servers and domain (https://samourai.io/) were seized.  Additionally, a seizure warrant for Samourai’s mobile application was served on the Google Play Store.  As a result, the application will no longer be available to be downloaded from the Google Play Store in the United States.**
> 
> ---
> 
> **U.S. Attorney Damian Williams said: “As alleged, Keonne Rodriguez and William Lonergan Hill are responsible for developing, marketing, and operating Samourai, a cryptocurrency mixing service that executed over $2 billion in unlawful transactions and served as a haven for criminals to engage in large-scale money laundering.  Rodriguez and Hill allegedly knowingly facilitated the laundering of over $100 million of criminal proceeds from the Silk Road, Hydra Market, and a host of other computer hacking and fraud campaigns.  Together with our law enforcement partners, we will continue to relentlessly pursue and dismantle criminal organizations that use cryptocurrency to hide illicit conduct.”**

> [!QUOTE] [Samourai Did Nothing Wrong, Self Custodial Tools Are Not Money Transmitters](https://bitcoinmagazine.com/legal/samourai-did-nothing-wrong-self-custodial-tools-are-not-money-transmitters)
> At no point did Samourai custody user funds, have control over user funds, and ESPECIALLY did not execute any transactions on behalf of the user. It is a completely self-custodial wallet in every way.
> 
> ---
> 
> Writing and releasing source code is free speech. The entire absurd argument of "unlawfully combining unique features'' is essentially boiling down to "you spoke wrongspeak." That is not legal. They are literally implicitly stating that certain types of speech, or combinations of speech, are unlawful. That is insane.
> 
> ---
> 
> Samourai does not create addresses for users, their own wallets do. Full stop. Samourai's servers have no part in generating addresses for users. That is a factually incorrect statement.
> 
> ---
> 
> At no point in any step of the process of users constructing a transaction does Samourai gain any control over users' funds, any influence over where those funds are spent, or ability to prevent those users' funds from being spent wherever and whenever they want.
> 
> ---
> 
> Literally every single wallet in existence for Bitcoin is capable of creating a chain of self spends like this. Every single one of them. You just keep sending your own Bitcoin to a new address in the wallet over and over. This is money laundering? This is illegal?
> 
> ---
> 
> No one is sending any money to anyone else inside a Whirlpool coinjoin. Every user involved is sending their own money back to themselves. There is no transfer of funds from one user to another occurring.
> 
> ---
> 
> Trying to paint this as facilitating users transferring funds between each other is technically incorrect, it is false.
> 
> ---
> 
> Samourai is not a money transmission business... All they provide, in all of their services being listed in their indictment, is "delivery, communication, or network access services used by a money transmitter to support money transmission services;"
> 
> ---
> 
> FinCEN in 2019 specifically and in completely unambiguous language clarified that exactly the types of services Samourai offered are not money transmitters.

> [!QUOTE] [The State Of Things: Open Source Developers Arrested For Writing Code](https://bitcoinmagazine.com/legal/the-state-of-things-open-source-developers-arrested-for-writing-code)
> The United States Attorney for the Southern District of New York claims Samourai has executed over “$2 billion in unlawful transactions” while facilitating “more than $100 million in money laundering transactions.” This accusation contains a complete misunderstanding - not to mention a simply unconstitutional reframing - of what a Bitcoin transaction is and how it should be treated by our elected officials. Writing code is not a crime. Even when said code was written with the express purpose to enable the committing of a crime, the criminal action takes place when actualizing said intention, not at the onset of the authoring or even distribution of the code. Code is speech. Distributing code is an expression between parties of bytes reduces to bits, to ones and zeroes. Any precedent that establishes anything other than this is in direct violation of the first amendment, and further more, against the should-be-obvious natural code of freedom of expression.

> [!QUOTE] [@sethforprivacy on X](https://x.com/sethforprivacy/status/1783270473121382845)
> Everything actionable you need to know about what this indictment means for you as a (SW) or Whirlpool user 👇
> 
> **As a Samourai Wallet user (no Dojo)**
> 
> Unfortunately, the architecture of SW meant that your xpub (a master public key, allowing anyone holding it to derive all your past/present/future Bitcoin addresses) was at some point in time held by Samourai, and could now possible in the hands of the DOJ. 
> 
> Though it's a worst-case scenario, you should assume that your xpub was compromised, and thus all previous mixes you have done have been unwound and are now traceable. You should also assume that the gov can now derive all past/present/future addresses of yours and track movement of funds if so desired.
> 
> In addition, Samourai's coordinator and backend sync server was seized, and so SW will no longer sync, show received funds, or allow sending funds out. As such, you have to migrate funds to another wallet like [@SparrowWallet](https://twitter.com/SparrowWallet) following the docs here:
> [https://docs.samourai.io/wallet/restore-recovery#export-to-external-wallet](https://t.co/kb5xjTnInQ)
> 
> In addition, I would recommend migrating funds to a new seed phrase to prevent anyone holding the xpub from seeing all future received/spent funds. 
> 
> You should also disable automatic updates in the Play Store (if used) to ensure no malicious updates are pushed.
> 
> **As a Samourai Wallet user (using your own Dojo)**
> 
> Thankfully, you avoided having your xpub potentially compromised. The worst case scenario for you is that your previous mixes may not have the full anon set you expected if non-Dojo users xpubs were compromised.
> 
> You will still be able to sync/send/receive from your Samourai Wallet app, but should also migrate funds eventually as no further updates will come out for Samourai Wallet. If you want to migrate, use the docs below:
> [https://docs.samourai.io/wallet/restore-recovery#export-to-external-wallet](https://t.co/kb5xjTnInQ)
> 
> You should, however, disable automatic updates in the Play Store (if used) to ensure no malicious updates are pushed.
> 
> **As a Sparrow Wallet user**
> 
> Thankfully, you avoided having your xpub potentially compromised as well. The worst case scenario for you is that your previous mixes may not have the full anon set you expected if non-Dojo/Sparrow users xpubs were compromised.
> 
> There is no real need to rotate to a new wallet etc, and Sparrow is still an excellent option. Unfortunately you will no longer be able to mix in Sparrow as the Samourai coordinator was seized.

# FBI Issues PSA On Crypto MSBs

> [!QUOTE] [Alert on Cryptocurrency Money Services Businesses](https://www.ic3.gov/Media/Y2024/PSA240425)
> The FBI warns Americans against using cryptocurrency money transmitting services that are not registered as Money Services Businesses (MSB) according to United States federal law (31 U.S.C. § 5330; 31 CFR §§ 1010; 1022) and do not adhere to anti-money laundering requirements. A few simple steps can prevent unintentional use of non-compliant services. For example, avoid cryptocurrency money transmitting services that do not collect know your customer (KYC) information from customers when required.
> 
> ## MSB REGISTRATION
> 
> The FBI has recently conducted law enforcement operations against cryptocurrency services which were not licensed in accordance with federal law. People who use unlicensed cryptocurrency money transmitting services may encounter financial disruptions during law enforcement actions, especially if their cryptocurrency is intermingled with funds obtained through illegal means.
> 
> ## RISKY SERVICES
> 
> Cryptocurrency money transmitting services that purposely break the law or knowingly facilitate illegal transactions will be investigated by law enforcement. Using a service that does not comply with its legal obligations may put you at risk of losing access to funds after law enforcement operations target those businesses.
> 

# Ripple Effects

Likely as a result of the above, some bitcoin businesses have announced they are withdrawing from US markets (like [[para/1. Projects/Honolulu BitDevs/Resources/Notes/ACINQ launches Phoenixd and announces Phoenix Wallet withdrawal from US app stores\|Phoenix Wallet]] and [Wasabi Wallet](https://www.nobsbitcoin.com/zksnacks-is-now-blocking-u-s-residents-and-citizens/)).

Recent events seem to mark a noticeable shift in regulatory posturing and oversight toward bitcoin businesses and software teams.

# More Resources
- [Samourai Did Nothing Wrong, Self Custodial Tools Are Not Money Transmitters](https://bitcoinmagazine.com/legal/samourai-did-nothing-wrong-self-custodial-tools-are-not-money-transmitters)
- [FBI Issues Warning Against Using 'No-KYC Cryptocurrency Money Transmitting Services'](https://www.nobsbitcoin.com/fbi-warns-americans-against-using-no-kyc-services/)
- [FBI Warns Americans Against Using Non-KYC Crypto Money Transmitting Services](https://bitcoinmagazine.com/markets/fbi-warns-americans-against-using-non-kyc-crypto-money-transmitting-services)
- [@sethforprivacy thread on X](https://twitter.com/sethforprivacy/status/1784298343755055214)