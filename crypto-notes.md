This talk was given by Vitalik Buterin in FC17



* Applications of crypto
  * Consensus layer
  * Smart contract layer \[this talk focuses on the smart contract layer\]

* Two ways to look at on chain apps
  * Separated concerns approach -- assume consensus layer works perfectly
  * Integrated approach -- check both layers

* Desired properties of consensus
  * Convergence
    * We don't want more than a couple blocks reverted
  * Validity
  * Data availability
    * It should be possible for anyone to download full data of a block
  * Non-censorship
    * All txs get through
* Security models
  * **Extremely important for smart contracts**
* * Honest majority assumption
    * More than 51% are nice
  * Crypto economic model
    * Measure coordination costs
  * \*Uncoordinated majority\*
    * All actors act independently and no actor controls x%
  * Coodrinated Choice
    * Most actors are colluding
  * Bribing attacker
    * All actors make choices independently but the attacker can bribe

* Bitcoin analysis vs different models
  * Honest majority- 1/2
  * Uncoordinated majority -
  * Coordinated majority - 0
  * Bribing attacker ~13.2 \* k budget, 0 cost

* Security model within smart contract system
  * Honest majority doesn't work in a smart contract system.
    * Because Ethereum provides a free entry property \(easy to buy a bunch of shares in smart contract systems\) it is very easy to quickly buy 51%

* Shelling coin
  * Reward people for converging on the same answer
  * Assume people will vote for the truth because it's what other people will want to vote for
  * **Analysis in coordinated choice model**
    * Doesn't matter what they choose, they get payoff either way
  * **Analysis in bribing attacker model**
    * With bribing attacker with a budget of P + e \(P = the payout, e = your extra incentive\)
    * There is zero cost!
    * The attacker can basically flip the outcome of the oracle, and if successful, will actually pay **nothing**!
* Are bribing attackers realistic?
  * Con: No because people won't do obviously evil things!
  * Pro: Yes, because bribes can be more subtle then flat out bribes
  * Example of bribing attacker
    * Subsidized stake pools in PoS

* Smart contract applications
  * Outsourcing computation & storage
  * Provably fair random numbers
  * Oracles
  * Governance
  * Stablecoins
    * Use smart contracts to create on chain financial derivatives, then use those for some more stable currencies 
  * Bounties for hard problems \(ex Math or CS problems\)
  * Telling the time

* **Outsourced computation:**
  * Solving NP hard problems
  * Problem 1
    * There is an attack! You can front-run a solution
      * Someone gets a tx with a solution, and then they don't include but instead submit the solution themselves
      * Solution:
        * Commit/reveal -- commit the answer with a hash of the answer / address, and then after that submit an answer
  * Problem 2
    * If you can check the correctness of a problem on chain, then there's no reason to pay for the solution and just do it yourself
      * Solution 1: Save intermediate states
        * Assume that the transition between each intermediate step can be computed on chain
        * A challenger can then compute each step locally, and then submit a challenge which the smart contract can verify that the computation was wrong
  * Is it profitable to cheat?
    * Turn it into a two player game and solve for the Nash equilibrium

* **In many situations, there will be an inherent tradeoff between capital efficiency and correctness**
  * We can expect that with a lot of games which require deposits, we can expect they will start competing for these deposits

* Interactive games and trust assumptions
  * Interactive games \(all the games above\) **lean very heavily on the non-censorship property of a blockchain**
  * If you can censor, you can steal in the context of interactive games \(eg deny service during the challenge period\)

* Challenge flood attacks
  * Send a large amount of challenges a the same time
  * Victims don't have enough block space to reply to all challenges in time
  * Attacker unfairly wins in some situations
  * This works on **any** interactive protocols

* Challenges
  * Can we detect censorship and have online full nodes reject censoring blocks?
  * Can we make it impossible to censor selectively?
    * "Ethereum is resistant to soft forks" -- this was shown because of the halting problem \(you cannot detect the nature of code without fully running it\)
    * There has been further research in how to soft fork Ethereum and it seems there are some cases where you can
    * Make censorship more resistant with on chain scheduling
  * Can we automatically detect flood attacks and trigger some kind of challenge delay?

* Usual second-price auction
  * Everyone submits a sealed bit
  * The top payer pays the 2nd highest bid's price
  * The Problem: Mechanism design assumes that the secrets are kept
  * Crypto challenges
    * Preventing submitting many sealed bids but only opening the ones you want, a sealed bid should have a deposit
    * How large is the deposit?
    * The deposit reveals information about the size of the bid
  * Possible solutions:
    * Allow deposits to exceed size of bid then distribute a small amount of the auction revenue to all bidders in proportion to excess deposits

* PoW randomness
  * Doesn't work because it is exploitable by the miners

* Cataloging attacks on randomness gadgets
  * Arbitrary selection
  * Dice re-rolling
  * Influence
    * Spread the randomness across many blocks, making influence attack more expensive

* PoS-style randomness
  * RANDAO github.com/randao/randao 
  * Everyone can join by submitting a hash and deposit
  * Then everyone submits the answers
  * Then you xor all of the results together and use that as random
  * If any party doesn't send, they lose their deposit and you reroll



* On chain governance
  * A lot of interest using for chain governance, Tezos, Dash, Bitshares
  * Create DAOs on top of the chain
  * Most popular governance mechanism is VOTING
  * **Problems with voting**
    * **Voter apathy** - Level of voter participation is very small
    * **Economic security **- 
      * Your incentive to vote the right way is very low
      * Very low security under the bribing attacker model
        * Eg. Favorable interest rates from stake pools
  * Solutions for voting
    * Make voting accountable
      * Coin lock voting
        * If your vote is chosen, your coin is locked up for some time
      * Futarchy
      * Use social layer to explicitly account for "attacks" against voting
        * Governance can _use _voting, but it must be loosely coupled
          * Eg, disable accounts which look like they are voting against other people's behalf

* Other challenges
  * Stablecoins
  * Provably fair games
  * Proving humanity





