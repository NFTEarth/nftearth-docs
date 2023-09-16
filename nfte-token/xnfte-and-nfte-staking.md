---
description: Aligning Incentives - Real Yield, Revenue Sharing, and Empowered Governance
---

# 🚦 xNFTE and NFTE Staking

***

<figure><img src="../.gitbook/assets/xNFTE_Icon (1).png" alt=""><figcaption><p>xNFTE</p></figcaption></figure>

Staked NFTE (xNFTE) is the value accrual and governance mechanism being developed for the long-term benefit of NFTEarth protocol. The staking solution is a contract that lives onchain in the form of a non-transferable governance token issued to users who stake NFTE LP tokens into the NFTEarth staking contract. xNFTE is received as a receipt token, much like veCRV and veBAL are received from Curve and Balancer staking programs.&#x20;

xNFTE balances dictate voting power in both governance proposals and incentive direction on the NFTEarth Protocol and receive all rewards, protocol revenue, and future value accrual that is split with stakers and the DAO.

Please reference the Medium article published on specifics relating to xNFTE.

{% hint style="info" %}
Curve innovated with veCRV pioneering locking up tokens and it worked exceptionally well for them and kicked off a massive amount of protocols moving to a ve (vote-escrowed) model. Lock your CRV and get veCRV which earns you rewards and governance control. Balancer then innovated what Curve built with veBAL, where instead of locking a single token, token holders lock a liquidity position (LP) consisting of BAL / WETH tokens— and they also reduced the amount of max-time lock. This change to an LP token as the locking token means that as more tokens get locked, \***LIQUIDITY INCREASES\*** which is absolutely ideal for any protocol looking to bootstrap long-term liquidity. The results of this change speak for themselves, BAL is currently one of the single most liquid tokens in all of crypto, with its liquidity nearly equal to the market cap of the token as of this writing. with xNFTE, we aim to expand on this conept that Balancer implemented with a couple slight improvements. We will be using the undisputed decentralized exchange (DEX) by volume on Arbitrum as wekk as deploying this solution on Arbitrum (the layer2 network). This creates significantly more opportunities for to attract new users interested in becoming part of the long-term vision of the protocol and taking part in protocol governance.

So, Why hasn’t any other protocols done this? Especially an NFT protocol?

The trend is clear, first off. This is the direction that many protocols are looking to move towards, and Balancer has even introduced an entire initiative to attempt to onboard new protocols to this type of LP as governance staking mechanism. The challenge with Uniswapv3 positions is that since they are created as non-fungible tokens, this makes them inherently not composable — meaning they can’t be used to simply transfer into a staking contract, like is possible with a Univ2 position. Enter AMM specialist Gamma Strategies. Gamma, like several other protocols that specialize in DEX liquidity management, enables the deposit of Univ3 positions in the form of an NFT, and creates a tokenized representation to the depositor, which can then use to be staked, thus solving the issue of composability. They can do so in a pre-set range as well, making the entire staking mechanism discussed here possible. As the goal for staking is to expand liquidity, and not focus on optimizing fee capture, the positions created through Gamma are full-range Univ3 positions — which makes them function in a similar essence to Univ2 positions in terms of the weight of each token in the liquidity pool. So, what Gamma does explicitly is: enables the functionality desired (a transferrable representation of the pro-rate share of Univ3 LP of NFTE / WETH to the staking contract). Since we will be partnering with Gamma Strategies to enable this, they create a full-range Univ3 position of NFTE / WETH that can be deposited into directly in their UI or via contract, and then the address that makes the deposit, receives a token receipt that represents their amount of shares pro-rata to the total supplied in this unique LP position. This token receipt is then what is used for reliable bookkeeping and what is staked to obtain xNFTE. NFTEarth is the first protocol to do this in web3, and also the first to do so on a layer2 network, enabling governance and value accrual for significantly more users than if deployed just on Ethereum Mainnet where costs to create and add to positions is prohibitive for the vast majority of people around the Earth.

Important note: Users can still add to Uniswapv3 pool for NFTE / WETH on Arbitrum outside of the Gamma Strategies partner protocol, or even add their position to the Gamma tokenized version and choose not to stake as well.

**In a single sentence, the more liquidity you provide and the longer time period you stake, the greater your rewards and governance power!**



**In a sentence, the more liquidity you provide and the longer you stake, the more rewards and governance power you get!**&#x20;
{% endhint %}

A user’s xNFTE balance is determined using the amount of NFTE LP (liquidity pool) tokens they have staked and the duration of the stake: staking more NFTE LP tokens for a longer duration will yield a larger xNFTE balance. This keeps voting power in the hands of users with the greatest commitment to the protocol’s long-term success.

Staked NFTE tokens cannot be redeemed from the contract until the end of the staking period. If a user claims their NFTE LP tokens at the end of the staking period, the associated xNFTE balance will be burned. Users can choose to extend the duration of their stake at any time.

NFTEarth intends to use the Stargate Finance [veSTG](https://arbiscan.io/token/0xfBd849E6007f9BC3CC2D6Eb159c045B8dc660268) implementation on Arbitrum One as the staking contract and the FeeDistributor as the rewards distribution mechanism.&#x20;

### Voting Power Calculation

A user’s xNFTE balance is a reflection of their voting power in the protocol. The xNFTE balance is computed based on two factors:

* Amount of NFTE LP tokens staked
* Duration of staking period

> **Example 1**\
> If two users stake the same amount of NFTE LP tokens on the same date, but select different end-dates for their stake, they will receive correspondingly different xNFTE balances. So, if Alice and Bob both stake 100 NFTE LP tokens on July 1, 2023, but Alice selects an end-date of July 1, 2024 and Bob selects an end-date of August 1, 2024, Bob will receive more xNFTE because his staking multiplier will be greater.
>
> **Example 2**
>
> If two users stake the same amount of NFTE LP tokens on different dates, but the end-date of their stake is the same, they will receive the same xNFTE balance. That is, if Alice stakes 100 NFTE LP tokens on July 1, 2023 and Bob stakes 100 NFTE LP tokens on July 1, 2024, but they both choose a staking period that ends on June 30, 2024, they will have the same xNFTE balance. This is because their 100 NFTE LP tokens are subject to the same multiplier.
>
> **Example 3**
>
> If two users stake the same amount of NFTE LP tokens and choose the same end-date, but then one of the users extends their staking period to a further end-date, that user will receive an increase to their xNFTE balance. That is, if Alice and Bob both stake 100 NFTE LP tokens on July 1, 2023 and both choose a staking period that ends on July 1, 2024, they will initially have the same xNFTE. But if Alice later extends her staking period to August 1, 2024, her xNFTE balance will increase because her staking multiplier will increase.

Over time, the voting power of older stakes will be diluted since new stakes will have higher multipliers applied to their xNFTE balance. **The best way to maximize your voting power and xNFTE balance is therefore to stake NFTE LP tokens for the maximum 1 year staking period and simply extend your staking period on a regular basis.**
