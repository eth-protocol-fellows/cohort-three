# Proposed projects

Here is a list of projects proposed by mentors. If you would like to know more about specific project or choose to work on it, contact corresponding mentor. 

- [Previous cohorts](#previous-cohorts)
- [prysmctl](#prysmctl)
- [Security system based on machine learning](#security-system-based-on-machine-learning)
- [CL light client](#cl-light-client)
- [CL + MEV software](#cl--mev-software)
- [Cryptoeconomic models](#cryptoeconomic-models)
- [P2P protocol tests](#p2p-protocol-tests)
- [By Łukasz Rozmej](#by-lukasz-rozmej)
- [Browser tooling](#browser-tooling)
- [Debug tools](#debug-tools)
- [Improving hive for End-to-End Testing](#improving-hive-for-end-to-end-testing)
- [By Potuz](#by-potuz)
- [Consensus client reward APIs](#consensus-client-reward-apis)
- [Stakers' testnet](#stakers-testnet)

### Previous cohorts

In previous cohorts, you can find many up to date ideas which haven't been solved yet. 

- [Project ideas in the first cohort](https://github.com/ethereum-cdap/cohort-one/issues?q=is%3Aissue+Project+idea)
- [Project ideas in the second cohort](https://github.com/ethereum-cdap/cohort-zero/issues?q=is%3Aopen+is%3Aissue+label%3A%22help+wanted%22)

### prysmctl

Proposed by Kasey

Prysm has a new accessory cli tool called `prysmctl` that we intend to expand to host various utilities. This work would be self-contained, high value for users and would range from simple (interacting with beacon node apis, replacing prysm.sh) to challenging (orchestrating testnet setup, interacting with the database, debugging tools for ssz values etc).

### Security system based on machine learning

Proposed by Frederik

Applying machine learning on for example the network protocol (or it could be on other areas too such as on-chain data) to create outliers and enable early warning systems for issues that start occurring is something I feel would be valuable. This could perhaps be a custom built system, or based off on elastic stack or similar existing solution.

There could also be more static data being shown such as validator performance, conflicting chains, etc.

### CL light client

Proposed by Alex Stokes

Assistance in building out a production-ready consensus layer light client.

### CL + MEV software

Proposed by Alex Stokes

Stack of CL + MEV software for any Rustaceans 

### Cryptoeconomic models

Proposed by Barnabé Monnot

Expand [economic model](https://twitter.com/barnabemonnot/status/1561194859238531073) or look into applying [rollup econ](https://barnabe.substack.com/p/understanding-rollup-economics-from) framework to existing rollups. Also other projects more practical or more theoretical

### P2P protocol tests

Proposed by Felix

Work on p2p protocol tests for [hive](https://github.com/ethereum/hive).

### By Łukasz Rozmej

- Virtual Machine with native code emission (IL VM)
- Danksharding prototyping
- Verkle Tries prototyping
- Experimental EIP's prototyping
- Protocol to synchronize traces to replace WarpSync in OE

### Browser tooling

By Cayman Nava

Simple webapps that may become useful, eg: https://enr-viewer.com/

### Debug tools

Tooling useful for debugging CL and EL. 

- [Compiled list by Paritosh](https://notes.ethereum.org/@parithosh/HJQDsoRr5)
- Progress tracking, discussion in the [issue](https://github.com/ethereum/pm/issues/520)

### Improving hive for End-to-End Testing

Proposed by Mario Vega

[Hive](https://github.com/ethereum/hive) can evolve into more sophisticated tool for e2e testing which allows to run the Consensus and Execution clients as they would be run by the end users. 

### By Potuz
Projects may require different protocol knowledge entry level and may end up
working with different members of the prysmaticlabs team. 
- Forkchoice fuzzer: Test different attack scenarios for our consensus algorithm. 
- Continuous benchmarking: Set meaningful realistic benchmarks and integrate them in CI
- Beacon API compliant validator client: Long term project of rewriting the validator client code to be compatible with the Beacon API instead of prysmaticlabs' internal API. 
- Type consistency between forkchoice and the beacon-chain package. 

### Consensus client reward APIs

Presently there are no cross-client APIs for calculating the rewards paid to validators for publishing attestations, block proposals and other messages.

This creates an unnecessary barrier to entry for the development of tools like block explorers and GUIs, requiring application devs to reverse-engineer consensus reward code.

To improve the situation it would be great to have a simple HTTP API available in every consensus client that outputs reward data. This project could involve:

- Design and standardisation of the HTTP API spec in [beacon-APIs](https://github.com/ethereum/beacon-APIs).
- Implementation of production-ready (or proof-of-concept) APIs in one or more consensus clients. Different fellows could implement the APIs in different clients.
- Design and implementation of a local indexing module to track rewards for nominated validators without a block explorer. This could either be a standalone tool leaning
  on the APIs, or integrated into a consensus client. For prior work along these lines see Nimbus' [attestation performance tracking](https://nimbus.guide/attestation-performance.html).

Mentor: @michaelsproul (SigP/Lighthouse)

### Stakers' testnet 

By Mario Havel

New testnet which is emphemeral and dedicated to stakers. Feasability of this solutions should be demonstrated by implementation in a client pair. The testnet is emphemeral so instead of just trivial network addition, you need to figure out the mechanism for rollbacks and devops setup. 

Details in this proposal: https://notes.ethereum.org/@mario-havel/stakers-testnet
