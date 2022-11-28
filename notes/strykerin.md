# strykerin notes

Doc for notes and resources collected on projects I am researching

## Updates

(18/10/2022 ~ 19/10/2022)

- Understand how Ethereum works in terms of eth-research, the spec, client implementations, and nodes. [Ethereum Explained: Research, Spec, Clients, & Nodes](https://www.youtube.com/watch?v=vzgNqO_obH4)
- [Read about Recursive Length Prefix (RPL)](https://medium.com/coinmonks/data-structure-in-ethereum-episode-1-recursive-length-prefix-rlp-encoding-decoding-d1016832f919)
- [Read Ethereum Yellow Paper Walkthrough articles](https://www.lucassaldanha.com/ethereum-yellow-paper-walkthrough-1/)
- Understand how addresses are generated. [A deep dive into Ethereum Addresses](https://www.youtube.com/watch?v=VRVAiVBNQ_E)
- Begin reading geth code on RLP following [this geth code walkthough](https://www.youtube.com/watch?v=ec6TxiGE_s8&t=635s) (`encode.go` and `encode_test.go` files)

(20/10/2022 ~ 21/10/2022): Focused on studying the networking layer of Ethereum

> [Here are my notes](https://hackmd.io/@jjeynlY4TTyXAPDIkvF7Rg/BJ5MhDWNs) from the research on the articles below:

- [Read about the overview of the Ethereum Networking Layer](https://ethereum.org/en/developers/docs/networking-layer/)
- [Read about Kademlia](https://medium.com/coinmonks/a-brief-overview-of-kademlia-and-its-use-in-various-decentralized-platforms-da08a7f72b8f)
- [Read about dhts](https://en.wikipedia.org/wiki/Distributed_hash_table)
- Read about Ethereum node Records (ENR):
  - <https://ethereum.org/en/developers/docs/networking-layer/#enr>
  - <https://ethereum.org/en/developers/docs/networking-layer/network-addresses/>
  - <https://github.com/ethereum/devp2p/blob/master/enr.md>
- [Begin reading the discv5 specification](https://github.com/ethereum/devp2p/blob/master/discv5/discv5.md)
- [Begin reading the devp2p specification](https://github.com/ethereum/devp2p)

(22/10/2022)

- Added my notes [here](https://hackmd.io/@jjeynlY4TTyXAPDIkvF7Rg/BJ5MhDWNs) for my research on consensus layer networking.
- [Overview of Ethereum Light Clients](https://www.youtube.com/watch?v=zxQvEEY9e4k)
- [Lodestar light client demo](https://www.youtube.com/watch?v=fTd9IQO7GOE)
- [EIP-778: Ethereum Node Records (ENR)](https://eips.ethereum.org/EIPS/eip-778)
- [From Kedemlia to discv5](https://vac.dev/kademlia-to-discv5)
- [Ethereum Explained: The EVM](https://www.youtube.com/watch?v=kCswGz9naZg)
- [Ethereum Virtual Machine Opcodes](https://ethervm.io/)

### Week 2

This week I started reading Hive code to better understand how it works. Also, I reviewed Docker since it's a lot used on this project.

This week I also read the ethereum-js client implementation of discv5.

### Week 3 and Week 4

This week I focused on going deeper on the [devp2p specs](https://github.com/ethereum/devp2p) and reading and debuging the devp2p implementation on geth.

I compiled here below the best talks about the p2p networking on ethereum I found this week:

- [Ethereum P2P Networking / Sharding by Felix Lange and Péter Szilágyi in Taipei, March 2018](https://www.youtube.com/watch?v=qJA6J0mP73w)
- [A Deep Dive into Go Ethereum](https://www.youtube.com/watch?v=c4N79UXZqSc&t=133s)
- [Networking: Dev P2P, RPLx, Discovery, and Eth Wire Protocol](https://www.youtube.com/watch?v=CncTBr_a1Zk&t=654s)
- [4 part video series going deeper on the p2p module on geth](https://www.youtube.com/watch?v=SRG1wzzSdes)
