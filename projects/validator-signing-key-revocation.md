# Compromised validator signing key revocation
This is a project proposal for [EPF Cohort Three](https://github.com/eth-protocol-fellows/cohort-three) by [abhudia04](https://github.com/abhudia04) (https://github.com/abhudia04/cohort-three/blob/master/development-updates.md#alpesh (https://hackmd.io/@alpesh/SyTasizro).

## Motivation

The goal of this project is to prevent hypothetical extortion attacks from becoming an issue in ETH 2.0 Proof-of-Stake (PoS) Consensus Mecha- nism. Preliminary work has shown that there are multiple highly successful extortion strategies that require only that some pre-existing memory access exploit can be used against target validators.

## Project description

Recent research has shown the viability of ransomware attacks on Ethereum 2.0 Proof-of-Stake (PoS) validators, whereby an attacker who has compromised a validator signing key threatens to perform slashable actions unless a ransom is paid. Given the size of Ethereum validator stakes (32 ETH or 35,000 USD), validators are likely to become an extremely attractive target for future ransomware.

The goal is to explore consensus protocol adaptations to mitigate the risks of ransomware attacks on Ethereum 2.0 validators.

The project's objective is to design a new revocation mechanism that will allow validators to improve their operational security by quickly revoking the compromised signing key and replacing it without having to execute voluntary exit or withdrawing the stake and setting up a new validator.

## Specification



## Roadmap

- Phase 1: Week 1
    - Learn about Ethereum protocol and read through the recommended reading material.
    - Set up a validator on goerli testnet to understand its inner workings.
- Phase 2: Week 2-3
    - Deep dive into specific areas of interest.
    - Connect and discuss with mentors the chosen topic.
    - Outline project proposal.
- Phase 3: Week 3-14
    - Continue participating in calls
    - Continue making weekly-biweekly updates on the research and development
    - Work to execute and deliver the project proposal.
- Phase 4: Week 14-16
    - Write a summary report and presentation outlining what I have worked on, the challenges faced, and the problems that were addressed and solved.

## Possible challenges

Many approaches to solving the current, exploitable, implementation of slash- ing involve additional complexity. Key chains, revocation mechanisms, and re-enrolment of affected validators all add significant complexity, in the form of command and control traffic over Ethereum (smart contract execution).

By modelling potential cyber attacks, we have identified the scope of exploita- tion and the degree of control the attacker can exercise over a compromised validator. As a result, we have been able to constrain our solution to the signing key itself.

## Goal of the project

The aim of the project is to increase resilience to ransomware/extortion at- tacks against ETH 2.0 validators, while respecting the stated objectives of ETH 2.0 penalty mechanisms for malicious behaviour. The main research ob- jective is to devise a signing key revocation mechanism which eliminates the profitability of extortion attacks by allowing validators to explicitly revoke signing keys after initial slashing (subject to cooling-off/quarantine periods as per the current ETH 2.0 slashing definition).

## Collaborators

### Fellows


### Mentors

- [Fredrik] Security
- [Hsiao-Wei Wang] PySpec implementation

## Resources
- Specification
    - [`consensus-specs`](https://github.com/ethereum/consensus-specs/blob/dev/specs/capella/beacon-chain.md#preset))

- Background reading
    - [`Execution-engine`] (https://github.com/ethereum/consensus-specs/blob/dev/specs/bellatrix/beacon-chain.md#execution-engine)

    - [`Process Execution Payload`] (https://github.com/ethereum/consensus-specs/blob/dev/specs/bellatrix/beacon-chain.md#process_execution_payload)

    - [`Execution Change`] (https://github.com/ethereum/consensus-specs/blob/dev/specs/capella/beacon-chain.md#new-process_bls_to_execution_change)

    - [`Executiion APIs`] (https://github.com/ethereum/execution-apis/blob/main/src/engine/specification.md)

    - [`Client Relationship`] (https://ethresear.ch/t/eth1-eth2-client-relationship/7248)