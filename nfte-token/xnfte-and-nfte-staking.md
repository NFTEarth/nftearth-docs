---
description: "xNFTE: Real Yield From Staking and Revenue\_Sharing"
---

# 🚦 xNFTE and NFTE Staking

***

<figure><img src="../.gitbook/assets/xNFTE_Icon (1).png" alt=""><figcaption><p>xNFTE</p></figcaption></figure>

### How xNFTE Works:

xNFTE (Staked NFTE) is a vesting system based on [Curve's veCRV mechanism](https://curve.readthedocs.io/dao-vecrv.html) which locks a Gamma Strategies NFTE/WETH UniswapV3 Token (NFTE LP) for a maximum of 1 year. The xNFTE system is designed to promote long-term token-holder alignment and facilitate fair revenue sharing of protocol fees generated.

By locking the [Gamma NFTE LP](https://app.gamma.xyz/vault/uni/arbitrum/details/nfte-weth-10000-wide) token, holders are given xNFTE, entitling them to governance rights and protocol fee sharing. A user's xNFTE balance is directly proportional to the amount of NFTE LP locked and the duration of time left in the lock period. In short, if a user locks 1 NFTE LP for 1 year, they will receive the same amount of “vote power” strength as someone who locks 2 NFTE LP for only 1/2 year.

Implications:

* xNFTE is the governance token of NFTEarth, used in Snapshot voting to authorize changes to the DAO including the management (adding/removing) of incentive programs, new gauges and funding of service providers.
* xNFTE holders will be entitled to all revenue sharing from NFTEarth. The handling and amount of protocol fees are subject to change based on NFTEarth Governance Process.&#x20;

In the same breath, the token supply schedule for NFTE has been defined and is set permanently. A key takeaway for the new tokenomic schedule is the total supply of NFTE being capped at 100,000,000. There are never going to be more than 100,000,000 NFTE tokens - and so over time, each token will grow more valuable as the protocol continues to create useful and revenue generating products and services.

### How is xNFTE different from veBAL and veCRV?

There are a few modifications that set xNFTE apart:

* Instead of locking pure NFTE, users obtain xNFTE by locking NFTE LP Gamma Tokens. This ensures that even if a large portion of NFTE tokens are locked, there is a sustainable form of deep liquidity onchain.
* xNFTE's maximum locking period is 1 year, a decrease from veCRV's 4 year period (though the same as veBAL). The minimum locking period is 1 month (veBAL is 1 week). What we have observed is that the NFT ecosystem and DeFi moves extremely fast, and in the event governance decides to implement a new voting system, this shorter duration of lock compared to veCRV creates a much shorter, but still sufficiently long, waiting period to transition.

### Motivation and Competitive Rationale for xNFTE:

\
Staked NFTE (xNFTE) is the value accrual and governance mechanism developed and deployed for the benefit of the long-term stakeholders in the NFTEarth protocol. The staking solution is a contract that lives onchain in the form governance token issued to users who stake NFTE LP tokens (obtained by depositing a UniswapV3 position on Gamma Strategies protocol) into the NFTEarth staking contract. xNFTE is received as a receipt token, much like veCRV and veBAL are received from Curve and Balancer staking programs when users stake into those contracts.

xNFTE balances dictate both voting power in governance proposals and incentive direction on the NFTEarth Protocol and receive all rewards, protocol revenue, and future value accrual that is split with stakers and the DAO.

Please reference the detailed Medium article published with the overall vision and specifics relating to xNFTE below.

{% embed url="https://medium.com/@nftearth/supercharge-your-future-xnfte-innovation-from-nftearth-becomes-first-nft-protocol-to-offer-real-88c4028d5a41" %}
Medium publication on xNFTE
{% endembed %}

### The 3 Contracts That Make xNFTE Work:

**There are 3 Contracts you need to understand to clearly grasp the xNFTE system:**

1. **NFTE/WETH LP - Gamma Vault** [0x82496243c0a1a39c5c6250bf0115c134ba76698c](https://arbiscan.io/address/0x82496243c0a1a39c5c6250bf0115c134ba76698c) on Arbitrum.  This is a Gamma Vault that turns a UniswapV3 position into a fungible token that can be staked in the xNFTE contract. (Tokenized NFTE / WETH LP Position).
2. **xNFTE** Contract Address — where you deposit your NFTE LP position obtained from Gamma Strategies: [0xE57bd15448C3b2D1dBAD598775DD2F36F93EBf90](https://arbiscan.io/address/0xe57bd15448c3b2d1dbad598775dd2f36f93ebf90) on Arbitrum. Once deposited, you will have an xNFTE balance.
3. **FeeDistributor** — the Revenue Sharing Vault where xNFTE stakers claim rewards from - Contract Address: [0x9138a2e628f92a42397b3b600e86047ae49aca98](https://arbiscan.io/address/0x9138a2e628f92a42397b3b600e86047ae49aca98) on Arbitrum.

### All Relevant Contracts:

| Name           | Function                                                                       | Arbitrum Address                                                                                                     |
| -------------- | ------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------- |
| NFTE/WETH LP   | Tokenized UniswapV3 LP Position - Staking Asset                                | [0x82496243c0a1a39c5c6250bf0115c134ba76698c](https://arbiscan.io/address/0x82496243c0a1a39c5c6250bf0115c134ba76698c) |
| xNFTE          | xNFTE (Staked NFTE)                                                            | [0xE57bd15448C3b2D1dBAD598775DD2F36F93EBf90](https://arbiscan.io/address/0xE57bd15448C3b2D1dBAD598775DD2F36F93EBf90) |
| FeeDistributor | Revenue Sharing Vault                                                          | [0x9138a2e628f92a42397b3b600e86047ae49aca98](https://arbiscan.io/address/0x9138a2e628f92a42397b3b600e86047ae49aca98) |
| NFTE           | NFTE Token (on Arbitrum)                                                       | [0x51B902f19a56F0c8E409a34a215AD2673EDF3284](https://arbiscan.io/address/0x51B902f19a56F0c8E409a34a215AD2673EDF3284) |
| WETH           | WETH Token (on Arbitrum)                                                       | [0x82aF49447D8a07e3bd95BD0d56f35241523fBab1](https://arbiscan.io/address/0x82af49447d8a07e3bd95bd0d56f35241523fbab1) |
| UniswapV3 Pool | Uniswap NFTE/WETH Pool                                                         | [0x17eE09e7a2cc98b0B053B389A162fC86A67b9407](https://arbiscan.io/address/0x17ee09e7a2cc98b0b053b389a162fc86a67b9407) |
| UniV3Proxy     | Utility For Simplifying Creating a Gamma NFTE LP Position (optional for users) | [0x82FcEB07a4D01051519663f6c1c919aF21C27845](https://arbiscan.io/address/0x82FcEB07a4D01051519663f6c1c919aF21C27845) |

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption><p>xNFTE in the NFTEarth UI</p></figcaption></figure>

### What is xNFTE in more detail and how do the mechanics work?

For some context, it’s important to understand some of the most successful governance and value accrual tokenomic models that have been built in web3 up until now. Curve innovated with veCRV - pioneering the concept of locking up tokens, and it worked exceptionally well for them and kicked off a massive amount of protocols moving to a ve (vote-escrowed) model. Lock your CRV tokens and get veCRV, which earns you rewards and governance control. Balancer then innovated on what Curve built with veBAL, where instead of locking a single token, token holders lock a liquidity position (LP) consisting of BAL / WETH tokens — and they also changed the duration of max-time locking from veCRV down to 1 year. The change to an LP token as the locking token means that as more tokens get locked, \*liquidity increases\* which is a fundamentally innovative and massive competitive advantage for any protocol that implements it — and absolutely ideal for any protocol looking to bootstrap long-term liquidity. The results of this change speak for themselves. The BAL token is currently one of the single most liquid tokens in all of crypto, with its liquidity nearly equal to the market cap of the token. See the image below from DexScreener and check it out for yourself. With xNFTE, we aim to expand on this concept that Balancer implemented, with a couple of slight improvements. We will be using the leading decentralized exchange (DEX) by volume on Arbitrum — UniswapV3 — and additionally our staking contract is also deployed to Arbitrum layer2 as well, opposed to Ethereum Mainnet because of the lower costs of completing transactions on Arbitrum. This creates significantly more opportunities to attract new users interested in becoming part of the long-term vision of the protocol and taking part in protocol governance.

**So, why haven’t any other protocols done this? Especially any NFT protocols?**

First off, the trend towards this type of governance staking mechanism is clear. This is the direction that many protocols are looking to move to, and Balancer has even introduced an entire initiative aiming to onboard new protocols to this type of “Locked LP as governance” staking mechanism. The challenge with doing this with UniswapV3 positions is this: since they are created as ERC-721 NFTs — non-fungible tokens — this by default makes them inherently not composable with the type of staking contract designed for protocol revenue sharing based on staking by token holders — meaning these positions can’t be used to simply transfer into a staking contract, like what is possible with a UniswapV2 position.

So, enter AMM specialist Gamma Strategies. We’ve partnered with Gamma to help innovate past this obstacle in order to create composability of the UniswapV3 LP positions to enable them to be staked (in our case the LP pair being NFTE / WETH), by creating a tokenized representation of the NFT LP position which can then be staked to obtain an xNFTE position. Innovation enabled. The depositor of the UniswapV3 position on Gamma Strategies receives an ERC-20 token that represents their deposit, which can then be used to be staked, thus solving the issue of composability. They can create this tokenized position (termed a Gamma Vault) in a pre-determined and fixed liquidity range as well — that for our purposes here, is full-range liquidity, thus making the entire staking mechanism discussed so far a new reality.

As the goal for the NFTEarth staking mechanism is to broadly expand liquidity, and not focus on optimization of fee capture, the positions created through Gamma are full-range UniswapV3 positions — which makes them function in a similar essence to UniswapV2 positions in terms of the weight of each token in the liquidity pool. Expanding on this a bit further for clarity, this means the positions will always seek to maintain a 50/50 ratio of tokens in the pool, different than many concentrated liquidity positions that are created from UniswapV3. So, what Gamma does explicitly is: enable the functionality desired (a transferrable representation of the pro-rata share of UniswapV3 LP position of NFTE / WETH… to the xNFTE staking contract in order for a user to create an xNFTE position and participate in protocol revenue sharing and governance). Users can deposit directly to the NFTE / WETH position in the Gamma UI, or via smart contract, and then the user that completes the deposit receives the token receipt which serves as the representation of their amount of shares in the Vault, pro-rata, to the total in existence for this this unique LP NFTE / WETH UniswapV3 position. This token receipt created by Gamma is then what can be used to reliably and precisely track the size of user positions and amounts staked to know precisely what each user share of xNFTE is at all times.

Important note: Users can still choose to add to the UniswapV3 pool for NFTE / WETH on Arbitrum outside of the Gamma Strategies partner protocol solution, or even create a Vault position on Gamma and choose \*not\* to stake in the NFTEarth staking contract as well.

{% hint style="info" %}
**In a single sentence, the more liquidity you provide and the longer time period you stake, the greater your rewards and governance power!**
{% endhint %}

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p>Balancer Liquidity / MC - Image Courtesy of DexScreener</p></figcaption></figure>

***

A user’s xNFTE balance is determined using the amount of NFTE LP (liquidity pool) tokens they have staked and the duration of the stake: staking more NFTE LP tokens for a longer duration will yield a larger xNFTE balance. This keeps voting power in the hands of users with the greatest commitment to the protocol’s long-term success.

Staked NFTE tokens cannot be redeemed from the contract until the end of the staking period. If a user claims their NFTE LP tokens at the end of the staking period, the associated xNFTE balance will be burned. Users can choose to extend the duration of their stake at any time.

NFTEarth has implemented the same voting escrow and fee distribution contracts used by Stargate Finance with their staking mechanism [veSTG](https://arbiscan.io/address/0xfBd849E6007f9BC3CC2D6Eb159c045B8dc660268) deployed on Arbitrum One as the staking contract (xNFTE) and their [FeeDistributor](https://arbiscan.io/address/0xaf667811a7edcd5b0066cd4ca0da51637db76d09) as the rewards distribution mechanism (Fee Distributor).&#x20;

### Voting Power Calculation

A user’s xNFTE balance is a reflection of their voting power in the protocol. The xNFTE balance is computed based on two factors:

* Amount of NFTE LP tokens staked
* Duration of staking period

### Miscellaneous:

\
Over time, the voting power of older stakes will be diluted since new stakes will have higher multipliers applied to their xNFTE balance. **The best way to maximize your voting power and xNFTE balance is therefore to stake NFTE LP tokens for the maximum 1 year staking period and simply extend your staking period on a regular basis. It is important to claim your rewards once they are available.**
