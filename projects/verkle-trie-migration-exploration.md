# Verkle Tries migration exploration

Help the research and engineering teams in whatever is necessary to succeed in the future Verkle Tries migration.

## Motivation

The switch from Merkle Patricia Tries (MPT) to Verkle Tries (VT) is part of the *Verge* phase. This phase, particularly Verkle Tries, will allow for truly stateless clients. Having stateless clients will be one of the most impactful changes aligning Ethereum to its main ethos: decentralization.

This switch from MPT to VT is a really hard problem for multiple reasons:

- It touches the way that all clients store network data.
- It changes how gas accounting will be calculated.
- It changes the block structure.
- It changes how Ethereum state proofs work.
- It changes the underlying cryptographic primitives from simple and mature ones (i.e: Keccak hashes), to more complicated and computationally expensive ones (i.e: Elliptic Curve math).

A more decentralized Ethereum is a stronger Ethereum, and we need to allow anyone to become a network validator without expensive hardware, high-bandwidth costs, or extra trust assumptions. Verkle Tries main intention is to try to achieve this.

## Project description

I’m a computer engineer that likes the sweet spot between engineering and research. My intuition before starting this project was that there were probably a lot of things to help with:

- The switch of cryptographic primitives can incur new computational costs that can affect validators’ hardware. I’ll dive into building reference benchmarks to understand this cost and how much it can be improved compared to other state-of-the-art implementations.
- Doing a data structure migration isn’t only about a spec on how the new data structure works but also is an engineering problem on how to do the switch without impact since there’s an existing state of being migrated. I’ll try to understand more about how this *switch* will happen and have an idea of the risks.
- The people working on these today have done great talks and blog posts that describe what this is all about. I still think people should understand more about how this works and why it is important. I’m open to help in writing documentation or technical blog posts to raise awareness of why this work is important. It can also bring more attention so more people can help.

I’ll have an open mind in this project, so I can ask or sense my mentor's current pain points and help them if possible. I’ll try to balance doing exploratory work and mainstream work that can be useful today and in the future.

## Specification

Two main forces will guide my work:

- My intuition as an engineer and amateur researcher is to build a mental model of the problems and solutions.
- Talking with my mentors to understand their current challenges and verify my understanding.

My solution will consist of the following:

- Detailed public documents (e.g., HackMD docs) that will do an in-depth analysis of details about the problem to be solved. This helps document and onboard more people into current affairs and challenges.
- Take a data-driven approach to validate hypotheses and bottlenecks. I’ll create reproducible benchmarks available in open-source repos that anyone can verify and reproduce. The idea is that all the work can keep evolving and isn’t lost in some code snippet.
- Open PRs into relevant repos to help with needed work (e.g: [go-ethereum](https://github.com/ethereum/go-ethereum), [go-verkle](https://github.com/gballet/go-verkle), [go-ipa](https://github.com/crate-crypto/go-ipa))
- Open discussion with mentors in #verkle-trie-migration so we can have a history of discussions and help raise awareness of some of the current work with Verkle Tries.

## Roadmap

Since there’s a lot of work happening quite fast in this area, it’s a bit hard to have a meaningful and stable roadmap; but I’d imagine the following steps:

- Gain an understanding of Verkle Tries specification and new cryptographic primitives.
- Gain an understanding of the impact of this switch coming from MPTs. Build some reference benchmarks and structure analysis to gain more knowledge of the overhead we’re buying with the switch.
- Explore potential solutions and performance improvements in all the found bottlenecks and hotspots. If possible, implement them and improve the current implementations.
- After being deeper into the VKT work track, take a step back and think about how we can help new people be onboarded to this topic. Can we (if worth it) craft a single document that can be the best place anyone can land to understand how VKT works and what is happening today?
- Consider taking a similar approach as with *The Merge*, and think of agnostic test vectors that can be helpful for other clients when they start working on Verkle Tries. Knowing that everyone has a green check on core tests to validate would be not only useful for core developers but catch bugs before more clients are onboarded to VKT testnets.

The above is a general strategy for multiple tracks of work happening simultaneously. There’re many layers involved in Verkle Tries, and probably all of them can benefit from this approach in parallel.

## Possible challenges

The main challenge is that Verkle Tries are still in an early phase, so despite their known problems today, I think they’ll continue to evolve during this program. Hopefully, if I can help the current team working on this to solve some problems, other new ones will appear, so it’s a fast-moving target.

I also think it’s very hard to predict how long some tasks will take since I’m trying to get closer to attacking open problems or potentially unknown unknowns. Also, my strategy is to add the least amount of overhead to my mentors since I’m fine with reading code for understanding or doing my research (this can be slower but more fruitful in the long term).

## Goal of the project

I’d summarize what success looks like for this project with a simple question that I’d like to ask myself at the end of the program:

- If you compare how VKTs worked and the main challenges that existed when the program started and how it is today (i.e: ~Feb 2023): was my work useful to make those improvements and overall progress?

If the answer is yes, I’d call it a success. I’m not here to be a hero but just a small part of a brighter Ethereum for the future. I like building for the long term, and probably anything I can help today might be useful in months or years.

## Collaborators

This section describes the collaborators of this project.

### Fellows

- Ignacio Hagopian ([https://github.com/jsign](https://github.com/jsign))

### Mentors

- Guillaume Ballet ([https://github.com/gballet](https://github.com/gballet))
- Kevaundray Wedderburn ([https://github.com/kevaundray](https://github.com/kevaundray))
- Dankrad Feist ([https://github.com/dankrad](https://github.com/dankrad))

## Resources

This section contains relevant work links of this project:

- Written public documents:
    - [Verkle Tries exploration about keccak vs pedersen commitments](https://hackmd.io/@jsign/verkle-tries-exploration-about-keccak-vs-pedersen-commitments)
- New repos:
    - https://github.com/jsign/verkle-vs-patricia (own repository for MPT vs VKT benches and explorations)
- [go-verkle](https://github.com/gballet/go-verkle) (Geth implementation of Verkle Tries):
    - https://github.com/gballet/go-verkle/pull/290
    - [https://github.com/gballet/go-verkle/pull/291](https://github.com/gballet/go-verkle/pull/291)
- [go-ipa](https://github.com/crate-crypto/go-ipa) (Go cryptographic primitives for `go-verkle`):
    - https://github.com/crate-crypto/go-ipa/pull/26
    - https://github.com/crate-crypto/go-ipa/pull/30
- [#verkle-trie-migration Discord channel](https://discord.com/channels/595666850260713488/824798757618188339)