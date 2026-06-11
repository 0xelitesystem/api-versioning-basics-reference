# Breaking versus non-breaking changes

A breaking change is any change that can break a client coded against the old behavior; a non-breaking change is one existing clients can ignore safely. The whole point of versioning is to contain breaking changes behind new versions while shipping non-breaking changes freely. Knowing the difference precisely is the most important skill in evolving an API.

## What breaks a client

Breaking changes are the ones that violate what a client already assumes. Removing a field, renaming a field, changing a field's type, making an optional request field required, removing an endpoint, changing a status code's meaning, tightening validation, or altering the meaning of an existing value all qualify. Each can cause an existing client to crash, misparse, or behave wrong. The test is simple: if a client built against the old contract could fail because of this change, it is breaking.

## What is safe to add

Non-breaking changes are additive and tolerant. Adding a new optional field to a response, adding a new endpoint, adding a new optional request parameter, or accepting a new value while still honoring the old ones are generally safe, provided clients follow the rule of ignoring fields they do not recognize. A well behaved client should not choke on extra data it did not expect. When clients honor that, you can grow the API substantially within a single version.

## The tolerant reader rule

Much of safe evolution rests on clients being tolerant readers: ignoring unknown fields rather than rejecting them, not depending on field order, and not assuming a response contains only the fields they know. You cannot force callers to be tolerant, but you can document the expectation and design responses that reward it. Producers should be conservative in what they remove or change; consumers should be liberal in what they accept. That pairing is what lets an API add features without a version bump.

## When in doubt, treat it as breaking

If you are unsure whether a change is breaking, assume it is and version it. The cost of an unnecessary version is some extra maintenance; the cost of an unexpected breaking change is broken integrations, support load, and lost trust. Edge cases, like changing default values, narrowing a numeric range, or altering null handling, break clients more often than people expect. Erring toward caution protects the contract, which is the entire reason versioning exists.
