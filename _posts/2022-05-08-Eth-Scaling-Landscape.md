---
layout: post
title: Ethereum Scaling Landscape
description: Everything you always wanted to know about Ethereum scaling but were afraid to ask.
summary: From L2, to side-chains, to on-chain scaling, everything you always wanted to ask about Eth scaling but were afraid to ask!
comments: true
tags: [ETH, L2, Scaling]
---

With all the momentum around L2s and ETH scaling, here’s a little mindmap and a short post to help make sense of it. Let’s start with scaling. Why do we need it?

![L2 Scaling Overview](/assets/images/eth-scaling/L2ScalingOverview.png)

## Blockchain Trilemma
To understand the need for scaling solutions, we need to take a step back and talk about the Blockchain Trilemma, a widely held belief that decentralized networks can only provide two of three benefits out of decentralization, security, and scalability. You can learn more about it here.

Blockchains like Solana sacrifice decentralization for the other two. This lets Solana process 50k transactions per second (TPS) vs ETH’s 15 TPS, but it comes at the expense of decentralization. How will ETH solve this problem? There are multiple scaling solutions that will likely emerge as the execution layer of the ecosystem, while Ethereum’s mainnet will remain being the settlement layer.

## On-chain Scaling
You can think of solutions for ETH scaling in two broad categories: On-chain and off-chain. On-chain solutions require changes to Ethereum’s protocol. The main focus in this respect is sharding, an idea that comes from database architecture, and simply means partitioning a database so you can spread the load among the different parts.

In Ethereum, sharding will create new chains (“shards”) to reduce the network’s congestion and increase TPS. Furthermore, this will lighten the load for each validator as they will no longer have to process the entirety of all transactions across the network. Sharding s expected to come in 2023, after the much expected “merge” happening in 2022.

So do we have to wait until then to pay lower gas fees? Fortunately not. First, sharding is not expected to be enough to solve all of ETH’s scaling issues. Second, there are other scaling solutions that don’t require changes to Ethereum’s protocol as they are “off-chain”. We can categorize these into “New Chains” and “L2s”. Let’s start with “New Chains”

## Off-chain Scaling - New Chains

### Sidechains 

Within “New Chains,” there are 3 approaches: sidechains, plasma chains, and validium.  Sidechains are independent, EVM-compatible blockchains that run parallel to mainnet. While they are compatible with Ethereum, they run under their own chosen rules of consensus and block parameters. 

Polygon, SKale, and Gnosis Chain are all examples of sidechains. Their benefit is that they’ve been around for a while and are a known technology. Their downside is that they’re less decentralized, use a separate consensus mechanism, are not secured by the L1, so a quorum of validators could commit fraud. Therefore, they require some level of trust.

### Plasma

Plasma chains are separate blockchains anchored to the main Ethereum chain that use fraud proofs to arbitrate disputes. These chains are smaller versions of Ethereum and use Merkle Trees to enable a endless stack of these to offload bandwdidth from parent chains, but each child chain has its own block validation mechanism. Their advantage is that they have high throughput and a low cost per transaction. However, they don’t support general use cases just basic token transfers, swaps, etc. Furthermore, you need to periodically monitor the network to ensure the security of your funds and withdrawals are delayed to allow for challenges.

### Validium

Validium uses validity proofs like ZK-Rollups, but the data isn’t stored on the main L1. This can lead to 10K TPS per validium chain and you can run multiple in parallel. The advantage is you have immediate withdrawals and are therefore more efficient as they don’t require to lock up capital and are less vulnerable to certain economic attacks than fraud-proof based mechanisms. The disadvantage is they have limited support for general smart contracts, require high computational power to generate ZK proofs (not effective for low-throughput applications), require off-chain data to be available at all times in order to generate a proof, and have slower subjective finality (although a faster final finality).

The arrow between Validium and zkRollups on the mind map is because the mechanisms are very similar. The main difference is that data-availability in a zkRollup is on-chain, while Validium keeps it off-chain.

## Off-chain Scaling - L2

The other large category of off-chain scaling solutions are L2. They get their names because they build on top of the L1 (Eth) and so inherit all its properties. The advantage of this is that by using the L2, you get the L1’s security and decentralization. L2s are a whole world on themselves, but they come in two flavors. Rollups and channels. Since rollups are all the rage right now and the forefront of innovation, lets start with channels.

### Channels

Channels require participants to lock an amount of ethereum into a multisig contract (a contract that requires the signatures of multiple private keys to execute). Locking the state opens up the channel so participants can transact quickly off the chain, and when the transactions are finished, an on-chain transaction is submitted to settle and unlock the state. There are two types: state and payment channels.

State channels work through a multi-sig smart contract on the L1 that governs transactions between parties. When the parties start their interaction, they open the channel. All their interactions happen off-chain and create a “nonce”. When the transactions are done, the parties submit the final state and thus only pay a single transaction fee. Payment channels are a simplified version of state channels limited to payments. 

The advantages of channels are they are instantaneous, enable extremelyhigh throughout and have the lowest cost of transaction. Their disadvantages are that they are costly to set up (so not good for one-off transactions), they need to periodically watch the network or delineate this responsibility, you have to lockup funds in order to use them, and don’t support open participation.

### Rollups

Lastly in our mindmap we have rollups. They fall into 2 categories - optimistic and zkrollups. The main difference between the two is the type of proof they use. Optimistic rollups assume transactions are true, but have a period in which you can challenge them by submitting a fraud proof. ZKRollups rely on zero knowledge validity proofs, which if verified by an L1 smart contract, you can be sure that the state root is a result of executing a valid transaction test.

The main difference between optimistic and zkrollups is that the latter don’t rely on a challenging mechanism, but immediately guarantees the final certainty of the chain. For end users this means that they need to wait for a period to withdraw their ETH if using optimistic rollups. On the other hand, ZKrollups are a newer cryptographic primitive, so we don’t fully understand them yet. The difference between the ZKrollups on the mindmap is the ZK Proof algorithm they use (Loopring and Hermez use Groth16, ZKsync and Aztec use Plonk, and Starkex uses Stark). 

Arbitrum and Optimism are the two largest optimistic rollups. As of this writing they have $3.31B and $611M TVL. There’s a lot that could be written about these projects. For example, Arbitrum recently launched AnyTrust chains that are faster than regular optimistic rollups as well as Nitro, a new prover that does Arbitrum’s interactive fraud proofs over WebAssembly (WASM) code.  Optimism is also making waves, with the recent launch of their own token with an interesting/innovative bicameral governance model that will also unlock retroactive public goods funding. 

Up to date, L2s have $5.86B TVL. Compared to ETH’s $300Bn market cap, this is still very early for L2s. Everyone is expecting more L2s to emmit their own tokens and continue to innovate to gain market share, so I’m excited to see what the L2 summer has in stock for us this year. If you want to gain some of the upside, go and try out the different L2s. The more activity you have on chain, the more likely it is you’ll receive some of the airdrops. But most importantly, the more you use them, the less gas you’ll have to pay and the faster Ethereum will be able to scale!

If you want to keep up to date, check out https://l2beat.com/ for a real-time leaderboard of L2s and https://l2fees.info/ for a real time view of fees. To learn more, I highly recommend ethereum foundation’s own documentation on scaling from where I got a lot of the information in this thread. https://ethereum.org/en/developers/docs/scaling/. As well as finematics videos https://youtu.be/BgCgauWVTs0 and https://youtu.be/7pWxCklcNsU.

