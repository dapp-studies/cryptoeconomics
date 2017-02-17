# Cryptoeconomic Concepts from Vitalik 

These concepts were pulled from Vitalik's talk on cryptoeconomics from Edcon.. Some notes may be missing

Economics Tools

* Tokens: Incentivize actors by assigning them units of a protocol-defined cryptocurrency
  * Eg. Blog rewards
* Privileges: Incentivize actors by giving them decision-making rights that can be used to extract rent
  * Eg. Transactions
  * If you have a block, and you can include transactions, you can use your $ to bribe the block creators to include your transaction / choice. 
    * Basically, limited space, you can pay to have voting rights on what the future state should look like

Concepts

* Cryptoeconomic security margin: Amount of money x such that "either a given guarantee G is satisfied, or those at fault for violating G are poorer than they otherwise would have been at least X
* Cryptoeconomic proof: a message signed by an actor that can be interpreted as "I certify that either P is true, or i suffer an economic loss of size X"
* Uncoordinated choice model: a model that assumes that all participants in a protocol do not coordinate with each other and have separate incentives, and are all smaller than size X
  * Competitive game theory 
* Coordinated choice model: a model that assumes that all actors ina  protocol are controlled by the same agent \(or coalition\)
  * Cooperative game theory
* Bribing attacker model: a model that starts off with an uncoordinated choice assumption, but also assumes that there is an attacker capable of making payments to actors conditional on them taking certain actions
  * Budget

P + epsilon attack

* A bribing attacker can corrupt the Schellingcoin game with a **budget** of P + ϵ and zero **cost**!

Griefing factors

* Even in an incentive-compatible protocol, there will almost always be opportunities to, at some cost to yourself, impose costs on others
  * How much you make other people lose / how much you lose
    * High is bad



