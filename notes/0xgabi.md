# Gabi's Notes

Hi I'm Gabi, or 0xGabi on [Github](https://github.com/0xGabi). I been working on the DAO space for the last 4 years doing smart contracts, testing, backend and front-end work. I'm interested on contributing to EIP-4844.

## Updates

### 10/25/2022
- I started a Notion page to organize study materials: [Fellowship](https://0xgabi.notion.site/Fellowship-0b629dbc572f499db254d40ea481e099)
- I participated on the last couple breakout calls and today's 4844 implementers' call
- Last few weeks I contributed with a couple of tools that were needed for 4844:
    - faucet: https://eip4844-faucet.vercel.app/
    - blobs explorer: https://www.blobscan.com/
- I published a docker image with a blob-indexer that we use on blobscan:
    - repo: [blob-indexer](https://github.com/BlossomLabs/blob-indexer)
    - docker image: [blossomlabs/blob-indexer](https://hub.docker.com/repository/docker/blossomlabs/blob-indexer)

#### Next steps
- Get up to speed with the latest spec changes of EIP-4844: https://github.com/ethereum/pm/issues/647.
- Get up to speed with the 4844 tracking on Lighthouse: https://github.com/sigp/lighthouse/issues/3625.
- Help with new 4844 devnet as needed to support both faucet and blobs explorer.


### 10/31/2022
- I meet Jimmy other fellowship memeber and we started a shared effort on 4844 front. We contacted with Lighthouse mentors and schedule a kick-off call. 
- I create a plan to [study Rust](https://0xgabi.notion.site/Rust-d5145f4840f1429481f74433871a2193).
- I continue learning about ETH 2.0 with [Ben's book](https://eth2book.info/bellatrix/part2/incentives/diversity).
- I did a deep dive on the p2p networking. Learn more about libp2p:
    - [Introduction](https://docs.libp2p.io/introduction/)
    - [Publish subscribe](https://docs.libp2p.io/concepts/publish-subscribe/)
    - [DHT](https://docs.ipfs.tech/concepts/dht/)
    - [phase0 p2p interface](https://github.com/ethereum/consensus-specs/blob/dev/specs/phase0/p2p-interface.md)

#### Next steps
- I got the fundamentals of Rust lenguage following my [study plan](https://0xgabi.notion.site/Rust-d5145f4840f1429481f74433871a2193).
- I will particate on 4844 implementers' call. And keep up to date with latest 4844 spec.
- I will review Lighthouse codebase and get familiar with their development process.


### 11/07/2022
- I particiapte of the mentor's kick-off with Lighthouse team. We discussed the project and the next steps. [Action items document](https://hackmd.io/BjROTQriTEq_VF6Wz9Zebw).
- I finished the core concept of the [Rust book](https://doc.rust-lang.org/book/) and most of [rustlings exercises](https://github.com/rust-lang/rustlings).
- I setup my dev environment and local testnet on the Lighthouse codebase.

#### Next steps
- I will investigate [Acount Abstraction](https://0xgabi.notion.site/EIP-4788-account-abstraction-9bf7e8f4acc44c6c9bd62e2df0b448d1).
- I will particiapte on 4844 implementers' call. And keep up to date with latest 4844 spec.
- I will address my first issues on Lighthouse codebase. Having the [4844 tracking into account](https://github.com/sigp/lighthouse/issues/3625#issuecomment-1304268350).


### 11/21/2022
- I read the [consensus-spec](https://github.com/ethereum/consensus-specs/tree/dev/specs) for altair, bellatrix, capella and 4844.
- I learned about the [Engine JSON-RPC API](https://github.com/ethereum/execution-apis/tree/main/src/engine) of the execution-apis spec.
- I kept up to date with the latest 4844 implementers' changes.

#### Next steps
- I will investigate the [builder API spec](https://github.com/ethereum/builder-specs)
- I will investigate about [PBS](https://ethresear.ch/t/proposer-block-builder-separation-friendly-fee-market-designs/9725) and how it's implemented on [mev-boost](https://github.com/flashbots/mev-boost)
- I will continue to learn about Lighthouse codebase and Rust lenguage.


### 11/28/2022
- I got familiar with the builder API spec changes needed for EIP-4844 and Capella, outlined on [this issue](https://github.com/sigp/lighthouse/issues/3689) and [this issue](https://github.com/flashbots/mev-boost/issues/392).
- I reviewed Jimmy's document about [Builder API for Blobs](https://hackmd.io/@jimmygchen/B1dLR74Io) and we started discussing about the next steps.
- I collaborate with Jimmy on our [EIP-4844 projects proposal](https://github.com/eth-protocol-fellows/cohort-three/blob/master/projects/4844-consensus-client.md).

#### Next steps
- I will review Jimmy's document about [LH architecture](https://hackmd.io/@jimmygchen/Sk9oPHO8s) following along with the codebase.
- I will work on a draft PR for the builder-specs changes needed for 4844.


### 12/05/2022
- I reviewed [Jimmy's PR that update types to support EIP-4844 on the beacon-APIs](https://github.com/ethereum/beacon-APIs/pull/271).
- I worked on a [PR to include Capella and EIP-4844 support](https://github.com/jimmygchen/builder-specs/pull/1) to the builder-spec.
- I wrote an Ecosystem Support Program [grant application for Layer 2 Community](https://esp.ethereum.foundation/layer-2-grants) to continue development of [Blobscan hackathon project](https://ethglobal.com/showcase/blobscan-explorer-5bmqk).

#### Next steps
- I will rewrite [Blobscan blob indexer](https://github.com/Blobscan/blob-indexer) using Rust.
- I will work on a document to share with the 4844 implementers' call about the work done by Jimmy and me on the builder-spec.
- I will generate test vectors for the builder-spec changes we introduced. And will share with the falshbot community to start testing the changes early.


### 12/19/2022
- I worked and review a [PR for the builder spec to support EIP-4844](https://github.com/ethereum/builder-specs/pull/58).
- I reviewed [Jimmy's PR that added Lighthouse support to the 4844-interop repo](https://github.com/Inphi/eip4844-interop/pull/77).
- I tried to sync with the 4844 devnet v3 and got some issues. I

#### Next steps
- I will work on devnet v3 changes for Blobscan explorer and 4844-faucet.

### 12/26/2022
- I update the 4844 faucet:
    - I create a separate repo to [handle smart contract deployments](https://github.com/0xGabi/eip4844-faucet-deployments).
    - I worked on a [PR to support devnet v3](https://github.com/0xGabi/MultiFaucet/pull/3).
- I started working again on Blobscan explorer to [sync with devnet v3](https://github.com/Blobscan/eip4844-testnet/pull/1).

#### Next steps
- I will keep in touch with EPS about Blobscan grant application.
- I will go on vacation for a week.

### 01/09/2023
- I got in contact with a devops engineer to help with Blobscan database and operations tasks. 
- I worked with a designer to create Blobscan [identity and initial designs](https://www.figma.com/file/ROLagIuJdrNExurszAt0Dn/Blobscan?t=Oq9PPjZa83tfuY5M-0).
- I [researched Account Abstraction learning about EIP-4337](https://0xgabi.notion.site/EIP-4337-Account-Abstraction-9bf7e8f4acc44c6c9bd62e2df0b448d1).

### 01/16/2023
- I made a call with a ESP grant reviewer to discuss about Blobscan project.
- I worked on a project [roadmap for Blobscan](https://hackmd.io/YbdJpl9ET-GXxTaTElp7DA) to share with ESP.

#### Next steps
- I will work on supporting 4844 devnet v4.
- I will continue working on providing 4844 support to the relay-spec and mev-boost (builder-spec).
- I will schedule a pair programing session with Jimmy to learn about Rust development on Lighthouse codebase.