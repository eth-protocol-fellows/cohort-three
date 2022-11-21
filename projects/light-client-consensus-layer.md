# Light client consensus layer development
This is a project proposal for [EPF Cohort Three](https://github.com/eth-protocol-fellows/cohort-three) by [robzajac](https://github.com/robzajac).

The goal of this project is to enable greater decentralization and trustless access to the Ethereum consensus layer by implementing the [light client protocol](https://github.com/ethereum/consensus-specs/tree/dev/specs/altair/light-client) in [teku](https://github.com/ConsenSys/teku). This will increase the availability of light client data in the CL and make it easier for light clients to sync to the latest block header without needing to trust a third party. 

## Motivation

[The light client protocol](https://github.com/ethereum/consensus-specs/blob/dev/specs/altair/light-client/sync-protocol.md) is a known way for clients in minimal computational environments to sync to the latest block header without needing to trust the data provider (e.g. a node hosted on Infura). For more on the protocol and its motivation, see [background reading](#Resources).

This protocol describes both the light client itself, and a "light client server" which provides the data needed for the light client to execute its sync protocol. While there have been several light client projects in development (e.g. recently announced RPC-proxy light clients [Kevlar](https://github.com/lightclients/kevlar) and [Helios](https://github.com/a16z/helios)), there are not as many implementations of the light client server.

Currently, the majority provider for light client data in beacon nodes is the consensus client [Lodestar](https://github.com/ChainSafe/eth2-light-client-demo). [Nimbus](https://github.com/status-im/nimbus-eth2) has also implemented the light client API. Serving this data is done altruistically, as light clients do not contribute any computation to the network. In order to contribute to greater availability of this data, as well as expand client diversity, more consensus clients should implement the light client protocol.

## Project description

The project is composed of essentially two parts.

The first and primary goal is to implement the light client APIs in teku and demonstrate a light client sync against a teku full node. This part is more defined given that the light client APIs are already included in the beacon node specification, and the main work is in implementing them up to teku's production standards.

The second and more open-ended goal of the project is to make headway in the research area of light client incentivization for full nodes. Light clients do not contribute any computation to the network, and full nodes can be resource-exhausted by light clients requesting data. Here this project will consolidate the current research done in RPC incentivization, and propose as well as possibly implement a prototype of an incentives model for full nodes.

## Specification

[Endpoints](https://github.com/ethereum/beacon-APIs/tree/master/apis/beacon/light_client)
[Data types](https://github.com/ethereum/consensus-specs/blob/dev/specs/altair/light-client/sync-protocol.md#containers)
- [`GetLightClientBootstrap`](https://github.com/ethereum/beacon-APIs/blob/master/apis/beacon/light_client/bootstrap.yaml): Returns the data for clients to startup into the light client protocol, including the current sync committee and latest block header
- [`GetLightClientUpdatesByRange`](https://github.com/ethereum/beacon-APIs/blob/master/apis/beacon/light_client/updates.yaml): Returns the `LightClientUpdate` for the provided sync committee range, including the attested block header and the next sync committee
- [`GetLightClientFinalityUpdate`](https://github.com/ethereum/beacon-APIs/blob/master/apis/beacon/light_client/finality_update.yaml): Returns the latest known `LightClientFinalityUpdate`
- [`GetLightClientOptimisticUpdate`](https://github.com/ethereum/beacon-APIs/blob/master/apis/beacon/light_client/optimistic_update.yaml): Returns the latest known `LightClientOptimisticUpdate`

Incentives solutions
- https://vipnode.org/ 
- https://www.pokt.network/

## Roadmap

- Implement `GetLightClientBootstrap`: 1 week
    - Interface already available. Only requires implementation
- Implement `GetLightClientUpdatesByRange`: 2 weeks
    - Standup of interface & new types required
    - And implementation itself
- Implement `GetLightClientFinalityUpdate` + `GetLightClientOptimisticUpdate`: 2 weeks
- Deploy and test on teku full node, including a light client sync with one of the available light client projects: 2 weeks
    - Extra time needed if existing light clients are not compatible with consensus light client protocol. In this case it may be necessary to develop a minimal light client to test against the new endpoints
    - Can leverage [Hive](https://github.com/ethereum/hive) for test infrastructure
- Consolidate incentives research and prototype a light client incentivization model, e.g. a node running on POKT Network: ~3-4 weeks

Total time estimated: ~10-11 weeks

## Possible challenges

- Continuing to learn the teku codebase, consensus layer ecosystem
- Verifying compatibility of existing light clients with the new teku implementation, or otherwise implementing a light client
- Less definition and more complexity in full node incentivization

## Goal of the project

1. Light client endpoints are fully implemented, tested and deployed in teku.
2. Demonstrated a sync with a light client against a teku full node.
3. Researched and proposed a mechanism to incentivize full nodes serving light client data.
## Collaborators

### Fellows 

I am working independently, but have benefitted from knowledge share on light clients with [AnthonyMadia](https://github.com/AnthonyMadia) and [EchoAlice](https://github.com/EchoAlice).

### Mentors

- [Paul Harris](https://github.com/rolfyone) with teku onboarding, technical advice, code review, etc.
- [Alex Stokes](https://github.com/ralexstokes) project inspiration and background

## Resources

- Specification
    - [`consensus-specs`](https://github.com/ethereum/consensus-specs/blob/dev/specs/altair/light-client/sync-protocol.md)
    - [Beacon API](https://github.com/ethereum/beacon-APIs/tree/master/apis/beacon/light_client)
- Implementation
    - [teku codebase](https://github.com/ConsenSys/teku)
        - [First PR merged](https://github.com/ConsenSys/teku/pull/6384) with `GetLightClientBootstrap` interface
        - [Tracking issue](https://github.com/ConsenSys/teku/issues/4230)
- Background reading
    - [High level: What is a light client](https://www.parity.io/blog/what-is-a-light-client/)
    - [Explanation of the sync protocol](https://mycelium.xyz/research/world-of-light-clients-ethereum)