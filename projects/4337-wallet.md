# 4337 Wallet

An EIP-4337 Compatible wallet that aims to challenge the status quo of Ethereum EOA wallets.

## Motivation

<!-- What problem is your project is solving? Why is it important and what area of the protocol will be affected? -->

We are moving closer towards the finalisation of [EIP-4337](https://eips.ethereum.org/EIPS/eip-4337). A lot of effort by the core team has been put into designing the contracts, mempool, DOS protections etc. But the team haven't had time to properly support UserOps through one of the browser extension wallets.

This project aims to make a user-facing wallet which can then pave the way forward for the wallets in the Ethereum ecosystem. The larger goal is to test the eip enough and make it ready for everyday use. Once we get AAs into everyday use we can then easily work towards the depreciation of EOAs from the ecosystem.

---

## Project description

<!-- What is your proposed solution?  -->

The proposed 4337 wallet will be a browser extension wallet that will split into modules, namely extension, auth and recovery. The split of modules is so that we can have support for multiple SCW implementations. Each wallet would be able to expose the API for the user to select the SCW implementation that they want to try out.

The extension will support the following features:

- Support multiple SCW implementations
- Ability to create a SCW
- Recover a SCW
- Support for sending transactions
- Expose API for Dapps to attach custom paymaster
- Ability to add user specified paymaster
- API to batch multiple transactions together
- Social recovery
- Ability to pause an account
- Define Spending limits

---

<!-- ## Specification -->

<!-- How will you implement your solutions? Give details and more technical information on the project. -->

<!-- ## Roadmap -->

<!-- What is your proposed timeline? Outline parts of the project and insight on how much time it will take to execute them. -->

## Possible challenges

<!-- What are the limitations and issues you may need to overcome? -->

- Onboarding and creation policies of new SCWs
- Support for multiple paymasters
- Removal of Guardians

---

<!-- ## Goal of the project -->

<!-- What does success look like? Describe the end goal of the project, scope, state and impact for the project to be considered finished and successful. -->

## Collaborators

### Fellows

<!-- Are there any fellows working with you on this project?  -->

- [Garvit Khatri](https://github.com/plusminushalf)
- [Jayesh Bhole](https://github.com/jayeshbhole)

### Mentors

<!-- Which mentors are helping you with the project?  -->

- [Yoav Weiss](https://github.com/yoavw)
- [Dror Tirosh](https://github.com/drortirosh)

## Resources

<!-- Provide links to repositories, PRs and other resources which constitute the project. -->

### Reading Material

https://eips.ethereum.org/EIPS/eip-4337

https://eips.ethereum.org/EIPS/eip-3074

https://hackmd.io/@matt/r1neQ_B38

https://github.com/eth-infinitism/account-abstraction

https://github.com/eth-infinitism/bundler

### Other References

UI Design: [Figma](https://www.figma.com/file/oM7MjvlOTO6L1vjZ6BxTH1/hex-wallet?node-id=2%3A3)

UX Design: [Figjam](https://www.figma.com/file/GASw8N72JnozdT2FxIlLgA/Wallet-design-flow?node-id=0%3A1)

### Garvit's notes

<details>
<summary>Expand</summary>

[[5.11.22] Feature list for the wallet](https://github.com/eth-protocol-fellows/cohort-three/blob/master/notes/garvit.md#51122-feature-list-for-the-wallet)

[[17.10.22] Onboarding to AA Wallet](https://github.com/eth-protocol-fellows/cohort-three/blob/master/notes/garvit.md#171022-onboarding-to-aa-wallet)

[[11.10.22] Create cusotm SCW](https://github.com/eth-protocol-fellows/cohort-three/blob/master/notes/garvit.md#111022-create-cusotm-scw)

[[03.10.22] Role of stake in paymasters](https://github.com/eth-protocol-fellows/cohort-three/blob/master/notes/garvit.md#031022-role-of-stake-in-paymasters)

</details>

### Jayesh's notes

<details>
<summary>Expand</summary>

[[13.11.22] Getting started with the UX design](../notes/jayesh.md#131122-getting-started-with-the-ux-design)

</details>

---
