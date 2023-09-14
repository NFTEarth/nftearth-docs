---
description: Aligning Incentives For All
---

# 🚦 xNFTE and NFTE Staking

***

<figure><img src="../.gitbook/assets/xNFTE_Icon (1).png" alt=""><figcaption><p>xNFTE</p></figcaption></figure>

Staked NFTE (xNFTE) is the value accrual and governance mechanism being developed for the long-term benefit of NFTEarth protocol. The staking solution is a contract that lives onchain in the form of a non-transferable governance token issued to users who stake NFTE LP tokens into the NFTEarth staking contract. xNFTE is received as a receipt token, much like veCRV and veBAL are received from Curve and Balancer staking programs.&#x20;

xNFTE balances dictate voting power in both governance proposals and incentive direction on the NFTEarth Protocol and receive all rewards, protocol revenue, and future value accrual that is split with stakers and the DAO.

{% hint style="info" %}
Curve innovated with $veCRV pioneering locking up tokens and it worked exceptionally well for them and kicked off a massive amount of protocols moving to a ve (vote escrowed) model. Lock your $CRV and get $veCRV which earns you rewards and governance control. Balancer then innovated on this with $veBAL, instead of locking a single token, they lock $BAL / $WETH - and reduced the amount of time max lock. This means as more tokens get locked, **LIQUIDITY INCREASES** which is absolutely ideal for any protocol. with xNFTE, we will be using the top DEX on Arbitrum by volume by a landslide - Uniswap - which until this point, has kept us from implementing this with a Univ3 position since they are NFTs and thus not composable. The NFTEarth team has found an exceptional partner that specializes in DEX liquidity management to create tokenized (ERC-20) positions from the Univ3 pool to enable the functionality desired (transferrable to the staking contract). Since we will be partnering with \_ to enable this, they create a full-range Univ3 position of $NFTE / $WETH that can be deposited into, and then the wallet that deposits gets an ERC-20 token receipt that represents their amount of shares pro-rate to the total supplied in this unique LP position. \
\
This ERC-20 is than what you can stake to get xNFTE. \
\
NFTEarth is the first protocol to do this in web3, and the first on a Layer2 network, enabling governance and value accrual for significantly more users than if deployed just on Ethereum Mainnet.&#x20;



Important note: Users can still add to Uniswapv3 on Arbitrum outside of the partner protocol, or even add their position to the tokenized version and choose not to stake as well.&#x20;



**In a sentence, the more liquidity you provide and the longer you stake, the more rewards and goverance power you get!**&#x20;
{% endhint %}

A user’s xNFTE balance is determined using the amount of NFTE LP (liquidity pool) tokens they have staked and the duration of the stake: staking more NFTE LP tokens for a longer duration will yield a larger xNFTE balance. This keeps voting power in the hands of users with the greatest commitment to the protocol’s long-term success.

Staked NFTE tokens cannot be redeemed from the contract until the end of the staking period. If a user claims their NFTE LP tokens at the end of the staking period, the associated xNFTE balance will be burned. Users can choose to extend the duration of their stake at any time.

NFTEarth intends to use the Stargate Finance [veSTG](https://arbiscan.io/token/0xfBd849E6007f9BC3CC2D6Eb159c045B8dc660268) implementation on Arbitrum One as the staking contract and the FeeDistributor as the rewards distribution mechanism.&#x20;

### Voting Power Calculation

A user’s xNFTE balance is a reflection of their voting power in the protocol. The xNFTE balance is computed based on two factors:

* Amount of NFTE LP tokens staked
* Duration of staking period

> **Example 1**\
> If two users stake the same amount of NFTE LP tokens on the same date, but select different end-dates for their stake, they will receive correspondingly different xNFTE balances. So, if Alice and Bob both stake 100 NFTE LP tokens on July 1, 2023, but Alice selects an end-date of July 1, 2024 and Bob selects an end-date of July 1, 2025, Bob will receive more xNFTE because his staking multiplier will be greater.
>
> **Example 2**
>
> If two users stake the same amount of NFTE LP tokens on different dates, but the end-date of their stake is the same, they will receive the same xNFTE balance. That is, if Alice stakes 100 NFTE LP tokens on July 1, 2023 and Bob stakes 100 NFTE LP tokens on July 1, 2024, but they both choose a staking period that ends on June 30, 2024, they will have the same xNFTE balance. This is because their 100 NFTE LP tokens are subject to the same multiplier.
>
> **Example 3**
>
> If two users stake the same amount of NFTE LP tokens and choose the same end-date, but then one of the users extends their staking period to a further end-date, that user will receive an increase to their xNFTE balance. That is, if Alice and Bob both stake 100 NFTE LP tokens on July 1, 2023 and both choose a staking period that ends on July 1, 2024, they will initially have the same xNFTE. But if Alice later extends her staking period to July 1, 2024, her xNFTE balance will increase because her staking multiplier will increase.

Over time, the voting power of older stakes will be diluted since new stakes will have higher multipliers applied to their xNFTE balance. The best way to maximize your voting power is therefore to stake NFTE LP tokens for the maximum 1 year staking period and simply extend your staking period on a regular basis.
