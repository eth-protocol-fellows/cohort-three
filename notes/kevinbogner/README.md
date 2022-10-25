# Ethereum Protocol Fellowship Program 2022 - Cohort Three

## 💾Data Analysis of Consensus Clients

:computer: **Code: https://github.com/kevinbogner/data-analysis-consensus-clients**.

## Journal
**[10/25/2022]**
- Code Cleanup.
- Realized that Consensus Client Block Rewards are different depending on the source used, e.g. [Etherscan API](https://etherscan.io/apis) or https://beaconcha.in/. Therefore I might tackle the issue by proposing a new endpoint for the [Beacon-API](https://ethereum.github.io/beacon-APIs/#/Beacon) with the help of [sproul](https://github.com/michaelsproul), who not only pointed the issue out but also has been working on an API for Consensus Client Block Rewards already.

**[10/24/2022]**
- Added [New Charts](https://user-images.githubusercontent.com/114221396/197732818-ea516e9c-cf90-4c51-8854-9a9e3d26afd3.png) with a [Dropdown](https://user-images.githubusercontent.com/114221396/197732953-87b3f4a3-9e7f-413e-975b-870e64a428bd.png).

**[10/23/2022]**
- [New Charts](https://user-images.githubusercontent.com/114221396/197408608-579d1049-2e83-475f-bb48-058e5be75821.png) with data for Slots after a skipped Slot.
- Updated the Website with [new data](https://user-images.githubusercontent.com/114221396/197408657-b96ef5a1-823d-42df-8d25-943337bcbd60.png).
- [More automation](https://user-images.githubusercontent.com/114221396/197408789-cf116660-8e6f-4432-8a58-8f805dfb11c4.png) for data extraction.

**[10/22/2022]**
- [Wrote a script](https://user-images.githubusercontent.com/114221396/197349383-831a1bac-5b35-4704-ac91-b7947e581126.png) to automize the .csv file creation.
- Reduced the amount of required .csv files to make the website more lightweight.
- Thinking about how I want to proceed: Mid-term, I want to group the data in different timeframes to allow users time-specific drill-downs. Long-term, I want to publish the data through a Twitterbot with daily reports.

**[10/21/2022]**
- Fetched [data of Clients and Relays](https://user-images.githubusercontent.com/114221396/197228380-c0a6eb72-f5b9-421b-a72a-1afcfeb617f8.png).
- [Created Dropdown](https://user-images.githubusercontent.com/114221396/197228617-374b8e22-3650-47f6-a8b0-6b6b67a3f2c9.png) to display Client data.
- Added [Dataset](https://user-images.githubusercontent.com/114221396/197270088-5a9d1297-b227-452f-9977-74c0be3abf73.png) of 'Last 7 Days'.

**[10/19/2022]**
- Published [Dev Update #2](https://hackmd.io/@lODlsf2CR9uWlyIyEdjjPQ/SkSBLnG7i).

**[10/18/2022]**
- Adding new charts to the Website.

**[10/17/2022]**
- Creating [visualization](https://user-images.githubusercontent.com/114221396/196202723-77851bae-bf00-4b4e-8e17-33e965782025.png) with https://plotly.com/graphing-libraries/
- Deployed the Website at https://kevinbogner-data-analysis-consensus-clients-app-lz484x.streamlitapp.com/

**[10/16/2022]**
- Pivot to https://www.python.org/ and https://streamlit.io/.
- [Visualize data](https://user-images.githubusercontent.com/114221396/196051309-7abcb35f-db99-4a3c-8031-b48254489724.png).

**[10/15/2022]**
- [Tables](https://user-images.githubusercontent.com/114221396/195984206-9690965b-7046-459f-ae15-1fcc1a41af41.png) displayed in React.
- Next Steps: Visualize Tables and Automate Data Import.

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
