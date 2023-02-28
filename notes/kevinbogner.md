# Ethereum Protocol Fellowship Program 2022 - Cohort Three

## Consensus client reward APIs

## Journal
**[02/19/2023]**
- Modify [`initialize_beacon_state_from_eth1`](https://github.com/kevinbogner/lighthouse/commit/e13faf69db1a740b9948c89bf70fd7b361d0004d).

**[02/17/2023]**
- Modified [`process_operations`](https://github.com/kevinbogner/lighthouse/pull/1/commits/7b2cf8b01fd34c56ffbf4c4543f3ed24bd197622) according to EIP-6110.

**[02/16/2023]**
- Kick-off meeting for PoC of EIP-6110.

**[02/15/2023]**
- [Implemented](https://github.com/sigp/lighthouse/commit/3df825173f07bd54ccc794e25128740d139b826f) `get_validator_from_indexed_deposit_data`, `apply_indexed_deposit_data`, and `process_pending_deposits`.

**[02/14/2023]**
- [Implemented `pending_deposits` into `BeaconState`](https://github.com/kevinbogner/lighthouse/commit/4cb28b99ed53bb8f9971bc811605693423a3cca1).
- Attended Office Hours call #14.

**[02/13/2023]**
- Continued working on EIP-6110. [Added structure for functions](https://github.com/kevinbogner/lighthouse/commit/fdd77388ef01ab9887addffad237e8c976e9593d).
- Attended standup call.

**[02/10/2023]**
- More research on [EIP-6110](https://hackmd.io/@n0ble/deposits-breakout).

**[02/09/2023]**
- Add [`DepositReceipt`](https://github.com/mkalinin/eth2.0-specs/blob/deposits/specs/eip6110/beacon-chain.md#depositreceipt).

**[02/08/2023]**
- Started research on [EIP-6110](https://eips.ethereum.org/EIPS/eip-6110).
- Initialized EIP-6110 [branch](https://github.com/kevinbogner/lighthouse/tree/eip6110).

**[02/07/2023]**
- Published [Dev Update #14](https://hackmd.io/@kevinbogner/dev-update-14).
- Attended Office Hours call #13.

**[02/06/2023]**
- Got the [`attestation_rewards`](https://github.com/sigp/lighthouse/pull/3822) merged. 
- NC got the [`block_rewards`](https://github.com/sigp/lighthouse/pull/3907) merged.

**[02/02/2023]**
- Working on an error that was caused by [this](https://github.com/sigp/lighthouse/pull/3822/commits/e8c93ffd79026d9ca8e517df747a99173ba1f071) commit, where pubkeys and validators aren`t accepted as request bodies.

**[02/01/2023]**
- Searching for test data to check if validators that are not eligible receive `0` rewards for their three votes.

**[01/31/2023]**
- Attended Office Hours call #12.
- Published [Dev Update #13](https://hackmd.io/@kevinbogner/dev-update-13).

**[01/30/2023]**
- Tested `attestation_rewards` manually.
- Attended standup call. 

**[01/25/2023]**
- Addressed the comments of the review.

**[01/24/2023]**
- Attended Office Hours call #11.
- Received a review on `attestation_rewards`.

**[01/23/2023]**
- Finished `attestation_rewards`; they are now ready for review.
- Attended standup call.

**[01/22/2023]**
- Finished `ideal_rewards` for `attestation_rewards`.

**[01/20/2023]**
- Continue working on `attestation_rewards`: fixed `execution_optimistic`, and added `log`.

**[01/19/2023]**
- Continue working on `attestation_rewards`: added `?` operator, renamed variables, and updated formatting.

**[01/18/2023]**
- Looked into the [question mark operator](https://doc.rust-lang.org/reference/expressions/operator-expr.html#the-question-mark-operator) but couldn't progress with the `attestation_rewards` just yet.

**[01/17/2023]**
- Convert `ideal_rewards` from a [HashMap into a Vector](https://github.com/naviechan/lighthouse/commit/d2bd6ed2df98aeb25ea2e0aefa23ade7d1274a1c).
- Attended Office Hours call #10.

**[01/16/2023]**
- Meeting with NC and sproul regarding the endpoints.
- Attended standup call.

**[01/14/2023]**
- Research on [EIP-6110](https://eips.ethereum.org/EIPS/eip-6110) and its [Engine API changes](https://github.com/ethereum/execution-apis/blob/main/src/engine/experimental/eip6110.md).

**[01/13/2023]**
- [Minor fixes](https://github.com/sigp/lighthouse/commit/90e6fb72017e2ac056ec22d01db0dcc24da1ac15) on [`attestation_rewards`](https://github.com/sigp/lighthouse/pull/3822).
- Sproul gave us [feedback](https://github.com/sigp/lighthouse/pull/3790#pullrequestreview-1246907504) on `sync_committee_rewards`.

**[01/12/2023]**
- Fixed some [errors](https://github.com/naviechan/lighthouse/commit/f3cc9d1ba0508856331782fbac1ec295f531053f) of [`attestation_rewards`](https://github.com/sigp/lighthouse/pull/3822).

**[01/11/2023]**
- Added [`actual_rewards`](https://github.com/naviechan/lighthouse/commit/9bcab4e89478899d1a5fb948e33aaa734dbfeeba) to [`attestation_rewards`](https://github.com/sigp/lighthouse/pull/3822).

**[01/10/2023]**
- Attended Office Hours call.
- Added [`ideal_rewards`](https://github.com/sigp/lighthouse/commit/4cd7486d7eebbcadd6090f49c2934d48896cd65f) to [`attestation_rewards`](https://github.com/sigp/lighthouse/pull/3822).

**[01/09/2023]**
- Attended standup call.
- Continued working on [`attestation_rewards`](https://github.com/sigp/lighthouse/pull/3822).

**[01/06/2023]**
- Published [Dev Update #11](https://hackmd.io/@kevinbogner/dev-update-11).

**[01/05/2023]**
- Continue working on [`attestation_rewards`](https://github.com/sigp/lighthouse/commit/c7aa610401afad662001f695c7d55c1fc21bf0a2).

**[01/04/2023]**
- Keep working on [`attestation_rewards`](https://github.com/sigp/lighthouse/pull/3822). Implemented some [minor changes](https://github.com/sigp/lighthouse/commit/390f33147d9b1876ed2d3e3571e0e9628178d3ab) suggested by NC.

**[01/03/2023]**
- Attended Office Hours call #8 - AMA with Piper Merriam.
- Received feedback from NC on the [`attestation_rewards`](https://github.com/sigp/lighthouse/pull/3822).

**[01/02/2023]**
- Attended standup call.
- Building our branch manually to test our endpoints.

**[12/29/2022]**
- Published [Dev Update #10](https://hackmd.io/@kevinbogner/dev-update-10).

**[12/27/2022]**
- Took a break during Christmas and will be fully back at the start of the coming year.
- Attended Office Hours call #7.

**[12/23/2022]**
- Adding the actual rewards for the [`attestation_rewards`](https://github.com/sigp/lighthouse/pull/3822) endpoint.

**[12/22/2022]**
- Adding the ideal rewards for the [`attestation_rewards`](https://github.com/sigp/lighthouse/pull/3822) endpoint.

**[12/21/2022]**
- Continue working on [`attestation_rewards`](https://github.com/sigp/lighthouse/pull/3822).

**[12/20/2022]**
- Working on [`attestation_rewards`](https://github.com/naviechan/lighthouse/commit/1d27163d0b15bb745628325bc1820bae97f21eb3).
- Attended Office Hours call.
- Opened `attestation_rewards` [draft PR](https://github.com/sigp/lighthouse/pull/3822).

**[12/19/2022]**
- Meeting with NC and sproul ([meeting notes](https://hackmd.io/@sproul/consensus-rewards-m2)).
- Attended EPF standup call.

**[12/16/2022]**
- Add endpoints to `common/eth2/src/lib.rs` ([`block_rewards`](https://github.com/naviechan/lighthouse/commit/2e0ee4beec245af01b51818d3be8b04c821aa648) and [`attestation_rewards`](https://github.com/naviechan/lighthouse/commit/b9046aa12da31fd4432f7776e05082266d332674)).
- Restructure [`block_rewards`](https://github.com/naviechan/lighthouse/commit/8283f594f8fe9dca21196496235a7b3be3a92907) and [`attestation_rewards`](https://github.com/naviechan/lighthouse/commit/20e57f03a4c56e2c1e4ec1f592dfb39f039c4e75).

**[12/15/2022]**
- Continue working on [`sync_committee_rewards`](https://github.com/sigp/lighthouse/pull/3790).

**[12/14/2022]**
- Published [Dev Update #9](https://hackmd.io/@kevinbogner/dev-update-9).

**[12/13/2022]**
- Attended [Office Hours call #5](https://github.com/eth-protocol-fellows/cohort-three/issues/193).

**[12/12/2022]**
- Opened [draft PR](https://github.com/sigp/lighthouse/pull/3790) on `sync_committe_rewards`.
- Received [feedback](https://discordapp.com/channels/605577013327167508/1035866197146742814/1051709012963508234) on Lighthouse Discord on the endpoint.
- Scheduled call with NC and sproul on 12/19/2022 to talk about the APIs.
- Attended EPF standup call.

**[12/09/2022]**
- Continue working on [`sync_committee_rewards`](https://github.com/naviechan/lighthouse/commit/29d18223ff8c9cbebed7a93285f9768f3f1ba27a).

**[12/08/2022]**
- [Discussion](https://discord.com/channels/605577013327167508/1035866197146742814/1050025366653239336) in the Lighthouse Discord regarding the `sync_committee_rewards`.

**[12/07/2022]**
- Continue working on [`sync_committee_rewards`](https://github.com/naviechan/lighthouse/commit/0b5d6ad5ec5425e8abaf5be486286ce2dc8dce79), [`attestation_rewards`](https://github.com/naviechan/lighthouse/commit/5470918d759cd9995a413227be5e76b8a7db02a8), and [`block_rewards`](https://github.com/naviechan/lighthouse/commit/6557a55e3f443614ed9ebc3647bccab9471c074e).

**[12/06/2022]**
- Created branch for [`block_rewards`](https://github.com/naviechan/lighthouse/commit/7d72bd06e9c50d33cc3b1afb600812990e381711).
- Attended [Office Hours call #4](https://github.com/eth-protocol-fellows/cohort-three/issues/176).
- Read [What in the Ethereum application ecosystem excites me](https://vitalik.ca/general/2022/12/05/excited.html) from Vitalik.

**[12/05/2022]**
- Created branch for [`attestation_rewards`](https://github.com/naviechan/lighthouse/commit/6b16115a91dc1576d629c2ccab80fcea974b57c8).
- Attended weekly standup call.

**[12/02/2022]**
- Continue working on [`sync_committee_rewards`](https://github.com/naviechan/lighthouse/commit/4cc09c6db0088b9dd0c27b952237e77d8e2beee4).

**[12/01/2022]**
- Meeting with NC ([notes](https://hackmd.io/@kevinbogner/meeting-notes-dev-rewards-API)).

**[11/30/2022]**
- Published [dev update #7](https://hackmd.io/@kevinbogner/HJOn-F7wi).
- Meeting with NC regarding the `sync_committee_rewards`.
- [Commits](https://github.com/kevinbogner/lighthouse/commit/85822c564e2193859a4d2d61b96c3f86391e5621) on `sync_committee_rewards` implementation for LH.

**[11/29/2022]**
- Attended EPF office hour call.
- Started writing dev update #7.
- Continued working on [`sync_committee_rewards`](https://github.com/kevinbogner/lighthouse/commit/5f244188e5ecb38af56270b48ba44e62191635e0).

**[11/28/2022]**
- Restructured [this repo](https://github.com/kevinbogner/data-analysis-consensus-clients/commit/b941fc5e0c7928d1f1f0a3e3fefe7d1107c2b3fc).
- Guide for Lighthouse merged on [how to run a beacon node](https://github.com/sigp/lighthouse/pull/3681).
- Attended EPF standup call.

**[11/25/2022]**
- Continue working with the [Rust book](https://doc.rust-lang.org/book/title-page.html) :crab:.
- Modifications on https://github.com/sigp/lighthouse/pull/3681.

**[11/24/2022]**
- Goal for this week is to finish the [Rust book](https://doc.rust-lang.org/book/title-page.html) to start next week with the implementation into Lighthouse.

**[11/23/2022]**
- [Dev Update #6](https://hackmd.io/@lODlsf2CR9uWlyIyEdjjPQ/rkNsMdm8j) published.

**[11/22/2022]**
- Call with NC and sproul - Kickoff call regarding validator rewards ([notes](https://hackmd.io/@sproul/consensus-rewards-m1)).
- We merged our endpoints ([#260](https://github.com/ethereum/beacon-APIs/pull/260) and [#262](https://github.com/ethereum/beacon-APIs/pull/262)) to the [`beacon-APIs`](https://github.com/ethereum/beacon-APIs).

**[11/21/2022]**
- Attended EPF standup call.
- Error on CI/CD pipeline probably caused by a faulty version.

**[11/18/2022]**
- [PR#260](https://github.com/ethereum/beacon-APIs/pull/260) and [PR#262](https://github.com/ethereum/beacon-APIs/pull/262) are ready for review. We got minor lint errors we need to fix.

**[11/17/2022]**
- Discovered [lint errors](https://user-images.githubusercontent.com/114221396/202462233-61615b34-2f6a-4fe9-af71-6c7e0a3af9d7.png) on our PRs.

**[11/16/2022]**
- Feedback and modifications on [PR#260](https://github.com/ethereum/beacon-APIs/pull/260) and [PR#262](https://github.com/ethereum/beacon-APIs/pull/262).

**[11/15/2022]**
- More work on [PR#260](https://github.com/ethereum/beacon-APIs/pull/260) and [PR#262](https://github.com/ethereum/beacon-APIs/pull/262). Getting feedback from different client teams.
- Published [Dev Update #5](https://hackmd.io/@lODlsf2CR9uWlyIyEdjjPQ/ryFpWr0Ss).
- Attended [Office Hours call #2](https://github.com/eth-protocol-fellows/cohort-three/issues/78) and presented the [project proposal](https://github.com/eth-protocol-fellows/cohort-three/blob/master/projects/consensus_client_reward_APIs.md).

**[11/14/2022]**
- Opened a [PR](https://github.com/eth-protocol-fellows/cohort-three/pull/117) for the project proposal at EPF.
- Implemented sprouls suggestions into [PR#260](https://github.com/ethereum/beacon-APIs/pull/260) and [PR#262](https://github.com/ethereum/beacon-APIs/pull/262).
- Attended [EPF standup call](https://github.com/eth-protocol-fellows/cohort-three#standup-calls).

**[11/13/2022]**
- Working on Dev Update #5 should be published at the start of the coming week.

**[11/12/2022]**
- Finished [project draft for the EPF](https://github.com/kevinbogner/cohort-three/blob/project/projects/consensus_client_reward_APIs.md).

**[11/11/2022]**
- Finished ['Run a Node' guide for the Lighthouse book](https://github.com/sigp/lighthouse/pull/3681).
- Again, minor modifications for [`sync_committee_rewards`](https://github.com/ethereum/beacon-APIs/pull/262).

**[11/10/2022]**
- Finished some modifications for the ['Run a Node' guide for the Lighthouse book](https://github.com/sigp/lighthouse/pull/3681). It should be ready tomorrow for review.
- Small modifications for [`sync_committee_rewards`](https://github.com/ethereum/beacon-APIs/pull/262).

**[11/09/2022]**
- Currently working on three things simultaneously:
  - [Add endpoints for `per-validator rewards`](https://github.com/ethereum/beacon-APIs/pull/260).
  - [Add endpoints for `sync_committee_rewards`](https://github.com/ethereum/beacon-APIs/pull/262).
  - [Add 'Run a Node' guide to the Lighthouse book](https://github.com/sigp/lighthouse/pull/3681).

**[11/08/2022]**
- More discussion on the [draft PR](https://github.com/ethereum/beacon-APIs/pull/260) for the beacon API endpoints.
- Published [Dev Update #4](https://hackmd.io/@lODlsf2CR9uWlyIyEdjjPQ/B1UFETvro).

**[11/07/2022]**
- Created a [draft PR](https://github.com/ethereum/beacon-APIs/pull/260) to work with [NC](https://github.com/naviechan) on beacon API endpoints.
- Attended weekly standup call.

**[11/04/2022]**
- Discussing with [NC](https://github.com/naviechan) the [design questions](https://github.com/sigp/lighthouse/issues/3661#issuecomment-1304482857).

**[11/03/2022]**
- Created a [PR](https://github.com/sigp/lighthouse/pull/3681) for [Issue #3672](https://github.com/sigp/lighthouse/issues/3672).

**[11/02/2022]**
- Continue working on a [Lighthouse Issue](https://github.com/sigp/lighthouse/issues/3672).

**[11/01/2022]**
- Attended [Office Hours Call #1](https://github.com/eth-protocol-fellows/cohort-three/issues/41).
- Started working on a [Lighthouse Issue](https://github.com/sigp/lighthouse/issues/3672) to add a guide for running a full node to the doc.

**[10/31/2022]**
- Attended EPF standup call and got some advice on handling big codebases in open-source projects. Focus on small areas; don't try to understand everything and familiarize yourself with testing.
- Installed and set up Linux for [Lighthouses' development environment](https://lighthouse-book.sigmaprime.io/setup.html).

**[10/30/2022]**
- Published [Dev Update #3](https://hackmd.io/@lODlsf2CR9uWlyIyEdjjPQ/HJhEF6wVj).

**[10/28/2022]**
- Continue working on Dev Update #3, which I will finish this week.
- Researching validator rewards because that's the next thing I will be working on: [Ben Edginton's book](https://eth2book.info/bellatrix/part2/incentives/rewards) and [Pintail's guide](https://pintail.xyz/posts/modelling-the-impact-of-altair/).
- Meanwhile, I continue setting up my [Lighthouse node](https://github.com/sigp/lighthouse), so I can start experimenting with APIs once my Dev Update is published. [Checkpoint sync](https://lighthouse-book.sigmaprime.io/checkpoint-sync.html?highlight=purge#automatic-checkpoint-sync) is done, and now the node is [reconstructing states](https://lighthouse-book.sigmaprime.io/checkpoint-sync.html#reconstructing-states).

**[10/27/2022]**
- Started working on Dev Update #3.
- Listened to [Ethereum Core Devs Meeting #148](https://www.youtube.com/watch?v=oQfEW8LdE88).

**[10/26/2022]**

- Setting up [Lighthouse](https://github.com/sigp/lighthouse).
- Experimenting with [Lighthouse API](https://lighthouse-book.sigmaprime.io/api.html).

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
