---
description: >-
  The NFTEarth Raffle is an onchain game powered by NFTEarth and Chainlink VRF,
  live on Arbitrum layer2 scaling network.
---

# 🎁 Raffle

## NFTEarth Raffles Overview

### 🎟️ NFTEarth Raffles, Explained[​](https://docs.looksrare.org/developers/raffle/raffle-overview#%EF%B8%8F-looksrare-raffles-explained) <a href="#looksrare-raffles-explained" id="looksrare-raffles-explained"></a>

The NFTEarth Raffles system is a decentralized application built on the Ethereum blockchain, empowering users to create, manage and participate in transparent, on-chain raffles. Winners are chosen through a **provabably fair**, trustless mechanism — built with [Chainlink's Verifiable Random Function (VRF)](https://docs.chain.link/vrf/v2/introduction). Jump to [How are winners selected](https://docs.looksrare.org/developers/raffle/raffle-overview#How-are-winners-selected) for more information on this.

Raffles can be hosted either by the NFTEarth team, or by users. Both can be viewed and interacted with via [nftearth.exchange](https://nftearth.exchange), but anyone is free to spin up their own user interface anywhere else.

The system is designed to handle a wide range of tokens as prizes:

* Native **ETH**
* Fungible tokens (**ERC20**)
* Non-fungible tokens (**ERC721**)
* Semi-fungible tokens (**ERC1155**)

NOTE

At present, Community Raffles (i.e., those created by users) only support ERC-721 NFTs. However, this will change in future iterations.

### Audit Report and Security Assurance[​](https://docs.looksrare.org/developers/raffle/raffle-overview#audit-report-and-security-assurance) <a href="#audit-report-and-security-assurance" id="audit-report-and-security-assurance"></a>

At LooksRare security is a top priority. The raffle smart contract has been rigorously audited by a reputable third-party auditor to ensure the highest level of safety and reliability. The audit assess the contract for potential vulnerabilities, and compliance with best practices in the blockchain industry.

We are committed to maintaining the highest security standards and to continuously improve our smart contract infrastructure responsibly. Below the audits reports for the LooksRare Raffle contract, of which the NFTEarth Raffle is a fork of.

#### PeckShield[​](https://docs.looksrare.org/developers/raffle/raffle-overview#peckshield) <a href="#peckshield" id="peckshield"></a>

**Audit Report Raffle V2:**

> [https://github.com/peckshield/publications/tree/master/audit\_reports/PeckShield-Audit-Report-RaffleV1-v1.0.pdf](https://github.com/peckshield/publications/tree/master/audit\_reports/PeckShield-Audit-Report-RaffleV2-v1.0.pdf)

**Audit Report Raffle V1:**

> [https://github.com/peckshield/publications/tree/master/audit\_reports/PeckShield-Audit-Report-Raffle-v1.0.pdf](https://github.com/peckshield/publications/tree/master/audit\_reports/PeckShield-Audit-Report-Raffle-v1.0.pdf)

### How to create and start a raffle[​](https://docs.looksrare.org/developers/raffle/raffle-overview#how-to-create-and-start-a-raffle) <a href="#how-to-create-and-start-a-raffle" id="how-to-create-and-start-a-raffle"></a>

A raffle can be created by anyone via the Raffle smart contract by calling the `createRaffle` function.

When creating a raffle you can define multiple parameters like the cutoff time, the minimum number of entries required, the maximum number of entries per participant, the prizes and pricing options.

Before creating a raffle ensure all the necessary approvals to the Transfer Manager are sorted. The prizes will be transferred to the contract at creation.

### How are winners selected?[​](https://docs.looksrare.org/developers/raffle/raffle-overview#how-are-winners-selected) <a href="#how-are-winners-selected" id="how-are-winners-selected"></a>

Once a raffle has reached the minimum amount of entries, the system will send a request to Chainlink VRF requesting a provably fair and verifiable random number. For each request, Chainlink VRF generates one or more random values and cryptographic proof of how those values were determined.

The proof is published and verified on-chain. This process ensures that results cannot be tampered with or manipulated by any single entity including oracle operators, validators, users, or smart contract developers.

**Methodology for Selecting Winners**

Let's take an example where we have a total of 106 winners - one tier 0 prize, five tier 1 prizes, and one hundred tier 2 prizes.

1. We initiate the process by generating a random number using Chainlink's VRF.
2. This random number is then utilized to select the first winner, who receives the tier 0 prize.
3. To maintain randomness for subsequent selections, we then hash the initial random number using the `keccak256` function, producing a new random number.
4. The second winner is then chosen using this new random number, and they are awarded the tier 1 prize.
5. In an event where a selected entry has already won, then the seed is rehashed instead to find the next winning entry.
6. This process is repeated for each remaining prize, moving from lower to higher tiers (with lower tiers being more valuable), until all the prizes have been distributed.

### How to cancel a raffle[​](https://docs.looksrare.org/developers/raffle/raffle-overview#how-to-cancel-a-raffle) <a href="#how-to-cancel-a-raffle" id="how-to-cancel-a-raffle"></a>

A raffle can be canceled by if the minimum number of entries required for the raffle to be successful (`minimumEntries`) is not reached by the cutoff time (`cutoffTime`).

When a raffle is canceled, the owner can withdraw the prizes, while participants can request refunds for their entries.

Additionally, the contract owner has the ability to cancel a raffle in case a Chainlink VRF request (initiated during the raffle drawing process) gets stuck for more than a day.

Typically, a Chainlink VRF request takes only a few minutes, depending on network conditions. This provision serves as an extra safeguard.

\


> [https://github.com/peckshield/publications/tree/master/audit\_reports/PeckShield-Audit-Report-LooksRare-YOLO-v1.0.pdf](https://github.com/peckshield/publications/tree/master/audit\_reports/PeckShield-Audit-Report-LooksRare-YOLO-v1.0.pdf)
