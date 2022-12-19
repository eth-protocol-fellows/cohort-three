# Project Template

We will use the [Open Game engine](https://github.com/philipp-zahn/open-games-hs) to model the compositional structure of contracts and games in the PoS protocol to model and find sources of MEV. 

## Motivation

The execution of contracts and the rules of the protocol can expose extractable value to block miners/proposers in the Ethereum system. Generally, this value (MEV) does not originate from a single entity, but rather from the way different parts of the system interact (for example, an arbitrage that requires multiple marker makers and transactions). Because of this, it is hard to understand or predict what choices or contracts expose MEV. This, however, is of crucial importance to developers of contracts, designers of the protocol mechanisms, and block proposers. 

## Project description

To address this issue of the compositional nature of MEV, [20squares](https://20squares.xyz) is running an [ESP supported project](https://blog.ethereum.org/2022/12/07/esp-allocation-q3-22) that aims to develop an open game engine backend for the [ACT specification language](https://github.com/ethereum/act), already used throughout the Ethereum ecosystem. Parallel to, and in coordination with, that project, I will implement some known games and MEV mechanisms in the Open Game engine to analyse different ways in which ways the compositional structure and MEV strategies can be represented. 

## Specification

As the Open Game engine is a DSL on top of Haskell, the internal types and logic of the models will be implemented as Haskell functions. A first example is shown in [this update](https://abeljansma.nl/2022/12/15/EPF8.html). However, ideally the open boundary of the games should be exploited to make composition explicit, so some of the complexity should be transferred from Haskell to the Open Game DSL. 

## Roadmap

### Regular updates are posted [here](https://abeljansma.nl/2022/10/18/EPF0.html).
### Rough outline
- First month: Familiarise myself with Haskell and the Open Game engine. 
- Second month: Learn about practical examples of MEV (e.g. from the [Clockwork Finance](https://arxiv.org/pdf/2109.04347.pdf) paper) and implement analysis of these in the Open Game DSL. 
- Third Month: Convert contracts directly (by hand) to open games.
- Afterwards: Coordinate with CyberCat & 20squares to see what would be useful for them. 

## Possible challenges

- How to make analysis of complex strategies tractable? In small tests, block sizes beyond 8 transactions already took minutes to analyse. Parallelisation of the equilibrium analysis is in development, which might mediate this to an extent. Still, smarter (i.e. non-brute force) ways to come up with strategies might be necessary. 
- Is the most natural way to model open contracts also what one can compile ACT into?

## Goal of the project

A natural way to model the compositional structure of value and information flow between agents and contracts, and a quantification of the exposed MEV. 

## Collaborators

### Fellows 
No other fellows are involved.

### Mentors
[Barnabé Monnot](https://barnabemonnot.com) at the[ Robust Incentives group](https://ethereum.github.io/rig/).

### External
The research team from [20squares](https://20squares.xyz) and the [CyberCat Institute](https://cybercat.institute/people/). 

## Resources

- [My fork](https://github.com/AJnsm/open-games-hs) of the [Open Game engine repo](https://github.com/philipp-zahn/open-games-engine)
- [This is MEV](https://www.youtube.com/watch?v=8qPpiMDz_hw)
- [Clockwork Finance](https://arxiv.org/pdf/2109.04347.pdf)
- [Bayesian Open Games](https://arxiv.org/abs/1910.03656)
- [Diegetic Open Games](https://arxiv.org/pdf/2206.12338.pdf)
- [Composing games into complex institutions](https://arxiv.org/pdf/2108.05318.pdf)
- [Compositional Game Theory](https://arxiv.org/abs/1603.04641)