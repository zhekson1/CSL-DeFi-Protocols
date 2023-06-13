# CSL-DeFi-Protocols
p2p-DeFi protocols for the Cardano Settlement Layer

## Introduction

The CSL-DeFi project seeks to standardize the basic building blocks of p2p finance on Cardano. It is a collection of open "smart contract" protocols that share common design patterns, chiefly centered around radical fairness, permissionlessness, and interoperability. By taking full advantage of the protocol architectures enabled by the eUTxO paradigm, CSL-DeFi can achieve an unprecedented level of scale. The protocols work synergistically with one another, and enable the formation of a truly independent economy on Cardano. 


## Motivation
Distributed ledger technologies have long sought to provide an alternative financial platform for the disenfranchised or unbanked peoples of the world. Throughout the years, much progress has been made. However, the current DeFi paradigm is still heavily reliant on the legacy financial system for critical pieces of infrastructure, namely fiat on/off ramps, pricing information, and identity management. To be a viable alternative, DeFi must further decouple from these bottlenecks, and establish its own *endogenous* infrastructure. 

### Current DeFi Drawbacks
To stress the drawbacks of current DeFi protocols, let's consider their attack surfaces. 

Firstly, most "DeFi dApps" rely on a *permissioned* set of batchers/arbitragers/aggregators for liquidity. Although a well designed dApp does not place user funds at risk of being outright stolen, the dApp cannot guarantee high availability, since permissioned actors are at a high risk of denial-of-service (DOS) attacks. This is doubly true for dApps that rely on oracles for external info feeds, where DOS *and* oracle collusion/corruption are major attack vectors. 

Secondly, the governance of these actors is a complex and nuanced topic: who decides who gets to be a batcher or oracle provider? How are they compensated? If the answers to these questions are DAOs and dApp tokens, respectively, doesn't this mean that over time, as the permissioned actors profit, they gain increasing control of the DAO, until they become their own overseers? Governance quickly gets messy, and should be minimized wherever possible. The answers to these questions will also have major regulatory consequences as well.

Thirdly, many DeFi dApps sacrifice full delegation control, especially in the case of liquidity pools. The more delegation control is decoupled from the ADA owners, the more distorted Ouroboros' game theory becomes. It is difficult to predict the extent of this distortion, so minimizing it is of paramount importance.



### The Blockchain Trilemma, Revisited

If mature DeFi protocols really do offer an alternative to the legacy financial system, they will likely be perceived as threat by those in positions of power. DeFi protocols must therefore be resilient to high-resource attacks by state-level actors. Minimizing the attack surface, and prioritizing both security ***and*** availability is essential for adoption at scale.



## The CSL-DeFi Protocol Paradigm
This document establishes a standard for all CSL-DeFi protocols. 

### Common Design Patterns
All CSL-DeFi protocols share some common characterisitics. 

- **Unique User Addresses** - CSL-DeFi users deploy and interact with each others' script addresses. Each user creates at least one unique address, composed of *identical* script-mediated payment credentials (per protocol), and *unique* user-mediated staking credentials. Owner-related actions (i.e. simple spending) are "overloaded" to the user's staking credential, so funds are never locked or stolen. Users always maintain full delegation authority over their addresses.

- **Fully p2p Finance** - since all users have there own addresses, there are no discrete liquidity pools. User's can trustlessly interact with each other without having to go through batchers (permissioned or permissionless). Furthermore, since every user gets their own UTxOs, the theoretical concurrency limit is always at least the number of users of the protocols.

- **Democratic Upgradability** - since addresses are unique, users choose if/when to use new contracts/protocols. Upgrades can happen without disrupting the liquidity/design of the protocols since v1 of a protocol can still compose with v2 of a protocol. This gives users the freedom to choose which contracts to use, per their own discretion.

- **Permissionless Indexing** - All CSL-DeFi protocols carefully marry their spending policies with the minting policies of specialized NFTs, dubbed "Beacon Tokens", to mediate protocol logic and indexing. All protocols have at least one Beacon Token that shares identical queryable properties with all other Beacon Tokens of the same protocol. As a result, users can locate each other's addresses by querying existing off-chain indexers, such as Blockfrost, Koios, db-sync, e.t.c. No specialized indexers/routers necessary.

- **No Oracles** - Protocols that rely on off-chain information feeds are subject to the integrity of the underlying oracle network. This raises many difficult questions about security, availability, governance, and greatly increases the attack surface. Instead, CSL-DeFi protocols forgo reliance on oracles, in favor of Cardano-native (*endogenous*) price discovery. 

- **No Superfluous "dApp" Tokens** - protocols do not *require* any new fungible tokens. There is no yield farming, no "bootstrapping rewards", no specialized incentive structures. There are never any permissioned batchers, DAOs, or otherwise central entities. ADA is all that this is needed to create UTxOs and pay TX fees. This means that these protocols are also significantly less restricted by regulations than dApps that do have their own tokens.

- **Frontend/Backend Agnosticism & Interoperability** - since all protocols are  ultimately just on-chain minting and spending policies, they are frontend-agnostic. They can be integrated in a wide variety of frontends, such as light wallets, simple webpages, or fully custom stacks. 

- **Censorship Resistance** - thanks to the aforementioned agnosticism and the distributed nature of unique user addresses, CSL-DeFi protocols offer the highest level of censorship-resistance of any dApp architecture. This is especially important considering that these protocols offer an alternative economy that is decoupled from the legacy financial system, which poses a threat to those in positions of power. 


## List of Protocols

### [Cardano-Swaps](https://github.com/fallen-icarus/cardano-swaps)
A simple, scalable, p2p-exchange protocol. Users create unique scripts and Beacon Tokens for every swap-pair, so all available pairs are easily queryable. Swaps are highly composable - any transaction can have inputs from swap addresses, provided they have an apporpriate output back to the swap address. The latest version of the protocol (written with Aiken) can support 10+ swaps in a single transaction. Liquidity arises from the incentive for arbitragers to find the most profitable "path" through a sea of open swap-pairs. That path can be through illiquid pairs which means liquidity spreads to **all** trading pairs instead of being siloed in a specific trading pair.


### [Cardano-Loans](https://github.com/fallen-icarus/cardano-loans)
A p2p-lending/borrowing protocol with trustlessly negotiable and repayable loans, an on-chain credit-history, compounding interest, and trade-able bonds/debts. Lenders and borrowers negotiate loan terms via a "two-way UTxO handshake". Borrowers can repay loans incrementally, and reclaim their collateral proportionally. Compounding interest and/or recurring minimum payments can be enforced by requiring the borrower to periodically "evolve" their Active Loan UTxO. Lenders may sell their credit in the form of a Bond NFT, which also serves as a Beacon to query the location of the borrower's Loan UTxO.


### [Cardano-Options](https://github.com/fallen-icarus/cardano-options)
A p2p protocol for writing and buying American-style *covered* options contracts. Spreads of contracts of varying parameters can be written against a single UTxO, and buyers can select which contract to purchase. Upon paying the premium, the buyer mints an "Exercise" Token that lets them exercise the contract up until expiry. The Exercise Token can be sold on a secondary market, just like traditional options contracts. The option writer/seller cannot reclaim the underlying assets until after expiry, but maintains delegation control the whole time. 


### [Cardano-Secondary-Market](https://github.com/fallen-icarus/cardano-secondary-market)
A secondary p2p marketplace for buying/selling NFTs, including financial contracts (options, futures, bonds, e.t.c.). Similar in scope to Cardano-Swaps, but geared towards NFTs rather than FTs.


## Inter-Protocol Composability

Since these protocols are fully open, a single transaction can utilize more than one of these protocols. For example, imagine Alice would like to buy an options contract for ADA/DJED where the payment due is in DJED but she currently only has USDC. She can use a swap from Cardano-Swaps to convert her USDC to DJED and then, within the same transaction, use the newly aquired DJED to purchase the options contract. Considering the current benchmarks of these protocols, the estimated fee for this kind of transaction would only be about 1.5 ADA.


## Next Steps

### Development Roadmap
Currently, all of the protocols have been successfully prototyped with PlutusTx. Only Cardano-Swaps has been rewritten in Aiken. Rewriting Cardano-Swaps in Aiken saw a 50% decrease in the average transaction fee and increased the throughput of the DEX by a facter of 3 (4 swaps per tx -> 14 swaps per tx). Considering this, it is highly likely that many of the advanced features (such as compound interest) can be successfully included in the next versions of the protocols. Therefore, the immediate next steps are to re-write the remaining protocols in Aiken.

### User Adoption
The community has been very supportive of these protocols which can be seen from these tweets [fill this in]. The goal is to keep the community informed of the development of these protocols so that early adopters (alpha and beta testers) will be available when the time comes.

### Frontend Integrations
All CSL-DeFi protocols employ a standardized JSON schema that allows for straightforward integration into existing frontends, like wallets and explorers. The UX/UI afforded by these integrations is essential from a usability perspective. Out of the gate, a CLI program will be available for users to use these protocols directly. When the time comes, wallet providers can easily integrate these protocols into their frontends.

### Funding
The funding requirements for these protocols is minimal; there is only the upfront cost of development. There are no recurring expenses once the protocols have officially launched. The only real expenses ahead are the security audits and the cost for fallen-icarus and zhekson1 to be able to continue (it is currently volunteer work). Considering there is no equity available for investors, here is an alternative proposition:

1. Development gets $100K to finish and pay for security audits.
2. The remaining money that would normally be invested would be set aside by Emurgo specifically for bootstrapping the protocols.

This path can still be seen as an investment with an ROI. Consider that Cardano-Loans works for anyone with an internet connect. Emurgo can give out thousands of over-collateralized loans at 10%. In most places of the world, this interest rate is unheard of. And the fact that the loan is over-collateralized makes the 10% return practically risk free. A similar logic can be applied to arbitraging if Emurgo looked to participate in that.

