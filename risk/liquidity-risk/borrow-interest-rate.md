# Borrow Interest Rate

Mitigating liquidity risk through the borrow interest rate model: EarthFi uses an interest rate algorithm that is calibrated to manage liquidity risk and optimize utilization. The borrow interest rates are derived from the utilization rate (_U_).​ _U_ is an indicator of the availability of capital within the pool. The interest rate model manages liquidity risk in the protocol through user incentives to support liquidity:

* When capital is available: low interest rates to encourage borrowing.
* When capital is scarce: high interest rates to encourage repayments of debt and additional supplying.

To retrieve the interest rate strategy contract on-chain - DEPLOYMENT ADDRESS TBD

### Interest Rate Model <a href="#interest-rate-model" id="interest-rate-model"></a>

Liquidity risk materializes when utilization is high, and this becomes more problematic as _U gets_ closer to 100%. To tailor the model to this constraint, the interest rate curve is split in two parts around an optimal utilization rate = _UOptimal_. Before reaching this, ​the slope is small, and after, it begins rising sharply.

Both the variable and stable interest models, are derived from the formula in place from the technical Whitepaper, with different parameters for each asset. Variable debts see their rate constantly evolving with utilisation. Alternatively, stable debts maintain their interest rate at issuance until the specific rebalancing conditions are met. In V1, interest models are optimized by new rate strategy parameter **Optimal Stable/Total Debt Ratio** to algorithmically manage stable rate.​

### Model Parameters <a href="#model-parameters" id="model-parameters"></a>

First, it’s crucial to distinguish assets that are used predominantly as collateral (i.e., volatile assets), which need liquidity at all times to enable liquidations. Second, the asset’s liquidity on EarthFi is an important factor as the more liquidity, the more stable the utilization. The interest rates of assets with lower liquidity levels should be more conservative.It is also key to consider market conditions (i.e., how can the asset be used in the current market?). EarthFi's borrowing costs must be aligned with market yield opportunities, or there would be a rate arbitrage with users incentivized to borrow all the liquidity on EarthFi to take advantage of higher yield opportunities. With liquidity mining, EarthFi will have adapted its cost of borrowing by lowering the _UOptimal_ of the assets affected. This will increase the borrow costs that are now partially offset by the liquidity reward.

#### Variable Interest Rate Model Parameters <a href="#variable-interest-rate-model-parameters" id="variable-interest-rate-model-parameters"></a>

Variable rate parameters:

* Base Variable Borrow Rate
* Variable Rate Slope 1
* Variable Rate Slope 2

#### Stable Interest Rate Model Parameters <a href="#stable-interest-rate-model-parameters" id="stable-interest-rate-model-parameters"></a>

Stable rate parameters:

* Base Variable Borrow Rate
* Variable Rate Slope 1
* Variable Rate Slope 2
* Stable to Total Debt Ratio

The stable rate provides predictability for the borrower; however, it comes at a cost, as the interest rates are higher than the variable rate. The rate of a stable loan is fixed until the rebalancing conditions are met:

1. Utilisation Rate
2. Overall Borrow Rate, the weighed average of all the borrow rates

The assets that are most exposed to liquidity risk do not offer stable rate borrowing.The base rate of the stable rate model corresponds to the average market rate of the asset.

#### V1 Interest rate Parameters <a href="#v3-interest-rate-parameters" id="v3-interest-rate-parameters"></a>

The interest rate parameters for V1 markets have been deployed with 3 interest rate strategies calibrated per cluster of assets that share similar risk profiles.

### Rate Strategy Volatile One <a href="#rate-strategy-volatile-one" id="rate-strategy-volatile-one"></a>

Volatile assets need liquidity at all times and are thus calibrated at a low Optimal Utilization Ratio

{% hint style="info" %}
AAVE, BAL, CRV, LINK, SUSHI, WBTC, WETH, WMATIC,
{% endhint %}

| Parameters                         | Value |
| ---------------------------------- | ----- |
| Optimal Usage                      | 45%   |
| Base Variable Borrow Rate          | 0     |
| Variable Rate Slope 1              | 4%    |
| Variable Rate Slope 2              | 300%  |
| Base Stable Borrow Rate            | 2%    |
| Stable Rate Slope 1                | 7%    |
| Stable Rate Slope 2                | 300%  |
| Optimal Stable to Total Debt Ratio | 20%   |

### Rate Strategy Stable One <a href="#rate-strategy-stable-one" id="rate-strategy-stable-one"></a>

Low liquidity stablecoins have lower Optimal Utilization Ratio than those with higher liquidity.

{% hint style="info" %}
DAI
{% endhint %}



| Parameters                         | Value |
| ---------------------------------- | ----- |
| Optimal Usage                      | 90%   |
| Base Variable Borrow Rate          | 0     |
| Variable Rate Slope 1              | 4%    |
| Variable Rate Slope 2              | 60%   |
| Base Stable Borrow Rate            | 2%    |
| Stable Rate Slope 1                | 0.5%  |
| Stable Rate Slope 2                | 60%   |
| Optimal Stable to Total Debt Ratio | 20%   |

### Rate Strategy Stable Two <a href="#rate-strategy-stable-two" id="rate-strategy-stable-two"></a>

High liquidity stablecoins which are calibrated to lower rates to encourage borrow.

{% hint style="info" %}
sUSD, USDC, USDT, EURS, jEUR, agEUR
{% endhint %}

| Parameters                         | Value |
| ---------------------------------- | ----- |
| Optimal Usage                      | 80%   |
| Base Variable Borrow Rate          | 0     |
| Variable Rate Slope 1              | 4%    |
| Variable Rate Slope 2              | 75%   |
| Base Stable Borrow Rate            | 1%    |
| Stable Rate Slope 1                | 0.5%  |
| Stable Rate Slope 2                | 75%   |
| Optimal Stable to Total Debt Ratio | 20%   |

{% hint style="info" %}
When market conditions change, the interest rate parameters must be changed to adapt to utilization on EarthFi's market as well as to incentives across DeFi.
{% endhint %}

### Supply rate <a href="#supply-rate" id="supply-rate"></a>

The borrow interest rates paid are distributed as yield for aToken holders who have supplied to the protocol, excluding a share of yields sent to the ecosystem reserve defined by the reserve factor. This interest rate is generated on the asset that is borrowed out then shared among all the liquidity providers.&#x20;

You can view the protocol's deposit APY on the EarthFi App for each asset. The average Supply APY over a period also includes Flash Loan fees.
