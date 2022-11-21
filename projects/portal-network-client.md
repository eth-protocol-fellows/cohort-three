# Portal Network - Ultralight Client

The [Portal Network](https://github.com/ethereum/portal-network-specs) is in a "get it built" phase and the core value it can offer is building a network with light-clients as first-class citizens. Specifically, the client I am focusing my efforts on is [Ultralight](https://github.com/ethereumjs/ultralight). The History Network is currently being built out and my efforts will be spent building out the rest of the subprotocols for the Ultralight client.

## Motivation

The Portal Network is an in progess effort to enable lightweight protocol access by resource constrained devices. The term "portal" is used to indicate that these networks provide a view into the protocol but are not critical to the operation of the core Ethereum protocol. Ultralight is an implementation of the Portal Network.

## Project description

My project will focus on building the subprotocols of the Ultralight client including:

- `Execution State Network`
- `Execution History Network`
- `Execution Transaction Gossip Network`
- `Execution Canonical Indices Network`
- `Beacon Chain Light Client Network`

## Specification

Each subprotocol will be built starting with its' SSZ types, objects based on those types, and following the specification for the rest of the networks.

## Roadmap

My timeline is based on me interacting with the ultralight team and their rough roadmap. This is by no means official and subject to change.

### Q1

- Wrap up any loose ends from History Network implementation - (alpha version of portalnetwork module for chain history)
- Implement prototype of Beacon light client update network
- Begin exploration of WebRTC to allow for p2p discovery of browser clients using libp2p/waku gossip

### Q2

- Explore integration of Lodestar or Kevlar CL light client with Ultralight for feeding light client update data to Beacon Light Client Update Network
- Build WebRTC transport layer for discv5 to allow direct p2p connections for browser clients
- Begin implementation of Rendezvous protocol in Discv5

### Q3

- Begin implementation of State Network prototype (or possible TX gossip)
- Finish implementation of Rendezvous protocol in Discv5

### Q4

- Launch portalnetwork v1.0.0 with history/light client update/state network functionality

## Possible challenges

There will be challenges around having browser clients be truly peer-to-peer. WebRTC and Nat Travesals will be researched to combat this. Currently, there is a proxy ultralight clients have to connect to but that may be changed to make the processes for connecting other clients more efficient. We do not want to open connections on other browsers because that will be quite expensive.

## Goal of the project

Success is a full, working implementation of the Portal Network.

## Collaborators

### Fellows

Independent

### Mentors

Ultralight Team

- [acolytec3](https://github.com/acolytec3)
- [ScottyPoi](https://github.com/ScottyPoi)

## Resources

[Ultralight](https://github.com/ethereumjs/ultralight)
[Portal Network Spec](https://github.com/ethereum/portal-network-specs)
