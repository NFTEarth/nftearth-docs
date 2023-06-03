# xNFTE Revenue Sharing

### Description

NFTEarth is a DAO that seeks to highlight and bring to the masses high impact Ethereum L2 protocols and projects. The DAO treasury receives revenue through LP provisioning, NFT marketplace fees, NFT royalties, and partner projects, and is always looking for new ways to generate income for stakeholders..

25% of fees generated from anything other than NFTE tokens will be converted to ETH each week (if received in a different form of asset) and sent to the Revenue Sharing Vault for stakers to claim. The amount of each staker’s claim is pro-rata to all other stakers in the xNFTE system.&#x20;

### Locking up NFTE

Your total amount of xNFTE depends on 2 inputs: the amount of NFTE you stake, and how long you lock up your NFTE tokens. The longer you lock up your tokens, the higher your proportional share of xNFTE and the larger your percentage claim and voting power. The most you can lock your tokens up for is 12 months. If you lock up 1 NFTE for 12 months, you receive 1 xNFTE. If you lock up 1 NFTE for 12 months, you receive 0.5 xNFTE, and so on. Once your NFTE is locked up, there is no way to unlock it until the lock period has expired. Be certain that you don’t need access to your NFTE before you lock it up!

### Specifications&#x20;

* You can lock up your L2DAO from 4 weeks (= 0.04 xNFTE / NFTE) up to 1 year (= 1 xNFTE / NFTE).
* You can only lock until Thursdays, if you select any other day, it will lock it for the previous Thursday (e.g if you choose to lock until Friday, June 25th it will lock it until Thursday June 24th)
* As you get closer to your unlocking date, **your balance of xNFTE decreases linearly**.
* xNFTE is non-transferable&#x20;
* **WARNING :** You can only have **one locking schedule**. It means you cannot lock a share of your NFTE for 1 year and another for 4 months.&#x20;
* You can extend your locking schedule at any time, but you cannot lock it for more than 2 years since you first locked some NFTE.

<figure><img src="../../.gitbook/assets/Untitled design (98).png" alt=""><figcaption><p>xNFTE</p></figcaption></figure>

### Contracts

Our contracts are forks of the Curve Finance veCRV contracts, modified slightly by Ribbon Finance. These contracts have been audited extensively and are some of the most used contracts in DeFi. All contracts can also be viewed on our [GitHub.](https://github.com/NFTEarth)

**Vote-escrowed NFTE (xNFTE)** - Arbitrum: TBA

**Revenue Share Fee Distributor** - Arbitrum: TBA

### Implementation Details

User voting power $$𝑤𝑖$$ is linearly decreasing since the moment of lock. So does the total voting power 𝑊. In order to avoid periodic check-ins, every time the user deposits, or withdraws, or changes the locktime, we record user’s slope and bias for the linear function $$𝑤𝑖(𝑡)$$ in the public mapping `user_point_history`. We also change slope and bias for the total voting power $$𝑊(𝑡)$$ and record it in `point_history`. In addition, when a user’s lock is scheduled to end, we schedule change of slopes of $$𝑊(𝑡)$$ in the future in `slope_changes`. Every change involves increasing the `epoch` by 1.

This way we don’t have to iterate over all users to figure out, how much should $$𝑊(𝑡)$$ change by, neither we require users to check in periodically. However, we limit the end of user locks to times rounded off by whole weeks.

Slopes and biases change both when a user deposits and locks governance tokens, and when the locktime expires. All the possible expiration times are rounded to whole weeks to make number of reads from blockchain proportional to number of missed weeks at most, not number of users (which is potentially large).

For more details, please visit [Curve Finance Docs](https://curve.readthedocs.io/dao-vecrv.html#querying-balances-locks-and-supply)
