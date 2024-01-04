---
description: "Revenue\_Sharing for Real Yield for Stakers"
---

# 🚦 veNFTE

## How veNFTE Works

veNFTE (Staked NFTE LP) is a vesting system based on [Curve's veCRV mechanism](https://curve.readthedocs.io/dao-vecrv.html) which locks a SushiSwap NFTE/WETH LP token for a maximum of 1 year. The veNFTE system is designed to promote long-term token-holder alignment and facilitate fair revenue sharing of protocol fees generated.

By locking the SushiSwap NFTE LP token, holders are given veNFTE as a receipt token, entitling them to governance rights and protocol fee sharing. A user's veNFTE balance is directly proportional to the amount of NFTE LP tokens locked and the duration of time left in the lock period. In short, if a user locks 1 NFTE LP for 1 year, they will receive the same amount of “vote power” strength as someone who locks 2 NFTE LP for only 1/2 year.

## Implications:

* veNFTE is the governance token of NFTEarth, used in Snapshot voting to authorize changes to the DAO including the management (adding/removing) of incentive programs, new gauges and funding of service providers.
* veNFTE holders will be entitled to all revenue sharing from NFTEarth. The handling and amount of protocol fees are subject to change based on NFTEarth Governance Process.&#x20;

{% hint style="info" %}
**In the same breath, the token supply schedule for NFTE has been defined and is set permanently. A key takeaway for the new tokenomic schedule is the total supply of NFTE being capped at 100,000,000. There are never going to be more than 100,000,000 NFTE tokens - and so over time, each token will grow more valuable as the protocol continues to create useful and revenue generating products and services.**
{% endhint %}

## How is veNFTE different from veBAL and veCRV?

There are a few modifications that set veNFTE apart:

* Instead of locking pure NFTE, users obtain veNFTE by locking NFTE LP tokens obtained on SushiSwap. This ensures that even if a large portion of NFTE tokens are locked, there is a sustainable form of deep liquidity onchain.
* veNFTE's maximum locking period is 1 year, a decrease from veCRV's 4 year period (though the same as veBAL). The minimum locking period is 1 month (veBAL is 1 week). What we have observed is that the NFT ecosystem and DeFi moves extremely fast, and in the event governance decides to implement a new voting system, this shorter duration of lock compared to veCRV creates a much shorter, but still sufficiently long, waiting period to transition.

## Motivation and Rationale for veNFTE

\
Staked NFTE (veNFTE) is the value accrual and governance mechanism for NFTEarth. veNFTE balances dictate both voting power in governance proposals and incentive direction on the NFTEarth Protocol and receive all rewards, protocol revenue, and future value accrual that is split with stakers and the DAO.

## The 3 Main Contracts of the veNFTE System

1. **NFTE/WETH LP:** [**0xd00CD4363bCF7DC19E84fDB836ce28D24F00716c**](https://basescan.org/address/0xd00CD4363bCF7DC19E84fDB836ce28D24F00716c) **NFTE/WETH LP - SushiSwap LP Token on Base: This is the LP token to stake in the contract.**
2.   **veNFTE:** [**0xc526c83849fb4424e4563a3b609a4ebf916cf6d0**](https://basescan.org/address/0xc526c83849fb4424e4563a3b609a4ebf916cf6d0)  **where you create your lock and deposit your NFTE LP position obtained from SushiSwap on Base. Once you create a lock, you will have a veNFTE balance.**
3. **FeeDistributor:** [**0x99032fd0727ded2a579dcb447e85359dde9223b6**](https://basescan.org/address/0x99032fd0727ded2a579dcb447e85359dde9223b6) **the Revenue Sharing Vault where veNFTE stakers claim weekly rewards from.**

## What is veNFTE in more detail and how do the mechanics work?

For some context, it’s important to understand some of the most successful governance and value accrual tokenomic models that have been built in web3 up until now. Curve innovated with veCRV - pioneering the concept of locking up tokens, and it worked exceptionally well for them and kicked off a massive amount of protocols moving to a ve (vote-escrowed) model.&#x20;

Lock your CRV tokens and get veCRV, which earns you rewards and governance control. Balancer then innovated on what Curve built with veBAL, where instead of locking a single token, token holders lock a liquidity position (LP) consisting of BAL / WETH tokens — and they also changed the duration of max-time locking from veCRV down to 1 year. The change to an LP token as the locking token means that as more tokens get locked, \*liquidity increases\* which is a fundamentally innovative and massive competitive advantage for any protocol that implements it — and absolutely ideal for any protocol looking to bootstrap long-term liquidity. The results of this change speak for themselves. The BAL token is currently one of the single most liquid tokens in all of crypto, with its liquidity nearly equal to the market cap of the token. See the image below from DexScreener and check it out for yourself.&#x20;

## Why hasn't anyone else tried this yet?

First off, the trend towards this type of governance staking mechanism is clear. This is the direction that many protocols are looking to move to, and Balancer has even introduced an entire initiative aiming to onboard new protocols to this type of “Locked LP as governance” staking mechanism. The challenge with doing this with UniswapV3 positions is this: since they are created as ERC-721 NFTs — non-fungible tokens — this by default makes them inherently not composable with the type of staking contract designed for protocol revenue sharing based on staking by token holders — meaning these positions can’t be used to simply transfer into a staking contract, like what is possible with a UniswapV2 position. The SushiSwap LP position on Base is a fork of UniswapV2, the common type of LP token.

{% hint style="info" %}
**In a single sentence, the more liquidity you provide and the longer time period you stake, the greater your rewards and governance power!**
{% endhint %}

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>Balancer Liquidity / MC - Image Courtesy of DexScreener</p></figcaption></figure>

***

A user’s veNFTE balance is determined using the amount of NFTE LP (liquidity pool) tokens they have staked and the duration of the stake: staking more NFTE LP tokens for a longer duration will yield a larger xNFTE balance. This keeps voting power in the hands of users with the greatest commitment to the protocol’s long-term success.

Staked NFTE tokens cannot be redeemed from the contract until the end of the staking period. If a user claims their NFTE LP tokens at the end of the staking period, the associated veNFTE balance will be burned. Users can choose to extend the duration of their stake at any time.

NFTEarth has implemented the same voting escrow and fee distribution contracts used by Stargate Finance with their staking mechanism [veSTG](https://arbiscan.io/address/0xfBd849E6007f9BC3CC2D6Eb159c045B8dc660268) deployed on Arbitrum One as the staking contract (veNFTE) and their [FeeDistributor](https://arbiscan.io/address/0xaf667811a7edcd5b0066cd4ca0da51637db76d09) as the rewards distribution mechanism (Fee Distributor).&#x20;

## Voting Power Calculation

A user’s veNFTE balance is a reflection of their voting power in the protocol. The veNFTE balance is computed based on two factors:

* Amount of NFTE LP tokens staked
* Duration of staking period

## Miscellaneous

\
Over time, the voting power of older stakes will be diluted since new stakes will have higher multipliers applied to their veNFTE balance. **The best way to maximize your voting power and veNFTE balance is therefore to stake NFTE LP tokens for the maximum 1 year staking period and simply extend your staking period on a regular basis (such as once every week as an example). It is important to claim your rewards once they are available.**
