# EIP-4337 Account Abstraction - Bundler implementation in Rust

*Account Abstraction has for a long time been a dream of the Ethereum developer community.* - **Vitalik Buterin**

Implementation of **EIP-4337 (Account Abstraction) Bundler in Rust**.

## Motivation

[**Account abstraction (AA)**](https://medium.com/infinitism/erc-4337-account-abstraction-without-ethereum-protocol-changes-d75c9d94dc4a) is one of the topics that has been in the air for quite a long time in the Ethereum community. While there have been several proposals for AA over the past years, most of them required core protocol changes (consensus/execution layer), making them complex and hard to implement alongside other protocol changes (transition to proof of stake, danksharding, PBS ...). The latter is one of the main reasons that the most traction today is getting **[EIP-4337: Account Abstraction using alt mempool](https://eips.ethereum.org/EIPS/eip-4337)**. EIP-4337 introduces a separate mempool for operations done by AA wallets and a new entity called bundler, which combines users' operations into the standard transaction. AA can be implemented and applied using this design without any protocol changes and, in the later stages ([The Splurge](https://twitter.com/VitalikButerin/status/1588669782471368704)), integrated more tightly into the protocol.

Similar to client diversity on the consensus and execution layer, diversity and several implementations of bundlers will make the AA world more healthy and secure. Some bundler implementations already exist ([JavaScript](https://github.com/eth-infinitism/bundler), [TypeScript](https://github.com/web3well/bls-wallet), [C#](https://github.com/NethermindEth/nethermind/tree/master/src/Nethermind/Nethermind.AccountAbstraction/Bundler), [Python](https://github.com/candidelabs/Candide-bundler-and-paymaster-RPC), [Go](https://github.com/stackup-wallet/stackup-bundler/)), either as standalone programs or as part of the execution clients ([Nethermind](https://github.com/NethermindEth/nethermind/)). Still, there is none in Rust, which is becoming one (if not the most) adopted programming language in the Ethereum ecosystem community on the core protocol level. Thus the implementation would benefit the **Ethereum/AA ecosystem**.

## Project description

Several goals are defined, one being in the scope of the fellowship duration and others oriented long-term.

The primary and core goals are to implement the complete bundler for EIP-4337 AA as a standalone entity that can work alongside any execution client (with communication taking place over JSON-RPC API). The main components thus include the bundler's specific JSON-RPC API, p2p user operation pool (mempool), and core bundling of user operations. Therefore, the aims of this project are: 
- implement a bundler in Rust
- contribute to bundler specs
- pass the bundler spec test suite (developed by **[eth-infinitism](https://github.com/eth-infinitism/)**)

On the other hand, I will pursue several long-term and more open-ended goals after the fellowship. One of these goals is to integrate it into the <del>**[Akula](https://akula.app/)**</del> **[Reth](https://github.com/paradigmxyz/reth/)** execution client written in Rust, which will probably lead to several adjustments to ensure correct integration in its main codebase. Other such plans include support for L2s.

## Specification

You can find the complete specification and architecture **[here](https://hackmd.io/@Vid201/aa-bundler-rust)** (the document will be updated on an ongoing basis).

The specification for EIP-4337 (WIP) is available **[here](https://github.com/eth-infinitism/account-abstraction/blob/develop/eip/EIPS/eip-4337.md)**.

The specification for EIP-4337 (latest stable) is available **[here](https://eips.ethereum.org/EIPS/eip-4337)**.

## Roadmap

During the fellowship:
- JSON-RPC API: 2 weeks.
    - Implement all JSON-RPC API endpoints and necessary logic.
    - `eth` and `debug`.
- User operation pool: 6 weeks.
    - Implement a standalone mempool.
    - Implement all the necessary verification of user operations, such as sanity checks and simulation verification (e.g., forbidden opcodes).
- Reputation: 2 weeks.
    - Manage reputation for different entities, such as paymasters, senders/accounts, and factories (of smart contract wallets).
- Bundler spec testing: 1 weeks.
    - Prepare the repo for bundler spec testing.
    - Prepare Docker files.

**Total time:** ~11 weeks.

**Note:** work on different parts overlapped due to testing and connecting them.

After the fellowship:
- User operation pool:
    - Finish the simulation verification.
- Core bundling:
    - Implement all logic for bundling - simulation, signature aggregation, bundle construction, and propagating bundles as transactions to the txpool.
    - First, start with public txpool, then add Flasbots Protect.
    - Check for finalized user operations in the blocks.
- Make mempool sanity checks validation and simulation verification generic (for multiple different mempools).
- P2P protocol.
    - P2P protocol for user operations based on libp2p and SSZ (according to the official spec).
- Integration into execution client
    - Research and sketch out necessary work to prototype integration into Reth or with Reth's libraries/crates.

## Possible challenges

1. Figuring out all implementation details, constraints, and specifications of EIP-4337 bundling.
1. Adapt to the changes in the EIP, which often happens due to the early stage of the specs.
1. Implementing and testing the p2p mempool can be more complicated than expected since no bundler implementation implements the p2p currently, and there are yet to be official tests.
1. Safety and security of bundling and user operations - sending bundles directly to block producers or Flashbots is needed to prevent front-running. That needs need to be analyzed and defined more thoroughly.

## Goal of the project

1. Bundler is fully implemented and tested.
1. Demonstrate successful implementation by connecting and using one of the EIP-4337 compatible wallets.
1. Contribute to official bundler specs and pass the test suite.
1. Successfully connect and form the p2p network with other bundler implementations.
1. Outline the plan and work to push the implementation into Reth's main codebase.

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
- [Spec for EIP-4337 bundlers](https://github.com/eth-infinitism/bundler-spec)
- [Test suite for EIP-4337 bundlers](https://github.com/eth-infinitism/bundler-spec-tests)
- [Test executor for EIP-4337 bundlers](https://github.com/eth-infinitism/bundler-test-executor)
- [P2P specs for bundlers](https://github.com/eth-infinitism/bundler-spec/blob/main/p2p-specs/p2p-interface.md)