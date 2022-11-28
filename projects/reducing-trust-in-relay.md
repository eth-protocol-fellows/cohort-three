# Project Proposal
This project attemts to identify and specify a mechanism to reduce the required trust in the PBS relay.

## Motivation
Currently, relays serve as an intermediary between the builders and mev-boost, while the proposer operates mev-boost. However, the relay serves as more than just a proxy for the proposer and builder; it also chooses the highest offer from among all builders, verifies the builders' blocks, and releases the block to the network once the auction is complete. Because of this, the relay must be trusted by both the builder and the proposer. The proposer must trust the relay to release the block to the network on time, and the builder is trusting the relay not to steal their mev opportunities. Since Ethereum is designed to be a decentralized, trustless system, this creates a bottleneck for these properties.

## Project description
To decrease the necessary trust in the PBS relay, a mechanism must be identified and specified. In order to produce a specification, we focus on finding such a mechanism or adopt an approach currently proposed by other entities. If there is still time after the approach has been specified, we will attempt to prototype the specification.

## Specification
The current approach, which will be refined regularly, is explained [here](https://hackmd.io/@echno/relay-trust).

## Roadmap
Week 3-11:
1. New idea
2. Collect feedback
3. Iterate on that idea
4. Go to step 1 if the issues that came up are not resolved; otherwise, move on to step 2 until no further feedback or open questions are received. 

Week 11-14:
6. Write a specification

If time left:
7. Prototyping

## Possible challenges
- Failing to find a suitable solution 
- There are compromises with most solutions, and not everyone would want the same tradeoff.

## Goal of the project
The goal is to have developed a solution and specification, with the fewest possible drawbacks, that to some degree reduces the trust of the relay. Additionally, it would be nice to have a prototype implementation of this specification.

## Collaborators
The project's collaborators are addressed in this section.

### Fellows 
- [Echno](https://github.com/ogechno)

### Mentors
- Alex Stokes
- Barnabé Monnot

## Resources
- [Proposal](https://hackmd.io/@echno/relay-trust)
