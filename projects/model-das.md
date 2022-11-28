# Project Proposal- Model DAS
*This is the first major iteration of my project proposal.  Ideas within this proposal are subject to change.  I'll create a rough timeline in next the version of my project proposal!*

**[Model DAS](https://github.com/EchoAlice/Model-DAS)** is a repository that aims to instantiate a Secure Kademlia DHT and blob creation+dissemination+reconstruction script that models and measures benchmarks for a possible solution to DAS Networking.

&nbsp;
## Motivation and Project Description

Danksharding has a lot of design questions still up in the air with respect to data availability sampling networking.

There are a few possible paths for p2p networking that are being explored, but nothing has been set in stone.  I want to model one of these possible networking solutions, a Secure Kademlia DHT, and benchmark measurements that will help provide insight into whether this might be a viable solution.

**Model DAS is a forked version of Proto's [dv5das](https://github.com/protolambda/dv5das) WIP repository** (written in Golang) that aims to:
- extend Geth's discv5 DHT into a secure Kademlia DHT that can be used for DAS
- create a blob script that allows for samples to be distributed across the network
- fill in other functionalities that haven't been completed within the repo
- integrate seamlessly with [Testground](https://github.com/testground/testground) to measure benchmarks for preliminary questions wrt to DAS Networking


&nbsp;
## Specification and Roadmap
*Expose functionality so S Kademlia could be integrated as an overlay network!**
*Test functionality for each benchmark within Testground.**

1.  **Integrate minimal start for Testground (WIP)**
    *What does this entail? Research Testground and Proto's original implementation that instantiates MS for repo.*

2.  **Extend Geth's discv5 to fit on top of DAS**
    *Maybe break down this benchmark...  Pretty big IMO
    - Make sure normal functionalities of the table work within my repo
    - Create fake blob data
    - Implement hash map to store sample data -->  H(Commitment, row, column)
    - Integrate Ethereum Node Records to store necessary blob data and other required metadata
    - Allow for sampling communication over Talkreq/Talkresp (Is there a better way to communicate?)
    *This is important.  Figure out how this should happen- lots of details in how this could play out*
    - Implement primary roles for the DHT:
        - Seed DHT with sample bundles as publisher
        - Fan out bundles as relayer
        - Query DHT for samples (searcher)
        - Respond to queries (host)

3.  **Create Secure Kademlia DHT logic**
    - Get in-depth understanding of Geth's discv5 DHT.  
    - Spec out how the 'secure' aspect can fit with the original Kademlia DHT.  Which functions do I need to expose and how?
    - Stub validator logic. Mark some amount of node IDs with --> validator == true
    *Important Secure Kademlia functionality*
    - Create a second routing table for each node. Only contains validators' node IDs. *First table contains both normal and validator nodes*
    - Allow for flag that switches to utilizing 2nd tier routing table when signaled as network being attacked
    - Implement [Properties and Optimizations](https://notes.ethereum.org/@dankrad/S-Kademlia-DAS#Properties) for S/Kademlia DAS from Dankrad's blog post.
    - Integrates with Geth's discv5 implementation seamlessly

4.  **Instantiate blob script**
    - Import crypto libraries
    - Post blob header. Where? Is there still some sort of global subnet for this?
    - Create real prototype original samples
    - Extend samples with erasure coding
    - Implement KZG polynomial commitments to map proofs to the header with each sample

5.  **Test blob creation, dissemination and reconstruction performance**
    - Seed sampling across the entire network
    - Sample requesting
    - Blob reconstruction

6.  **Extra Credit:**
    - Implement final open TODO from Proto: Tree balancing
    - Begin implementing [Peer scoring](https://github.com/protolambda/dv5das#peer-score) mechanisms

&nbsp;
### Current Specification Questions:
- Is there a way to test DHT functionality locally?  Probably depends on what I'm wanting to test
- How early should I be trying to integrate the repo with Testground?  Before or after creating a S/Kademlia DHT?
- How should I expose functionality so the S/Kademlia DHT could be integrated as an overlay network?  On top of... Consensus Network? Ethereum-only discv5 nodes?
- How should I expose functionality of S/K DHT to integrate with original DHT?
- Should I implement validator logic or keep it as a stub for each node?
- What's the deal with where the blob header should be placed?


---------------------------------------------------------
## Possible Challenges
- Figuring out how Testground works.  I'm sure there will be complexities
- Integrating Geth's discv5 implementation with my repository
- There are a lot of moving parts to this thing;  Harmonizing it all will be a challenge.
- Don't worry... I've got more coming in the next draft


---------------------------------------------------------
## Goals of the Project
A successful Model Danksharding looks like a test suite which...
- implements architectural designs and functionality of a Secure Kademlia DHT for DAS networking
- creates prototyped blobs, which utilizes cryptography libraries and disseminates/reconstructs original data through the network
- integrates seamlessly into a p2p networking testground
- measures benchmarks, derived from the model, which lead to insight within DAS networking problems
- is a great resource for understanding one of the most promising networking designs for Danksharding

By the end of this project, I'll be a stronger Ethereum developer with deep understanding of Danksharding. I hope to help solve future problems within this scaling solution (and Ethereum at large).

**I want to help build the thing.**


---------------------------------------------------------
## Collaborators
Independent

### Mentors
*WIP*
- Cayman 
- Dankrad? Maybe one day...
- Marius? Geth Dev and he's into blobs!


---------------------------------------------------------
## Resources

Project Repo:  [Model DAS](https://github.com/EchoAlice/Model-DAS)
Notion Board:  [Wonderland](https://www.notion.so/Wonderland-d59a677c4bdd45318e54945e6b1d5580)