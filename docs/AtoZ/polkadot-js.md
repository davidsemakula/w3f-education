---
id: polkadot-js
title: J for Polkadot JS
sidebar_position: 11
---

![J for Polkadot JS](assets/J.png)

Polkadot.js is a collection of tools that interfaces with the Polkadot blockchain in very granular
ways. Polkadot.js as a term has multiple moving parts that are worth mentioning:

1. **[Polkadot.js UI](https://polkadot.js.org/)**: This is the hosted application that loads when
   you navigate to your browser and click apps wallet (hosted). This is also sometimes called the
   “Polkadot-JS UI”.
2. **[Polkadot.js API](https://github.com/polkadot-js/api)**: This is the JavaScript API, a reusable
   library to allow programs to interface with the functionality of Polkadot.
3. **[Polkadot.js Extension](https://polkadot.js.org/extension/)**: This Chrome extension allows you
   to manage your accounts and sign transactions. Note that all it does is sign messages; it has
   limited functionality compared to full-featured wallets and cannot connect to the Polkadot
   network.
4. **[Polkadot.js codebase](https://github.com/polkadot-js/)**: The codebase contains all the code
   repositories required to have the suite of tools working. You can navigate to the codebase here.
5. **[Polkadot.js Phishing List](https://polkadot.js.org/phishing/)**: The Phishing List website is
   a community-driven curation of a list of less-than-honest operators. This list of URLs and
   addresses is constantly updated, and the polkdot.js extension uses it as a source to warn you
   when you navigate to a URL included in the list and blocks the addresses from the apps UI. Users
   can also contribute suspicious sites and addresses if they come across them.

## Polkadot-JS UI

This post will focus on the UI, a powerful web application with granular functionality support when
interacting with the Polkadot blockchain. It is not just a wallet; it has more abilities than
creating accounts or sending and receiving transactions.

## Abilities

Among other things, it also allows us to:

1. Participate in staking
2. Take part in governance
3. Contribute to parachain crowdloans
4. Run Parachain auctions
5. Query chain metadata
6. Query on-chain data using RPC calls

Essentially, the UI allows you to perform all functionalities that a user can do on either the relay
chain or any parachain (although the user interface may not be aligned precisely with the
functionality of any individual parachain). If you’re building a Substrate based blockchain, you can
utilize the Polkadot.js UI to test your code's functionality.

Interacting with the Polkadot JS UI involves either querying on-chain data or issuing an extrinsic.
Let's talk about what that means exactly.

## Querying On-chain Data

To populate the UI, the web application queries the Polkadot.js API. The API then queries a Polkadot
node and uses JavaScript to return information that the UI will display on the screen. You can
choose which node to connect to by changing it in the upper-left-hand corner of the screen.

## Issuing an Extrinsic

Extrinsics are information from outside the chain and are included in a block. Extrinsics can be one
of three types: **inherents**, **signed** and **unsigned transactions**. Most extrinsics made from
the Polkadot JS UI will be signed transactions. **Inherits** are non-signed and non-gossiped pieces
of information included in blocks by the block author, such as timestamps, which are “true” because
a sufficient number of validators have agreed about validity. **Unsigned transactions** are
information that does not require a signature but will require some spam prevention. **Signed
transactions** are issued by the originator account of a transaction that contains a signature of
that account, which will be subject to a fee to have it included on the chain.

## Considerations

Concerns have been raised by the community about the complexity of Polkadot-JS UI . However,
Polkadot.js UI aims to support as much functionality as the relay chain requires of its users. Every
time there is a runtime update(which can be quite often), a potential change needs to be made on the
Polkadot.js codebase. For example, with most 3rd party wallets, when there are runtime updates, they
usually need to add support. Polkadot.js UI is focused less on a user-friendly UI but rather to
support the Polkadot runtime without any bugs.

For more user-friendly but more straightforward wallet implementations, check out the wiki page
where we list
[Parity-developed and Treasury-funded wallet projects](https://wiki.polkadot.network/docs/build-wallets#treasury-funded-wallets)

Please take a look at some of the educational content we have created to learn more about
Polkadot.js

[Introduction to Polkadot.js](https://www.youtube.com/watch?v=4EQqwGFV1D8)

[Create an account using Polkadot.js](https://www.youtube.com/watch?v=sy7lvAqyzkY)
