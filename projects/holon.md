# Holon (Rollup analytics software suite)

Holon is a software service geared towards collecting and processing L1 block to data to produce insights about rollup activity on Ethereum. It is designed to run alongside an Ethereum full node.

(Holon video presentation(16 min))[https://www.youtube.com/watch?v=m94kB8SxO4U]

## Motivation

There are not many services that illustrate/communicate about how L1 blockspace is leveraged by rollup solutions (be it data availability, or arbitration). While there are some websites/services (described further below) and L1/L2 block explorers to help describe L2 activity and cross-domain messaging, I believe a rollup analytics service designed to be run alongside an Ethereum full node may prove useful to various parties interested in research or running live services between L1 and L2 solutions.

Currently the rollup analytics landscape includes projects such as [L2Beat](https://l2beat.com/scaling/tvl/) and various [Dune dashboards](https://dune.com/niftytable/rollup-economics). L2Beat serves as more of an educational resource around L2 scaling rather than a verbose L2 analytics service, and while their L2 solution profiles provide excellent context for researchers, the site is fairly light on metrics. Meanwhile, Dune contains a lot of data to work with, however there are clear limits to how expressive we can truly be in producing complex insights using SQL queries. To circumvent the SQL limitation of Dune, one could argue that use of the upcoming Dune API solves this, however this will likely not be cheap given how expensive such network requests will be.

With the context provided above, I believe there is room for improvement in introducing a service that carefully collects and curates on-chain information associated with rollups.

## Project description

The main goal with this project is to produce a software suite fully capable of performing highly specific data collection and analysis to produce insights around rollup activity on Ethereum.

The motivation for building this software is rooted in a desire to produce data-rich insights based on the highly-specific context of rollup systems. These goals can be achieved with the modular approach being leveraged in this software suite that is designed to perform highly-specific processing of block information pertaining to rollup solutions.

The project is in its infancy stage, but the core decisions around architecture and technologies being utilised are mostly finalised (e.g. databases, caches, messaging protocols being used). There are many other components and sub-processes that are currently being worked on.

> NB: this service will be designed to run alongside an Ethereum full node!

<div style='display: flex; justify-content: center;'>
<image src='https://storage.googleapis.com/rollup-research/holon-arch-2.png'>
</div>

## Specification

The service will leverage multi-container communication enabling easy deployment and a separation of concerns thus making management of the service easier. Furthermore, such a decision provides a clear, modular architecture sets the stage for extending the service at a later stage.

As Holon is designed to be a specialised software suite delivering analytics and insights about various rollup solutions, there are various core features that aiming to be provided such as providing data like:

- <b>Calldata-related information such as transaction batches (including metrics around their size, L1 publication costs, bandwidth burdens on L1)</b>.
- <b>State root proposals submitted to rollup contracts on L1</b>.
- <b>Proof-related messages</b>.
- <b>Withdrawal/Deposit messages</b>.
- <b>Blob transaction utilisation by rollup solutions (including blobspace distribution leveraged by calldata and proof-related information)</b>.

Fundamentally, these are some of the insights that we can derive by inspecting and processing rollup-related transactions made to L1. In addition to producing these insights, Holon also intends to provide features like:

- <b>Historical analysis of rollup-related metrics</b>.
- <b>Aggregated metrics and comparisions between different rollup solutions</b>.
- <b>The ability to toggle which rollups you want to acquire insights about</b>.

<br>

### Progress Report
As mentioned above, the project is currently in its infancy stage, but the system architecture is mostly implemented and being worked upon. At the present moment only <b>Optimism</b>'s optimistic rollup is being tested and collecting data such as state root proposals and calldata publication transactions but insights have yet to be produced. The focus has been on architecture for the most part but as development work has been slowly producing the reliable behaviour required, this is due to make the implementation of the functional requirements very simple and intuitive.

<u>Please refer to this video here for a detailed presentation about the current state of the project</u>: [Holon Presentation (16 minutes)](https://www.youtube.com/watch?v=m94kB8SxO4U&t=4s)

## Possible challenges

- Scope creep (addition of extra features).
- Lack of context around measuring more nuanced dynamics despite the presence of empirical data.
- Volume of development by a single person (the scope is manageable but certainly would be quicker if more people could work alongside myself).

## Goal of the project

The goal is to provide a well-designed and accessible software service to acquire meaningful information about rollup activity on top of Ethereum.

As we move more towards a rollup-centric roadmap, the way we discover and interpret rollup data will become more important to various actors ranging across users, DApp developers, validators, cross-domain MEV searchers, optimistic security actors (fraud proof challengers), researchers and more.

If such a service benefits any of the above-mentioned actors, I would consider the project to be successful. I see the project as having a MVP milestone and beyond that a capability of being an actively maintained open-source effort if meaningful adoption ensues.

## Collaborators

### Fellows

Currently developing this alone but I am in communication with several people doing research work with the Robust Incentives Group (RIG).

### Mentors

Consulting with Barnabé Monnot.

## Resources

TBC
