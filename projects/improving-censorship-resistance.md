# EPF Project Proposal

Improving censorship-resistance under proposer-builder separation (PBS).

## Motivation

*What problem is your project is solving? Why is it important and what area of the protocol will be affected?*

Since the merge, PoS validators have the option to outsource their block production to specialized entities that can extract value. Basically out-sourcing their duties to the highest bidder to increase their APR. There are currently [8 major relays](https://beaconcha.in/relays) (update: 10 relays, since Dec 6) of which 50% have some sort of censoring. This means that currently [+70% of all blocks have some sort of OFAC censoring](https://www.mevwatch.info/). This goes against the core protocol values of

- Censorship resistance
- Credible neutrality

## Project description

*What is your proposed solution?*

This proposal aims to [improve censorship resistance under proposer-builder separation (PBS)](https://notes.ethereum.org/s3JToeApTx6CKLJt8AbhFQ#Hybrid-PBS-can-we-use-proposers-only-for-inclusion-of-last-resort). Since there are still a lot of [open research questions on PBS](https://barnabe.substack.com/p/pbs), the scope and details of the project are defined on a higher-level.  

Define a method that analyzes which transactions are getting censored. Criteria to consider

- blockspace
- gas prices
- tx fees
- other transactions in mempool
- ..?

This could get used and implemented in various ways

1. A public mempool explorer that shows which transactions are getting censored and should be included
1. A poor man's CR/IL prototype, inspired by [Terence's Devcon talk](https://www.youtube.com/watch?v=mXGA-u-sH_w&t=1150s)
1. Analyzers to Alex' [relay monitor](https://github.com/ralexstokes/relay-monitor)
1. An option for [mev-boost](https://github.com/flashbots/mev-boost/issues/215)
1. ..?

## Specification

*How will you implement your solutions? Give details and more technical information on the project.*

tbd

## Roadmap

*What is your proposed timeline? Outline parts of the project and insight on how much time it will take to execute them.*

1. Create a Dune Dashboard to track network health and block utilization https://dune.com/wslyvh/network-utilization

1. These same metrics will be used to define a methodology to analyze censored transactions. This will be used for a new mempool explorer to make it easier to track and monitor.

1. Create proposal to standardize execution API call to return current pending transactions mempool. Some execution clients have developed their own, custom implementations, but there's currently no standardized (execution) API call.

    Geth: txpool_content 
    Besu: txpool_besuTransactions 
    Nethermind: parity_pendingTransactions

1. Implement the methodology in any of the existing tools. E.g. mev-boost, relay-monitor or as stand-alone tool.

## Possible challenges

*What are the limitations and issues you may need to overcome?*

1. Standardizing the API calls across different clients might take time. This should not be a dependency for the project, but will be explored as a side-task
1. PBS still has a lot of open research questions. This project is intended to move things forward by creating a prototype
1. Not familiar with Go (mev-boost, relay-monitor). So an additional learning curve to contribute to these external tools.

## Goal of the project

*What does success look like? Describe the end goal of the project, scope, state and impact for the project to be considered finished and successful.*

This goal for this project is to provide options for validators to select relays that are aligned with their values and [keeping relays honest](https://notes.ethereum.org/@yoav/BJeOQ8rI5). It should make it easier to switch or completely fall back to local block building.

## Collaborators

### Fellows

*Are there any fellows working with you on this project?*

Not at the moment. Open to collaborations.

### Mentors

- Barnabe
- Lightclients
- Alex Stokes
- Yoav Weiss

## Resources

Provide links to repositories, PRs and other resources which constitute the project.

- https://notes.ethereum.org/@wslyvh/epf-3