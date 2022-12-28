# Untitled Rollup Service (Run alongside L1 full node)

A configurable service dedicated towards collecting, recording and processing rollup-related data posted by rollup systems leveraging Ethereum for data availability.

## Motivation

There are not many services that illustrate/communicate about how L1 blockspace is leveraged by rollup solutions (be it data availability, or arbitration). While there are some websites/services (described further below) and L1/L2 block explorers to help describe L2 activity and cross-domain messaging, I believe a rollup analytics service designed to be run alongside an Ethereum full node may prove useful to various parties interested in research or running live services between L1 and L2 solutions.

Currently the rollup analytics landscape includes projects such as [L2Beat](https://l2beat.com/scaling/tvl/) and various [Dune dashboards](https://dune.com/niftytable/rollup-economics). L2Beat serves as more of an educational resource around L2 scaling rather than a verbose L2 analytics service, and while their L2 solution profiles provide excellent context for researchers, the site is fairly light on metrics. Meanwhile, Dune contains a lot of data to work with, however there are clear limits to how expressive we can truly be in producing complex insights using SQL queries. To circumvent the SQL limitation of Dune, one could argue that use of the upcoming Dune API solves this, however this will likely not be cheap given how expensive such network requests will be.

With the context provided above, I believe there is room for improvement in introducing a service that carefully collects and curates on-chain information associated with rollups.

## Project description

The project being proposed is a software suite which runs on the same machine operating an Ethereum full node. This software suite describes a configurable service that watches for rollup-related interactions on-chain. It will consist of the following features:

- Easy setup (docker compose script spinning up containers with created images).
- Scraping rollup batch publication and cross-domain messaging events in autonomous fashion (empirical data and insights deduced from such).
- Producing insights such as aggregated publication costs incurred by rollups, value inflow/outflow pertaining to rollup TVL and more.
- Configurable service settings to change or add crawling of arbitrary account interactions.
- Seeder utilities to acquire data within any data range including from Genesis to present.
- API to interact with the service.
- Admin UI to configure service settings and view analytics data.

> NB: this service will be designed to run alongside an Ethereum full node!

## Specification

The service will leverage multi-container communication enabling easy deployment and a separation of concerns thus making management of the service easier. Furthermore, such a decision provides a clear, modular architecture sets the stage for extending the service at a later stage.

The components of the system are as follows:

- <b>Scraper</b>: communicates directly with the full node via JSON-RPC and collects and processes data autonomously.
- <b>Worker</b>: handles jobs such as seeding as well as processing batch jobs to abstract blocking work from the API service.
- <b>API</b>: capable of configuring scraper settings, querying data and insights from storage, and other client requests.
- <b>Database</b>: persistant data store that records various sets of data and relationships to be (or have been) processed.
- <b>Cache</b>: Cache specific data to optimise for API request/response speed.
- <b>Dashboard</b>: local web application to configure service settings as well as viewing analytics collected and produced by the service.

The diagram below gives a higher-level overview of the service architecture in the context of the environment it is designed to run in:

<div style='display: flex; justify-content: center;'>
<image src='https://storage.googleapis.com/rollup-research/architecture.png'>
</div>

<br>

## Roadmap

Estimating a 2 month period of work to see this project (and what has been mentioned in the specification) to completion.

### Work Done

There are several components that have already been developed and used in practice over the period of November/December (pertaining to the <b>Worker</b> and <b>Scraper</b>):

- Scraper architecture planned out (serves role of being a WebSockets server that streams data to other microservices).
- Scraping and seeding all batch publication transactions from Optimism regenesis to head of the chain functionality has been developed as well as scraping of cross-domain messaging across both Arbitrum and Optimism with Ethereum respectively
- Database controller methods.

### Todo

- Set up containerisation architecture and YML configurations for the containers and inter-process communication.
- Build up the API and Dashboard microservices.
- Discuss analytics approach with rollup economic researchers (identify potential heuristic techniques to leverage in generating insights).
- Explore health check schemes for the service.
- Custom garbage collection/log rotation scheme decisions.

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
