# CSL-DeFi-Protocols
p2p-DeFi protocols for the Cardano Settlement Layer

## Introduction

The CSL-DeFi project seeks to standardize the basic building blocks of p2p finance on Cardano. It is a collection of open "smart contract" protocols that share common design patterns, chiefly centered around radical fairness, permissionlessness, and interoperability. By taking full advantage of the protocol architectures enabled by the eUTxO paradigm, CSL-DeFi can achieve an unprecedented level of scale. The protocols work synergistically with one another, and enable the formation of a truly independent economy on Cardano. 


## Motivation
Distributed ledger technologies have long sought to provide an alternative financial platform for the disenfranchised or unbanked peoples of the world. Throughout the years, much progress has been made. However, the current DeFi paradigm is still heavily reliant on the legacy financial system for critical pieces of infrastructure, namely fiat on/off ramps, pricing information, and identity management. To be a viable alternative, DeFi must further decouple from these bottlenecks, and establish its own *endogenous* infrastructure. 

### Current DeFi Drawbacks
To stress the drawbacks of current DeFi protocols, let's consider their attack surfaces. 

Firstly, most "DeFi dApps" rely on a *permissioned* set of batchers/arbitragers/aggregators for liquidity. Although a well designed dApp does not place user funds at risk of being outright stolen, the dApp cannot guarantee high availability, since permissioned actors are at a high risk of denial-of-service (DOS) attacks. This is doubly true for dApps that rely on oracles for external info feeds, where DOS *and* oracle collusion/corruption are major attack vectors. 

Secondly, the governance of these actors is a complex and nuanced topic: who decides who gets to be a batcher or oracle provider? How are they compensated? If the answers to these questions are DAOs and dApp tokens, respectively, doesn't this mean that over time, as the permissioned actors profit, they gain increasing control of the DAO, until they become their own overseers? Governance quickly gets messy, and should be minimized wherever possible. 

Thirdly, many DeFi dApps sacrifice full delegation control, especially in the case of liquidity pools. The more delegation control is decoupled from the ADA owners, the more distorted Ouroboros' game theory becomes. It is difficult to predict the extent of this distortion, so minimizing it is of paramount importance.



### The Blockchain Trilemma, Revisited

If mature DeFi protocols really do offer an alternative to the legacy financial system, they will likely be perceived as threat by those in positions of power. DeFi protocols must therefore be resilient to high-resource attacks by state-level actors. Minimizing the attack surface, and prioritizing both security ***and*** availability is essential for adoption at scale.


It is a set of open, Plutus-mediated protocols 




## The CSL-DeFi Protocol Paradigm
This document establishes a standard for all CSL-DeFi protocols. 

### Common Design Patterns
All CSL-DeFi protocols share some common, minimalist design patterns. 

- **Unique User Addresses** - CSL-DeFi users deploy and interact with each others' script addresses. Each user creates at least one unique address, composed of *identical* script-mediated payment credentials (per protocol), and *unique* user-mediated staking credentials. Owner-related actions (i.e. simple spending) are "overloaded" to the user's staking credential, so funds are never locked or stolen. Users always maintain full delegation authority over their addresses.

- **Fully p2p Finance** - since all users have there own addresses, there are no discrete liquidity pools. Users 

- **Democratic Upgradability** - since addresses are unique, users choose if/when to use new contracts/protocols. Doing so bifurcates liquidity during upgrade periods, but gives users the freedom to choose which contracts to use, per their own discretion.

- **Permissionless Indexing** - All CSL-DeFi protocols carefully marry their spending policies with the minting policies of specialized NFTs, dubbed "Beacon Tokens", to mediate protocol logic and indexing. All protocols have at least one Beacon Token that shares identical queryable properties with all other Beacon Tokens of the same protocol. As a result, users can locate each other's addresses by querying existing off-chain indexers, such as Blockfrost, Koios, db-sync, e.t.c. No specialized indexers/routers necessary.

- **No Oracles** - Protocols that rely on off-chain information feeds are subject to the integrity of the underlying oracle network. This raises many difficult questions about security, availability, governance, and greatly increases the attack surface. Instead, CSL-DeFi protocols forgo reliance on oracles, in favor of Cardano-native (*endogenous*) price discovery. 

- **No Superfluous "dApp" Tokens** - protocols do not *require* any new fungible tokens. There is no yield farming, no "bootstrapping rewards", no specialized incentive structures. There are never any permissioned batchers, DAOs, or otherwise central entities. ADA is all that this is needed to create UTxOs and pay TX fees. 


  
### Advantages of p2p-DeFi Design Patterns

Below is an overview of these features:

- **Full Custody** - users always maintain complete spending *and* delegation control over their assets. The only exception is when locking is required to enforce protocol logic, which restricts spending (but never restricts delegation). 
  
- **P2P Concurrency** - throughput scales *with* the number of users. No specialized batchers/indexers are necessary, though they *may* be used in proprietary backends of large lending providers.

- **Frontend/Backend Agnosticism & Interoperability** - since all protocols are  ultimately just on-chain minting and spending policies, they are frontend-agnostic. They can be integrated in a wide variety of frontends, such as light wallets, simple webpages, or fully custom stacks. 

- **Emergent Liquidity** - the only incentive to participate in the protocols are 


- **Zero Slippage** - User interactions are fully p2p, there are no discrete liquidity pools, and all assets are priced purely in relation to other on-chain assets. Slippage is impossible, since orders will only execute if they fulfill the exchange 


- **Censorship Resistance** - thanks to the aforementioned agnosticism and the distributed nature of unique user addresses, CSL-DeFi protocols offer the highest level of censorship-resistance of any dApp architecture. This is especially important considering that these protocols offer an alternative economy that is decoupled from the legacy financial system, which poses a threat to those in positions of power.
  

  




## List of Protocols

### [Cardano-Swaps](https://github.com/fallen-icarus/cardano-swaps)
A simple, scalable, p2p-exchange protocol. Users create unique scripts and Beacon Tokens for every swap-pair, so all available pairs are easily queryable. Swaps are highly composable - almost any transaction can have inputs from swap addresses, provided they have an apporpriate output back to the swap address. Using reference scripts, single transaction can support 10+ swaps. Liquidity arises from the incentive for arbitragers to find the most profitable "path" through a sea of open swap-pairs. Users maintain full delegation control of 


### [Cardano-Loans](https://github.com/fallen-icarus/cardano-loans)
A p2p-lending/borrowing protocol with trustlessly negotiable and repayable loans, an on-chain credit-history, compounding interest, and trade-able bonds/debts. Lenders and borrowers negotiate loan terms via a "three-way UTxO handshake". Borrowers can repay loans incrementally, and reclaim their collateral proportionally. Compounding interest and/or recurring minimum payments can be enforced by requiring the borrower to periodically "evolve" their Active Loan UTxO. Lenders may sell their credit in the form of a Bond NFT, which also serves as a Beacon to query the location of the borrower's Loan UTxO.


### [Cardano-Options](https://github.com/fallen-icarus/cardano-options)
A p2p protocol for writing and buying American-style *covered* options contracts. Spreads of contracts of varying parameters can be written against a single UTxO, and buyers can select which to purchase. Upon paying the premium, the buyer mints an "Exercise" Token that lets them exercise the contract up until expiry. The Exercise Token can be sold on a secondary market, just like traditional options contracts. The option writer/seller cannot reclaim the underlying until after expiry, but maintains delegation control the whole time. 


### [Cardano-Secondary-Market](https://github.com/fallen-icarus/cardano-secondary-market)
A secondary p2p marketplace for buying/selling NFTs, including financial contracts (options, futures, bonds, e.t.c.). Similar in scope to Cardano-Swaps, but geared towards NFTs rather than FTs.




## Future Directions


### Frontend Integrations
All CSL-DeFi protocols employ a standardized JSON schema that allows for straightforward integration into existing frontends, like wallets and explorers. The UX/UI afforded by these integrations is essential from a usability perspective. Outreach to such providers is ongoing.

### Aiken 
Currently, all CSL-DeFi protocols are written in IOG's PlutusTx language. Although this is a good choice for prototyping, auditing, and maintaining code, it is relatively resource-intensive. With current node parameters, some features are bottlenecked by script execution limits. Newer, more resource-efficient languages like Aiken offer more headroom for additional features and throughput. Aiken implementations for the protocols are currently being worked on.


### QA, Auditing, and Standardization


### Community Outreach
The success of CSL-DeFi protocols depends on wide user adoption. 

### Bootstrapping Users



## Long Term Considerations:


### DAO Managed LPs
via Mithril sigs?

### Hydra/Sidechain Accelerators


### Formal Verification


