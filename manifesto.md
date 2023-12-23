# P2P-DeFi Manifesto

## Table of Contents

- [Abstract](#abstract)
- [Priorities for a True Blockchain Economy](#priorities-for-a-true-blockchain-economy)
- [The DeFi Hierarchy](#the-defi-hierarchy)
- [Funding](#funding)
- [Conclusion](#conclusion)
- [The P2P-DeFi Protocols](#the-p2p-defi-protocols)

## Abstract

For the first time ever, permissionless blockchain technology allows for an international economy
(DeFi economy) that is impervious to influence from "those in power". No entity can freeze your bank
account, deny you access to loans, prevent you from doing business, etc. Permissionless blockchains
are the ultimate check on government power. However, to actually live up to this potential, the
permissionless economy must rival that of the traditional economy. Yet, contemporary DApp designs
are not capable of satisfying this requirement; they fundamentally prioritize the wrong things.
Blockchains like Cardano are already capable of supporting a competitive DeFi ecosystem. All that is
required is a different approach to building DeFi DApps.

## Priorities for a True Blockchain Economy

There are five requirements for a blockchain economy to actually live up to its potential:

---
### Maximum Expressiveness of Market Sentiment

Healthy price discovery, proper risk-management, and even the security of Proof-of-Stake blockchains
require DApps to *always* allow users to directly express their preferences. *This is the number
one requirement for a healthy economy and is also the number one failing of contemporary DeFi
DApps.* Most problems facing DApps are actually a result of a lack of expressivity; they are *not*
the result of the underlying blockchain.

- Impermanent loss - a user is forced to sell/buy at a price they do not actually want to trade at.
Impermanent loss is only possible when users are unable to explicitly set their desired prices. This
lack of control makes it impossible for users to manage risk. Most institutions and regulators will
not accept this lack of proper risk management.

- Governance issues - updating the DApp is fundamentally centralized and to mitigate this risk,
governance tokens are issued for users to vote with. But ultimately, this governance is just for
show since there is no trustless connection between the governance tokens and what actually happens
with the DApp. This issue only exists because users are not allowed to individually choose which
version of the DApp they want to use, like they can with node versions. If they could, upgrading
DApps would be a democratic process without having to rely on governance tokens.

- Loss of delegation control - users cannot individually delegate their assets in the DApps to the
stake pools of their choice. At best they must choose between a curated subset of stake pools. This
is an existential threat to Proof-of-Stake blockchains.

- Loss of voting power - users cannot vote with any assets that are in a DApp. This is an
existential threat to decentralized governance.

- No composability - users cannot trustless chain DApps together into a single transaction. For
example, imagine a DApp where borrowers make loan payments directly to the lender's address. Also
imagine that this loan (the bond that the lender controls) can be freely traded on the secondary
market. If someone buys the bond from a lender, they must quickly update the payment address before
the borrower makes the next payment. What if Alice bought the bond from Bob on the secondary market
in the same transaction transaction where she updates the payment address? If Charlie (the
borrrower) makes the final payment before Alice's transaction goes through, Alice's transaction will
fail and she will keep her money (Bob would still own the bond). But what if Alice was unable to
compose the secondary market DApp with the lending/borrowering DApp like this? She would need to buy
the bond in one transaction and then update the payment address in another one. She is now risking
that Charlie will pay off the loan before Alice can update the payment address; Bob would still get
the loan payment even though he sold the bond to Alice. The issue in this second scenario is that
Alice is unable to express that she only wants to buy the bond if she is guaranteed to update the
payment address before Charlie makes the next payment; the transaction should fail if this condition
is not met. As this hypothetical situation highlights, trustless composability between DApps is a
critical part of how users can manage risk.

- No trustless integration with new assets - when a new asset is issued, users cannot automatically
start using it with DApps because DApps do not work with arbitrary assets. They only work with
assets that have been effectively whitelisted. As with the governance issue, getting a new asset
supported is usually a permissioned process. Imagine what would happen if a new nation was created
that issued its currency on the blockchain. In order to get this new currency supported by DApps and
have it join the blockchain economy, the new nation needs permission from the DApp developers. *This
gatekeeping is an absurd amount of power that no entity should have.*

*In the case of Cardano, none of the above issues are due to the underlying blockchain; they are
all consequence of how the DApps are designed.* 

In any economy, if the expressiveness of true market sentiment is hampered, that economy will be
very limited in what it can do. There is zero chance of an economy like this being able to compete
with the traditional economy. The appeal for trustlessness is not enough to convince the average
person to use the blockchain economy; if it was, the world would have already mass adopted the
blockchain economy. Developers have been so focused on making their DApps maximally performant that
they have sacrificed expressiveness almost entirely. A DEX with as much throughput as VISA but no
ability for users to properly manage risk will never be mass adopted. If the blockchain economy is
to successfully compete with the traditional economy, *DApp developers must be uncompromising in
their pursuit of expressiveness*. 

### Maximum Availability

Availability is the technical term for how censorship resistant something is; it must always be
*available*, even under pressure. In order for something to be censorship resistant, the entire
stack must be censorship resistant. This is another aspect that developers get wrong; they see one
part of the stack that allows for 100x more throughput, but miss that another area of the stack now
has a centralization bottleneck that allows for censorship as a consequence of the increased
throughput.

An example is the Radix hype. Radix has been heralded as a major innovation in permissionless blockchain
technology due to the performance of the consensus protocol, Cerberus. However, the following quote
is taken directly from the [Cerberus Whitepaper](https://assets.website-files.com/6053f7fca5bf627283b582c2/608811e3f5d21f235392fee1_Cerberus-Whitepaper-v1.01.pdf)
(emphasis ours):

> This mapping provides good consensus performance and security on transaction writes. *Transaction
> read queries, however, such as requesting a complete transaction history for a given account, are
> more difficult since every transaction is addressed by content rather than by a single identifier.*
> 
> -- page 16 under the `Shard Mapping` section

The following is the very last sentence of the `Shard Mapping` section:

> A more specific description of the precise query layer mechanism to be used in Radix is left for
> future work.

In other words, the Radix team doesn't actually know the full trade-offs of Cerberus because they
have yet to fully explore the entire stack. They have optimized the *write* step for the blockchain
but it may come at the cost of the *read* step. If reading from the blockchain requires specialized
hardware, it doesn't matter how performant the writing step is, the reading step will be a
centralized bottleneck that can allow for censorship. (To be fair, it is possible that there will be
a decentralized method for reading from the Radix blockchain. However, it is also possible that there
won't be one.)

Considering that DeFi is about finance, reading from the blockchain must be just as decentralized as
writing to it. If Bob is the only person who can read a person's credit history, everyone must now
go through Bob. This asymmetric access to financial information would give Bob incredible influence
over the DeFi economy, and would effectively guarantee the birth of Wall Street on the blockchain and
open up the door for government influence.

*Every part of the DeFi economy must be maximally available.* Any bottleneck, no matter how small,
can and will be weaponized by those in power.

### Open-Source Code

This one is a hotly debated topic but the arguments for closed-source code are absurd if the goal is
a true permissionless, blockchain economy. Consider the following questions and think of how
open-source code and closed-source code would answer each of these:

- How can new features be added as the economy grows and changes?
- What would happen if the creators of the DApp leave?
- How can the developers resist pressure from governments?
- How can users verify the smart contract they are signing their assets over to?

If the code is closed-source, only the creators can add the new features. While the low-level code is
technically on the blockchain, this code is very difficult to work with and would effectively need
to be reverse engineered by others in order to add the new feature. This is the same problem that
exists with the second question. In short, if the creators ever left the project, the DApp's
features would effectively be frozen in time until some brave developers manage to reverse engineer
the low-level code. Open-source code doesn't have either of these issues because the code is easily
accessible by other developers who are willing to take over. 

As for the third question, unless the identities of the developers are 100% anonymous (which is
arguably impossible nowadays), the developers simply cannot resist pressure from governments.
Furthermore, since the code is closed-source, the developers could be pressured by governments to
add something during a feature update and users would not be able to know unless they reverse
engineered the low-level code (a lot of governments issue gag orders so the developers can't say
anything). If they refused on principle, they would effectively have to walk away from the project
which goes back to the second question. Since the closed-sourced developers have privileged access
to the code, they would need to whitelist any developers that take their place. This is another
bottleneck where governments can exert their influence. Open-source development doesn't have the
same issues: since the code is open-sourced it is easy to see what gets added in the feature update
and if a developer did leave, they are easy to replace without derailing the DApp. In other words,
it is significantly harder for a government to target open-source DApps than closed-source DApps.
Closed-source DApp developers are essentially asking to be targeted by governments...

Additionally, regulations will likely not allow institutions to use closed-source DApps. Like with
all contracts, institutions must be able to read the terms of the contracts they are agreeing to.
This will be doubly important for institutions that use public money. While individual users will
likely be able to use closed-source DApps if they so choose, this will always be significantly more
risky than an open-source smart contract.

Finally, the argument for open-source smart contract development being harder to fund is
fundamentally wrong. But this argument will be saved for the [Funding](#funding) section.

No matter how you look at it, a DeFi economy built on a foundation of open-source code will *always*
be more anti-fragile and resistant to abuse by governments than one built on closed-source code.

### Financially Self-Stabilizing

In order for a blockchain economy to be immune to outside influence, everything it needs to keep
going must be intrinsic to it. In other words, it cannot rely on perpetual outside funding for it to
keep running; it must naturally incentivize its own sustainablility.

Example DApps that do not satisfy this requirement are those that use yield farming to incentivize
liquidity. Yield farming is essentially printing money to pay users to provide liquidity to DApps
that cannot incentivize the liquidity otherwise. To give a more concrete example, since users who
provide liquidity to liquidity pool based DEXs must accept the risk of impermanent loss, there is no
intrinsic incentivize to provide liquidity. In fact, the impermanent loss incentivizes users to
*not* provide liquidity. To overcome this, the DApp creators print money and pay the providers as a
type of compensation for accepting the risk of impermanent loss. But this is a short term fix, at
best.

It is common knowledge that increasing the supply of something will decrease its value overtime.
Even the DApp creators who do yield farming are aware of this and try to create demand for the newly
minted tokens by using them as governance tokens, or minimizing fees if you hold the token, or
giving VIP access if you hold the token. However, they have yet to come up with any *market* demand
for the token. These tokens are not compensation for Alice who just lost $1000 to impermanent loss.
Consider Alice's position: she wants to sell the yield tokens to recoup her $1000, but who will buy
them? They are fundamentally useless tokens. In the short term, DApps have prevented a run on the
tokens by making yield farming payments a percentage of the amount of yield tokens users hold.
Therefore, Bob may be willing to buy the tokens from Alice so that he can make more from yield
farming. But it is important to note that Bob's thinking is to ultimately sell the tokens later; he
doesn't have any market use case for them.

Right now, all DeFi ecosystems that use yield farming are in this "quiet" state. But if the printing
keeps happening, the yield tokens will eventually go to zero. Some DApp creators are aware of this
and are saying the yield farming is temporary. However, it fundamentally cannot be temporary. If the
yield payments stop, what incentive is there to accept impermanent loss and continue providing
liquidity to the DApp? Remember that impermant loss actually incentives users to *not* provide
liquidity. Therefore, if the yield payments stopped, the liquidity would dry up and the DApp would
collapse. So the payments must continue but the yield tokens cannot continually be printed... 

The only way to achieve this is for the DApp to have a re-filling pot from which to continue making
yield farming payments, similar to how stake pool rewards will ideally come from Cardano transaction
fees. But this fundamentally requires real market use cases for the tokens where the services
directly result in the re-filling of the pot. Since there are no real market use cases, it is
extremely unlikely that the re-filling pot path will be possible. This ultimately means yield
farming based DApps are only temporarily stable.

If first principle reasoning suggests yield farming should collapse, why hasn't it yet? The short
answer is "the market can stay irrational longer than you can stay solvent." Just because it hasn't
happened yet doesn't mean it won't. Celsius Network ran for 5 years before reality finally caught up
to it (it promised returns higher than what the market could support). The long answer is that yield
farming has yet to be fully tested. Imagine what would happen at the beginning of a bear market when
people are panic selling to protect their gains from the bull market. This is the time when the risk
from impermanent loss will be highest. Users will force liquidity providers to sell at a loss and
liquidity providers will be compensated in yield tokens whose value is also plummeting, not only
from the bear market but also from the printing. The liquidity providers will then rush to sell
their yield tokens to recoup their losses. But without any real market use case for the yield
tokens, who will buy them? Unlike blockchains whose token value is tied to the future market
potential of the tokens, there is no, and likely never will be any, market potential for yield
tokens. The yield tokens are not even directly used by their own DApps... At least ada is used for
every transaction. In this hypethetical scenario, the value of the yield tokens will plummet
significantly faster than most other cryptocurrency assets. It will essentially be a currency
crisis. Not only would this result in the collapse of the DApp at the time when users need it the
most (without a DEX, how will people exit their investments to protect their gains?), but it will
likely also open up the DApp creators to lawsuits and possibly criminal charges for their negligence
in managing the value of the yield tokens. 

Furthermore, even if the value of the yield tokens somehow managed to stabilize, if the minting and
distribution of the tokens is centralized (which, on Cardano, it currently is), this is a bottleneck
for governments to go after. The more popular the DApp, the more a government will want to control
the yield tokens. This centralization also makes yield token based DApps a major target for
securities regulations.

*DApp developers should not issue tokens unless there is real market demand for the tokens AND the
control of the tokens is truely decentralized.* Doing otherwise only opens pandora's box of
concerns. There are other ways to incentivize self-stabilization of DApps and fund DApp development
that don't rely on yield tokens. The [Funding](#Funding) section at the end explains how.

### Scalability

Finally, scalability is important. *However, of all of the requirements, it is the least important.*
The reason for this is that scalability can almost always be augmented with things like sidechains
and L2s. The same is not true for any of the previous requirements. The difference is in the
systemic risks that the disconnect between the foundational layer and the rest create.

##### A peripheral application adds a feature that does not exist at the foundational layer (expressiveness).

Consider fractional reserve banking. In fractional reserve banking, depositors believe they can
withdraw their money at any time but the banking foundation doesn't actually support this. The banks
only "act" like this feature exists; the depositors' money isn't actually present at the bank
despite their bank account saying otherwise. If depositors actually try to withdraw their money en
masse, a banking failure can cascade throughout the economy and create another Great Depression of
1929. 

##### A peripheral application adds availability.

Consider the international SWIFT system for international money transfers. This application allows
any country/entity to send US dollars anywhere. However, as some countries recently learned the
hard-way, this availability only existed as long as the US government did not consider you an enemy.
Since the availability did not exist at the foundational layer, the resource could be taken away at
the disgression of the controlling entity. This is massively risky for nations and has resulted in
many trying to migrate away from the SWIFT system.

On a smaller scale, freezing bank accounts is another example that can have catastrophic
consequences for individuals on the wrong side of the controlling group's good graces. When Canada
froze the bank accounts of its citizens, many weren't even able to buy food.

##### A peripheral application adds scalability.

Consider the T+2 settlement rules: a securities transaction takes two days to settle. Despite this,
users are typically able to act as if the settlement happens immediately (assuming they aren't
day-trading). For example, if Alice buys Apple stock today at $190/share, she gets the stock at
$190/share even though two days later it is worth $200/share.

The Robinhood-GameStop issue from 2021 was a result of the disconnect between the foundational layer
only supporting T+2 throughput while Robinhood supported immediate throughput. While the fallout
from this systemic risk was bad (users could not buy GameStop which sent the price crashing), this
is significantly less damaging to the overall economy than a great depression or wide spread bank
account freezing.

---

Not all DApps get all of the above priorities wrong, however, the overwhelming majority get at least
a few wrong which disqualifies the DApp from helping to achieve a true blockchain economy. The
rest of the document will explain a blockchain economy architecture that may actually bring about
the full potential of permissionless blockchains.

## The DeFi Hierarchy

The architecture is fundamentally a pyramid where the foundation is the core DeFi foundation and
peripheral applications can be built on top of it. These peripheral applications may exist in
side-chains or L2s but don't need to (they can also exist on L1).

### The Foundation

The foundation should prioritize:

1. Maximum expressiveness
2. Maximum availability
3. Open-source
4. Financial self-stabilization
5. As much scalability as possible without sacrificing any meaningful amount of the previous four
priorities.

Any remaining scalability that is desired can be supplemented with peripheral applications. The
availability requirement makes it easy to create both alternative frontends for the foundational
DApps, and peripheral applications that build on the foundational DApps. Furthermore, maximum
availability also allows the foundational DApps to act as checks against abuse from peripheral
applications (users can always choose to interact with the foundational DApps directly). As a
consequence of the maximum availability requirement, the foundation *must* exist on L1 and natively
support at least the following DApps:

- DEX
- Lending/Borrowing

These DApps must be on L1 because DApps can only ever be as censorship resistant as the underlying
blockchain; L1 will always be the most censorship resistant. (If another layer was more censorship
resistant while also providing better throughput, it would very quickly become the new L1). These
activities make up the lion's share of the core activities in all economies.

> Note: Other DApps like options and secondary market should also probably exist on L1. The above is
> only considering the bear minimum for creating an economy. While options and secondary markets have
> definite use cases, they are more "wants" than "needs". The same is not true for DEXs and
> lending/borrowing DApps; you fundamentally cannot have an economy without these two.

---
##### Features Common To All Foundational DApps

All foundational DApps *must* be trustlessly composable with each other and their other versions
(e.g., v1 for the DApp should compose with v2 for the DApp); if the L1 blockchain is Proof-of-Stake,
they *must* also support full delegation control (choosing from a subset of pools does not count);
if the blockchain supports a decentralized government, the foundational DApps *must* also support
full voting control; and they *must* natively support ALL assets (both those that already exist and
those that have yet to be invented).

##### The Foundational DEX

The foundational DEX *must* have the following features (in addition to those mentioned above):

- Users must be able to specify their own desired prices *exactly*. This is not only a requirement
for swappers but also for liquidity providers. Anything less would make risk management difficult
and would only limit the DEXs' adoption.
- Users must be able to interact directly with the DEX; batchers can be optional. This is the only
way to get true composability between other foundational DApps and have maximum availability. Fee
markets can be used to make it even easier for desperate users to interact with the DEX directly.

##### The Foundational Lending/Borrowing DApp

The foundational lending/borrowing DApp *must* have the following features (in addition to those
mentioned before):

- Lenders must be able to specify their own desired interest rates. Algorithmic interest rates
cannot accurately reflect true market sentiment that depends, not only on tangible factors like
supply and demand, but also intangible factors like personal risk tolerance and macro-economic
outlook.
- Users must be able to negotiate everything permissionlessly: collateral and their relative values,
loan length, compounding periods, etc. No one should need to ask for permission to use a new
collateral or borrow a different asset.
- It must allow for partially under-collateralized loans. The global economy never would have gotten
anywhere if all loans required at least 100% backing all the time.
- The credit history must be trustlessly baked into the DApp. Checking a borrower's credit history
and updating it after a loan is just as important as preventing double spending and theft. There is
simply no way to have a healthy economy without a trustless credit history. Psuedonymous identities
are fine.

For the credit history, some people believe that you can't have credit histories for psuedonymous
identities. What is stopping someone from ripping off a lender (which hurts their credit history) and
then just burning that credit history and starting over? While this is a legitimate concern, this is
not a real issue. Consider the dark web marketplaces. For those that don't know, "stores" exist on
the dark web. Yet, despite these sales effectively being criminal <-> criminal, there is very little
"ripping-off" of customers. These are probably the most dishonest people in the world and yet they
are behaving honestly, despite using psuedonymous (if not anonymous) identities. The reason for this
is that there is a trustless reputation system that is hard to build up. A store with 5 stars but
only 10 reviews in not weighted anywhere near the same as a store with 4.5 stars and 10k reviews;
the latter is guaranteed to get more business than the former. Etsy works the same way despite
buyers and sellers being located all over the world (including in jurisdictions where it is hard to
enforce proper behavior from sellers).
 
People sometimes forget that reputation is an asset that gains value non-linearly based on how long
it stays in good condition. Therefore, what is important isn't whether the identity is psuedonymous
or not, but whether the reputation system is trustless and a good reputation is hard to obtain. For
under-collateralized loans, even in traditional finance, it usually requires 5 years of good credit
to be considered a good enough credit risk to get an under-collateralized loan. Furthermore, some
people think the reputation can be gamed by borrowers borrowing from themselves for a while. Again,
this is not an issue; it is not only common but also encouraged in TradFi. Checkout [secured credit
cards](https://www.investopedia.com/terms/s/securedcard.asp) for an example.
 
As with all reputation systems, a social contract is required for it to work properly, yet it has
never failed to develop as long as the reputation system is trustless. For lending/borrowering, the
social contract will likely match that of the traditional economy: if you want an
under-collateralized loan, you will need several years of good credit history. In this context, if
Bob is malicious and rips off a lender that gave him an under-collateralized loan, it would take Bob
another several years to build up another reputation to get another under-collateralized loan. It is
exponentially easier for Bob to behave honestly and get another under-collateralized loan in just a
few months. Under-collateralized loans are so economically valuable that all users are heavily
incentivized to behave honestly *as long as it is hard to build up enough of a reputation to get
one*. And finally, in order for the reputation system to be trustless, it must be located on L1
along with the actual lending/borrowing DApp.

---

The above requirements for the foundational DeFi DApps fundamentally rule out liquidity pools as
the underlying design. There is no way to pool assets together while still being maximally
expressive and available. Cardano's eUTxO design allows for other architectures that can satisfy all
of the above requirements.

### The Peripherals

The peripheral applications can be used to provide throughput services for all foundational DApps.
For example, consider the situation where Alice wants to swap ADA for AGIX immediately but the
foundational DEX's throughput is too slow. Bob, a market maker, can front the AGIX to Alice with the
intention of settling up with the foundational DEX later, ideally for a profit. This is essentially
how market makers work in TradFi. And, while liquidity pools are not suitable for being used for the
foundational DApp, they are actually perfectly suited for peripheral applications like market
makers.

Since the foundational DApps maximized availability, creating peripherals to augment performance is
permissionless.

## Funding

DApps are a unique type of application in the sense that they have literally zero maintainence cost.
As this [blog](https://jacob.energy/hyperstructures.html) puts it:

> Crypto protocols ... can run for free and forever, without maintenance, interruption or intermediaries.

This means the *only* cost for DApps are the upfront costs for development. To use a chemistry term,
there is a minimum "activation energy" required to get a DApp up and running, but after that, it runs
for as long as the underlying blockchain runs.

### Funding Initial Development

Proof-of-Stake blockchains like Cardano are uniquely suited to fund foundational DApp development
due to the use of delegated Proof-of-Stake. A team of developers can create a stake pool and have
people delegate to them with the expectation that the profits will fund the initial development of
the foundational DApp.

> :warning: This is not an ISPO! There should be no token offering of any kind unless
> there is a real market demand for it and the token minting/distribution is fully decentralized.

Using stake pools like this allows for crowd-sourced funding without requiring users to actually
give any "principle" to the developers; users just give up some delegation profits. Crucially, since
no principle was given up by users AND no tokens were issued, using stake pools like this flies
under the radar of MOST regulations. No harm, no foul.

This is the best way to fund initial development. Not only does this approach circumvent most
regulatory risk, but it is also maximally expressive for users since they can undelegate their
assets if they ever start to doubt the team; instead of losing their life savings from a scam, users
only miss out on some delegation rewards. Likewise, once development is done, users can delegate
away if they wish. This approach is even more well suited to initial development than Project
Catalyst.

### Funding Future Development

As creators of these foundational DApps, the developers are perfectly suited to build the peripheral
applications that rely on the foundation DApps. In essence, by creating the foundational DApp, the
developers are creating a brand new niche for themselves where they will have first mover advantage.

For example, as the creator of the P2P-DeFi protocols, fallen-icarus is *not* altruistic about
this; he is working on these protocols with every intention of building businesses on top of them
(an arbitrager for the DEX and lending for the lending/borrowing DApp). The incentives for this
approach are very real and is why he has dedicated the last year to the P2P-DeFi protocols.

Even if the developers don't build the peripheral applications themselves, other companies that do
will also have every incentive to fund future developments just like how Linux development is funded
by the companies that use it.

Finally, the stake pool funding option will also always be available for future development. Just
don't do anything that attracts the ire of regulators...

## Conclusion

If permissionless blockchain technology is actually going to be a check on governments, the
blockchain economy needs to be properly architected. The wrong architecture is just as impotent
against government abuse as no blockchain economy at all. Cardano's eUTxO architeture is uniquely
suited to satisfy all of the requirements for building a real DeFi economy that can rival TradFi.
While there is still room for improvement with Cardano, it is already capable of supporting a
vibrant DeFi ecosystem; no hard-forks are needed. The only reason a vibrant DeFi ecosystem has not
yet developed is that the DApp developers have fundamentally designed the DApps incorrectly for the
target niche. By following the requirements outlined above, this situation can be corrected.

## The P2P-DeFi Protocols

The following P2P-DeFi protocols are our approach of satisfying the requirements outlined in this
document:

**[Cardano-Swaps](https://github.com/fallen-icarus/cardano-swaps)** - A simple, scalable, P2P-swap
protocol that incentivizes its own liquidity. It forms the "liquidity basin" for composition with
the other three protocols. One-way swaps are akin to limit orders, while two-way swaps enable more
advanced market making techniques. This design is modular and allows for seemless integration with
other order types such as dutch auctions.

**[Cardano-Loans](https://github.com/fallen-icarus/cardano-loans)** - A P2P-lending/borrowing
protocol with trustlessly negotiable and repayable loans, an on-chain credit-history, fixed or
compounding interest, and tradable credit (in the form of Bond NFTs). Lenders and borrowers
negotiate loan terms via a "UTxO handshake". Borrowers can repay loans incrementally (or in full),
and reclaim their collateral proportionally. Lenders can sell their credit on an aftermarket, just
like traditional bonds.

**[Cardano-Options](https://github.com/fallen-icarus/cardano-options)** - A P2P protocol for writing
and buying American-style *covered* options contracts. Users can write multiple offers of varying
parameters against a single UTxO, one of which can then be accepted by a prospective buyer. Buyers
can sell their options (in the form of an NFT) on an aftermarket, just like traditional options. 

**[Cardano-Secondary-Market](https://github.com/fallen-icarus/cardano-secondary-market)** - A P2P
aftermarket protocol for buying/selling NFTs. Works especially well for Bond and Option NFTs of the
previous two protocols, since purchasing *and* using the NFT(s) can be composed in a single
transaction.

If you agree with the overall philosophy of this manifesto and like our approach, please consider
delegating to our stake pool to help fund the initial development:

Ticker: P2PFI  
Hex: bbebbbf81c42de5b84fbbc82c4feab78f8bd8bcf8b5af7c73a06664a  
Bech32: pool1h04mh7qugt09hp8mhjpvfl4t0rutmz703dd003e6qeny5jf9c57
