# Garvit Khatri's notes

Hey everyone, this is Garvit Khatri, a Software Engineer for past 6 years who studied Engineering physics and graduated in 2016.

## What I am interested in?

Account Abstraction - I intend to work on creating a wallet application for users to use a Smart Contract Wallet compatible with 4337. The idea is to help the community understand it's importance and help people adopt 4337 faster. This if successfull can help us pave the way forward to destruction of EOAs.

### EIP

[https://eips.ethereum.org/EIPS/eip-4337](https://eips.ethereum.org/EIPS/eip-4337)

## Notes

Below are the notes & links that I will be collecting during my research, the date format is [dd.mm.yy]

### [18.11.22]

Blog - [How to store private keys securely in local storage?](https://mirror.xyz/plusminushalf.eth/vtRuTou-XjWjQvkigtRrTjKeQ3ZKx5ujyUFZ-W_2s74)
Notes - [Metamask snaps & 4337 wallet challenges & solutions](https://hackmd.io/@plusminushalf/metamask-snaps-4337-wallet)

![Wallet design flow](/images/wallet-design-flow.png)
![Wallet Recover design](/images/recovery-design.png)

### [5.11.22] Feature list for the wallet

I have compiled objectives that this wallet must complete & also documented the finalised flow for onboarding at https://hackmd.io/t34kODtfRw2ITA8hR8eV1g.
Next I have to make the front-end architecture for the modules that will be needed.

### [17.10.22] Onboarding to AA Wallet

Research about challanges - https://hackmd.io/@plusminushalf/onboarding-aa-challenges

Feedback recieved from [Dror](https://github.com/drortirosh) & [Yoav](https://github.com/yoavw) -

- seed phrases: these are a bad way to keep a secured key. A multi-factor or social recovery mechanism is better. Can we make an onboarding with no need to save seed phrase at all?
- Importing a wallet should be by address of a wallet & not through a private key
- with AA, we use the term "owner" or "signer", and never EOA, since we don't consider private key as an "account" in any way.
- The extension could come with a default SampleWallet authenticator, and over time you can add more builtin authenticators to support more wallets.

### [11.10.22] Create cusotm SCW

I wanted to create a repo that will demonstrate how can we create a custom SCW which will be compatible with 4337 & will be using the `@account-abstraction/sdk`. Find the demo repo below

Repo: https://github.com/plusminushalf/demo-aa

In case you want to use a test bundler, you can use the bundler hosted by me at `https://eip4337-bundler-goerli.protonapp.io/rpc`. NOTE: this only works for goerli network & entrypoint `0x2167fA17BA3c80Adee05D98F0B55b666Be6829d6`. This bundler is a basic bundler that can be found at [https://github.com/eth-infinitism/bundler/tree/main/packages/bundler](https://github.com/eth-infinitism/bundler/tree/main/packages/bundler)

### [03.10.22] Role of stake in paymasters

by [Dror](https://github.com/drortirosh):

The stake is a sybil resistance mechanism. It's not used on-chain but by the mempool nodes and bundlers. Unlike GSN stake, there's no slashing.

ERC 4337 protects the mempool participants against DoS attacks caused by invalidating a large number of previously-valid ops. That's what the opcode banning rules are for (so you can't invalidate an op based on block number for example). It also forbids wallets from accessing 3rd party storage during validation. This ensures that a single state change can only invalidate the op of a single wallet. The gas cost of invalidating n ops is therefore O(n).

Paymasters are allowed to violate the latter rule, since a paymaster can access its own storage but is used by multiple wallets. Consider an EvilPaymaster whose validation function includes require(!attack). The attacker then sends 10000 ops from different wallets, all specifying the same EvilPaymaster. The ops are accepted to the mempool because EvilPaymaster.attack==0. The attacker then frontruns them with a transaction that sets attack=1. Now all 10000 ops are invalid, and each bundler has to test all 10000 ops and drop them (unpaid). Therefore the attacker caused O(n) off-chain work to all bundlers, at the cost of a single on-chain state change. O(1) attack cost for causing O(n) damage is something the network can't sustain.

Therefore paymasters must have a reputation and a throttling/banning mechanism. If a paymaster's acceptance ratio drops below a certain threshold, it is throttled for a while. If it keeps causing drops, it gets banned. The algorithm is described in the EIP.

However, a reputation system is meaningless if there's no sybil resistance. The attacker could keep deploying more paymasters and sustain the attack. Here's where the stake comes into play. The paymaster is considered valid by the mempool participants only if it is staked and hasn't started the unstaking process. The attacker has to lock the stake, cause a little bit of damage (off-chain work to drop some ops) and then the paymaster is banned. To deploy a new paymaster, the attacker must either commit more funds, or wait for an hour before being able to redeploy the same funds. It brings the financial cost of the attack to O(n) and much higher than the damage it could cause.

Technically the same could be achieved by any other sybil resistance mechanism. For example, we could have a whitelist of paymasters and not accept any other. Then, there's no need to stake because they can't change their address. We chose to use a stake because it keeps things permissionless and allows anyone to innovate on paymasters.

The reason the stake is separated from the deposit and never used to pay for gas, is that it could be used by an attacker to indirectly withdraw the stake and redeploy it without waiting an hour. It's unsafe to use the stake for anything other than for preventing attacks.
