# Model Danksharding 
*~Rough Draft~   The real deal is in the works now!  See this week's [Dev Update](https://hackmd.io/3tD1zgNqSkalAuUAjMyf0w?view#Development-Update-3-v1)*

Model Danksharding is a python test suite that aims to instantiate a Secure Kademlia DHT and blob creation/dissemination script to model a possible solution for DAS networking.  

&nbsp;
## Motivation and Project Description

Danksharding has a lot of design questions still up in the air with respect to DAS networking.  There are a few paths that have been thought about/prototyped but nothing has been set in stone.  I want to implement one of these possible networking solutions, a Secure Kademlia DHT, and benchmark measurements that will help provide insight into whether this might be a viable solution.

&nbsp;
## Specification and Roadmap
*WIP*

A 2nd draft of my project proposal is being reviewed by Cayman.  I'll be reaching out to Dankrad once Cayman's reviewed the proposal again.  

*Specification and Roadmap will be drawn out in the next draft of the templet!*

&nbsp;
## Possible Challenges

- Creating bindings for a Discv5 implementation if there's no working python implementation 
- Understanding how to design the model elegantly, for easy interpretation and integration with a testnet
- *There are a lot more...  Iterating on this within next draft*

&nbsp;
## Goal of the Project

A successful Model Danksharding looks like a test suite which...
- implements architectural designs and functionality of a Secure Kademlia DHT for DAS networking
- creates prototyped blobs, which utilizes cryptography libraries and disseminates/reconstructs original data through the network
- integrates seamlessly into a p2p networking testground
- measures benchmarks, derived from the model, which lead to insight within Danksharding's DAS networking problems
- is a great resource for understanding one of the most promising networking designs for Danksharding

By the end of this project, I'll be a stronger Ethereum developer with deep understanding of Danksharding. I hope to help solve future problems within this scaling solution, (and Ethereum at large) and implement the thing.

&nbsp;
## Collaborators
Independent

### Mentors
*WIP*
- Cayman 
- Dankrad (Hopefully)  <-- Waiting on revised proposal feedback from Cayman before reaching out
- Marius???  He said he likes blob things. Maybe one day...

## Resources

Project Repo:  [Model Danksharding](https://github.com/EchoAlice/Model-Danksharding)
Notion Board:  [Wonderland](https://www.notion.so/Wonderland-d59a677c4bdd45318e54945e6b1d5580)