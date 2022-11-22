# EIP-4337 Account Abstraction - Bundler implementation in Rust

*Account Abstraction has for a long time been a dream of the Ethereum developer community.* - **Vitalik Buterin**

Implementation of **EIP-4337 (Account Abstraction) Bundler in Rust**.

## Motivation

[**Account abstraction (AA)**](https://medium.com/infinitism/erc-4337-account-abstraction-without-ethereum-protocol-changes-d75c9d94dc4a) is one of the topics that has been in the air for quite a long time in the Ethereum community. While there have been several proposals for AA over the past years, most of them required core protocol changes (consensus/execution layer), making them complex and hard to implement alongside other protocol changes (transition to proof of stake, danksharding, PBS ...). The latter is one of the main reasons that the most traction today is getting **[EIP-4337: Account Abstraction using alt mempool](https://eips.ethereum.org/EIPS/eip-4337)**. EIP-4337 introduces a separate mempool for operations done by AA wallets and a new entity called bundler, which combines users' operations into the standard transaction. AA can be implemented and applied using this design without any protocol changes and, in the later stages (The Splurge), integrated more tightly into the protocol.

Similar to client diversity on the consensus and execution layer, diversity and several implementations of bundlers will make the AA world more healthy and secure. Some bundler implementations already exist ([JavaScript](https://github.com/eth-infinitism/bundler), [TypeScript](https://github.com/web3well/bls-wallet), [C#](https://github.com/NethermindEth/nethermind/tree/master/src/Nethermind/Nethermind.AccountAbstraction/Bundler), [Python](https://github.com/candidelabs/Candide-bundler-and-paymaster-RPC), [Go](https://github.com/stackup-wallet/stackup-bundler/)), either as standalone programs or as part of the execution clients ([Nethermind](https://github.com/NethermindEth/nethermind/)). Still, there is none in Rust, which is becoming one (if not the most) adopted programming language in the Ethereum ecosystem community on the core protocol level. Thus the implementation would benefit the **Ethereum/AA ecosystem**.

## Project description

The project goals can be composed into two groups: main and long-term.

This project's primary and core goals are to implement the complete bundler for EIP-4337 AA as a standalone entity that can work alongside any execution client (with communication taking place over gRPC). The main components thus include standardized JSON-RPC API, p2p user operation pool, and core bundling of user operations. Therefore, this project aims to implement a bundler in Rust, help with bundler specs currently in the works, and pass the test suite that the **[eth-infinitism](https://github.com/eth-infinitism/)** is developing.

On the other hand, I will pursue several long-term and more open-ended goals at the end of the fellowship (if some time is left) or after its end. One of these goals is to integrate it into the **[Akula](https://akula.app/)** execution client written in Rust, which will probably lead to several adjustments to ensure correct integration in its main codebase. Other such plans include support for L2s and other more advanced functions of the AA.

## Specification

You can find the complete specification and architecture **[here](https://hackmd.io/@Vid201/aa-bundler-rust)** (the document will be updated on an ongoing basis).

The specification for EIP-4337 (WIP) is available **[here](https://github.com/eth-infinitism/account-abstraction/blob/develop/eip/EIPS/eip-4337.md)**.

The specification for EIP-4337 (latest stable) is available **[here](https://eips.ethereum.org/EIPS/eip-4337)**.

## Roadmap

- JSON-RPC API: 2 weeks.
    - Implement all JSON-RPC API endpoints and necessary logic.
- User operation pool: 5 weeks.
    - First, implement a standalone mempool with gRPC endpoints and all the necessary logic, such as simulation and validation of user operations.
    - Work on p2p mempool and connect with other bundlers (this requires p2p connections to other clients - will look into reusing Akula p2p interfaces and code).
- Bundler: 3 weeks.
    - Implement all logic for bundling - simulation, signature aggregation, bundle construction, and propagating bundles as transactions to the txpool.
    - First, start with public txpool, then add Flasbots Protect (or send directly to the block producer over gRPC).
- Others: 1 week (and later).
    - Research and sketch out necessary work to prototype integration into Akula.
    - Other advanced features.

**Total time estimated:** ~11 weeks.

**Note:** work on parts of different components can end up being overlapped due to testing between the development.

## Possible challenges

1. Figuring out all implementation details, constraints, and specifications of EIP-4337 bundling - at the moment, there are no official bundler specs (yet), so I will look deeply into several existing implementations.
1. p2p mempool can be more complicated and complex to implement - it builds upon the core p2p communication between Ethereum nodes. Reusing Akula interfaces can take more time than expected.
1. Safety and security of bundling and user operations - sending bundles directly to block producers or Flashbots is needed to prevent front-running. That needs need to be analyzed and defined more thoroughly.

## Goal of the project

1. Bundler is fully implemented and tested.
1. Demonstrate successful implementation by connecting and using one of the EIP-4337 compatible wallets.
1. Contribute to official bundler specs and pass the test suite.
1. Outline the plan and work to push the implementation into Akula's main codebase.

## Collaborators

### Fellows 

- [Vid Kersic](https://github.com/Vid201)
- [WillQ](https://github.com/zsluedem)

### Mentors

- [Yoav Weiss](https://github.com/yoavw)
- [Dror Tirosh](https://github.com/drortirosh)

## Resources

- [GitHub repository](https://github.com/Vid201/aa-bundler)
- [Architecture and specification](https://hackmd.io/@Vid201/aa-bundler-rust)
- [Vid's notes and development updates](https://github.com/eth-protocol-fellows/cohort-three/blob/master/notes/vidkersic.md) (you can find all the reading material, examined codebases and projects, and other useful things there)
