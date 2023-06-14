## Introduction
CSL-DeFi primitives seek to establish the basic building blocks of p2p finance on Cardano. It is a family of open "smart contract" protocols that share common design patterns, chiefly centered around radical permissionlessness, simplicity, and interoperability. By taking full advantage of the protocol architectures enabled by the eUTxO paradigm, CSL-DeFi primitives can achieve an unprecedented level of scale, with both high security *and* high availability guarantees. The primitives work synergistically with one another, enabling the formation of a truly independent and complex economy on Cardano. 


## Motivation
Distributed ledger technologies have long sought to provide an alternative financial platform for the disenfranchised or unbanked peoples of the world. Throughout the years, much progress has been made. However, the current DeFi paradigm is still heavily reliant on the legacy financial system for critical pieces of infrastructure, namely fiat on/off ramps, pricing information, and identity management. To be a viable alternative, DeFi must further decouple from these bottlenecks, and establish its own *endogenous* infrastructure. 


### Current DeFi Drawbacks
Current DeFi dApps have a number of drawbacks:

1. Most DeFi dApps rely on a *permissioned* set of batchers/arbitragers/aggregators for liquidity. Although a well designed dApp does not place user funds at risk of being outright stolen, the dApp cannot guarantee high availability, since permissioned actors are at a high risk of denial-of-service (DOS) attacks. This is doubly true for dApps that rely on oracles for external info feeds, where DOS *and* oracle collusion/corruption are major attack vectors. Furthermore, these batchers take an unnecessarily large cut of transaction fees. As you'll see, current DeFi dApps are an order of magnitude more expensive than what CSL-DeFi Primitives offer simply due to the middlemen that run these dApps. Lastly, since dApps currenty **require** users to go through batchers, composability with other dApps only exists if the batchers are uniquely set up to support it. This is out of the control of the users.

2. Governance of these actors is a complex and nuanced topic: who decides who gets to be a batcher or oracle provider? How are they compensated? If the answers to these questions are DAOs and dApp tokens, respectively, doesn't this mean that over time, as the permissioned actors profit, they gain increasing control of the DAO, until they become their own overseers? Governance quickly gets messy, and may result in a variety of regulatory issues down the line. It should be minimized wherever possible. 

3. Many DeFi dApps sacrifice full delegation control, especially in the case of liquidity pools. The more delegation control is decoupled from the ADA owners, the more distorted Ouroboros' game theory becomes. It is difficult to predict the extent of this distortion, so minimizing it is of paramount importance.

4. In order to incentivize liquidity, DeFi dApps generally resort to yield farming which is economically unstable. These protocols are effectively minting an asset that has zero value outside of paying fees on the dApp. This is arguably worse than a government printing money to pay its bills since at least a government's currency is widely used throughout an economy. Therefore, while the insider token (equity) is being distributed, its value can only fall as the circulating supply begins to dwarf the demand.


### The Blockchain Trilemma, Revisited
If mature DeFi protocols really do offer an alternative to the legacy financial system, they will likely be perceived as a threat by those in positions of power. Therefore, DeFi protocols must not only be scalable, but must also be resilient to high-resource attacks by state-level actors. 

These considerations are glaringly similar to the blockchain trilemma; **security, availability, and throughput *must all be uncompromisable priorities*** of an alternative financial system. Taking inspiration from Cardano, the trilemma is addressed through the following principles:

1. **Radical Permissionlessness** - there are no permissioned or specially provisioned actors. All protocol participants, including large market-makers/batchers, are treated equally and permissionlessly.

2. **Minimum Viable Expressiveness** - protocols are simple, predictable, and are never subject to external off-chain variables, such as fiat-denominated prices. They are expressive enough to form a full fledged economy, without having to rely on a preexisting one. 

3. **Proportional P2P Scaling** - total throughput/liquidity scales with the number of users. The more users there are, the deeper the liquidity, the higher the throughput. Much like Bittorrent, efficient p2p protocols are ones that scale *with* the number of users.


CSL-DeFi primitives are similar to Hydra, in that they are ledger-wide, Plutus-enabled extensions of the CSL, albeit with a focus on finance.


## A Fully P2P DeFi Paradigm
Here are the design patterns shared by all CSL-DeFi protocols, and a discussion of their advantages over the status quo.

### Common Design Patterns 

- **Unique User Addresses** - CSL-DeFi users deploy and interact with each others' script addresses. Each user creates at least one unique address, composed of *identical* script-mediated payment credentials (per primitve), and *unique* user-mediated staking credentials. Owner-related actions (i.e. simple spending) are "overloaded" to the user's staking credential, so funds are never locked or stolen. Users always maintain full delegation authority over their addresses.

- **Beacon Tokens** - All CSL-DeFi primitives coordinate their spending policies with the minting policies of specialized NFTs, dubbed "Beacon Tokens". The tokens' functions include: mediating protocol logic, tagging TXs, UTxOs, and/or addresses for querying, and categorizing on-chain events. Beacon Tokens are highly generalizable, and can be very expressive when used in combination with each other. They are used extensively in all CSL-DeFi protocols. 

- **Permissionless Indexing** - All CSL-DeFi primitives have at least one Beacon Token that shares identical queryable properties with all other Beacon Tokens of the same protocol. As a result, users can locate relevant addresses and/or UTxOs using existing off-chain indexers, such as Blockfrost, Koios, local db-sync, e.t.c. No specialized indexers/routers necessary.

- **No Oracles** - Protocols that rely on off-chain information feeds are subject to the integrity of the underlying oracle network. This raises many difficult questions about security, availability, governance, and greatly increases the attack surface. Instead, CSL-DeFi primitives forgo reliance on oracles, in favor of *endogenous* price discovery. 

- **No Superfluous "dApp" Tokens** - primitives do not *require* any new fungible tokens. There is no yield farming, no "bootstrapping rewards", no specialized incentive structures. There are never any permissioned batchers, DAOs, or otherwise central entities. ADA is all that this is needed for minUTxO and TX fees. Instead, primitives align demand with market forces to incentivize participation.

  
### Advantages of Fully P2P DeFi Protocols

- **Full Custody** - users always maintain complete spending *and* delegation control over their assets. The only exception is when locking is required to enforce protocol logic, which restricts spending (but never restricts delegation). 

- **P2P Concurrency** - all user interactions are fully p2p and occur to and from each others' unique addresses. This means there must be at least one UTxO for every user of the protocol, so throughput scales *with* the number of users. 

- **Frontend/Backend Agnosticism & Interoperability** - since all protocols are ultimately just on-chain minting and spending policies, they are frontend-agnostic. They can be integrated in a wide variety of frontends, such as light wallets, simple webpages, or fully custom stacks.

- **Emergent Liquidity** - Instead of placing orders "against" specialized market-makers, liquidity aggregates naturally from high user volume. Over time, sophisticated traders using bespoke systems/algorithms will arise that become de-facto market makers.

- **Zero Slippage** - All assets are priced purely in relation to other on-chain assets. Slippage is impossible, since transaction validity depends only on exact fulfillment of individual users' terms, and no external variables.  

- **Censorship Resistance** - thanks to frontend agnosticism, ultralow attack surface, and the atomized nature of user interactions, CSL-DeFi primitives offer the highest level of censorship resistance of any DeFi architecture. 

- **Democratic Upgradability** - since addresses are unique, users choose if/when to use new contracts/primitives. Doing so does not impact the functionality of the primitives since they are interoperable with other primitives as well as with other versions for the same primitive.


## List of Working Protocols

### [Cardano-Swaps](https://github.com/fallen-icarus/cardano-swaps)
A simple, scalable, p2p-exchange protocol. Users create unique scripts and Beacon Tokens for every swap-pair, so all available pairs are easily queryable. Swaps are highly composable - almost any transaction can have inputs from swap addresses, provided they have an appropriate output back to the swap address. Using Aiken, the latest version of the protocol can support 10+ swaps composed in a single transaction. Liquidity arises naturally from the incentive for arbitragers to find the most profitable "path" through a sea of open swap-pairs. Users maintain full delegation control at all times.

#### Comparison to Cardano DeFi Leader
- **Cardano-Swaps primitive** - 1.5 ADA transaction fee for a transaction with 14 different currency conversions. Composable with any other dApp.
- **Minswap** - a minimum of 2 ADA transaction fee for a single currency conversion<sup>[1]</sup>. Non-composable with other dApps.


### [Cardano-Loans](https://github.com/fallen-icarus/cardano-loans)
A p2p-lending/borrowing protocol with trustlessly negotiable and repayable loans, an on-chain credit-history, compounding interest, and trade-able bonds. Lenders and borrowers negotiate loan terms via a "two-way UTxO handshake". Borrowers can repay loans incrementally, and reclaim their collateral proportionally. Compounding interest and/or recurring minimum payments can be enforced by requiring the borrower to periodically "evolve" their Active Loan UTxO. Lenders may sell their credit in the form of a Bond NFT, which also serves as a Beacon to query the location of the borrower's Loan UTxO.

#### Comparison to Cardano DeFi Leader
- **Cardano-Loans primitive** - All terms are negotiable: what assets can be used as collateral, how long the loan will be, what asset will be loaned out, the interest rate, etc. All assets, even ones that don't exist yet, are supported. Composable with any other dApp.
- **Liqwid** - Only DJED, ADA, SHEN, and iUSD are supported<sup>[2]</sup>. Adding support for more assets requires a governance action and trust that the maintainers will actually add the support. Nothing is negotiable. Non-composable with other dApps.


### [Cardano-Options](https://github.com/fallen-icarus/cardano-options)
A p2p protocol for writing and buying American-style *covered* options contracts. Spreads of contracts of varying parameters can be written against a single UTxO, and buyers can select which to purchase. Upon paying the premium, the buyer mints an "Exercise" Token that lets them exercise the contract up until expiry. The Exercise Token can be sold on a secondary market, just like traditional options contracts. The option writer/seller cannot reclaim the underlying asset(s) until after expiry, but maintains delegation control the whole time. 

#### Comparison to Cardano DeFi Leader
There currently is no Cardano Leader for options contracts.


### [Cardano-Secondary-Market](https://github.com/fallen-icarus/cardano-secondary-market)
A secondary p2p marketplace for buying/selling NFTs. Works in conjunction with Cardano-Loans and Cardano-Options for seamlessly creating a secondary market for bonds and options contracts.



## Future Directions
CSL-DeFi Protocols have a ways to go before they are ready for mass adoption. Here are some roadmap items:

### Aiken 
Currently, all CSL-DeFi primitives (except for Cardano-Swaps) are written in IOG's PlutusTx language. Although this is a good choice for prototyping, auditing, and maintaining code, it is relatively resource-intensive. With current node parameters, some features are bottlenecked by script execution limits. Newer, more resource-efficient languages like Aiken offer more headroom for additional features and throughput. Aiken implementations for the primitives are currently being worked on. To express the promise of switching to Aiken, here are the before and after benchmarks for Cardano-Swaps:

| Language | Maximum Number of Swaps | Tx Fee |
|--|--|--|
| PlutusTx | 4 | 1.5 ADA |
| Aiken | 14 | 1.5 ADA |

Similar improvements are expected for the other primitives.

### QA, Auditing, and Standardization
CSL-DeFi primitives are more than the sum of their parts. They are not just standalone dApps, but are an ecosystem of protocols that explore a new design paradigm. Concepts like Beacon Tokens need to be fleshed out and standardized across the community, perhaps in the form of CIPs. At minimum, each protocol should undergo an external audit prior to wide adoption.

### User Adoption
CSL-DeFi protocols are purely p2p, so bootstrapping users and building liquidity may be challenging. However, there are some large key players that can help catalyze the process. Existing DEXes and lending/borrowing protocols with their own "dApp tokens" are especially interesting, since they may be able to offer additional profit-sharing rewards to token holders in a kind of "decentralized market maker" model. 

### Frontend Integrations
All CSL-DeFi primtives employ a standardized JSON schema that allows for straightforward integration into existing frontends, like wallets and explorers. The UX/UI afforded by these integrations is essential from a usability perspective. Outreach to such providers is ongoing.

### Community Outreach
The growth of CSL-DeFi primitives depends on community involvement. Collaboration on Github, Funding from Catalyst, or Twitter discussions are all great contribution vectors. Additional community resources like video demos, tutorials, and a website are being worked on.


-------


### Emurgo Build 2023 Hackathon

For the judges' consideration:

Due to the nature of this project, there is no straightforward way to profit from a VC perspective; there are no tokens, no equity, it is just a family of open protocols. However, it lays the foundation for *massively* increasing use and utility of the Cardano blockchain. All ADA holders (especially whales like Emurgo) stand to greatly benefit from increased value of Cardano as a whole.

Furthermore, this project creates a platform for others to build on. Traders, creditors/lenders, or something more exotic like DAO-managed hedge funds can all use these protocols to profit for themselves and their investors.

Since this project is not a typical VC project, here is an alternative funding plan:
1. Development gets $100K to finish and pay for security audits.
2. The remaining money that would normally be invested would be set aside by the VC specifically for bootstrapping the protocols.

The VC can earn a return on its investment by participating in the protocols as lenders, arbitragers, etc.

---
## References
1. https://docs.minswap.org/min-token/usdmin-tokenomics/trading-fee-discount
2. https://app.liqwid.finance/
