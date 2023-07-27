# 🚦 veNFTE and NFTE Staking

Vote-escrowed NFTE (veNFTE) is a non-transferable governance token issued to users who stake NFTE LP tokens into the NFTEarth voting-escrow contract. veNFTE balances dictate voting power in both governance proposals and incentive direction on the NFTEarth Protocol.

A user’s veNFTE balance is determined using the amount of NFTE LP (liquidity pool) tokens they have staked and the duration of the stake: staking more NFTE LP tokens for a longer duration will yield a larger veNFTE balance. This keeps voting power in the hands of users with the greatest commitment to the protocol’s long-term success.

Staked NFTE tokens cannot be redeemed from the contract until the end of the staking period. If a user claims their NFTE LP tokens at the end of the staking period, the associated veNFTE balance will be burned. Users can choose to extend the duration of their stake at any time.

NFTEarth uses the Origin Protocol's (OGN) voting-escrow contract that has been [audited by OpenZeppelin](https://github.com/OriginProtocol/security/blob/master/audits/OpenZeppelin%20-%20Origin%20Dollar%20Governance%20-%20June%202022.pdf).

### Voting Power Calculation

A user’s veNFTE balance is a reflection of their voting power in the protocol. The veNFTE balance is computed based on two factors:

* Amount of NFTE LP tokens staked
* Duration of staking period

A multiplier is applied to the amount of NFTE LP tokens staked, and this multiplier increases according to the duration of staking period chosen. The longer the stake, the higher the multiplier. The maximum staking period is 1 years The minimum staking period is one week.

The staking multiplier increases according to an exponential curve. It grows by 1.5x with each additional step in the staking period. Thus, if a user chooses to extend their staking period, they will gain an additional 1.5x boost to their veONFTE balance.

The staking multiplier curve can be expressed as `1.5^(staking period end - contract launch)`. The further the staking period end is from the contract launch, the higher the staking multiplier will be.

> **Example 1**\
> If two users stake the same amount of NFTE LP tokens on the same date, but select different end-dates for their stake, they will receive correspondingly different veNFTE balances. So, if Alice and Bob both stake 100 NFTE LP tokens on July 1, 2023, but Alice selects an end-date of July 1, 2024 and Bob selects an end-date of July 1, 2025, Bob will receive more veNFTE because his staking multiplier will be greater.
>
> **Example 2**
>
> If two users stake the same amount of NFTE LP tokens on different dates, but the end-date of their stake is the same, they will receive the same veNFTE balance. That is, if Alice stakes 100 NFTE LP tokens on July 1, 2023 and Bob stakes 100 NFTE LP tokens on July 1, 2024, but they both choose a staking period that ends on June 30, 2024, they will have the same veNFTE balance. This is because their 100 NFTE LP tokens are subject to the same multiplier.
>
> **Example 3**
>
> If two users stake the same amount of NFTE LP tokens and choose the same end-date, but then one of the users extends their staking period to a further end-date, that user will receive an increase to their veNFTE balance. That is, if Alice and Bob both stake 100 NFTE LP tokens on July 1, 2023 and both choose a staking period that ends on July 1, 2024, they will initially have the same veNFTE. But if Alice later extends her staking period to July 1, 2024, her veNFTE balance will increase because her staking multiplier will increase.

Over time, the voting power of older stakes will be diluted since new stakes will have higher multipliers applied to their veNFTE balance. The best way to maximize your voting power is therefore to stake NFTE LP tokens for the maximum 1 year staking period and simply extend your staking period on a regular basis.
