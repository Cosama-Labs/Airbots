# AIRbot Security Standard

AIRbots are executable/agentic artifacts and MUST be treated as software supply-chain objects, not merely prompt files.

## Baseline requirements

Verified packages MUST:

- contain no production secrets;
- declare external permissions and network access;
- use least privilege;
- declare credential bindings instead of credentials;
- provide enough dependency/provenance information for scanning;
- bind verification to a cryptographic digest;
- be immutable after verification;
- require a new version after any behavior-affecting change.

## Marketplace security gates

A conforming verification profile SHOULD include:

1. malware/static code scan where applicable;
2. dependency vulnerability inspection;
3. secret detection;
4. prompt/instruction review for hidden unsafe behaviors where feasible;
5. network destination review;
6. permissions review;
7. credential-flow review;
8. data-exfiltration risk review;
9. deployment artifact integrity validation;
10. sandbox/dynamic execution testing for higher-risk packages.

## Credential protection

Secrets MUST be supplied by a secure runtime/provider mechanism such as a secrets manager, encrypted environment binding, delegated OAuth token, workload identity, or equivalent platform capability.

AIRbot packages MUST NOT log secrets or return them in outputs.

## Vulnerabilities discovered after verification

A newly discovered vulnerability does not rewrite historical verification evidence. A registry MAY suspend or revoke an affected version and SHOULD link the event to that version's incident and reputation history.
