# Ethereum Protocol Fellowship Program 2022 - Cohort Three

## 💾Data Analysis of Consensus Clients

:computer: **Code: https://github.com/kevinbogner/data-analysis-consensus-clients**.

## Journal
**[10/14/2022]**
- Updated README.md.

**[10/13/2022]**
- Fetching [block's data](https://user-images.githubusercontent.com/114221396/195835697-98904eae-5f4f-46ae-a113-708e6e6760c1.png) from https://beaconcha.in/.
- Fetching [data of skipped slots](https://user-images.githubusercontent.com/114221396/195837203-b616384b-3e27-4d39-bb60-ce2a084b5eb7.png) from https://beaconcha.in/.

**[10/12/2022]**
- [Merged Data](https://user-images.githubusercontent.com/114221396/195393208-22f25978-e616-4cb5-94db-a5483a13d4ad.png) of Clients and Rewards.
- [Overview](https://user-images.githubusercontent.com/114221396/195393717-a99d6698-29ed-4965-b73b-fa136499a4ba.png) of fetched Data.

**[10/11/2022]**
- [Fetched data](https://user-images.githubusercontent.com/114221396/195311091-ec87b902-5954-40f6-a23e-c7ed193b6f7b.png) from [blockprint](https://github.com/sigp/blockprint).
- [Fetched data](https://user-images.githubusercontent.com/114221396/195311259-010cdd73-0a01-445b-987f-7d34f95cf84c.png) from https://beaconcha.in/.

**[10/10/2022]**
- [Table](https://user-images.githubusercontent.com/114221396/194887188-86056520-642b-4961-b09c-079fdca08486.png) with manually injected data.

**[10/09/2022]**
- Implement Etherscan API to [getReward](https://docs.etherscan.io/api-endpoints/blocks#get-block-and-uncle-rewards-by-blockno).
- [Flowchart](https://user-images.githubusercontent.com/114221396/194756321-49beb9f3-c710-4678-a667-2190920ce963.png) of Process.

**[10/08/2022]**
- Research on [Attestations](https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/attestations/) & [MEV-Boost](https://boost.flashbots.net/).
- Asking for [guidance](https://user-images.githubusercontent.com/114221396/194708102-d20af266-4912-4f05-81c8-db54e1ef850d.png) in R&D Discord.

**[10/07/2022]**
- Published [Dev Update #1](https://hackmd.io/@lODlsf2CR9uWlyIyEdjjPQ/HkeQ_Qnfi).
- [Tweet](https://twitter.com/kevin_bogner/status/1578353105623601152) about [Dev Update #1](https://hackmd.io/@lODlsf2CR9uWlyIyEdjjPQ/HkeQ_Qnfi).

**[10/06/2022]**
- Started writing [Dev Update #1](https://user-images.githubusercontent.com/114221396/194361684-e8f2f590-1dd2-4e39-ac20-7f1899eeebc2.png), which I will probably finish tomorrow.

**[10/05/2022]**
- Got private API of [blockprint](https://github.com/sigp/blockprint) from [Michael Sproul](https://twitter.com/sproulM_).
- Added [Axios](https://github.com/axios/axios) to fetch public API.
- Setup a proxy to [Heroku](https://dashboard.heroku.com/apps) to avoid CORS errors ([Guide](https://stackoverflow.com/questions/43871637/no-access-control-allow-origin-header-is-present-on-the-requested-resource-whe)).
- Added [blockprint](https://github.com/sigp/blockprint) public API ([Demo](https://user-images.githubusercontent.com/114221396/194077899-a7e846ba-493e-4751-b2b4-6f27ca700f40.png)).

**[10/04/2022]**
- Implemented the [chart](https://user-images.githubusercontent.com/114221396/193872844-dfb4a9b9-eb5c-4eed-84a5-fd7a238dae84.png) with manually injected data.
- Gathered feedback from R&D Discord: Maybe fees earned/client is interesting.
- Asked in Sigma Primes Discord about the API of [blockprint](https://github.com/sigp/blockprint).

**[10/03/2022]**
- Research on Consensus Layer and Execution Layer.
- Research on React App.
- Configured the [first Layout](https://user-images.githubusercontent.com/114221396/193602030-5ab6b761-93c2-4416-8331-ab14fc7a1218.png) of my project.

**[10/02/2022]**
- Created the [draft](https://user-images.githubusercontent.com/114221396/193452397-19a40781-27bc-4218-b08c-5a42183c37e2.png) of how my project could look like.
- Gathered feedback from R&D Discord regarding the draft and some additional clarifications.
- Writeup of the [README](https://github.com/kevinbogner/data-analysis-consensus-clients).

**[10/01/2022]**
- Create my Folder structure for EPF cohort 3.
- Research about [Miga Labs](https://migalabs.es/api-documentation), similar to Blockprint, also provides data for the Consensus Client diversity.

**[09/30/2022]**
- Research about the [Project ideas](https://github.com/eth-protocol-fellows/cohort-three/blob/master/projects/project-ideas.md) proposed by the program's mentors.
- Brainstorming about [Browser tooling](https://github.com/eth-protocol-fellows/cohort-three/blob/master/projects/project-ideas.md#browser-tooling) and with input from [potuz](https://github.com/potuz) & [parithosh](https://github.com/parithosh) decided to dig deeper into **forkchoice** and **Client diversity**.
- Checked out [protovis](https://github.com/tbenr/protovis) work by [tbenr](https://github.com/tbenr), which visualizes the forkchoice. This could possibly be expanded by additionally offering historical data.
- Checked out [Blockprint](https://github.com/sigp/blockprint) work by [Sigma Prime](https://sigmaprime.io/), which gathers data for the Client diversity of the Beacon chain as shown in [sproulM_'s](https://twitter.com/sproulM_/status/1481109509544513539) tweet. There's already [this](https://clientdiversity.org/) site, which shows the client diversity of Ethereum. Partially based on Blockprint data.
- Experimented with [Blockprint's Public API](https://github.com/sigp/blockprint/blob/main/docs/api.md).
- [potuz](https://github.com/potuz) suggested tracking events like block proposals and attestations to catch network splits across clients.
- Set up [my repo](https://github.com/kevinbogner/data-analysis-consensus-clients) for EPF with [Create React App](https://create-react-app.dev/).
