---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/FinCEN Seeks to Impose Strict Surveillance Requirements onto Bitcoin Mixers.md","permalink":"/bit-devs/resources/notes/fin-cen-seeks-to-impose-strict-surveillance-requirements-onto-bitcoin-mixers/","title":"FinCEN Seeks to Impose Strict Surveillance Requirements onto Bitcoin Mixers","tags":["bitdevs","bitcoin","socratic-28","privacy","regulation","surveillance"],"noteIcon":"3","created":"2023-11-16T20:11:45.305-10:00","updated":"2023-11-19T22:49:11.043-10:00"}
---



# What happened?

According to a [press release](https://www.fincen.gov/news/news-releases/fincen-proposes-new-regulation-enhance-transparency-convertible-virtual-currency) on 10/19/23, the U.S. Department of the Treasury’s Financial Crimes Enforcement Network (FinCEN) announced a Notice of Proposed Rule Making (NPRM) that identifies international **Convertible Virtual Currency Mixing** (**CVC mixing**) as a class of transactions of primary money laundering concern.

> [!QUOTE] [FinCEN Seeks to Impose Strict Surveillance Requirements onto Broadly Defined Class of 'Bitcoin Mixers'](https://www.nobsbitcoin.com/fincen-wants-to-outlaw-certain-bitcoin-on-chain-transactions/)
> - “**Today’s action underscores Treasury’s commitment to combatting the exploitation of Convertible Virtual Currency (CVC) mixing by a broad range of illicit actors**, including state-affiliated cyber actors, cyber criminals, and terrorist groups,” said Deputy Secretary of the Treasury Wally Adeyemo. 
> - “This is FinCEN’s **first ever use of the Section 311 authority to target a class of transactions of primary money laundering concern**, and, just as with our efforts in the traditional financial system, Treasury will work to identify and root out the illicit use and abuse of the CVC ecosystem,” said FinCEN Director Andrea Gacki.
> 
> ---
> 
> - "**The lack of transparency surrounding international CVC mixing activity is an acute money laundering and national security risk**, and increasing transparency in connection with this activity is a key component to denying illicit actors access to the U.S. and global financial systems," was stated in the press release.
> - "The global nature of the problem is further demonstrated by the fact that no CVC mixers are currently registered with FinCEN. CVC mixers are required to register with FinCEN if they do business as money transmitters wholly or in substantial part within the United States."
> - "FinCEN recognizes that there are legitimate reasons why responsible actors might want to conduct financial transactions in a secure and private manner given the amount of information available on public blockchains. FinCEN also recognizes that, in addition to illicit purposes, CVC mixing may be used for legitimate purposes, such as privacy enhancement for those who live under repressive regimes or wish to conduct licit transactions anonymously. Still, CVC mixing presents an acute money laundering risk because it shields information from responsible third parties, such as financial institutions and law enforcement," was stated in the document.
> - "If the designation is made, the Treasury Department can impose restrictions on U.S. financial firms' dealings with the mixers, which "range from **requiring additional due diligence and special attention concerning particular account transactions among U.S. financial institutions to prohibiting the opening or maintenance of any correspondent or payable-through accounts**," reported CoinDesk.
> - "The FinCEN issued a notice of proposed rulemaking on Thursday, which **will be open to public comment for 90 days**." 

> [!QUOTE] [FinCEN Seeks to Impose Strict Surveillance Requirements onto Broadly Defined Class of 'Bitcoin Mixers'](https://www.nobsbitcoin.com/fincen-wants-to-outlaw-certain-bitcoin-on-chain-transactions/)
> - To really get a sense for the scope of things, the first thing to look at is the definitions of mixing provided in the proposal. Obviously, the act of mixing is obscuring the source of funds, but the specific technical definitions they give for what falls under the definition of mixing are incredibly broad when looked at together. Let’s go through them:
> - 
> 	1. **“Pooling or aggregating [funds] from multiple persons, wallets, addresses, or accounts”** This encompasses so many different activities other than a traditional custodial mixing service. Lightning channels? That is multiple persons pooling and aggregating funds together. Multisig wallets held by multiple people in general are doing the same thing. Just combining a recent withdrawal from Coinbase with coins you had from Kraken from the point of view of both exchanges is pooling funds from multiple addresses. According to the language of this proposal, something that just happens on a regular basis in the normal course of using Bitcoin, with no attempt whatsoever to obscure or render private anything about the activity, fits into the definition of mixing.
> 	2. **“Using programmatic or algorithmic code to coordinate, manage, or manipulate the structure of a transaction”** Again, that completely covers the Lightning Network. Coinjoins fall into this definition. In fact…you know what? This is so ridiculously and absurdly broad — it doesn’t even specify manipulating the structure of a transaction to attain obfuscation of the source of funds — that this literally encompasses any piece of Bitcoin software that handles making and signing transactions. 100% of the transactional activity on the Bitcoin [blockchain](https://bitcoinmagazine.com/guides/what-is-blockchain) out of sheer logical necessity fits this definition of mixing.
> 	3. **“Splitting [funds] for transmittal and transmitting the [funds] through a series of independent transactions”** This is also incredibly broad. How are legitimate independent transactions between the same parties to be distinguished from a single transaction split into many for obfuscation purposes? What about situations where that is a perfectly legitimate thing to do for no reason other than your personal privacy? What if I only have three different UTXOs that three separate people know about, and I don’t want to reveal to all three of them my payment history with the other two in order to make a payment requiring all three UTXOs? Does opening multiple independent Lightning channels with the same node constitute this?
> 	4. **“Creating and using single-use wallets, addresses, or accounts, and sending [funds] through such wallets, addresses, or accounts through a series of independent transactions”** So default behavior of the super majority of Bitcoin wallets — not reusing addresses — constitutes mixing? When I go to my exchange to withdraw with a unique address every time, are they required to consider that action “mixing” my coins? Do physical Bitcoin bearer instruments constitute “single-use wallets?”
> 	5. **“Exchanging between types of [cryptocurrencies] or other digitals assets”** So every single person trading NFTs, dumb tokens, utility tokens, and just outright shitcoins, whether on an exchange or on-chain through different mechanisms, is now mixing?
> 	6. **“Facilitating user-initiated delays in transactional activity”** Uhm.. timelocks in Lightning? Any type of 2FA rate limited multisig set up? Just the DCA scheduled withdrawal function at different on-ramps? All of this is now mixing?
> 	
> The definition of [cryptocurrency] mixer is “_any person, group, service, code, tool, or function that facilitates [cryptocurrency] mixing._” 
> 
> ---
> 
> Here is the information, within 30 days of being noticed by a business subject to the proposed rule, that would be required to be reported to the government, _for every single transaction_:
> 
> - The amount of cryptocurrency transferred, in native units and USD value at the time.
> - The cryptocurrency involved.
> - The mixer protocol/service/etc. used, if known.
> - Any addresses associated with the mixer used.
> - Any addresses associated with the user who mixed.
> - The TXID of the relevant transaction.
> - The date of transaction.
> - Any IP addresses associated with the transaction.
> - A “narrative” explaining context, the transaction itself, what the institution did, etc.
> 
> In terms of private information about the user involved in the transaction, here is the information proposed to be collected and directly reported to the government for every transaction:
> 
> - User’s full name.
> - User’s date of birth.
> - User’s full address.
> - User’s email address.
> - User’s IRS Taxpayer Identification Number (TIN) or foreign equivalent.

# More Resources

- [FinCEN Proposes Insane Special Measures](https://bitcoinmagazine.com/legal/fincen-proposes-insane-special-measures)
- [U.S. Treasury Seeks to Name Crypto Mixers as 'Money Laundering Concern'](https://www.coindesk.com/policy/2023/10/19/us-treasury-seeks-to-name-crypto-mixers-as-money-laundering-concern/)
- [Full FinCEN proposal](https://fincen.gov/sites/default/files/federal_register_notices/2023-10-19/FinCEN_311MixingNPRM_FINAL.pdf)

