# [Consensus client reward APIs](/projects/project-ideas.md#consensus-client-reward-apis)

**Implement APIs to fetch `per-validator rewards`**

Collaboration between [`NC`](https://github.com/naviechan) and [`kevinbogner`](https://github.com/kevinbogner) under the mentorship of [`sproul`](https://github.com/michaelsproul).

## Motivation

The Ethereum Merge joined the original execution layer with its new proof-of-stake *consensus layer*, the beacon chain. In the beacon chain, validators are rewarded for behaving according to the protocol. [*Altair*](https://github.com/ethereum/consensus-specs/tree/dev/specs/altair), the first upgrade of the beacon chain, redefined the way of allocating rewards and penalties.

Currently, there are *no* APIs to calculate the rewards paid to validators for fulfilling their duties.
This hinders the development of tools like block explorer and GUIs, requiring the devs to reverse engineer to get some data on rewards paid to validators.

## Project description

Within this project, we propose `per-validator reward` endpoints to the [beacon-APIs](https://github.com/ethereum/beacon-APIs).

The [Ethereum beacon-APIs](https://github.com/ethereum/beacon-APIs) is a collection of RESTful APIs and aims to *enhance interoperability* across beacon node implementations. The APIs are designed to be *minimal* and *generic* to support a wide range of use cases.

Once the API endpoints are merged, we implement those APIs in one or more consensus clients.

## Specification

There are *three* main activities validators are getting paid for:
1. Making *attestations*, which consist of three votes, each vote can be rewarded if they are subject to certain conditions:
    - voting for a *source* checkpoint,
    - voting for a *target* checkpoint,
    - voting for a chain *head* block.
1. *Proposing blocks* in the beacon chain.
1. Participating in *sync committees*.

These three reward types must be separately designed and implemented in both the [beacon-APIs](https://github.com/ethereum/beacon-APIs) and the consensus clients:

---

`/eth/v1/beacon/attestations/{epoch}/rewards`

*Get attestation rewards*

```json
{
  "data": [
    {
      "validator_index": 0,
      "head": 2000,
      "target": 4000,
      "source": 4000
    }
  ]
}
```

---

`/eth/v1/beacon/blocks/{slot}/rewards`

*Get block rewards*

```json
{
  "proposer_index": "123",
  "total": "5000",
  "attestations": "3000",
  "sync_aggregate": "2000",
  "proposer_slashings": "0",
  "attester_slashings": "0",
}
```
---

`/eth/v1/beacon/blocks/{block_id}/sync_committee_rewards`

*Get sync committee rewards*

```json
{
    "data": [
        {
            "validator_index": "0",
            "reward": "-1000",
        },
        {
            "validator_index": "1",
            "reward": "1000",
        },
    ]
}
```

## Roadmap

```mermaid
gantt
    title Consensus client reward APIs - Timeline
    dateFormat  YYYY-MM-DD
    section Beacon-APIs
        codebase:2022-11-05, 3d
        attestation:2022-11-07, 10d
        block:2022-11-07, 10d
        sync committee:2022-11-09, 8d
    section Consensus clients
        codebase:2022-11-14, 14d
        block:2022-11-28, 21d
        attestation:2022-12-19, 21d
        sync committee:2023-01-09, 21d
```

## Possible challenges

There are mainly *two* significant challenges that we identified:
- navigating and understanding the vast codebase of consensus clients; and
- predicting how long a particular milestone takes. 

Understanding the terminologies of Ethereum was another issue at the start of the project; however, we both improved in this area.

## Goal of the project

The project is *finished* when our APIs are successfully implemented in *one* consensus client.

Our project was *successful* as soon as *more than one* consensus customer implemented our APIs, either through their teams or through us.

Our *expectations are exceeded* when several applications like block explorer or GUIs use our endpoints to gather data.

## Resources

[`Beacon-APIs`](https://github.com/ethereum/beacon-APIs):
- [PR: Add reward-endpoints for `attestations` and `blocks`](https://github.com/ethereum/beacon-APIs/pull/260)
- [PR: Add reward-endpoint for `sync_committee`](https://github.com/ethereum/beacon-APIs/pull/262)

`Consensus clients`:
- [Issue - Lighthouse](https://github.com/sigp/lighthouse/issues/3661)

---

[`NC`](https://github.com/naviechan):
- [Dev Updates](https://github.com/eth-protocol-fellows/cohort-three/blob/master/development-updates.md#nc)

[`kevinbogner`](https://github.com/kevinbogner):
- [Dev Updates](https://github.com/eth-protocol-fellows/cohort-three/blob/master/development-updates.md#kevinbogner)
- [Notes](https://github.com/eth-protocol-fellows/cohort-three/blob/master/notes/kevinbogner.md)
- [Repo of a dashboard that later uses the APIs](https://github.com/kevinbogner/data-analysis-consensus-clients)
- [Dashboard](https://kevinbogner-data-analysis-consensus-clients-app-lz484x.streamlit.app/)
