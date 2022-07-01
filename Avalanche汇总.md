# Avalanche Paltform

Avalanche 内置 3 条区块链：交易链（X-Chain）、平台链（P-Chain）和合约链（C-Chain）。所有 3 个区块链均由主网络验证和保护。 Primary Network 是一个特殊的子网，所有自定义子网的所有成员也必须通过至少 2,000 AVAX 成为 Primary Network 的成员。

X-Chain 用于创建资产和交换资产，在整个系统中承担“造血”和“输血”的功能；

C-Chain 是生态中智能合约的集合，是 Avalanche DeFi 生态的载体

P-Chain 产生的成果不会展示在“台前”，作为 Avalanche 上的元数据区块链，P-Chain 负责协调生态中的验证器、追踪活动的子网并且创建新的子网。

[了解“公开叫嚣”以太坊的Avalanche子网：支持自定义，着力GameFi、合规性](https://www.panewslab.com/zh/articledetails/1649924587083808.html)

![Image](https://res.craft.do/user/full/8f8055bd-b4a8-566b-436f-9e0d5edb8a8b/doc/68E82879-08E5-4A6E-AACE-D4AC49624EDC/7914840B-4204-4FD4-A60C-FE39FCCA94E7_2/zn9VxJkcITEnyopUfylah40jY4pSUPX4uEG1CTRPqSkz/Image)

#### 共识

- Avalanche Snow*协议族  [https://tedyin.com/archive/snow-bft-demo/#/snow](https://tedyin.com/archive/snow-bft-demo/#/snow)
- Avalanche 上的交易通过“投票”结果确认，验证者监听网络中的交易，并投票来决定其是否被接受。每个验证者进行投票后，再将所有节点的投票结果进行汇总，这与经典共识协议的机制大体相同。
- Avalanche 投票的不同之处在于，在 Avalanche 中每个验证者彼此独立，没有领导者角色。每个验证者都对一笔交易进行权限完全相同的投票，最终投票的结果由“重复随机采样”决定——即每个节点都将一个事件传播给几个不同的节点进行验证，一旦多轮“重复随机采样”结果保持一致（接受或拒绝），就会生成最终的交易共识，以进行下一步动作。
- 经典共识的泛化，结合中本聪共识
- 不会不断运行，有工作时才会运行

#### 架构

- 子网：子网是一组动态验证器，它们一起工作以达成对一组区块链状态的共识；**每个区块链被一个子网验证，每个子网验证任意多个区块链，一个验证者可以是任意子网的成员，每个子网可以决定谁可以成为它的验证者，并且可以对它的验证者提出某些要求**。Avalanche可以创建和操作任意数量的子网，为了创建或加入子网必须支付以$AVAX计价的费用。
- PoS权益证明防止女巫攻击，节点抵押AVAX可加入子网作为验证者
- 子网支持不同的智能合约，evm、wasm等

#### 治理

$AVAX 原生Token

交易费：由F表示，可被治理。F是一个元组，描述了各种指令和交易的费用，最后，质押时间和金额也是可被治理的。这些参数列表的定义如下。

- Δ：质押数量，以AVAX表示，该值定义了参与系统前需要以债券形式呈现的最小权益数量。
- δmin：节点在系统中质押的最短时间。
- δmax：节点可质押的最长时间。
- ρ：(πΔ, τδmin) -> R：奖励率函数，也可称为挖矿速率。决定了参与者的回报速率，即：给定公开披露的节点依据质押的资金数量、在一段连续的时间窗口内获取的回报。
- F: 手续费标准，一组可治理的费用参数指定了多种交易的成本。

根据金融系统的可预测原则，AVAX的治理是具有**滞后性**的，意味着参数的变更高度依赖最近的变化。每个治理参数有两个限制：**时间和范围；一旦参数被治理交易修改，要立即再次大幅修改它会非常困难。这个难度和值的约束随着时间的推移逐渐放松。**总体来说，这使得系统在短时间内不会发生剧烈的变化，允许用户在短期内安全地预测系统参数，同时长期具有强大的控制和灵活性。

----

#### Staking

- 验证者必须质押的最低金额为 2,000 AVAX
- 委托人必须委托的最低金额为 25 AVAX
- 一个人可以质押资金进行验证的最短时间是 2 周
- 一个人可以质押资金进行验证的最长时间是 1 年
- 一个人可以为委托质押资金的最短时间是 2 周
- 一个人可以为委托质押资金的最长时间为 1 年
- 最低委托费率为2%
- 验证人的最大权重（他们自己的股份 + 委托给他们的股份）是 **300 万 AVAX**和 **验证人质押金额的 5 倍**的最小值。例如：如果您质押 2,000 AVAX 成为验证人，则只能将 8000 AVAX 委托给您的节点总数（不是每个委托人）

质押金额会影响共识过程中的影响力和收益率

#### Slashing

- 无削减惩罚机制

#### Validators

如果验证者在线并且响应超过 80% 的验证期（由大多数验证者衡量，按权益加权），则验证者将获得权益奖励。您的目标应该是让您的验证者 100% 在线并做出响应。

#### Validator Stats

数据大盘

[Avalanche Stats: Validator Health Check](https://stats.avax.network/dashboard/validator-health-check/)

[Avalanche Stats: Staking](https://stats.avax.network/dashboard/staking/)

#### AVASCAN.INFO

staking详细数据指标

[Staking: Validators (1255) \ AVASCAN](https://avascan.info/staking/validators)

**Staking Guide**

[Staking - Avascan Knowledge Base](https://docs.avascan.info/how-to-use-avascan/staking)

#### Delegators 委托人

[How to delegate - Avascan Knowledge Base](https://docs.avascan.info/guide-delegation-avalanche-network/guide-delegation-avax-web-wallet)

----

[一文理解Avalanche共识：设计、演变_腾讯新闻](https://new.qq.com/omn/20200813/20200813A0Q10M00.html?pc)

三种共识协议：

- 经典共识：实用拜占庭容错（PBFT）和HotStuff
- 中本聪共识 Nakamoto Consensus
- Avalanche Snow*协议族

Snowball共识

[Snowball BFT Demo](https://tedyin.com/archive/snow-bft-demo/#/snow)

Avalanche features 3 built-in blockchains: [**Exchange Chain (X-Chain)**](https://docs.avax.network/overview/getting-started/avalanche-platform#exchange-chain-x-chain), [**Platform Chain (P-Chain)**](https://docs.avax.network/overview/getting-started/avalanche-platform#platform-chain-p-chain), and [**Contract Chain (C-Chain**)](https://docs.avax.network/overview/getting-started/avalanche-platform#contract-chain-c-chain). All 3 blockchains are [validated](http://support.avalabs.org/en/articles/4064704-what-is-a-blockchain-validator) and secured by the [**Primary Network**](http://support.avalabs.org/en/articles/4135650-what-is-the-primary-network). The Primary Network is a special [subnet](http://support.avalabs.org/en/articles/4064861-what-is-a-subnetwork-subnet), and all members of all custom subnets must also be a member of the Primary Network by staking at least 2,000 AVAX.

Avalanche 内置 3 条区块链：交易链（X-Chain）、平台链（P-Chain）和合约链（C-Chain）。所有 3 个区块链均由主网络验证和保护。 Primary Network 是一个特殊的子网，所有自定义子网的所有成员也必须通过至少 2,000 AVAX 成为 Primary Network 的成员。

验证者可能是许多子网的成员。

A validator may be a member of many subnets.

Contract Chain (C-Chain)

Platform Chain (P-Chain)[​](https://docs.avax.network/overview/getting-started/avalanche-platform#platform-chain-p-chain)

Exchange Chain (X-Chain)[​](https://docs.avax.network/overview/getting-started/avalanche-platform#exchange-chain-x-chain)

## avax调研

- PoS详细规则
- 奖励机制、金额
   - Staking 金额不仅影响参与者在共识过程中的影响力，而且也影响他们的收益率。
- Slashing：没有削减机制
- 提现冷冻期
   - 最少2周，最多一年
- Validator资格：如下

[What is Staking? | Avalanche Docs](https://docs.avax.network/nodes/validate/staking)

## Validators 验证者

质押奖励就会在质押期限结束时发送到钱包地址

对于验证 Avalanche 上的区块链的节点，必须质押 AVAX

Staking rewards are sent to your wallet address at the end of the staking term **as long as all of these parameters are met**.

```other
- The minimum amount that a validator must stake is 2,000 AVAX
- The minimum amount that a delegator must delegate is 25 AVAX
- The minimum amount of time one can stake funds for validation is 2 weeks
- The maximum amount of time one can stake funds for validation is 1 year
- The minimum amount of time one can stake funds for delegation is 2 weeks
- The maximum amount of time one can stake funds for delegation is 1 year
- The minimum delegation fee rate is 2%
- The maximum weight of a validator (their own stake + stake delegated to them) is the minimum of 3 million AVAX and 5 times the amount the validator staked. For example, if you staked 2,000 AVAX to become a validator, only 8000 AVAX can be delegated to your node total (not per delegator)

验证者必须质押的最低金额为 2,000 AVAX
委托人必须委托的最低金额为 25 AVAX
一个人可以质押资金进行验证的最短时间是 2 周
一个人可以质押资金进行验证的最长时间是 1 年
一个人可以为委托质押资金的最短时间是 2 周
一个人可以为委托质押资金的最长时间为 1 年
最低委托费率为2%
验证人的最大权重（他们自己的股份 + 委托给他们的股份）是 300 万 AVAX 的最小值，是验证人质押金额的 5 倍。例如，如果您质押 2,000 AVAX 成为验证人，则只能将 8000 AVAX 委托给您的节点总数（不是每个委托人）
```

A validator will receive a staking reward if they are online and response for more than 80% of their validation period, as measured by a majority of validators, weighted by stake. **You should aim for your validator be online and responsive 100% of the time.**

如果验证者在线并且响应超过 80% 的验证期（由大多数验证者衡量，按权益加权），则验证者将获得权益奖励。您的目标应该是让您的验证者 100% 在线并做出响应。

#### slashing削减惩罚机制

Unlike other systems that also propose a PoS mechanism, $AVAX does not make usage of slashing, and therefore all stake is returned when the staking period expires. This prevents unwanted scenarios such asa client software or hardware failure leading to a loss of coins. This dovetails with our design philosophy of building predictable technology: the staked tokens are not at risk, even in the presence of software or hardware flaws

与其他也提出 PoS 机制的系统不同，$AVAX 不使用 slashing，因此当质押期到期时，所有质押都会返还。这可以防止不必要的情况，例如导致硬币丢失的客户端软件或硬件故障。这与我们构建可预测技术的设计理念相吻合：即使存在软件或硬件缺陷，质押的代币也不会面临风险

When you add a node to the validator set, you specify:

- Your node’s ID
- When you want to start and stop validating
- How many AVAX you are staking
- The address to send any rewards to
- Your delegation fee rate (see below)

**Note** that once you issue the transaction to add a node as a validator, there is no way to change the parameters. **You can’t remove your stake early or change the stake amount, node ID, or reward address.**

The only secret that you need on your validating node is its Staking Key, the TLS key that determines your node’s ID. The first time you start a node, the Staking Key is created and put in `$HOME/.avalanchego/staking/staker.key`. You should back up this file (and `staker.crt`) somewhere secure. Losing your Staking Key could jeopardize your validation reward, as your node will have a new ID.

[Monitor an Avalanche Node | Avalanche Docs](https://docs.avax.network/nodes/maintain/setting-up-node-monitoring)

## Delegators 委托者

A delegator is a token holder, who wants to participate in staking, but chooses to trust an existing validating node through delegation.

When you delegate stake to a validator, you specify:

- The ID of the node you’re delegating to
- When you want to start/stop delegating stake (must be while the validator is validating)
- How many AVAX you are staking
- The address to send any rewards to

