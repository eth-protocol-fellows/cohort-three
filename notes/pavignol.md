# pavignol's Notes
## Introduction
Hi, I'm Pat! I haven't decided on a project yet, but so far I've been leaning towards the Prysm Beacon API compatibility.

## Updates
### Update 1 (2022/24/10)
- I cloned the Prysm repo and started looking through the codebase for references to the Beacon API.
- I found [this PR](https://github.com/ethereum/beacon-APIs/pull/242) that was merged recently, which led me to the [API specification for the beacon node](https://github.com/michaelsproul/beacon-APIs/blob/master/beacon-node-oapi.yaml)
- The API specification yaml file lists a bunch of endpoints, which all reside in their own yaml file.
- The API spec mentions [SSZ data](https://github.com/michaelsproul/beacon-APIs/blob/e36b026ef1265dba9b9c6bc984236088d3759f87/beacon-node-oapi.yaml#L11), which is not a serialization format that I've heard before. After a google search, I stumbled upon [this link from the ethereum website](https://ethereum.org/en/developers/docs/data-structures-and-encoding/ssz/) that explains how it works.

    SSZ is a deterministic serialization format that is supposed to be easy to Merkleize. It can be split into 2 components: Serialization/Deserialization and Merkleization
    - Serialization
        - Represents objects of arbitrary complexity as strings of bytes
        - Contains 2 basic types, why are serialized as hexadecimal bytes: **unsigned integers** and **booleans**
        - Complex types with **fixed** lengths are serialized by joining the little-endian bytestrings of each element
        - Complex types with **variable** lengths are serialized by having an offset to the element's position in the serialized object. The data gets added to the heap at the end of the serialized object that the offset points to. Refer to the examples on the [SSZ page](https://ethereum.org/en/developers/docs/data-structures-and-encoding/ssz/) for an illustration of how offsetting works, or refer to the [SSZ spec](https://github.com/ethereum/consensus-specs/blob/dev/ssz/simple-serialize.md) for the complete specification.
    - Deserialization
        - Requires the schema of the serialized object
        - Allows all information of the serialized object to be reinstantiated, including the field names
        - [ssz.dev](https://www.ssz.dev/overview) has a good interactive explainer
    - Merkleization
        - Serialized objects can easily be merkleized into a Merkle-tree
        - The number of leaves in the tree is the number of 32-byte chunks in the serialized object
        - If the number of 32-byte chunks is not a power of 2, additional empty leaves (32 bytes of zeros) are added
        - Each parent in the tree is a hash of their 2 immediate children:
        ```
                hash tree root
                    /     \
                   /       \
                  /         \
                 /           \
           hash of leaves  hash of leaves
             1 and 2         3 and 4
              /   \            /  \
             /     \          /    \
            /       \        /      \
          leaf1     leaf2  leaf3     leaf4
        ```
        - The tree is not necessarily perfectly balanced; some elements can be more complex and require more depth
        - Elements can easily be identified by generalized indices. The generalized index of each element can be retrieved by the following formula: `2**depth + idx`, where `idx` is the zero-indexed position of the element in the serialized object.
        - Generalized indices can be used to prove that any new data inserted into the tree doesn't change the root, which means the data is valid.