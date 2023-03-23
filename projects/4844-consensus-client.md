# EIP-4844 Consensus Client

Contribute to the implementation of [EIP-4844](https://eips.ethereum.org/EIPS/eip-4844) in [Lighthouse](https://github.com/sigp/lighthouse/) and the broader Ethereum ecosystem.

## Motivation

Ethereum has grown quite significantly in recent years, and for it to continue to support the growth leading to mass adoption, it would have to be able to handle larger amounts of data, and the transaction fees would have to be significantly reduced to make more practical applications possible.

Ethereum's [rollup-centric roadmap](https://ethereum-magicians.org/t/a-rollup-centric-ethereum-roadmap/4698) aims to solve these scaling issues. Many rollups have emerged in the recent years; however, today's rollup solutions would still have to compete for blockspace at L1 and it could still be too expensive for users at peak times. Hence changes need to be made at the protocol to introduce a new type of transaction for "blob space", which is what [EIP-4844](https://eips.ethereum.org/EIPS/eip-4844) is for.

High transaction fees have been a long-standing problem, and with EIP-4844 moving to CFI status this is a really impactful upgrade for the Ethereum ecosystem. We hope to be a small part of it by contributing to the implementation, testing & tooling, or anything that would help us get there. We're really excited about where this change will get us to :rocket:. 

## Project description

We decided to contribute to the **EIP-4844 implementation, testing and tooling**. Focusing our efforts on the Lighthouse client. 

### Areas of focus

Below are areas we'd like to focus on, however we are open to changes and jump into areas where we can provide more help. Most topics are relatively new to us, so we'll be working closely with our mentors from the Lighthouse team.

1. [Builder API updates](https://github.com/sigp/lighthouse/issues/3689) for EIP-4844
2. Interop and help with [devnet v3 related tasks](https://github.com/sigp/lighthouse/issues/3625)
3. Help with testing for EIP-4844
4. Make enhancements to blobs explorer: [blobscan](https://github.com/BlossomLabs/blobscan)

## Specification

### Builder API updates for Blobs

![](https://i.imgur.com/RNrDMbT.png)

- Investigate required Builder API changes, propose spec changes and initiate discussions
- Implement changes in CL client (could be done in parallel if it make sense)
- Collaborate with other teams on testing, such as creating test vector for Flashbots to run tests
- Update the Builder API test tool used by the Lighthouse team

### Add Lighthouse to [eip4844-interop](https://github.com/Inphi/eip4844-interop/pull/47) repo

- Add scripts and docker-compose sections to run Lighthouse on local EIP-4844 testent 
- Make sure all interop tests passes, and raise issues if necessary

### Testing for EIP-4844

There are a bit of dependencies and unknowns at this stage, but what we know so far:
- [Consensus spec tests updates](https://github.com/sigp/lighthouse/issues/3688)
    - waiting on test vectors to be released on [consensus-spec-tests](https://github.com/ethereum/consensus-spec-tests/) before tests can be implemented
- [Local EIP-4844 testnet](https://github.com/sigp/lighthouse/issues/3691)
    - need to explore whether enhancing existing simulator, or using docker makes more sense
- Network simulation with blobs using [Testground](https://docs.testground.ai)
- Unit testing in Lighthouse on EIP-4844 related modules

### Blob explorer enhancements 

- Visualization details of blob transactions data gas versus legacy transactions
- Analytics that shows blob usage over time
- Tag system to identify from which L2 blobs are comming (i.e. Optimism / Bedrock)
- Improved UX focused on blob data
- Decoding support of Sequencer batched transactions sent as blob transaction data, for each L2

## Roadmap

1. Phase 1 (2 weeks, 2022-11-24 - 2022-12-08)
    - Start Builder spec discussion & PR drafted out, and get feedback from mentors
    - Contribute to testing & interop for devnet v3
2. Phase 2 (3 weeks, 2022-12-09 - 2022-12-29)
    - Publish builder spec PR and discuss with other teams, hopefully finalised by the end of the period
    - Builder API update initial implementation & testing
3. Phase 3 (4 weeks, 2022-12-30 - 2023-01-25)
    - Complete Builder API for blobs implementation
    - Continue to contribute on 4844 related testing & toolings, including blobscan
4. Phase 4 (1 week, 2023-01-26 - 2023-02-02)
    - Project wrap up and showcase preparation

## Possible challenges

- For the Builder API work, we haven't really been through the consensus spec creation process, so our first attempt is most likely going to be challenging and we'll have to learn how the core devs work and get consensus from multiple teams. There will be some lead time for getting the spec finalised and for us this creates some unknowns.
- Integration testing on builder API changes could be challenging as it may involve regular sync with other teams. However there is a Builder API test tool in Lighthouse we could look into.
- Staying up to date with all 4844 discussions and changes have been a challenge for us so far, there are many teams working on this and we'll find a balance between staying up to date and implementation work.

## Goal of the project

Our goal is to learn as much as about core development as we can, and at the same time we hope to make an overall positive impact on deliverying a solid EIP-4844 implementation. We have defined some prelimary scope of the project, however this may change depending on how things go, where our experience fits and which areas need more help. This also means our contributions won't be limited to just the Lighthouse code base, but could include other aspects of core development.

What does success look like for this project
- We made small contributions to the Lighthouse code base (and other repos where applicable)
- We contributed to spec discussions and documentation.
- Any toolings we worked on gets used by others working on EIP-4844, and helped them get their jobs done.
- We got the fundamentals about Ethereum core development and Rust language.
- Last but not least, we learned how to collaborate with other core team devs, and become recognised as part of the team.

## Collaborators

### Fellows 

- [Gabi](https://github.com/0xGabi)
- [Jimmy Chen](https://github.com/jimmygchen)

### Mentors

Lighthouse team:
- [Paul Hauner](https://github.com/paulhauner)
- [Sean Anderson](https://github.com/realbigsean)
- [Divma](https://github.com/divagant-martian)
- [Michael Sproul](https://github.com/michaelsproul)

## Resources

- [EPF Final Dev Update](https://hackmd.io/@jimmygchen/Sy_Z5qj0j)
- [My Rust Journey](https://hackmd.io/@jimmygchen/r17PNqmri)
- [Builder API For Blobs](https://hackmd.io/@jimmygchen/B1dLR74Io)
- [Lighthouse Beacon Node Architecture](https://hackmd.io/@jimmygchen/Sk9oPHO8s)
- [Blobscan Explorer](https://0xgabi.notion.site/Blobscan-b42ab695f3464f3f8e90a3ec0e211156)

### Pull Requests

| PR Link                                                                              | Description                                                                                                                                                                             | PR Merged? |
| ------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |:----------:|
| [beacon-APIs#271](https://github.com/ethereum/beacon-APIs/pull/271)                  | Add Capella & 4844 types to Beacon API                                                                                                                                                  |     ✅     |
| [builder-specs#60](https://github.com/ethereum/builder-specs/pull/60)                | Builder spec update for Capella                                                                                                                                                         |     ✅     |
| [builder-specs#61](https://github.com/ethereum/builder-specs/pull/61)                | Builder spec update for Deneb                                                                                                                                                           |     🚧     |
| [ethereum-consensus#168](https://github.com/ralexstokes/ethereum-consensus/pull/168) | Rust library update: add Capella types and presets                                                                                                                                      |     ✅     |
| [ethereum-consensus#170](https://github.com/ralexstokes/ethereum-consensus/pull/170) | Rust library update: add 4844 types and presets                                                                                                                                         |     🚧     |
| [mev-rs#77](https://github.com/ralexstokes/mev-rs/pull/77)                           | Rust library update: add 4844 types                                                                                                                                                     |     🚧     |
| [lighthouse#3808](https://github.com/sigp/lighthouse/pull/3808)                      | Lighthouse draft implementation                                                                                                                                                         |     🚧     |
| [eip4844-interop#77](https://github.com/Inphi/eip4844-interop/pull/77)               | Added Lighthouse to `eip4844-interop`, a testing tool created by [@Inphi](https://github.com/Inphi) to help with 4844 interop testing and testing some of the key features of EIP-4844. |     ✅     |
| [devnet-v3](https://github.com/jimmygchen/devnet-v3)                                 | docker-compose setup for devnet-v3 (Lighthouse + Geth)                                                                                                                                  |     ✅     |
| [lighthouse#3830](https://github.com/sigp/lighthouse/pull/3830)                      | Implement a Beacon API endpoint in Lighthouse to support retrieval of blobs, and endpoint for users and testing                                                                         |     ✅     |
| [beacon-APIs#282](https://github.com/ethereum/beacon-APIs/pull/286)                  | Add the above download blob endpoint to the standard spec                                                                                                                               |     🚧     |
| [lighthouse#3979](https://github.com/sigp/lighthouse/pull/3979)                      | Implement Lighthouse Blob signing APIs and VC signing functionalities                                                                                                                   |     🚧     |
| [lighthouse#3936](https://github.com/sigp/lighthouse/pull/3936)                      | Rate limiting historic backfill sync                                                                                                                                                    |     🚧     |