---
id: phragmén
title: P for Phragmén
sidebar_position: 15
---

![P for Phragmén](assets/P.png)

Phragmén is a collection of election mechanisms emphasizing fair representation created by or
inspired by Lars Edvard Phragméns work. In the late 19th century he noticed that the most popular
political party occupied the Swedish parliamentary seats and that minority parties were not
represented. In order to have better voter representation in parliament he designed a method which
would distribute votes across seats fairly. This became known as the Phragmén method, which works
well for elections with multiple winners. Since several methods are associated with Lars Phragmén,
in this post, I will talk about the specific method used in Polkadot called **sequential Phragmén
(seq-Phragmén)**, and the newer optimization that will increase security qualities and improve the
representation of voters called **Phragmms**.

**How seq-Phragmén is used in Polkadot**

Fair representation is important when electing a pool of validators in **Nominated Proof of Stake
(NPoS)**. Or when electing **Council members**. Both of these elections have many voters with
varying stake, many candidates to elect or nominate, and many available seats in either the
validator set or the council. seq-Phragmén has a property called proportional justified
representation(PJR), which ensures that no candidate is over or under-represented; it is a method
that finds a fair distribution of stake across the highest-backed candidates. By sequentially
optimizing the elected set of candidates and the stake distributed across those elected, it gets us
closer to ideals that would ensure high security of the network, better representation of token
holders in elections, as well as decentralization of validators and council members. The algorithm
has two critical roles:

1. **Elect the highest backed candidates**: Make sure that only the candidates with the highest
   backing get elected to the active set of validators or council
2. **Distribute the stake evenly among them**: Make sure all staked DOTs for a given election are as
   evenly distributed across the elected set as possible.

**NPoS validator elections**

For NPoS, the election needs to be designed to maximize security. NPoS nominators stake their DOTs
to elect validators to build blocks. And since a proof-of-stake network's security partially depends
on the amount staked in the system and how decentralized that stake is across the participants,
seq-Phragmén needs to take into account three points and optimize those as much as possible with a
given sensible computation input:

1. **Maximize the total amount at stake.**
   - Meaning elect the most backed validators into the active set.
   - More staked DOTs = higher security.
2. **Maximize the stake behind the minimally staked validator.**
   - Meaning distributing the total stake as evenly as possible among the elected validators.
   - This is an [NP-hard problem](https://en.wikipedia.org/wiki/NP-hardness), meaning it is
     computationally difficult and requires optimization.
3. **Minimize the variance of the stake in the active set.**
   - Meaning the difference in stake between the most backed validator and the least backed
     validator is minimized.
   - Ensures higher security by raising the cost to attack the lowest-backed validator.

Aiming to optimize these properties of the NPoS validator set will increase the security of the
network and the payout that validators and nominators will gain.

:::note NP-hard problems tend to be computationally heavy and tend to require optimizations. When
developing blockchain runtimes, it's essential to ensure computation on-chain is kept to a minimum
or that it has no potential to stall block production. :::

**Council elections**

When it comes to electing Council members, seq-Phragmén is also used. In each election cycle, the
election yields 20 top-backed potential accounts and then picks the top 13 backed to be in the
active Council and 7 to be runner-ups.

:::note

Stake-backed voting might seem un-democratic at first sight, but it is straightforward to game a
system that does not have a stake-backed voting system on a pseudonymous blockchain system. In a
non-stake-backed system where one account has one vote, any entity could create multiple accounts,
give their single vote to the same candidate, and make it look like many voters back them.

:::

**Off-chain Phragmén**

Due to its computationally heavy process, seq-Phragmén is run preferably **off-chain**, and the
result is submitted to the chain via a transaction. This is done by
[off-chain workers(OCW)](https://docs.substrate.io/how-to-guides/v3/ocw/transactions/). And any
validator node by default runs as an off-chain worker. This means that the computation happens on
the validator's machine/hardware and is responsible for the person running the validator; the
computation does not happen on-chain. A validator can turn off the OCW option if they choose to.

**Phragmms**

One of the risks of combating only underrepresentation is that some minorities may well end up being
overrepresented, which is also troublesome for the goal of decentralization. Phragmms, the next
stage of improvements, will enable an election resulting in the most verifiably fair representation
of candidates based on given votes and stake. Though still computationally heavy, the beauty of
Phragmms is its strong verification properties, which allow even an untrusted third party to run the
elections privately and off-chain, and then prove to the network that the corresponding election
results are fair and proportional. This opens up an excellent opportunity for the trustless
computation of elections off-chain.

**Resources**

[Solving the NPoS problem with Phragmén video by Kian Paimani](https://www.youtube.com/watch?v=MjOvVhc1oXw)

[Polkadot Wiki: Sequential Phragmén](https://wiki.polkadot.network/docs/learn-phragmen)

[W3F Research: Overview of NPoS](https://research.web3.foundation/Polkadot/protocols/NPoS/Overview)

[Phragmms research paper](https://arxiv.org/pdf/2004.12990.pdf)
