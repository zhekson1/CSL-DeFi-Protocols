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
Sustainability is key to the viability of an alternative financial system. Many DeFi protocols have an associated "Utility" token, which carries heavy implications for the sustainability of the protocol. Below are discussions of a few areas where such tokens' sustainability is questionable, at best.

#### 3.4.1 Real Value
What is the real value of a protocol's utility token?

Many DeFi protocols 


incentivize liquidity via "yield-farming", where inventory (or liquidation/collateralization) risk is compensated with a token that, optimistically, derives its value from profit-sharing with the protocol's market makers. This means the protocol must charge "batcher" fees in addition to regular Cardano transaction fees, which limits the viability of smaller-sized trades. More often than not, there is also an aggressive emission schedule and 

Setting aside securities laws and governance risk, at best we are left with a situation where users have no choice but to use protocols whose parameters are governed by collectively managed entities. This limits users' financial expressivity, which impedes market efficiency. To be clear, such "decentralized" market makers / banks / funds are not an issue in and of themselves, but they cannot be the only option in a free market.

#### Liquidity


#### Interest Rates & Loan Terms
Credit/debt markets are often the largest market in any economy, and are thus the most impactful. If as an industry we aspire to build better systems than those that came before, then credit/debt markets must be driven bottom-up by individuals, not top-down by few entities. This requires giving individuals maximum freedom in negotiating loan terms - interest rates, collateralization, risk assessment, e.t.c. Unfortunately, most lending/borrowing platforms do not offer this level of control, and instead opt for pooled liquidity, formulaic interest rates, and constrained loan terms. Due to the pooled nature of their liquidity and collective management, such platforms are more akin to a "collective bank", rather than a "decentralized protocol". 

Semantics aside, the point is that collectively-managed lending/borrowing protocols are not an issue in and of themselves, but they cannot be the only option in a robust free market. 

#### Governance
dApps that opt for token/plutocratic-based governance are subject to a pandora's box of concerns, especially when "enshrined" actors (oracles, batchers e.t.c.) are involved. 


To be clear, good governance is not impossible, but increases in difficulty proportional to the width of dApps' scope. For something like DeFi (the basis of an alternative financial system) the scope may be

For brevity's sake we won't dive too deep into this topic, though we offer the following considerations:

1. Who decides who gets to be a batcher or oracle, and how are they compensated?
2. If the answer to #1 is DAOs/dApp-tokens, what guardrails are in place to prevent batchers/oracles from using their profits to gradually become their own overseers?

## Supporting Development
Much like the Hydra Protocol family, this project belongs to the community, so the best way to support its development is with your time. Spread the word on social channels, contribute to Github discussions/PRs, and seek understanding. This is especially true for the developers out there - we need your attention and expertise!

In the near to mid term, this project will require an enormous grassroots lift. There is nothing to sell, no token/equity for would-be investors, and a lot of work to do. 

If you would like to support development of P2P-DeFi protocols, please consider delegating to our stake pool:

Ticker: P2PFI
Hex: bbebbbf81c42de5b84fbbc82c4feab78f8bd8bcf8b5af7c73a06664a
Bech32: pool1h04mh7qugt09hp8mhjpvfl4t0rutmz703dd003e6qeny5jf9c57



