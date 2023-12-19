# P2P-DeFi Manifesto: A Bedrock for DeFi

## Table of Contents
1. Abstract
2. Introduction
3. Existing Limitations of DeFi
4. Desired Properties
5. P2P-DeFi Paradigm
6. Future Directions
7. Conclusion & Support

## 1 - Abstract
Blockchain-based decentralized finance (DeFi) protocols have long sought to provide an alternative financial platform for the disenfranchised or unbanked peoples of the world. Although we've come a long way since Bitcoin's genesis, the industry has yet to deliver on such promises sustainably, at scale. A key reason for this is the lack of a comprehensive and unified framework for DeFi, even within a particular L1 blockchain. This is especially regrettable in context of Cardano, for three principal reasons:

1. The full potential of the eUTxO model cannot be realized without a set of (composable) standardized protocols upon which domain-specific scaling solutions are built. 
2. The viability of PoS is critically dependent on individuals' free and sovereign ability to express stake-based preferences (consensus, voting, e.t.c.)
3. An alternative financial system must provide high availability guarantees to compete with, and resist disruption by, incumbents of the status quo, whom may be incentivized to rally against it.

We argue why the three aforementioned points are critical to the success of DeFi on Cardano, and why current DeFi platforms *cannot* sufficiently address them. We then argue that the best way to address these points is through a separation of concerns via a *layered* architecture, wherein a **standardized** "smart contract layer" sits between the Cardano blockchain and DeFi service providers. Finally, we introduce *P2P-DeFi Protocols*, a family of open plutus contracts - our take on what such a contract-layer could look like. This document is intended to serve as a high level overview of our philosophical and architectural decision making for Cardano-based DeFi.

## 2 - Introduction & Motivation (A Brief Overview of Past, Present, and Future)
For all of recorded history, people have been striving towards a world that protects and upholds our most noble ideals. In what has been referred to by many as an "upwards spiral" of death and rebirth, from Roman Democracy to the American Constitution, we have long been in the business of engineering and reengineering society for the betterment of mankind. Every revolution up this spiral has been a result of new technologies that shine a light on the inadequacies and weaknesses of the status quo. The printing press, for example, enabled the spread of information at an unprecedented scale, which highlighted the failures of the existing system while *simultaneously* unifying the populace around a new class of systems, never before possible. This culminated in the Constitutional Republic, a first-of-its-kind, rules-based order, that elevated *written principles* to the highest authority, and drove forward the greatest economic and social advancements humanity had ever seen. 

The internet appears to be evolving over a similar trajectory. Much like the printing press, it has revolutionized the spread of information; enabling an unprecedented level of idealogical or cultural closeness between geographically disparate populations. With this closeness comes an understanding of common values, common enemies, and a shared desire for systems that protect the former from the latter. And as if on cue, the advent of distributed ledger technologies paved the way for a reimagining of what a rules-based world order could look like. One that elevates *code* to the highest authority, thereby insulating itself from the openness of human interpretation. For the first time ever, we, the "people of the internet", have the tools to build systems that sanctify our newfound commonalities and defend us from discretionary overreach. As the powers-that-be continue miring future generations with unpayable debts, we find ourselves at a precipice not so dissimilar to the one faced by the American colonists just a few short centuries ago. 

However, such transitions do not come without their challenges. 

The United States' early visionaries were fraught with disagreement over the rules of the nation, all while the greater British Empire wasn't taking kindly to its loss of power. Those pioneers paid a heavy price, in blood and in treasure, to sort out their internal differences whilst hanging on to the commonalities that distinguished them from the monarchy. It took multiple wars and many rewrites, but it was ultimately out of this tension - between maximizing freedom and minimizing chaos - that The Constitution was born. Likewise, the pioneers of the new order must strive for a set of rules that balance generalizability of scope with internal cohesion. <\WILL PHRASE BETTER - THIS IS THE KEY POINT> , all while the old guard resists its loss of power. 

----
WIP

Cardano's eUTxO model, with its asset-oriented programming paradigm, is uniquely well suited to achieve this balance. 

This is especially true in the realm of DeFi, where eUTxO eases development of robust, scalable, and capital efficient protocols. However, its full potential has yet to be realized, largely due to its novelty, and thus a lack of standards. 

----

## 3 - Existing DeFi Limitations
Current DeFi protocols on Cardano share some undesirable properties that all stem from a common set of assumptions and design philosophies. In this section we lay out these properties and discuss what makes them so undesirable. In the next section, we discuss how all of these properties are consequences of the same few design philosophies. 

Note:  Every protocol doesn't suffer from *all* of these properties, but enough of them do, so as to underrepresent the power of Cardano-based DeFi. 

### 3.1 - Fractured, Non-Composable Protocols
One of the greatest advantages of eUTxO is *atomic composability*, or the ability to "combine" different pieces of (related or unrelated) logic in the same transaction. This is great for throughput, but also enables the creation of complex, multi-step protocols. However, composability is not a given; it only works for contracts that are co-designed to work well with each other. Here lies one of the greatest challenges of eUTxO: how can we develop standards that **strike the right balance between being specific enough to enable robust composability, but also generalizable enough to minimally restrict the scope of adherent protocols?** Current DeFi platforms lack composability due to their dependence on various off-chain actors that are siloed in scope and "enshrined" (hardcoded in the smart contracts) within the protocol. 

<POOLED ARCHITECTURE TOO?>

### 3.2 - Low Availability Guarantees
An alternative financial system will likely be perceived as a threat by those in positions of high (legacy) power, who may employ a variety of regulatory or cyber-offensive tactics to disrupt it. Current DeFi protocols on Cardano rely on "enshrined" off-chain entities (i.e. oracles, batchers, e.t.c.), which greatly increases the protocols' attack surface. If DeFi is to ever meet the needs of a global economy, it must be highly resilient against such disruptions, and, at its *core*, it must be agnostic to governmental regulation. Security without availability is not enough to challenge the status quo; a well designed system must preserve both. 

### 3.3 - Threats to Ouroboros PoS
Many DeFi protocols sacrifice full delegation/voting control, especially in cases of "pooled" liquidity. Such protocols usually attempt to compensate via DAO-based delegations, but this is never as expressive individual stake-control, and opens the door to a variety of governance-based attacks. There are too many scenarios to list here, but suffice to say that **the more delegation control is decoupled from the ADA owners, the more distorted Ouroboros' game theory becomes.** It is difficult to predict the extent of this distortion, so minimizing it is of critical importance.

### 3.4 - Questionable Sustainability
Sustainability is key to the viability of an alternative financial system. Many DeFi protocols have an associated "utility" token, which carries heavy implications for the sustainability of the protocol. Below are discussions of a few areas where such tokens' sustainability is questionable, at best.

#### Capital Inefficiency
The popularity of Accounts based ledgers gave rise to the pooled AMM-style architectures that dominate the DeFi landscape today. However, AMM liquidity providers suffer from inventory risk (i.e. impermanent loss), due to the models' inefficient provisioning of liquidity over the cost curve. Even for AMMs with "concentrated liquidity", such models can never be as capital efficient as a true orderbook-style protocol. Unfortunately, many DeFi protocols on Cardano have adopted AMM-style designs, which is regrettable given how uniquely well suited the eUTxO model is for orderbooks. This is perhaps one of the main reasons why traditional financial professionals have yet to take DeFi seriously. Capital efficiency, and by extension orderbook-style protocols, are a prerequisite for robust DeFi markets.  

#### Constrained Lending/Borrowing
The above point (capital inefficiency) applies in a similar manner to lending/borrowing protocols. This is perhaps even more impactful, since credit/debt markets are usually the largest market(s) in a mature economy. Many lending/borrowing protocols on Cardano employ pooled liquidity architectures, which necessitates the constraining of loan terms, thereby limiting lenders' flexibility to issue loans as they best see fit. Furthermore, such protocols' parameters are usually governed via their "utility" tokens, which makes them more akin to a "collective bank", rather than a "decentralized protocol". If as an industry we aspire to build better systems than those that came before, then credit/debt markets must be driven bottom-up by individuals, not top-down by few entities. This requires giving individuals maximum freedom in negotiating loan terms (interest rates, collateralization, risk assessment, e.t.c.).

Semantics aside, the point is that **collectively-managed lending/borrowing protocols are not an issue in and of themselves, but they cannot be the *only* option in a robust economy.**

#### Yield Farming
Many DeFi protocols incentivize liquidity via "yield-farming", where inventory (or liquidation/collateralization) risk is compensated with a token that, optimistically, derives its value from profit-sharing with the protocol's market makers. This means the protocol must charge "batcher" fees *in addition* to regular Cardano transaction fees, which limits the viability of smaller-sized trades. Usually there is also an aggressive emission schedule (early on) that catalyzes initial liquidity, but inflates the value of the token over time. The issue is that **if inventory risk is being compensated by the utility token, then the liquidity (and thus the viability) of the protocol is heavily dependent on the value of the token**. This begs the question: how sustainable is the price of the utility token? The answer depends on the token's function - what does it actually do, beyond incentivizing liquidity? 

Again, one argument might be profit-sharing with a protocol's batchers / market makers. Although this may be necessary in the case of AMMs, it is not necessary in the case of orderbooks. And since AMMs themselves are inferior to orderbooks (as outlined in the previous section). As soon an orderbook-based protocol outcompetes the AMMs, the value of the latter's token drops, which drains liquidity, which further lowers the token's value. In other words, a death spiral. 

---
WIP

At best, we are left with a situation where users have no choice but to use protocols whose viability depends not on technical merit alone, but on the value of the corresponding token. 

This is a liquidity crisis waiting to happen. 

On these grounds it is worth questioning whether the term "protocol" is even applicable to such platforms, given how tightly coupled they often are with a specific team or product. 


Incentivizing liquidity does not count, as that would be a circular argument. Incentivizing batchers is also insufficient 

Setting aside securities laws and governance risk, if these are the only options, it is a liquidity crisis waiting to happen. 


users have no choice but to use protocols whose parameters are governed by collectively managed entities. This limits users' financial expressivity, which impedes market efficiency. To be clear, such "decentralized" market makers / banks / funds are not an issue in and of themselves, but they cannot be the only option in a free market.

----
#### Governance Risk - WIP
Protocols that opt for token/plutocratic-based governance are subject to a pandora's box of concerns, especially when "enshrined" actors (oracles, batchers e.t.c.) are involved. 


To be clear, good governance is not impossible, but increases in difficulty proportional to the width of a protocol's scope. For something like DeFi (the basis of an alternative financial system) the scope is so wide and the attack vector is so large that 

For brevity's sake we won't dive too deep into this topic, though we offer the following considerations:

1. Who decides who gets to be a batcher or oracle, and how are they compensated?
2. If the answer to #1 is DAOs/dApp-tokens, what guardrails are in place to prevent batchers/oracles from using their profits to gradually become their own overseers?

#### Regulatory Concerns - WIP
Most of DeFi are products, not protocols. 



dApp-issued "utility" tokens impose high regulatory burdens or uncertainties to users and developers, particularly with regard to securities laws. It is unclear 

We discuss why such properties are i

These protocols are our take on what the bedrock of a  robust and unified DeFi ecosystem should look like.




If we aspire to build a truly egalitarian economy, great care must be taken to ensure agnosticism and neutrality of the *core* protocols. 

In the words of Erik Voorhees, "If you are a DeFi Protocol, 'jurisdiction' is a meaningless concept."



We posit that to achieve a truly decentralized economy, it is imperative that the foundational elements of DeFi are architected in a manner that

Although the decentralization of asset *ownership* is a stride towards this goal, it alone is insufficient. 


with a level of decentralization that parallels the decentralization of asset ownership facilitated by blockchain technology


If the goal is to decentralize the economy, it is not enough to decentralize asset custody. 


We argue that such design patterns are not only superior to the current status quo, but are necessary for the success of eUTxO-based DeFi at large. 

collection of *elemental* protocols that can 

TradFi example: SWIFT


The (idealized) economy is one in which individuals are free to trade with one another. 

All other financial "tools" and "instruments" (securities, derivatives, trading platforms, )

Most of the DeFi landscape is filled with products, not protocols. 

Products target end users



### Essential Properties of a Free Economy
The most basic building block of any free economy is voluntary trade between *two* parties. Everything else (brokers, enforcement agencies, margin trading, credit cards, e.t.c.) is peripheral infrastructure built *atop* the basics. Critically, peer-to-peer trades do not *depend* on anything other than the two parties involved, though additional entities *can* be involved, where and when desired. 

If the two parties had full custody of their assets, but had *no option* to exchange without a middleman, this would not be a free economy, 


### Domain-Specific Scaling

### Towards Common DeFi Standards

### Money, Tokens, and Liquidity




## 4 - A Return to First Principles
Astute readers will have noticed a pattern in the previous section; each subsection's critique centers around one or both of the following two points:

1. Pooled liquidity architectures
2. Enshrined off-chain entities

We've arrived at the crux of the matter: **DeFi protocols, in their current form, are overly siloed in scope.** Be it the enshrinement of oracles/batchers, or the concentration of liquidity into pooled form, DeFi users are locked into the entire on-and-off-chain stack of their preferred protocol(s). 

---
WIP
### A Separation of Concerns (WIP)
There's a reason why the internet seems like magic for regular users (and even some developers!). From compilers, to TCP/IP, to HTTPS, to the app; a huge number of standards sit at multiple layers between the machine and the app; expediting development while preserving interoperability. A useful analogy is that of a tree: its roots are to machine code what its leaves are to apps; standards give structure and rigidity to its trunk. This *separation of concerns* lets innovators and entrepreneurs shine, unburdened by the nitty-gritty details relegated to the low-level engineers. 

Blockchains are a similar beast - as the technology matures, the number of possible applications (even within one vertical, like DeFi) explodes. Currently, every DeFi provider architects an entire stack, from smart contracts to the frontend, each of which is siloed and lacks interoperability with others. 




Layers upon layers of protocols abstract away all the low-level nonsense from higher-level developers and end-users alike. 

the distance between the on-chain backend and the end-user app widens, 

What if instead of 


### On Throughput & Scalability (WIP)
Cardano L1 is a "Nakamoto" style blockchain, meaning it formally prioritizes liveness over consistency. In other words, at any point in time all nodes are *not* expected to have the same view of the latest state, but are guaranteed to *eventually* converge on the same view. This imposes a fundamental "speed limit" on the network (even with future L1 scaling techniques like Input Endorsers). Consequently, although Cardano L1 *can* handle fully P2P DeFi, we cannot expect it to do so for billions of users simultaneously. So how do we get these protocols to scale? The answer lies in the kinds of "abstractions" and/or third-party services that can be built atop these protocols. To illustrate by analogy, lets examine the traditional financial system:

At the highest level, there are domestic and international money transfers standards (i.e. FedWire and SWIFT, respectively). Individuals can send money directly using these standards (albeit through a bank intermediary), but this is relatively slow and expensive. There are alternative services that lower fees by batching transactions (i.e. ACH), or accelerate the process by taking on counterparty risk (i.e. CashApp, Venmo, credit cards, e.t.c.). None of these services are *strictly* necessary for any one individual to transfer money, but they enable a level of scale that the higher level protocols could not achieve on their own. 

Things seem to be playing out in a similar fashion for the cryptocurrency industry. There is a broad recognition that decentralization implies limits to the speed at which individuals can transact directly. Some blockchains choose to forgo decentralization altogether, but leaving those aside, there is obviously a need for alternative scaling services built atop the core systems. Bitcoin's Lighting Network and Ethereum's ecosystem of L2s/rollups are prime exemplars. And so the motif is echoed once more: how can we architect systems than enable a wide scope of such services, without fracturing liquidity and preserving interoperability?

Cardano's eUTxO model is 

----
## 5 - A Family of Protocols


### 5.1 The Four Protocols
Currently there are four protocols in the P2P-DeFi family. They are linked and summarized here:

**[Cardano-Swaps](https://github.com/fallen-icarus/cardano-swaps)** - A simple, scalable, P2P-swap protocol, forming the "liquidity basin" for composition with the other three protocols. One-way swaps are akin to limit orders, while two-way swaps enable more advanced market making techniques.

**[Cardano-Loans](https://github.com/fallen-icarus/cardano-loans)** - A P2P-lending/borrowing protocol with trustlessly negotiable and repayable loans, an on-chain credit-history, fixed or compounding interest, and tradable credit (in the form of Bond NFTs). Lenders and borrowers negotiate loan terms via a "UTxO handshake". Borrowers can repay loans incrementally, and reclaim their collateral proportionally. Lenders can sell their credit on an aftermarket, just like traditional bonds.

**[Cardano-Options](https://github.com/fallen-icarus/cardano-options)** - A P2P protocol for writing and buying American-style *covered* options contracts. Users can write multiple offers of varying parameters against a single UTxO, one of which can then be accepted by a prospective buyer. Buyers can sell their options (in the form of an NFT) on an aftermarket, just like traditional options. 

**[Cardano-Secondary-Market](https://github.com/fallen-icarus/cardano-secondary-market)** - A P2P aftermarket protocol for buying/selling NFTs. Works especially well for Bond and Option NFTs of the previous two protocols, since purchasing *and* using the NFT(s) can be composed in a single transaction. 

### 5.2 Common Principles
The four protocols share common design principles, chiefly centered around permissionlessness, full custody, and composability. The following principles are prerequisites for any other protocols wishing to join the P2P-DeFi family, further discussed below.

#### 5.2.1 Open Source
All aspects of the core protocols (on-chain code, standards, documentation) will always be free and open source. Sophisticated users can of course develop closed-source peripheral software (i.e. arbitrage bots). There are no "dApp" Tokens associated with any of the core protocols. 

#### 5.2.2 Full Custody
Ouroboros' game theory, and thus Cardano's viability as a whole, is critically dependent on (ADA) stakeholders' free and unobstructed control over delegation and voting. All P2P-DeFi protocols preserve users' full delegation and voting rights. Users create and interact with each others' script addresses, and never have to send or lock assets in "shared" addresses. The only possible exception is a DAO-managed Plutus/multisig addresses. 

#### 5.2.3 Radically Permissionless / Zero Enshrinement
In other words, *zero enshrinement of any entities.* There are no oracles, batchers, or any other "privileged entities" within the core protocols. Prices/terms are set by individuals (via inline datums), and routing is achieved via specialized NFTs, dubbed "Beacon Tokens". 

#### 5.2.4 Endogenous Liquidity
P2P-DeFi protocols do not use oracles and do not artificially incentivize liquidity through "yield farming". Instead, **liquidity emerges from the (healthy) incentive to arbitrage**. Involved or professional users are incentivized to find the most profitable paths through relevant UTxOs, becoming de facto market makers in the process. "Prices" arise in an orderbook-like manner. where buyers and sellers meet across the whole UTxO set. 

#### 5.2.5 Availability/Unstoppability
Thanks to the previous principle of zero enshrinement, the core protocols inherit the same availability and permissionlessness guarantees as the underlying Cardano ledger. A variety of frontends from multiple hosts would ensure there is no single point of failure. Existing wallet providers are a great example of this, and are well-positioned to provide such services directly from their wallet interfaces.


#### Efficiency, Composability, and Interoperability
Broadly speaking, scaling eUTxO-based protocols involves two considerations at the execution layer:
1. Minimizing total on-chain resource utilization.
2. Maximizing utilization of individual transactions.

eUTxO already forces much of a transaction's "lifecycle" off-chain, but protocols must nonetheless be architected in a way that maximizes *useful "stuff" per transaction*. Achieving ideal throughput of Cardano L1 requires not only maxed out block sizes, but maxed out transaction sizes as well. In some cases, this may involve the inclusion of many *unrelated* inputs/outputs in the same transaction. 

Critically, this is not just a "nice to have" speedup, but in some cases composability is a necessity. One example is the interplay between Loans and Secondary-Market:

In Cardano-Loans, debt ownership is represented in the form of a "Bond" NFT that is associated with the "Active" UTxO of the corresponding borrower (the latter contains the loan state + collateral). The owner of the bond has the right to update the repayment address in the Active UTxO (the address to which the borrower must make their repayments). 

Now, suppose a Bond is traded on Secondary-Market. The new owner of the bond should immediately update the borrower's "Active" UTxO with a new repayment address. However, if purchasing the bond and updating the repayment is done in two separate transactions, there is a risk that the borrower makes a loan repayment to the old bond owner in the interim. However, this is not an issue if the new bond owner can update the repayment address in the same transaction that they purchase the bond. 


## Future Directions & Considerations
Although the four core protocols are largely feature-complete, there is still a ways to go before they are viable for wide adoption. 

### Alternative Implementations
All four protocols were originally prototyped in IOG's PlutusTx language. Aiken, a newer, more resource-efficient language is proving itself as a better alternative, enabling greater throughput and/or more features. Cardano-Swaps and Loans have already been rewritten in Aiken, with Options and Secondary-Market soon to follow. If upon wider adoption it becomes clear that more efficient throughput is required, even more optimized implementations may be warranted (i.e. using [Plutarch](https://github.com/plutonomicon/plutarch-plutus)).

### Off-Chain (Backend) Software
Additional off-chain software is necessary to use these protocols in any practical manner. Here is a brief list of workflows that would benefit from automation:

- Screening/selecting relevant UTxO (via Beacon-Token queries, context dependent)
- Determining profitable trades (for users and market makers)
- Building & submitting transactions (i.e. Lucid library or future iterations)

There will likely be competition between open source, community-driven projects and proprietary, high performance bots. Genius Yield's [Smart Order Router](https://github.com/geniusyield/smart-order-router) is a great example of the former. 

### Frontends & Integrations
User-friendly frontends are critical for adoption. Thanks to the fully open source and agnostic nature of the protocols, there can be multiple (competing) frontend providers, much like existing wallet providers. In fact, existing wallet providers have a head start here - they can already incorporate these protocols into their interfaces! Proprietary to open source, browser extensions to full fledged desktop apps, there's plenty of room for creative designs here. The biggest challenge will be designing a UI that balances elegance with high feature density.

### Minimal Governance
P2P-DeFi protocols have no "utility token", and thus no "enshrined" on-chain management; they are accessible by, and belong to, anyone using the Cardano blockchain. Their maintenance ultimately rests on the shoulders of the community, so the process of agreeing on canonical contracts must be sorted out. This can be done via a combination of on-chain standards (i.e. trustless script sharing via [Cardano-Reference-Scripts](https://github.com/fallen-icarus/cardano-reference-scripts)) and off-chain outreach (i.e. Twitter/Discord discussions).

---
### State Channel & zk Accelerators - WIP
It may be possible to achieve much higher throughput using clever combinations of state channel and/or zero-knowledge tech. 

The Hydra Protocol Family is promising in this regard, though it is too early in its development to know exactly how so. 

##### Optional, opt-in scaling techniques (batchers, hydra, zk, etc )

likely not enough in its current iteration 

Although its current iteration (The Head Protocol) is likely insufficient for these purposes, future developments hold promise 

Although this is beyond the scope of this document, such schemes are not outside the realm of possibility, especially in domain-specific contexts where trust assumptions can be relaxed. 

IOG's [Maravedi](https://iohk.io/en/research/library/papers/maravedi-a-secure-and-practical-protocol-to-trade-risk-for-instantaneous-finality/) scheme is one such example; a credit-card-like protocol where third parties provide fast finality by trading settlement risk for a fee. 

### Beyond DeFi (WIP)
- Discuss the protocols' potential to bridge the gap between DeFi and TradFi
- DeFi as the anchor (like FedWire), TradFi as regulated end user apps (like banking)

## Conclusion - WIP
To some, this document may come off as self-aggrandizing and dismissive of existing DeFi platforms. Nothing could be further from the truth. Our intention is for this document to serve as a rallying cry for the community - *especially* for existing DeFi providers. They are in the best position to begin incorporating these principles into their stacks, 


Cardano would not be where it is without them, and needs them to keep evolving and pushing forward. 

---

## Supporting Development
Much like the Hydra Protocol family, this project belongs to the community, so the best way to support its development is with your time. Spread the word on social channels, contribute to Github discussions/PRs, and seek understanding. This is especially true for the developers out there - we need your attention and expertise!

In the near to mid term, this project will require an enormous grassroots lift. There is nothing to sell, no token/equity for would-be investors, and a lot of work to do. 

If you would like to support development of P2P-DeFi protocols, please consider delegating to our stake pool:

Ticker: P2PFI
Hex: bbebbbf81c42de5b84fbbc82c4feab78f8bd8bcf8b5af7c73a06664a

Bech32: pool1h04mh7qugt09hp8mhjpvfl4t0rutmz703dd003e6qeny5jf9c57


