# Project Proposal- Model DAS
*Ideas within this document are subject to change upon feedback from peers and mentors.*

[Model-DAS](https://github.com/EchoAlice/Model-DAS) is a Rust implementation of a Secure Kademlia DHT overlay atop the discv5 protocol, modeling one possible solution to DAS networking.


## Motivation
Full-scale Danksharding requires a lot of small pieces of data (samples), and attestations to said data, to be communicated efficiently across a large peer to peer network. 

There are a few ideas for how peers should communicate about data availability within Danksharding, but nothing has been set in stone. Model-DAS aims to provide insight into one of these possible DAS networking solutions.

"In an ideal world we have a low-latency DHT that is also sybil-resistant.  Doing all of this is an open research question."  - Alex Stokes

## Project Description

**Model-DAS is a forked version of Eric and Timofey's [das-prototype](https://github.com/ChainSafe/das-prototype) that creates a *Secure* Kademlia DHT overlay on top of [Trin's](https://github.com/ethereum/trin) implementation of Discv5.**

Eric and Timofey (from Chainsafe's DAS R&D) have been prototyping and benchmarking different DAS networking solutions within [das-prototype](https://github.com/ChainSafe/das-prototype).   One of their models creates a Kademlia DHT on top of discv5's TALKREQ rpc.  The idea for Model-DAS is to leverage their work, adding an additional routing table on top of this prototype (three routing tables in total).  This additional table will only store validator nodes and can be utilized when the network is under attack.  


See Dankrad's post, [Data Availability Sampling based on S/Kademlia](https://notes.ethereum.org/@dankrad/S-Kademlia-DAS#Optimizations) for more details on this design.

There are 4 major processes within DAS networking:
    - Seeding the network with sample bundles as publisher
    - Fanning out bundles as relayer; dissemination
    - Query peers for samples (searcher)
    - Respond to queries (host)

Model-DAS will primarily focus on modeling the S/Kademlia DHT as it pertains to querying samples.

&nbsp;
## Specification and Roadmap
### Part 1:  Lay Groundwork (12/6/22 - 12/19/22)
1. Fork and download repository.  Run previously implemented simulation cases within das-prototype to get a feel for how the repository works
2. Get in-depth understanding of Timofey's Kademlia DHT overlay and how it integrates with the rest of the repository
3. Understand what functionality should be exposed/what's needed to create a [simulation case](https://github.com/ChainSafe/das-prototype/issues?q=is%3Aissue+is%3Aclosed+label%3A%22simulation+case%22) within das-prototype
4. Stub out where and how the new routing table will fit within the repository. Stub validator logic within ENR

### Part 2:  Instantiate Validator Routing Table (12/20/22 - 2/15/23)
1. Add additional logging if necessary
2. Create Validator Routing Table
3. Integrate the additional routing table with original Kademlia DHT overlay. 
Nodes should now have 3 routing tables:  
&nbsp;&nbsp;    a.&nbsp;&nbsp; Normal discovery routing table for all peers
&nbsp;&nbsp;    b.&nbsp;&nbsp; Overlay Kademlia DHT routing table that supports FIND_VALUE RPC queries (Timofey's)
&nbsp;&nbsp;    c.&nbsp;&nbsp; Secure routing table with same functionality as overlay routing table, but only stores validator nodes.
4. Write tests that verify peers can communicate with one another through the newly implemented table
5. Pre-populate the DHT.  Make sure random sampling works
6. Create new parameters within CLI tailored to validator-only benchmarks  

### Part 3:  Measure Benchmarks (2/16 - Eth Denver)
*Open to benchmarking suggestions!*

Run simulations and write up findings from benchmarks.

&nbsp;&nbsp; **Efficiency**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    - Time it takes network to switch from main overlay table to validator-only table
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    - Latency of sample querying:  normal overlay routing table vs validator-only routing table
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    - Extra storage needed per node

&nbsp;&nbsp; **Security:**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    - Look into the ratio of normal peers/validator peers when under attack.  Network might not have to only rely on validators.  What's the ideal ratio here?







### Part 4: Future Topics to Explore/Model (TBD)
- Implement logic to check for validator public keys, remove stubbed validator logic
- Create functionality that allows the network to know when it's under attack
- Build out a blob creation+dissemination+reconstruction module to use within tests
- Model [Peer scoring](https://github.com/protolambda/dv5das#peer-score) mechanisms

&nbsp;
## Goals of the Project
A successful Model DAS...
- implements architectural designs and functionality of a Secure Kademlia DHT for DAS networking
- measures benchmarks, derived from the model, which lead to insight within DAS networking problems

By the end of this project, I'll be a stronger Ethereum protocol developer with deep understanding of Danksharding. I hope to help solve future problems within this scaling solution (and Ethereum at large). 

**I want to help build the thing.**

&nbsp;
## Collaborators
Independent,

But working along-side Eric and Timofey (Chainsafe DAS research developers) and utilizing their repositories.

I may be able to help contribute to building out their peer to peer tooling for prototyping DAS models along the way.

### Mentors
- Cayman 
- Dankrad
- Fredrik?  (Alex recommended to reach out)


## Current Proposal Questions:
- Should I stub out the underlying discv5 table and only work with the overlay routing tables?
- Is the process of creating the validator table more complex than making a few modifications to Timofey's overlay table?  
  Dive into the repository, expand on "Create Validator Routing Table" in Part 2.
- How does the validator routing table change engineering details wrt communication between peers?
- Should there be different parameters/types of parameters for this validator-only table?
- When should I add [optimizations](https://notes.ethereum.org/@dankrad/S-Kademlia-DAS#Optimizations) as suggested by Dankrad?


## Resources

Project Repo:  [Model DAS](https://github.com/EchoAlice/Model-DAS)
Notion Board:  [Wonderland](https://www.notion.so/Wonderland-d59a677c4bdd45318e54945e6b1d5580)