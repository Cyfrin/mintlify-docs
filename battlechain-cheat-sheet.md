# **BattleChain Cheat Sheet**

## **Problem**

* There is no real staging environment in Web3
* Projects go from $0 → $5M overnight after audit
* Bug bounties are difficult for ethical hackers
* AI bots don’t have a home to be stress tested
* We keep losing billions as an industry, so we clearly need to do something more

## **Solution**

* BattleChain is a pre-mainnet, post-testnet environment with real funds (incentivized testnet)
* The chain encourages ethical hackers, AI bots, and experimental DeFi advocates to stress test protocols pre-initial contract launch with real liquidity

## **Mechanisms**

* When a protocol launches a contract, it can submit to the L2 DAO to become a “hackable” or “Attackable mode” contract. 
    * "Attackable mode" = open season for ethical hacking
    * "Production mode" = protected, same as mainnet
    * All contracts with the “Attackable” flag are covered by a[ safe harbor agreement](https://frameworks.securityalliance.org/safe-harbor/overview), which gives ethical hackers the confidence to attack them. **The entire contract is considered under attack under this stage.**
        * Ethical hackers send money hacked to the safe harbor, with a 10% or  $5 $5M cap, whichever is lower
* A project can choose to “promote” a contract from “Attackable” to “Production” by calling the “promote” function on a special contract on the chain that tracks the status of each contract.
* The stages of a contract are:
    * Warming up (NOT ok to attack)
    * Attackable
    * Production (NOT ok to attack)

## **Pre-initial contract launch flow**

1. A project not deployed finishes the audit
2. The project deploys to BattleChain as an “attackable” contract, and with some amount of real funds deployed (ie, $100,000)
3. Once the protocol has been live for some duration of time, they move it from “attackable” to “production” and deploy it on their other target chains

## **FAQ**

* Q: Will there be a time when the contacts on BattleChain mirror the contracts on another mainnet?
* A: Yes. In fact, contracts on BattleChain should either be:
    * Mirroring 100% production contracts (and have their bounty flag set to “production”)
    * Have a new feature not on mainnet yet (and a new contract set to “attackable”)
  
* Q: If an ethical hacker hacks a BattleChain contract, isn’t that telling non-ethical hackers about an exploit?
* A: Yes. This is why it’s important to have only “attackable” contracts marked as such if you’re OK with them being attacked. There is an approvable process for becoming attackable as well, and this includes filtering out projects that mirror already production contracts.

* Q: What if a contract on mainnet mirrors an attackable contract on battlechain?
* A: We have an approval process to approve contracts to move to the attackable phase. We will filter out “copycat” projects, and will be watching mainnet to make sure that contracts on BattleChain in attackable mode are different. We also have a function to “force promote” a contract to production if either:
    * Too much TVL enters the contract
    * A mainnet contract is launched with similar TVL
  
* Q: Do I keep my BattleChain contracts monitored after we’ve completed the stress test on BattleChain?
* A: Yes! Once you promote, you treat it as production code.
  
* Q: Who should deploy to BattleChain?
* A: Everyone, but actually. Every project should have a BattleChain instance.
  
* Q: Will low liquidity be an issue? 
A: Maybe, there are some protocols that might have issues with this, but it’s more likely that if your protocol has issues with low liquidity, that is a potential security issue. For bugs that exist in high liquidity environments only, this class of bug might be difficult to stress test for on BattleChain. To be honest, though, I’m nervous we are going to attract a lot of attention and liquidity.

* Q: Should the contracts on BattleChain be different than those on mainnet?
* A: No. The contract logic should be exactly the same. Your audited contracts should be exactly what you deploy to BattleChain. The only difference is the parameters (such as the same contract being deployed on Arbitrum One will have different parameters from Base)
  
* Q: Monitoring. Will BattleChain hacks trigger actions on mainnet?
* A: It can! It’s up to you! That might be a good idea. 
  
* Q: Why not do a Kusama-like play? Where do you deploy a system like this for the core of the blockchain itself? Like to test geth/lighthose/teku/etc?
* A: Yes! We are considering doing that in the future.
  
* Q: What is the economic model?
* A: We have several monetization strategies, each of which we will test to see how the market responds.
    * Early play:
        * 1. Protocols pay to enter attack mode
        * 2. Percentage fee from safe harbor payouts
        * 3. Transaction fees
    * Mid-game play:
        * 4. Foundations to move subsidy programs to BattleChain
    * Late-game:
        * 5. Run BattleChain for multiple ecosystems and get paid from the foundations to run them (we can do BattleChain Solana, Monad, Arbitrum, anything)
    * Super late-game:
        * 6. We do a Kusama-esque play where we also have a BattleChain for the L1/L2s themselves
    * Additionally, we plan to launch a governance token to help facilitate the payments, payment parameters, safe harbor copy, etc.
  
* Q: Why does this need to be an L2?
* A: Having an environment where these types of attacks happen, isolated from more stable liquidity, is important. Isolating this to its own chain so it has a smaller chance of contagion with other production liquidity is important. The branding of the chain (being the experimental chain) is very important. The “status” of each contract is very difficult to change without access to the transaction level. We will be launching on the ZKsync L2, which gives us access to mark each deployed contract with its flag at the point of deployment.
  
* Q: Is this just putting user funds at risk?
* A: No. Historically, the protocol would just “ship it” and wait for a black hat to hack it. Here, they are doing the same flow they would do, but essentially with a “warm-up” period. People know that they are in this unstable state, and people will be encouraged to look at how long and with how much liquidity a project survived on BattleChain before being promoted.
  
* Q: Will projects want to pay for this?
* A: It will be part of their security budget, but the friction to deploy is almost none. Some projects are already doing this! They deploy to a “cheaper” chain first as a staging ground (ie: Polygon). It’s just another RPC to deploy, a single “requestAttackableStatus” to become attackable, and a single “promote” function to call. Three transactions. The flow and payments are nearly identical to what they would be doing anyway.
  
* Q: Why not a testnet?
* A: Anytime a testnet has some money attached to it, it becomes ruined as a testnet and is shut down. We’ve seen examples of this already (such as Goerli).
  
* Q: What if this exposes a bug on mainnet?
* A: This is the hardest question. White hats will have to do due diligence to make sure they are not exposing a hack, and instead use a bug bounty platform to submit. The same due diligence audit firms should do before they publish audit reports.
  
* Q: Why do you need a token?
* A: For governance over the safe harbor/attackable genesis contract parameters