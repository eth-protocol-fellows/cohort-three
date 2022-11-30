# Dynamic Sharding

Using AI(PSO/ML) to optimize the load balancing to provide a dynamic sharding 

## Motivation

The majority of sharding proposals are static in nature as they cannot be adjusted. These proposals are insufficient to meet the upcoming demand since blockchains are expected to operate for many years without interruption. To fully take advantage of the parallelism of a sharded blockchain, the processing load of shards must be equally distributed. In practice, however, the problem of computing balanced workloads is further complicated by the fact that transaction processing times are unknown prior to shard allocation.

A number of issues remain to be resolved in regards to the design of the DAS networking for Danksharding. I intend to implement one of these possible networking solutions, a dynamic schema based on memory pools and block propagation. This will provide insight into whether this might be a viable option. It aims to develop a flexible sharding algorithm that will pave the way for Danksharding solutions to be implemented within the Ethereum ecosystem in the future. We aim to provide a more scalable implementation of sharding that is ready for everyday use.
## Project description

We present dynamic blockchain sharding, a technique for creating and closing shards and adjusting their size based on demand. This idea involves reconfiguring sharding. In addition to improving security, this method also makes sharding reconfiguration as transparent as the rest of the data on the blockchain. The purpose of this project is to introduce a dynamic workload-balancing algorithm in which the strategy for allocating transactions to shards is periodically adjusted according to the recent workload history of each shard. We use artificial intelligence techniques in order to learn these histories and to attempt to forecast for future periods. The model we propose is an intelligent load-balancing algorithm that has been adapted for sharded blockchains. In line with network-based applications such as blockchains, it is a fully distributed algorithm. Second, and more generally, the project aims to make progress in the research area of application sharding implementations for post-merge Ethereum.

But I still need to consult with mentors about the details of the project to ensure it is relevant and useful. In the next draft, we will include more detailed information about the project.
## Specification

- The development of the learning model is based on the PSO/ML approach
- A diffusion algorithm for balancing the load on a sharded blockchain
- An approach to modeling dynamic sharding based on mempool and block propagation parameters
This part will be updated on an ongoing basis.
## Roadmap

I need to make sure about the project specification after reaching out to mentors and then I will provide a detailed roadmap.
## Possible challenges

- The first challenge is that sharding implementation is at an early stage, so determining the requirements will be a challenge.
- It is necessary to understand the sharding problem and its multi-objective nature.
- In order to solve the sharding problem effectively, we must find the most appropriate model incorporating all of the various parameters that are influential.
- Additionally, finding an easy way to integrate the proposed model with the core would be a challenge.
## Goal of the project

When I have completed the following steps, the project will be completed:

- A satisfactory solution was found to the problem of sharding, and a proper model of the problem was developed.
- Testing and development have been completed for the AI model.
- A more scalable sharding implementation is demonstrated by the proposed model.
- Make a contribution to the existing implementation of sharding solutions within the core ecosystem.
## Collaborators

### Fellows 

Independent

### Mentors

- Fredrik
- Dankrad Feist(??)

## Resources

This section contains relevant resources of this project:

- Background reading and implementation
  - https://notes.ethereum.org/@vbuterin/proto_danksharding_faq#Proto-Danksharding-FAQ
  - https://research.thetie.io/danksharding-ethereums-scalability-killer-post-merge/
  - https://github.com/ethereum/consensus-specs/blob/dev/specs/phase0/fork-choice.md
  - https://notes.ethereum.org/@vbuterin/serenity_design_rationale#Sharding---or-why-do-we-hate-supernodes
  - https://ethereum.org/en/upgrades/sharding/
  - https://notes.ethereum.org/@dankrad/new_sharding
  - Cybenko, G.: Dynamic load balancing for distributed memory multiprocessors. https://doi.org/https://doi.org/10.1016/0743-7315(89)90021-X
