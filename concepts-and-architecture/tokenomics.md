# Tokenomics

### Aramid Tokens

**AramidUSD**&#x20;

Aramid USD is the utility token of the bridge. Initially AramidUSD presale is used to onboard investors and bootstrap liquidity on selected networks. Users earn AramidUSD tokens by farming LP tokens as reward. Further AramidUSD token can be staked in protocol staking pool to get voting escrowed Aramid token and be a part of protocol governance.&#x20;

**VeAramid**&#x20;

Voting escrowed Aramid token (VeAramid) is the governance token of protocol. Voting power is distributed among stakeholders of the protocol in form VeAramid token. Emission of VeAramid token is dependent on the amount of AramidUSD tokens staked in the staking pool and time period for which they are staked.

_Voting Power ∝ Amount of Tokens staked in staking pool_

To ensure that long term stakeholders of the protocol get more say in protocol governance a time weighted locking mechanism will be used to issue VeAramid tokens such that people with tokens locked for a greater amount of time are rewarded more. Since VeAramid tokens will represent voting power in the protocol, governance decisions will be at the discretion of true stakeholders of the system who are loyal to the network.

_Voting Power ∝ Time period of staking_

**LP Tokens**&#x20;

Users who provide liquidity on a chain in the protocol liquidity pool will get LP Tokens as a representation of their share in the pool. Rewards earned by a user against his provided liquidity in the pool could be claimed using these LP Tokens. Users can earn additional rewards by farming these LP Tokens in protocol Yield Farming pool. Yield Farming Rewards are distributed among users in the AramidUSD token. Users can further stake these earned AramidUSD tokens in a staking pool to become part of protocol governance.

### Mechanism Design

**Workflow**

<mark style="color:orange;">**add diagram**</mark>

* Liquidity provider, provides liquidity on Aramid bridge&#x20;
* It will be utilized to enable bridging for users&#x20;
* Bridging fee earned is divided in three pools&#x20;
* Protocol earned bridging fee is distributed among liquidity providers, reward pool and for buy backs and burns of Aramid token

**Agents of the system**

**Users**&#x20;

* Users no longer need to swap out undesirable synthetics on the destination chain or have a scenario where a transfer fails due to state change&#x20;
* They can operate their assets across chain in native currencies of different blockchains without their trust dependence on any central authority&#x20;

**Liquidity Providers**&#x20;

* LPs will be able to stake into a single-sided asset pool with no impermanent loss and collect fees from all incoming transfers regardless of their source chain&#x20;
* Instead of fractured liquidity which is not efficient use of liquidity, capital efficiency is achieved by using liquidity available on one chain across multiple chains&#x20;
* A bridge could also be designed using pools of native assets with unified liquidity, meaning a single USDT pool on Chain A and additional pools on Chains B-F. All chains share access to each other’s liquidity resulting in orders of magnitude greater capital efficiency vs. pairwise pools&#x20;

**Protocol**&#x20;

* Simultaneously have deep pools of native assets tied to all chains, creating orders of magnitude greater capital efficiency&#x20;
* Uses received transaction proofs alongwith block headers and validates the commitment of transaction&#x20;
* A transaction is validated if the block header provided by the Oracle and the transaction proof provided by the Relayer are both valid.&#x20;
* Merkle tree validation&#x20;

**Message Relayers**&#x20;

* Brings proof of a specific transaction&#x20;
* Stores proof of transaction off chain&#x20;
* Relayer must be independent from oracle&#x20;
* Initially 20 trusted relayers provided by Aramid protocol will perform this function &#x20;
* Later users can implement their own relayer service&#x20;

**DON**&#x20;

* Third party service&#x20;
* Chain Link&#x20;
* To read block header from one chain and send it to another chain

### Operational Mechanics

* Users wants to transfer his Token X from source chain A to destination chain B&#x20;
* Liquidity is available on Chain B provided by Liquidity providers in token X’s liquidity pool&#x20;
* Assets are added in liquidity pool on source chain A&#x20;
* Assets are transferred to user on destination chain B using token X’s liquidity

<mark style="color:orange;">**add diagram**</mark>

### **Governance Model**

**G**overnance is vital to the decentralization and autonomy of the protocol. Governance determines all network and incentives matters, including protocol development, integrations, tokenomics, and the distribution of mining rewards to liquidity providers Voting escrowed Aramid token is a unit to measure the voting power. VeAramid is issued when a user locks/stakes his tokens in protocol staking pool. Amount of VeAramid tokens issued to the user is the amount/time weighted. Greater the time of lock, greater will be the voting power thus it enables long term Community-led initiatives, including grants to contributors. Instead of voting with token amount a, in AramidUSD tokens are lockable in a VotingEscrow for a selectable locktime T where Tmin < T< Tmax, and Tmax = 365 days, Tmin = 7 days. After locking, the time left to unlock is Tu ≤ T.&#x20;

The voting weight is equal to:

<figure><img src="https://lh6.googleusercontent.com/y2dlBboTErqXOISSCuL8f2QUfKzJoQtVmnkmwHi1sN1Se_sq4GLiBm7pdEykuV5o1qvps6_xMiGGl55b-5OZj0zkkQJK7r4N0yG30G-T1QNdMSJE6K9dOnmGx0NJiq3ElM-e_dU2l-LuBnFr9C9icDuv9bMSXcinQy5MzzZZ5DFwG6cYVo6HnLGf5Q" alt=""><figcaption></figcaption></figure>

Where Su is the amount of tokens staked by the user in the staking pool, Tu is the remaining time of staking period, Tmax is maximum allowable time of staking.  In other words, the vote is both amount- and time-weighted, where the time counted is how long the tokens cannot be moved in future

### **DAO Mechanics**

Proposal is submitted in the DAO community discussion forum before proceeding to the snapshot voting process. Community can propose any changes in the proposal through their opinion. After making changes suggested by the community, the proposal is open to the voting for a period of 36 hours. Quorum threshold for any proposal is 10% which means at least 10% of the voting power should vote in favor or against the proposal in order to further process it. If a proposal after completion of the voting process gets a support majority threshold of 65% it will be implemented. Aramid DAO will be responsible for the following**:**

* Parameter Changes (Emissions, Fee structure, Reward distribution, etc.)&#x20;
* Partnerships with other protocols&#x20;
* Marketing & communication initiatives&#x20;
* Day to day operations and maintenance of the protocol&#x20;
* Listing of new tokens

### Framework for Listing of new tokens

New tokens can become part of Aramid bridge by the self listing platform of Aramid. Process of listing new tokens is approved by DAO and that token owner has to provide liquidity on connected chains.&#x20;

* Approval of DAO to list new tokens
* &#x20;Provide the necessary liquidity on each of the connected chains for the Aramid bridge

### Economic Model

#### **Token Utility**&#x20;

* Used to participate in protocol Governance&#x20;
* Staking token&#x20;
  * Stake Aramid tokens to get voting escrow tokens&#x20;
  * Longer the period of staking larger the amount of voting escrowed tokens the user will receive&#x20;
* Liquidity provisioning token&#x20;
* Reward Token

#### Bridging Fee Structure Model

**Fee Tiers**&#x20;

There are two different fee tiers of Aramid Bridge Protocol

* &#x20;For regular and self listed tokens 0.09%&#x20;
* For stablecoins and Aramid USD token 0.05%

**Bridging Fee Distribution**&#x20;

Bridging fee is distributed among stakeholders based on pro rata distribution. Major portion of the fee goes to liquidity providers who provided the liquidity in bridged token pool. Fee is distributed in liquidity providers on the basis of their share in said pool. A portion of bridging fee is given to protocol treasury which is further used to Buyback and burn tokens to keep supply of AramidUSD token in control. Users who have staked their token in a staking pool also earn a portion of the bridging fee on each transaction.&#x20;

* Liquidity Mining rewards - 50%&#x20;
* Protocol Treasury - 30%&#x20;
* Aramid Lab (founding team) - 10%&#x20;
* Buybacks and Burns - 20%&#x20;
* VeAramid Token Holders - 20%

<mark style="color:orange;">**add diagram**</mark>

**Emissions - Reward Pool Distribution**

**Liquidity Mining Rewards**&#x20;

Liquidity providers can earn liquidity mining rewards by providing liquidity in a token’s liquidity pool. Liquidity provider’s share in liquidity pool is calculated by following formula;

<figure><img src="https://lh3.googleusercontent.com/WzYf5GRi6HlaXu5feYPFc6DjLYkDpkjBYDHEPiL__oiVWXf4vY9f8oViGpsyITfrLHPUkj4HJUrLaPqQYQZSZ_FbJ91_b1DIOLOWHY2LzlVCfN6R4-q8SkjIu92AsS-oFtY3wl78lKhgMX3S3dGeJxerNQ3aJ-Bqck4bNXJLAmxlZtJpZwRMn_YypA" alt=""><figcaption></figcaption></figure>

Where Lu is the user's liquidity provided in the liquidity pool and Lt is the total amount of liquidity in the pool. \ <mark style="color:orange;">****</mark>Liquidity mining rewards of users are 50% of the bridging fee generated by that particular liquidity pool.

<figure><img src="https://lh4.googleusercontent.com/2TCSyiqY8YnLHOFWKIZJ2XorQSU_1-F3_pQe7Oet2Wk6bpmRjOEVlpYSuvN8m6j2sZgtCOvKBlJppj4I0QTcA62ylPPupukLwxT6SHwXUMD7KDQuwdN073jqNwz3sCI30CJLC4MkLgMbEYWTu6I-OTuRQMCdJrHIKr5OZPtb_NEDPVBTvznzePYcyQ" alt=""><figcaption></figcaption></figure>

**Yield Farming Rewards**&#x20;

Token emissions are used as an incentive mechanism to attract liquidity providers. Liquidity providers apart from their reward from bridging fee will earn yield farming rewards in form of emissions. These emissions are directed on different liquidity pools as per following formula;

<figure><img src="https://lh6.googleusercontent.com/AHJcqe4x131vT7_iX9d46oJKouYaMJDMFP706jN9ITC508rKEwME1eEZnbf9dDM2A8OQ-BPE0eMFGBs4qyUf2yAgzqqAX-2iXDwdb6k5asm6Uia86HYBMm_bI2o3evIoBdWQClb41z9WWJHrAhjQRNt-uNl3Phs_LUUTCQg17HaY8mb7H1W1NQkWfg" alt=""><figcaption></figcaption></figure>

* LPs can Farm their LP tokens to earn farming rewards in AramidUSD token&#x20;
* They can stake these Aramid tokens to get VeAramid tokens and become a part of protocol governance

**Staking rewards**

Users who stake their tokens in Aramid staking pool will earn rewards in AramidUSD tokens

<figure><img src="https://lh5.googleusercontent.com/vQ0aqmVG3Tr9I5lWLrVWRAYUZgnEwfSqgb_9KYKEWxYm6VA09pyz5Tn0dt-5WOTz4sAYu2rZSxBgGG6_D445jFiNEU1cAsO6OTetv7MMBQE6b_iVK8h03Ooi0nf9vJ50-Pfgd4tOAMuOS0ATk_VqTZ2xFoOyR9vYoUK2LkhYNnnNNUQ6uHQhzrkEFA" alt=""><figcaption></figcaption></figure>

**Relayer rewards**

Message relayers are incentivized to participate in network operations and earn rewards.

<figure><img src="https://lh5.googleusercontent.com/rd8e_q_IPI1P59JhTLslYNnh4EGzNyQp7aqsr6CXrmzTYXeZraoogghEpM9nMbv6j-i0fAYjLW1HPLTCVp_nwiHLsbi--trlmLsPRPEVEKAuxAdbPhY0rNmMHtuItKYGGKDfhiTwg8SsIhlzIsXOlitIUWvkEx8DziG0cbJ4c2eL3jiKa5MvesdDZw" alt=""><figcaption></figcaption></figure>

### **Token Vesting Schedule**

Total Supply: 1 Billion&#x20;

Token Allocation:

* 15% Presale&#x20;
* 20% Aramid Lab (team)&#x20;
* 10% Investors&#x20;
* 30% Community&#x20;
* 25% Emissions (Farming Rewards, Relayers)&#x20;

Initial Supply&#x20;

Unlock Schedule:

* 15% tokens pre sale to provide liquidity across different networks&#x20;
* 20% are dedicated for Aramid Team Linear unlock 7-24 months&#x20;
* 10% Investors Linear unlock from 1-18 months&#x20;
* 30% community to develop and grow protocol (Grants)&#x20;
  * Unlock 10% at launch&#x20;
  * Unlock 10% after 12 months&#x20;
  * Unlock 10% after 18 months&#x20;
* 25% Emissions - Yield Farming Rewards&#x20;
  * Unlocked as per requirement&#x20;
  * 0.12\*Fee Generated by All pools daily

<mark style="color:orange;">**add diagrams**</mark>
