# Helios Consensus Layer P2P Connection

The goal of this project is to make Helios, a Rust based light client implementation, able to fetch consensus layer data through a peer-to-peer network connection with consensus layer clients. The implementation will be able to work side-by-side, if needed, with the current RPC and allow the client to seamlessly switch between them.

## Motivation

Helios currently relies on a centralized provider for consensus layer data fetching. I briefly mention the importance of why should we stop relying on them in [this post](https://mirror.xyz/brechy.eth/0EeMjGThVX8wTJ25R-3xbEdFKbr1uYBaKMO9z1XrQ10). Implementing a peer-to-peer network connection with the blockchain within a light client it’s a big step towards trust minimization.

## Project description

The main components of the project are the implementation of a Peer Discovery service able to find new peers whom are able to provide the necessary data, a P2P Network service capable of managing the discovery and connecting to these peers in order to receive and parse the messages, and the integration with the current Helios architecture. However, my main focus will be on the implementation of the P2P Network Service, since the other tasks may be assigned to other devs. This is very dependant on the Discovery, so that will become part of my scope as well.

The overall project outline can be seen in [this document](https://hackmd.io/@brech1/helios-p2p-outline).

## Specification

I’ll detail the specifics for the Discovery and P2P Network services. I already started working on a minimal setup of these at work in [this repository](https://github.com/brech1/cl-p2p-setup).

### Peer Discovery Service

- Based on the Node Discovery v5 protocol.
- Will use the [Sigma Prime Discv5 Rust implementation](https://github.com/sigp/discv5).
- Should filter nodes by capabilities, we’re interested in nodes capable of providing aggregated block attestations and block headers.
- Discv5 nodes are identified using ENRs but should also provide the peers `Multiaddress` to be used in libp2p swarm dialing.
- It should be able to process queries to find new peers on demand.

### P2P Network Service

- As detailed in the [consensus specs](https://github.com/ethereum/consensus-specs/blob/dev/specs/phase0/p2p-interface.md), it should support the TCP libp2p transport, thus relying on [rust-libp2p](https://github.com/libp2p/rust-libp2p).
- Should establish and maintain connections with consensus layer peers capable of providing the necessary data.
- Should manage peer connections (start/end/request new peers) in order to maintain a stable amount of peers that publish the required topics to keep track of the CL head.
- Setup SSZ decoding and Snappy decompression to parse received messages.

## Roadmap

### Initial Research - Nov 22

- Ethereum PoS
- Consensus Layer
- Light Clients
- Consensus Layer P2P Networking

### Minimal Working Implementation - Dec 22

Create a research based working implementation that:

- Finds new peers through bootnodes using discv5.
- Subscribe to gossipsub topics.
- Dial to the discovered peers using libp2p swarm.
- Receive and decode messages of the subscribed topics.

### Implementation In Feature Branch - Jan 23

- Migrate working implementation to the feature branch.
- Achieve all project requirements.
- Review integration.

### Benchmarking - Feb 23

- Work on code optimization.
- Assess the increase resource requirements of the final working implementation.
- Final report.

## Possible challenges

I see the biggest challenge in making the Discovery and P2P Network services to work steadily and with a clear interaction between them (query management). It’s of big importance that the data flow is stable and that depends on both of them. The discovery filtering and gossipsub configuration should also be thought thoroughly.

As a second challenge I find making an optimized solution. This implementation is being made for a light client, which by nature will live in a constrained environment. Its important that the finalized code does not increase the need of networking or other resources in a big way.

## Goal of the project

This project will succeed if Helios is able to fetch and decode all the required consensus layer data to track the head of the chain, the latest state roots and the aggregated sync committee attestations, in a stable and reliable manner.

## Collaborators

### Fellows

- [Mustapha Saeed](https://github.com/mustaphasaeed)

### Mentors

- [Alex Stokes](https://github.com/ralexstokes) - EF Consensus Research

## Resources

- [Diminishing Trust At Scale](https://mirror.xyz/brechy.eth/0EeMjGThVX8wTJ25R-3xbEdFKbr1uYBaKMO9z1XrQ10)
- [Consensus Layer P2P Networking](https://mirror.xyz/brechy.eth/gE8NFWIQ6sCcW7ayjy-79Uq6UDLKJ5UCvbBVA2XrBNg)
- [Minimal CL P2P Implementation](https://github.com/brech1/cl-p2p-setup)
- [Project Outline](https://hackmd.io/@brech1/helios-p2p-outline)
- Tracking Issue: [https://github.com/a16z/helios/issues/59](https://github.com/a16z/helios/issues/59)
- Feature PR: [https://github.com/a16z/helios/pull/130](https://github.com/a16z/helios/pull/130)
- Contribution branch: [https://github.com/a16z/helios/tree/%40refcell/p2p](https://github.com/a16z/helios/tree/%40refcell/p2p)
- Technical guideline: [https://hackmd.io/BihePpvfQ3mSH2MZiVBT1Q](https://hackmd.io/BihePpvfQ3mSH2MZiVBT1Q)
