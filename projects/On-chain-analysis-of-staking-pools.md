# On-chain analysis of staking pools attestations

On-chain analysis of staking pools attestations and their impact on Ethereum network

## Motivation

The Ethereum protocol has reached around ~0.5 million validators. And the majority of the validators on the Ethereum network are part of staking pools. This makes up about ~78% (Dec. 2022) of the network. The staking pools have their own infrastructure for managing user nodes using clustering multiple nodes. Therefore if a large portion of the network shows anomaly i.e (late block production, inclusion delays, missed attestations, sync-committee participation, etc) this could be one of the reasons. Having as much information & analysis of the network could be very helpful & potentially prevent adverse outcomes.

## Project description

I will be following this [`open-issue`](https://github.com/eth-protocol-fellows/cohort-one/issues/29) that has details much more in depth.
To perform attestation analysis of major staking pools. The analysis will include: 
 -  Average performance of staking pool validators to the network.
 -  Number of missed attestations & inclusion delays.
 -  Sync-committee participation.

I will be working with top 5 pools that could be found on the [`beaconcha.in`](https://beaconcha.in/) website.

## Specification

In order to perform the analysis we need to work on the dataset of the validators & blocks produced in the past by the pool validators & non-pool validators to get a rough or average performance that we can compare to later. I have also come across a tool called [`chaind`](https://github.com/wealdtech/chaind). It structures raw beacon-chain data & saves it to a database that can later be queried. We might need to modify the existing code-base schema to add more tables for custom data retrieval.

I plan to follow the following steps.
- Get the list of validators associated with pools in `Beaconcha.in`.
- Staking validator attestation profiling. 
    - How many of these pool validators were supposed to attest and then how many did correctly?
- Identify blocks with a large number of missed attestations and percentages that were proposed by the pools. (This may require assistance from the `mentors`)
- Identify if pool validators attested with average performance as the whole network.

## Roadmap

### 1st & 2nd Month
- Enagage in the research of understanding the role of validators & their roles.
- Identify & explore tool codebase that could help in performing analysis. 

### 3rd & 4th Month
- Develop a basic working model with a small dataset & gradually expand to cater ~78% of the network. This will take most if the time as the list of pool validators are least 70k validators/pool & data to process is huge.
- Work on visualizing the data. Also, identify how to display the data that makes sense.

### Post Co-hort (TBD)
- Live analysis of the validator profiling, attestaion data & pool monitoring system (Could be very useful for live network alerts).

## Possible challenges

Initially, I intend to work on a pre-defined dataset i.e validator data for past 6 months. However, an access to an archival node (which might need being setup) would result in a more complete analysis with old & more recent data.
Another challenge I might run into is getting the exact address of the validators associated with staking pools as each pool has atleast 70k validators. The `beaconcha.in` website has a very basic chart on validators per pool but does not expose an API to get more details on them. This is important for the accuracy of the final result.

## Goal of the project
My goal is to learn the fundamentals of core development & infrastructure of Ethereum. There are a lot of components and not every one of them could be covered therefore I defined the scope of the project that will revolve around how validators work.
- Carry out analysis of attestation data of large pools. This might shape into a tool that could be used to visualize.
- Tooling & research notes I worked on helped others to carry the research & analysis forward.
- Lastly, collaborate with the core devs to create a positive impact in the ecosystem.

## Collaborators

### Mentors

- This project is highly shaped by [`Potuz`](https://github.com/potuz) therefore I will be in touch with him for further guidance.
- [`Michael Sproul`](https://github.com/michaelsproul)
- [`Protolambda`](https://github.com/protolambda/)

## Resources

I will add more reousrces & repos that seem important to this project.
