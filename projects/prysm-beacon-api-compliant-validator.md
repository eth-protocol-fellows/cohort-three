# Beacon API Compliant Prysm Validator

Rewriting the validator client code to be compatible with the Beacon API instead of Prysm's internal API

## Motivation

Historically, Prysmatic Labs was advocating for communication between validator and beacon nodes to be done via gRPC, so they started implementing their validator in that manner before a standard was established. But when the Beacon Node API eventually became the standard, all the existing gRPC code wasn't standard-compliant and therefore the beacon node couldn't be used by other validators or tools (e.g. block explorers). The team decided to use a project called [grpc-gateway](https://github.com/grpc-ecosystem/grpc-gateway) to automatically handle the conversion between gRPC and REST API, but because of the intricacies of Ethereum (e.g. 0x prefixed strings, endianness, hex-encoded numeric values), they needed to add a lot of middlewares to handle this translation. They also ended up needing to mainintain [a fork of grpc-gateway](https://github.com/prysmaticlabs/grpc-gateway) to support custom types from their [SSZ encoding library](https://github.com/prysmaticlabs/fastssz).

In addition to those layers and that additional complexity being a huge maintenance burden, the Validator was never rewritten to call into beacon nodes via the Beacon REST API. This means that the validator is still not compatible with other beacon nodes, and the Prysm beacon node needs to keep its gRPC support to keep supporting its own validator.

More background can be found [over here](https://github.com/prysmaticlabs/prysm/issues/11580).

## Project description

A 4-month project to rewrite the Prysm validator code to be compatible with the standard Beacon API. This will be the first step to take in order to reduce the complexity of the codebase and will accomplish the following:
- Make the Prysm validator compatible with other beacon node implementations
- Remove the need to support a separate fork of the grpc-gateway project
- Reduce the possibility of bugs hidden within the many layers of grpc-gateway, the grpc-gateway fork and the middlewares
- Make the project easier to maintain

## Specification

Here is how the current gRPC validator client interface looks like:

```go
type BeaconNodeValidatorClient interface {
	GetDuties(ctx context.Context, in *DutiesRequest, opts ...grpc.CallOption) (*DutiesResponse, error)
	StreamDuties(ctx context.Context, in *DutiesRequest, opts ...grpc.CallOption) (BeaconNodeValidator_StreamDutiesClient, error)
	DomainData(ctx context.Context, in *DomainRequest, opts ...grpc.CallOption) (*DomainResponse, error)
	// Deprecated: Do not use.
	WaitForChainStart(ctx context.Context, in *empty.Empty, opts ...grpc.CallOption) (BeaconNodeValidator_WaitForChainStartClient, error)
	WaitForActivation(ctx context.Context, in *ValidatorActivationRequest, opts ...grpc.CallOption) (BeaconNodeValidator_WaitForActivationClient, error)
	ValidatorIndex(ctx context.Context, in *ValidatorIndexRequest, opts ...grpc.CallOption) (*ValidatorIndexResponse, error)
	ValidatorStatus(ctx context.Context, in *ValidatorStatusRequest, opts ...grpc.CallOption) (*ValidatorStatusResponse, error)
	MultipleValidatorStatus(ctx context.Context, in *MultipleValidatorStatusRequest, opts ...grpc.CallOption) (*MultipleValidatorStatusResponse, error)
	GetBeaconBlock(ctx context.Context, in *BlockRequest, opts ...grpc.CallOption) (*GenericBeaconBlock, error)
	ProposeBeaconBlock(ctx context.Context, in *GenericSignedBeaconBlock, opts ...grpc.CallOption) (*ProposeResponse, error)
	PrepareBeaconProposer(ctx context.Context, in *PrepareBeaconProposerRequest, opts ...grpc.CallOption) (*empty.Empty, error)
	GetFeeRecipientByPubKey(ctx context.Context, in *FeeRecipientByPubKeyRequest, opts ...grpc.CallOption) (*FeeRecipientByPubKeyResponse, error)
	GetAttestationData(ctx context.Context, in *AttestationDataRequest, opts ...grpc.CallOption) (*AttestationData, error)
	ProposeAttestation(ctx context.Context, in *Attestation, opts ...grpc.CallOption) (*AttestResponse, error)
	SubmitAggregateSelectionProof(ctx context.Context, in *AggregateSelectionRequest, opts ...grpc.CallOption) (*AggregateSelectionResponse, error)
	SubmitSignedAggregateSelectionProof(ctx context.Context, in *SignedAggregateSubmitRequest, opts ...grpc.CallOption) (*SignedAggregateSubmitResponse, error)
	ProposeExit(ctx context.Context, in *SignedVoluntaryExit, opts ...grpc.CallOption) (*ProposeExitResponse, error)
	SubscribeCommitteeSubnets(ctx context.Context, in *CommitteeSubnetsSubscribeRequest, opts ...grpc.CallOption) (*empty.Empty, error)
	CheckDoppelGanger(ctx context.Context, in *DoppelGangerRequest, opts ...grpc.CallOption) (*DoppelGangerResponse, error)
	GetSyncMessageBlockRoot(ctx context.Context, in *empty.Empty, opts ...grpc.CallOption) (*SyncMessageBlockRootResponse, error)
	SubmitSyncMessage(ctx context.Context, in *SyncCommitteeMessage, opts ...grpc.CallOption) (*empty.Empty, error)
	GetSyncSubcommitteeIndex(ctx context.Context, in *SyncSubcommitteeIndexRequest, opts ...grpc.CallOption) (*SyncSubcommitteeIndexResponse, error)
	GetSyncCommitteeContribution(ctx context.Context, in *SyncCommitteeContributionRequest, opts ...grpc.CallOption) (*SyncCommitteeContribution, error)
	SubmitSignedContributionAndProof(ctx context.Context, in *SignedContributionAndProof, opts ...grpc.CallOption) (*empty.Empty, error)
	StreamBlocksAltair(ctx context.Context, in *StreamBlocksRequest, opts ...grpc.CallOption) (BeaconNodeValidator_StreamBlocksAltairClient, error)
	SubmitValidatorRegistrations(ctx context.Context, in *SignedValidatorRegistrationsV1, opts ...grpc.CallOption) (*empty.Empty, error)
}
```

The idea is for the REST API validator client to implement this interface in terms of the Beacon API endpoints. This will accomplish a few things:
- Allow the rest of the Prysm code to stay intact, thus limiting the changes to a very small surface area and reducing the possibility of bugs. If the inputs and outputs to the function are the same, it doesn't matter whether the actual implementation of the function is using gRPC or REST endpoints, as long as they return the same data.
- Allow the existing test collateral to easily be reused for the REST API version simply by changing how the client is instantiated.
- Allow REST endpoints who don't have an implementation yet to simply fall back to the gRPC ones in the short term instead of failing.

For the JSON marshalling/unmarshalling, we will use the [structs that are already used by the beacon node](https://github.com/prysmaticlabs/prysm/blob/develop/beacon-chain/rpc/apimiddleware/structs.go).

As for the actual Beacon API spec, [it's already well defined](https://ethereum.github.io/beacon-APIs/) and the Prysm beacon node already supports it, so all we have to do is follow the spec and make sure that the end to end tests keep passing.

## Roadmap

Weeks 1-2: Write a design document that outlines the current architecture of the Prysm Validator, how it interacts with the beacon node via gRPC and the mapping between the gRPC and REST API endpoints.
Weeks 3-4: Refactor the Prysm Validator and tests to have an option to use the REST API, while keeping existing behavior intact in order to not disrupt ongoing client development.
Weeks 5-16: Add endpoints that use the beacon API to communicate with the beacon node instead of the gRPC API

## Possible challenges

The gRPC API and the Beacon REST API do not always map 1 to 1, so for some endpoint it can be very hard to have a perfect mapping. In those scenarios, it may be necessary to change the actual validator logic or just keep falling back to the gRPC in the short term while we try to find a better long term solution.

## Goal of the project

The main goal of the project is for the Prysm validator to be able to work with any beacon node that has a spec-compliant Beacon REST API, but doesn't support the Prysm gRPC API. For example, we should be able to run a Lighthouse beacon node and have the Prysm validdator interact with it. A good test to see how well it works would be to a Prysm validator together with a non-Prysm beacon node on a testnet for many days or weeks and make sure that it behaves as expected.

Since the main goal is already a big task, removing gRPC support is out of scope for this project. This would be an interesting goal for followup projects though in an effort to keep improving the quality of Prysm.

## Collaborators

### Fellows 

[@nalepae](https://github.com/nalepae)

### Mentors

[@rkapka](https://github.com/rkapka)

Other members of Prysmatic Labs have also helped with reviewing PRs and ironing out the details of the project:

[@nisdas](https://github.com/nisdas)

[@kasey](https://github.com/kasey)

[@prestonvanloon](https://github.com/prestonvanloon)

[@potuz](https://github.com/potuz)


## Resources

[Design Document (WIP)](https://hackmd.io/@pavignol/SJh-plvNo)

[Prysm Repository](https://github.com/prysmaticlabs/prysm)

PRs that I ([@pavignol](https://github.com/PatriceVignola)) have submitted to the Prysm repo so far:

[Add support for building a Beacon API validator client versus a gRPC one #11612](https://github.com/prysmaticlabs/prysm/pull/11612)

[Add customizable endpoints for the validator's REST API #11633](https://github.com/prysmaticlabs/prysm/pull/11633)

[Add REST implementation for Validator's WaitForChainStart #11654](https://github.com/prysmaticlabs/prysm/pull/11654)

[Add a gRPC fallback mode to the validator Beacon REST API #11679](https://github.com/prysmaticlabs/prysm/pull/11679)

[Onboard validator's beacon REST API tests to CI #11682](https://github.com/prysmaticlabs/prysm/pull/11682)

[Make the validator REST API's WaitForChainStart blocking #11695](https://github.com/prysmaticlabs/prysm/pull/11695)

[Onboard validator's Beacon REST API usage to e2e tests #11704](https://github.com/prysmaticlabs/prysm/pull/11704)

[Add REST implementation for Validator's DomainData #11711](https://github.com/prysmaticlabs/prysm/pull/11711)

[Add REST implementation for Validator's GetAttestationData #11714](https://github.com/prysmaticlabs/prysm/pull/11714)

[Fix DeepSource errors in the Validator's REST API #11726](https://github.com/prysmaticlabs/prysm/pull/11726)

[Add REST implementation for Validator's ProposeBeaconBlock #11731](https://github.com/prysmaticlabs/prysm/pull/11731)

[Add REST implementation for Validator's GetBeaconBlock #11772](https://github.com/prysmaticlabs/prysm/pull/11772)


PRs submitted by [@nalepae](https://github.com/nalepae):

[Update mockgen #11615](https://github.com/prysmaticlabs/prysm/pull/11615)

[Add REST implementation for Validator's WaitForActivation (Ethereum Protocol Fellowship) #11671](https://github.com/prysmaticlabs/prysm/pull/11671)

[Add REST implementation for Validator's ValidatorIndex #11712](https://github.com/prysmaticlabs/prysm/pull/11712)

[Add REST implementation for ValidatorStatus #11757](https://github.com/prysmaticlabs/prysm/pull/11757)
