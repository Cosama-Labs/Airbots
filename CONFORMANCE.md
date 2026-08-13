# AIRbot Conformance

## AIRbot Package Conformance

A package conforms when it contains a valid AIRbot manifest, A2A Agent Card, resolvable workload, package digest, and all required behavior/security contracts.

## AIRbot Registered

A conforming package is **AIRbot Registered** when a registry has assigned or resolved its AIRbot ID and version record.

Registration does not imply verification.

## AIRbot Verified

A specific AIRbot version is **AIRbot Verified** only when the exact package digest has passed the registry's declared verification profile and has a valid verification record.

A Verified badge MUST resolve to the AIRbot ID, version, package digest, verifier, verification timestamp, and verification profile.

## AIRbot Marketplace Conformance

A marketplace conforms when it:

- requires verification for items labeled **Verified AIRbot**;
- checks the exact digest before deployment/listing;
- distinguishes verification from reputation;
- exposes version and verification history;
- does not permit post-verification package mutation;
- removes or marks suspended/revoked versions promptly;
- never distributes embedded production secrets as part of an AIRbot package.
