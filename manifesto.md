# P2P-DeFi Manifesto: A Bedrock for DeFi

## Table of Contents
1. Abstract
2. Introduction: Principles of Money and Finance
3. Motivation: Existing Limitations of DeFi
4. Solution: A Family of DeFi Primitives
5. Conclusion & Support

## 1 - Abstract
Blockchain-based decentralized finance (DeFi) protocols have long sought to provide an alternative financial platform for the disenfranchised or unbanked peoples of the world. Although we've come a long way since Bitcoin's genesis, the industry has yet to deliver on such promises sustainably, at scale. A key reason for this is the lack of a comprehensive and unified framework for DeFi, even within a particular L1 blockchain. This is especially regrettable in the context of Cardano, for three principal reasons:

1. The full potential of the eUTxO model cannot be realized without a set of maximally expressive (and composable) protocols, upon which domain-specific scaling solutions are built. 
2. The viability of PoS is critically dependent on individuals' free and sovereign ability to express stake-based preferences (consensus, voting, e.t.c.)
3. An alternative financial system must provide high availability guarantees to compete with, and resist disruption by, incumbents of the status quo, who are incentivized to rally against it.

We argue why the three aforementioned points are critical to the success of DeFi, and why they cannot be addressed by current DeFi platforms that rely on pooled liquidity architectures and enshrined off-chain actors. We then argue that the best way to address these points is through a separation of concerns via a *layered* architecture, wherein a **standardized** "smart contract layer" sits between an expressive and high-availability blockchain (like Cardano), and DeFi service providers. Finally, we introduce *P2P-DeFi Protocols*, a family of open plutus contracts - our take on what such a contract-layer could look like. This document is intended to serve as a high level overview of our philosophical and architectural decision making for a robust DeFi economy.

## Introduction: Principles of Money & Finance
The advent of distributed ledger technologies (DLT) has heralded a reimagining of what a global rules-based order could look like. Economics plays a central role in any society, so the first applications of blockchain naturally center around money and finance. However, challenging the status quo requires not only a superior system, but also a means to thwart attempts at disruption by the incumbents.  If the goal is to reengineer the backend of global finance, it pays to take a step back and approach the task from a first principles perspective. Therefore, it is important to first outline an idealized economy, then describe how the current system falls short. Finally, we explore how DLTs can improve on the status quo.

### Economics as an Information Network
Economics is best viewed through the lens of information theory, where money/financial systems serve to propagate information about the reality of individuals' values. 

#### Axioms
The basic observation is that there is infinite demand in a world of scarce resources, so individuals are forced to prioritize those resources which are most valuable to them. What is more valuable to one may be less valuable to another, so trade occurs to settle this value-difference. Prices *arise* bottom-up from the collection of these value-differences throughout the population. Prices can therefore be thought of as pieces of information that convey the reality of individuals' collective value-differences. Individual value-differences are in a constant state of change, so the faster and more faithfully prices are updated to reflect them, the sooner and more appropriately resources are allocated. However, real resources are highly varied; some are intangible, some decay, and many are indivisible. All of these properties impede the speed and accuracy of price movement, resulting in slower and less accurate resource allocation. Money solves this problem by serving as a medium of exchange; smoothing out and accelerating price discovery. To do so, money must transmit price-information *more effectively* than the resources could on their own. The best (and therefore the most competitive) moneys are those that are *most* effective at transmitting price-information. 

Keeping in mind the role of money as defined above, we've arrived at the central question of this document: **what makes a money *effective* at transmitting price-information**? Many have answered this question by listing the *properties* of commodities that have historically been used as money (i.e. fungibility, portability, durability, e.t.c). However, this doesn't actually answer the question from first principles; it only hints at the answer by precedent. Since we're questioning the whole system, it pays to step back even further.

Again, the purpose of money (and money systems) is to propagate information that reflects underlying *reality* as faithfully and with as little friction as possible. Since this reality is nothing more than the collective value-differences of individuals, and since swift allocation of resources depends on individuals' ability to *always express* these differences, then **the most effective money system is one that enables the fastest propagation of individuals' value-differences *without* sacrificing accuracy and reliability.**  Money's advantage over raw commodities (as an value-difference propagator) is that it is faster or more scalable, but It is critical that speed never undermines, or takes precedence over, accuracy and reliability. When a money system fails to reliably and accurately propagate value-differences, resources are increasingly misallocated, eventually resulting in societal decay or breakdown, and a reversion to raw commodity-moneys. This happens naturally, as the market finds the best way to express itself. The point is that the speed of a money system is advantageous only insofar as it does not sacrifice the primary role of the system: accurate propagation of information. All of this is not purely theoretical; it is evidenced by the evolution of money throughout history.

#### Historical Precedent
From bartering, to commodity-moneys, to commodity-backed paper, to derivatives and modern financial institutions; technological innovation fuels this trend, pushing it towards the aforementioned ideal in a darwinian manner. For example, although paper notes are obviously a faster and more expressive method of information transfer than raw commodities, it wasn't until the rise of an entity or system that could enforce the reliability and faithfulness of said paper that commodities were outcompeted as the dominant money. The first such entity was the Dutch Empire in the 1600's; advancements in printing, shipbuilding, and mercantilism afforded them enough power/influence that they could enforce their notes *reliably* enough, such that the notes became more effective at propagating price-information than commodities. Although other moneys existed, the Dutch monetary system (the Guilder) became *the* dominant monetary system wherever the empire held significant economic and/or military influence. This is a key point; the success of the Guilder depended *not* on the technicalities of the money alone (quality paper, quality ships, e.t.c.), but on the Empire's overall ability to administer a reliable and expressive (and thus competitive) price-information *network*. In other words, **the Dutch paper-based monetary system was only ever as effective as the Empire's effectiveness as network administrators, where the effectiveness of the network is defined by how reliable it is at propagating individuals' value-differences.** It just so happens that, at the time, the effectiveness of being such an administrator was heavily intertwined with economic/military might; there simply was no better way to enforce a money-network's reliability. This is further attested by the rise of the British Empire, several decades later. Although the British Empire operated its money system (the Sterling) with methods and technologies very similar to those of the Dutch Guilder (paper notes backed by real resources), it was nevertheless supplanted as the dominant money system. This had nothing to do with the physical money itself, and everything to do with the robustness of the socioeconomic network that a money gave its users access to. This also explains why moneys were always the last "asset" to rise in a rising empire; a money's success depends on the quality of its network, which is defined by how reliable it is at providing its users access to favorable socioeconomic conditions. 

And so we have the long arc of an Empire's money system, or what Ray Dalio calls the "Long Term Debt Cycle". The main idea is that all fiat moneys eventually decay due to weakening socioeconomics, which undermines the Empire's power to reliably administer the network. For small economies this usually leads to outright default, whereas in large economies (whose money is used as a global reserve) this usually leads to discretionary abuse (Triffin's Dilemma). Looking back, it is no surprise why the Sterling supplanted the Guilder, why the Dollar eventually supplanted the Sterling, and why the Dollar is now losing its position as the global reserve.

#### Issues with Current World Order
Ever since the end of WW2, and especially after the collapse of the Soviet Union, the United States has been the dominant economic and military power of the world. Consequently, the Dollar system has been the most reliable avenue for individuals to express their value-differences. However, the dollar system is not without its problems:

- New Dollars are created and distributed by few individuals on a discretionary basis, resulting in an inflation burden that is unfairly spread across the population (also known as the Hume-Cantillon effect). Essentially, the first to receive new money enjoy the most benefit and suffer the least consequences, whereas the last to receive new money enjoy the least benefit and suffer the most consequences. Usually, the order of first to last looks something like: politicians, then bankers, then owners of businesses and financial assets, and finally workers. 

- Access to the Dollar system is mediated by the same few individuals, also on a discretionary basis. Individuals', corporations', and whole countries' access to the Dollar can be quickly restricted, which can be catastrophic for them. For example, the entire country of Iran (and all its people) are cut off from the Dollar, and are thus cut off from much of humanity's goods and services.

As is common for many empires throughout history, the United States' dominance has led to a stagnation of the drivers that made it great in the first place. This is evidenced by the the loss of manufacturing capabilities, exponentially increasing debt levels, and an overextension of military power throughout the globe. Since the United States is quickly losing its credibility to faithfully administer the Dollar, and since the effectiveness of a money system ultimately depends on the robustness of its administrator(s), there is an ever-increasing demand for an alternative to the Dollar. 

### A Return to the Fundamentals
In seeking an alternative to the (declining) status quo, we must be careful and precise in defining a system that is more effective (and can thus outcompete) the status quo. 

#### System-agnostic Principles
The most basic building block of any free economy is *voluntary and expressive* trade between *two* parties. All other parties (brokers, enforcement agencies, margin trading, credit cards, e.t.c.) is peripheral infrastructure built *atop* the basics. Critically, peer-to-peer trades do not *depend* on the will of anyone besides that of the two parties involved, though additional parties *can* be involved, where and when desired. If the two parties had full custody of their assets, but had *no option* to exchange without a middleman, this would not be a free economy. 

From these basic axioms we can derive some essential properties that a free economy must have. We've established that money systems are really just price-information networks, where prices are the value-differences of individuals. To be an effective money, its network must continuously transmit these value-differences as reliably and as accurately as possible. 

#### The Rise of Blockchain
Distributed ledger technologies have, for the first time ever, illuminated a path towards systems that handle value-information far more reliably and accurately than central administrators ever could. Much like any new and promising technology, a great deal of initial trial and error must occur to iron out the details for sustainable growth/adoption. The industry is indeed still in such early phases, having thus produced a myriad of protocols attempting to "crack the code" of global finance. It is worth exploring where these protocols fall short, and how they can be improved upon. 


## 3. Motivation: Limitations of DeFi
Although DeFi has great potential to improve the global economy, the blockchain industry as a whole is in its early stages and is undergoing rapid development. "There are no solutions, only trade-offs" is a quote by Thomas Sowell that could not be more applicable to the current state of affairs in the industry. It applies to L1 blockchains *and* to competing DeFi protocols within a particular blockchain network. It is therefore imperative to examine these tradeoffs as they relate to the principles outlined in the previous sections. By conducting this examination in order from L1 -> DeFi protocol, we can quickly narrow down on a set of design patterns that best instantiate these principles.

### Limitations of Existing L1s
Recall from the previous section that an effective money system is nothing more than an effective information system, where "effectiveness" is defined by the system's ability to *reliably facilitate the expression of individual value-differences*. Since no DeFi protocol can be more reliable nor more expressive than the underlying blockchain, it is natural to ask the following two questions when evaluating a candidate network for DeFi:

1. How *reliable* is the underlying blockchain?
2. How *expressive* is the underlying blockchain?

These are foundational questions that dictate the trajectory of any protocol built atop a blockchain, and so are worth exploring further.

#### Reliability
Reliability is a key aspect of an effectiveness of a money system. It can be thought of as the properties that guarantee users continuous or *uninterruptible* read and write access to the system (or in this case, to the blockchain). Recall that speed/throughput is a competitive advantage for a money system, as long as it does not sacrifice reliability. Unfortunately, many L1 blockchains have chosen to go down precisely this road. 

Solana is one such example; best in class speed for a single-shard blockchain, at the cost of a formal consensus argument. 

Some L1 blockchains 

Solana (monolithic BFT speed):
- no guarantees of consensus
- centralized tokenomics -> centralized PoS

Radix (sharding with no backup)
- no availability guarantees for individual shards

One of the key trade-offs in the blockchain industry is that of resiliency vs speed. 


Many L1 networks have chosen to sacrifice 


In the context of blockchains, this naturally leads to two 

#### Expressivity = Flexibility + Composability - WIP
Accounts cannot maintain expressivity 

honesty: between accounts vs utxo latter is better


### Limitations of Cardano-based DeFi
Current DeFi protocols on Cardano share some undesirable properties that all stem from a common set of assumptions and design philosophies. In this section we lay out these properties and discuss what makes them so undesirable. Next, we discuss how all of these properties are consequences of the same few design philosophies. 

Note:  Every protocol doesn't suffer from *all* of these properties, but enough of them do, so as to underrepresent the power of Cardano-based DeFi. 

#### 3.1 - Fractured, Non-Composable Protocols
One of the greatest advantages of eUTxO is *atomic composability*, or the ability to "combine" different pieces of (related or unrelated) logic in the same transaction. This is great for throughput, but also enables the creation of complex, multi-step protocols. However, composability is not a given; it only works for contracts that are co-designed to work well with each other. Here lies one of the greatest challenges of eUTxO: how can we develop standards that **strike the right balance between being specific enough to enable robust composability, but also generalizable enough to minimally restrict the scope of adherent protocols?** Current DeFi platforms lack composability due to their dependence on various off-chain actors (i.e. batchers, oracles, sequencers, e.t.c.) that are siloed in scope and "enshrined" (hardcoded in the smart contracts) within the protocol. Such actors can be permissioned, permissionless, or anything in between, but their "enshrinement" within the protocol makes it challenging to preserve composability in a trustless manner. 

< CONCRETE EXAMPLE >

#### 3.3 - Low Availability Guarantees
An alternative financial system will likely be perceived as a threat by those in positions of high (legacy) power, who may employ a variety of regulatory or cyber-offensive tactics to disrupt it. Current DeFi protocols on Cardano rely on "enshrined" off-chain entities (i.e. oracles, batchers, e.t.c.), which greatly increases the protocols' attack surface. This is obvious in the case of permissioned actors, but is often the case for permissionless actors as well, as the number & diversity of such actors is usually quite low relative to the underlying blockchain. Since these enshrined actors are currently highly specific/siloed to each protocol with no or low standards in between, each "subnet" is divided and thus easier to take down. 

If DeFi is to ever meet the needs of a global economy, it must be highly resilient against such disruptions, and, at its *core*, it must be agnostic to governmental regulation. Security without availability is not enough to challenge the status quo; a well designed system must preserve both. This aligns with the original cypherpunk ethos of the blockchain industry, and is well exemplified in [this article](https://jacob.energy/hyperstructures.html).

#### 3.4 - Threats to Ouroboros PoS
Many DeFi protocols sacrifice full delegation/voting control, especially in cases of "pooled" liquidity. Such protocols usually attempt to compensate via DAO-based delegations, but this is never as expressive individual stake-control, and opens the door to a variety of governance-based attacks. There are too many scenarios to list here, but suffice to say that **the more delegation control is decoupled from the ADA owners, the more distorted Ouroboros' game theory becomes.** It is difficult to predict the extent of this distortion, so minimizing it is of critical importance.

#### 3.5 Low Expressivity
The viability of *any* financial system depends on its constituency's freedom to express individual sentiment. This is a foundational principle of free market economies; any deviation from individuals' ability to express themselves (financially) distorts the information system that is money and prices. The extent of this distortion is nonlinear and difficult to predict, so minimizing it is of critical importance. To give a more concrete example, modern economies depend on sophisticated risk-management strategies employed by professional financiers. Such entities play a key role in the viability and efficiency of the market at large. Since risk and value are both subjective, there must be tools that are expressive enough to propagate individual risk-value sentiments. Unfortunately, many DeFi protocols employ pooled liquidity architectures, which limits individuals' expressivity. This has broad implications for the efficiency and sustainability of the protocol, further discussed in the next two subsections.

To be clear, concentrating liquidity into collectively managed pools is not an issue in and of itself - in many cases such entities serve to accelerate price discovery and market efficiency (i.e. hedge funds, banks, .e.t.c.). The issue is when such entities are the *foundation* of the DeFi economy, in which case their outsized influence on the market undermines efficient price discovery. Even if there are many such entities competing with each other, they can never be as efficient as a market composed of individuals' sentiments, as no algorithm or collection of algorithms, no matter how sophisticated, can capture true market sentiment as effectively as that which is expressed by individuals. This is especially true in the context of intangibles, outliers, or macroeconomic risks that are not reflected by the broader market. If DeFi is to ever challenge or compete with the legacy financial system, it must allow individuals to freely express themselves.

##### 3.5.1 Capital Inefficiency
The popularity of Accounts based ledgers gave rise to the pooled AMM-style architectures that dominate the DeFi landscape today. However, AMM liquidity providers suffer from inventory risk (i.e. impermanent loss), due to the models' inefficient provisioning of liquidity over the cost curve. Even for AMMs with "concentrated liquidity", such models can never be as capital efficient as a true orderbook-style protocol. Unfortunately, many DeFi protocols on Cardano have adopted AMM-style designs, which is regrettable given how uniquely well the eUTxO model maps onto orderbook architectures. In fact, expressivity (granular risk-value differences) is much easier to capture in the eUTxO model, since each UTxO's execution conditions can be tuned to individuals' preferences. This is perhaps one of the main reasons why traditional financial professionals have yet to take DeFi seriously: they cannot employ adequate risk management techniques without a true orderbook, wherein exact prices can be specified. Capital efficiency, and thus *expressive* eUTxO-based orderbook-style protocols, are a prerequisite for robust DeFi markets.  

##### 3.5.2 Constrained Lending/Borrowing
The above point (capital inefficiency) applies in a similar manner to lending/borrowing protocols. This is perhaps even more impactful, since credit/debt markets are usually the largest market(s) in a mature economy. Many lending/borrowing protocols on Cardano employ pooled liquidity architectures, which necessitates the constraining of loan terms, thereby limiting lenders' flexibility to issue loans as they best see fit. Furthermore, such protocols' parameters are usually governed via their "utility" tokens, which makes them more akin to a "collective bank", rather than a "decentralized protocol". Collective financial decision making, whether algorithm-based, DAO-based, or a combination of both is antithetical to the vision DeFi, especially if there are no other options. In many cases this also means assets must go through some kind of centralized or DAO-based "approval" process before they can be lent/borrowed. Suppose a new startup company or "startup nation" wants to issue new debt; current approval processes means joining the economy is essentially permissioned, which stifles competition.

All of these restrictions inhibit the efficient price discovery and proper risk management of lending/borrowing protocols, which limits DeFi's ability to challenge the status quo. If as an industry we aspire to build better systems than those that came before, then credit/debt markets must be driven bottom-up by individuals, not top-down by few entities. This requires giving individuals maximum freedom in negotiating loan terms: asset(s), interest rates, collateralization, risk assessment, e.t.c., must all be left to end-users. Semantics aside, the point is that **collectively-managed lending/borrowing protocols are not an issue in and of themselves, but they cannot be the *foundation* of a robust economy.**

#### 3.5 - Questionable Sustainability
Sustainability is key to the viability of an alternative financial system. Many DeFi protocols have an associated "utility" token, which carries heavy implications for the sustainability of the protocol. Below are discussions of a few areas where such tokens' sustainability is questionable, at best.

##### Yield Farming
Many DeFi protocols incentivize liquidity via "yield-farming", where inventory (or liquidation/collateralization) risk is compensated with a protocol-specific "utility" token. The issue is that **if inventory risk is being compensated by the utility token, then the liquidity (and thus the viability) of the protocol is heavily dependent on the value of the token**. This begs the question: how sustainable is the price of the utility token? The answer depends on the token's function - what does it actually do, beyond incentivizing liquidity? 

Firstly, initial liquidity is often catalyzed by an aggressive emission schedule (rapidly inflates supply & decreases its value), which is obviously unsustainable. This is justified as a "bootstrapping" phase, followed by some notion of a path towards sustainable value generation - usually in the form of profit sharing with the protocol's market makers. This means the protocol itself must somehow turn a profit that backs its own token, which is problematic for a number of reasons:

1. Some protocols collect "batcher" fees that are split between batcher providers and utility token holders. However, such fees are charged *on top* of regular Cardano transaction fees (in some cases these fees are up to 10x higher than regular Cardano Tx fees), which limits the viability of smaller-sized trades. Furthermore, it means such protocols suffer from all the drawbacks of relying on "enshrined" off-chain entities, as mentioned in previous sections. This ultimately makes them less competitive against protocols that don't charge additional fees.
2. Some protocols create value for their tokens by sharing profits generated by liquidity providers / market makers. However, collective liquidity provisioning is only necessary for pooled DeFi architectures, which are inferior to orderbooks for the reasons mentioned in previous sections. And since orderbooks *don't* require collective liquidity and will outcompete AMMs, profit sharing cannot sustainably back the utility token. 

Hence, we are left with a situation where users have no choice but to use protocols whose viability depends *not* on technical merit alone, but on the value of the corresponding token. And since the parameters of such protocols (especially those to do with liquidity) are collectively managed, users' financial expressivity is limited, which impedes market efficiency. As soon as a more efficient protocol comes along, the value of the utility tokens plummets, causing a liquidity crisis. On these grounds it is worth questioning whether the term "protocol" is even applicable to such platforms, given how tightly coupled they often are with a specific team or product. To be clear, such "collective" market makers / banks / funds are not an issue in and of themselves, but they cannot be the *only* option in a robust DeFi economy.

##### Governance Risk
Protocols that opt for token/plutocratic-based governance are subject to a pandora's box of concerns, especially when "enshrined" actors (oracles, batchers e.t.c.) are involved. Present difficulties/debates over Cardano's governance are a testament to how hard this problem is. Governance is a complex topic beyond the scope of this document, but suffice to say that current governance mechanisms are not enforced trustlessly. Protocol-voting is actually more of a vote, whose results must be implemented and enforced by the dApp administrators (via special "governance" keys that only they control). Furthermore, issuance of said governance tokens is a delicate process that usually isn't equitable nor permissionless, presenting significant regulatory concerns.  

To be clear, good governance is not impossible, but increases in difficulty proportional to the width of a protocol's scope. The scope of something like DeFi (the basis of an alternative financial system) is so wide and the attack vector is so large that governance should be minimized, wherever possible. Hence, there is a need for agreed upon standards in the DeFi space, at least within the L1 context. This way, users have full control over which contracts to trust/use, eliminating the need for on-chain governance altogether.

##### Regulatory Concerns
Protocol-specific "utility" tokens impose high regulatory burdens or uncertainties to users and developers, particularly with regard to securities laws. As mentioned in the previous section, the value of the token is usually tightly coupled with a single team or product, which can easily illicit action from regulators. In fact, this may be a good litmus test for distinguishing "products" from "protocols". The former's dependence on one or few entities is already problematic from the perspective of resiliency/availability, let alone regulatory scrutiny. If we aspire to build a truly egalitarian economy, great care must be taken to ensure agnosticism and neutrality of the *core* protocols. In the words of Erik Voorhees, "If you are actually a DeFi platform, 'jurisdiction' is a meaningless concept."


### A Return to First Principles
Astute readers will have noticed a pattern in the previous section; each subsection's critique centers around one or both of the following two points:

1. Pooled liquidity architectures
2. Enshrined off-chain entities

We've arrived at the crux of the matter: **DeFi protocols, in their current form, are overly siloed in scope.** Be it the enshrinement of oracles/batchers, or the concentration of liquidity into pooled form, DeFi users are locked into the limited on-and-off-chain stack of their preferred protocol(s), which limits the robustness of the DeFi as a whole. 

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



Existing DeFi providers have a headstart in this department, and are already in a great position to evolve into such services.

----
## 5. Solution: A Family of DeFi Primitives
We advocate for an industry-wide move towards standardized DeFi contracts, used by most or all DeFi service providers. The intention is not to standardize *all* parts of a product's on-chain code, but enough of it so as to avoid the pitfalls of Section 3, without sacrificing the flexibility of products, as mentioned in section 4. To this end, we introduce a family of fully composable P2P protocols that possess all functionalities of a full DeFi stack.

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

### State Channel & zk Accelerators - WIP
It may be possible to achieve much higher throughput using clever combinations of state channel and/or zero-knowledge tech. The Hydra Protocol Family is promising in this regard, though it is too early in development to have a clear picture of *exactly* how. 
Although this is a nuanced topic (beyond the scope of this document), there are many promising avenues to explore here.
 
Firstly, there may be a large number of domain-specific contexts where trust assumptions can be relaxed (especially with regards to custodial vs non custodial execution). One such example is IOG's [Maravedi](https://iohk.io/en/research/library/papers/maravedi-a-secure-and-practical-protocol-to-trade-risk-for-instantaneous-finality/) scheme; a credit-card-like protocol where third parties provide fast finality by trading settlement risk for a fee. Other schemes involving multiple competing (potentially [interconnected](https://iohk.io/en/research/library/papers/interhead-hydra-two-heads-are-better-than-one/)) Head networks may prove useful as well. 

More exotic schemes with heavy use of zero knowledge techniques may allow non-custodial execution in an asynchronous setting. This was hinted at via the term "Hydra Tail", though this is entering speculative territory.  

## Conclusion
To some, this document may come off as self-aggrandizing and dismissive of existing DeFi platforms. Nothing could be further from the truth. Our intention is for this document to serve as a rallying cry for the community - *especially* for existing DeFi providers. They already have a headstart in terms of brand recognition and liquidity, and will benefit themselves *and* their users by incorporating these principles into their stacks. Cardano would not be where it is without them, and needs them to keep evolving and pushing forward. As mentioned many times throughout this document, existing DeFi platforms with utility tokens, enshrined actors, and pooled architectures are not issues in and of themselves, but they cannot be the *only* option in a robust economy. 

## Supporting Development
Much like the Hydra Protocol family, this project belongs to the community, so the best way to support its development is with your time. Spread the word on social channels, contribute to Github discussions/PRs, and seek understanding. The ideas here are just as much philosophical as they are technical, so lots of community discussions is the best way to capture the attention of developers. The more attention these ideas receive from developers, the faster they will be iterated upon and incorporated into the DeFi ecosystem.

That being said, there is a real need for funding ongoing development of the core protocols. There is nothing to sell, no token/equity for would-be investors, and a lot of work to do. Fortunately, delegated PoS networks like Cardano present a great opportunity for alternative funding: stake pools.

Stake pools are one of the best mechanisms for funding development of DeFi "primitives" that are of the style presented in this document, for the following reasons:

- Delegations are sticky; once a delegation is made, it sticks around until the delegator chooses to opt out. This equates to a more reliable/consistent income stream, as opposed to the sporadic nature of donations. 
- Projects that opt for token-based fundraising (i.e. public sales, ISPOs, e.t.c.) are subject to regulatory scrutiny, especially if their project is successful enough that it poses a threat to governments or the financial elite. On the other hand, the nature of the SPO-delegator relationship in Cardano PoS lends itself to less regulatory scrutiny, since there is never anything that could be construed as an investment contract, nor is there every any principle at risk. 

If you would like to support development of P2P-DeFi protocols, please consider delegating to our stake pool:

Ticker: P2PFI
minFee: 170
variableFee: 2%

Hex: bbebbbf81c42de5b84fbbc82c4feab78f8bd8bcf8b5af7c73a06664a

Bech32: pool1h04mh7qugt09hp8mhjpvfl4t0rutmz703dd003e6qeny5jf9c57


