---
description: Revenue Sharing Program
---

# xNFTE

## The core tenets of the NFTEarth DAO are:&#x20;

* Self sustaining&#x20;
* Community governed&#x20;
* Governance minimized
* Flexible

### Description <a href="#description" id="description"></a>

NFTEarth is a DAO that seeks to highlight and bring to the masses high impact Ethereum L2 protocols and projects. The DAO treasury receives revenue through NFT marketplace fees, NFT collection mint fees, NFT royalties, LP provisioning, and partner projects. 25% of fees generated from anything other than NFTE tokens will be converted to ETH (if received in a different digital asset) and sent to the Revenue Sharing Vault - for xNFTE stakers to be claimed. The amount that each staker of NFTE is eligible to claim is pro-rata to all other stakers in the xNFTE system - aligning incentives for long-term success of the DAO and stakeholders.&#x20;

#### Locking up NFTE <a href="#locking-up-l2dao" id="locking-up-l2dao"></a>

The total amount of xNFTE you hold depends on 2 inputs: first, the amount of NFTE tokens you stake. Second, how long you lock up your NFTE tokens. The longer you lock up your tokens, the higher your proportional share of xNFTE, and the larger your percentage claim AND voting power. The longest duration you can lock your tokens up for is 2 years (24 months). Let's see how this looks in action!

**Hypothetical example:** If you lock up 1 NFTE for 24 months, you receive 1 xNFTE. If you lock up 1 NFTE for 12 months, you receive 0.5 xNFTE, and so on. Once your NFTE is locked, there is no way to unlock it until the lock period has expired. Be certain that you don’t need to access to your NFTE before you lock it up, because you will not be able to withdraw it until your lock expires!

#### Specifications  <a href="#specifications" id="specifications"></a>

* You can lock up your NFTE from 2 weeks (= 0.02 xNFTE / L2DAO) up to 2 years (= 1 xNFTE / NFTE).
* You can only lock until Thursdays each week at 00:00 UTC; if you select any other day, it will lock it for the previous Thursday (e.g if you choose to lock until Friday, June 25th it will lock it until Thursday June 24th).
* As you get closer to your unlocking date, **your balance of xNFTE decreases linearly**.
* xNFTE is non-transferable
* **WARNING :** You can only have **one locking schedule per address**. It means you cannot lock a share of your NFTE for 1 year and another share for 4 months. Each address may only have 1 locking duration.
* You can extend your locking schedule at any time, and this is how you can maintain the highest level of benefits from the revenue sharing program, but you cannot lock it for more than 2 years at any point.

#### Contracts <a href="#contracts" id="contracts"></a>

Our contracts are forks of Curve’s vote-escrowed (veCRV) contracts, modified slightly by Ribbon Finance. These contracts have been audited extensively and are some of the most used contracts in DeFi. All contracts can also be viewed on our [GitHub](https://github.com/nftearth).\
\
Vote-escrowed NFTE (xNFTE) - Arbitrum:

​Revenue Share Fee Distributor - Arbitrum: ​

#### Implementation Details <a href="#implementation-details" id="implementation-details"></a>

**User voting power**

User voting power $$𝑤𝑖$$ is linearly decreasing since the moment of lock. So does the total voting power 𝑊. In order to avoid periodic check-ins, every time the user deposits, or withdraws, or changes the locktime, we record user’s slope and bias for the linear function $$𝑤𝑖(𝑡)$$ in the public mapping `user_point_history`. We also change slope and bias for the total voting power $$𝑊(𝑡)$$ and record it in `point_history`. In addition, when a user’s lock is scheduled to end, we schedule change of slopes of $$𝑊(𝑡)$$ in the future in `slope_changes`. Every change involves increasing the `epoch` by 1.

\
By implementing the functionality of the revenue share program in this way, we don’t have to iterate over all users to figure out, how much should $$𝑊(𝑡)$$ change by, neither do we require users to check in periodically. However, we limit the end of user locks to times rounded off by whole weeks.

Slopes and biases change both when a user deposits and locks governance tokens, and also when the locktime expires. All the possible expiration times are rounded to **whole weeks** to make number of reads from blockchain proportional to number of missed weeks at most, not number of users (which is potentially large).\
\
For more details and specifications of these mechanisms, please visit the [curve docs](https://curve.readthedocs.io/dao-vecrv.html#querying-balances-locks-and-supply).
