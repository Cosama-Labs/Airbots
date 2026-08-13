# AIRbot Versioning and Immutability

## Core rule

**One verified version = one immutable package digest.**

Example:

```text
airbot:example.com:social-media-manager
  1.0.0  sha256:AAA...  verified  retired
  1.1.0  sha256:BBB...  verified  active
  1.1.1  sha256:CCC...  submitted
```

A registry MUST NOT replace `sha256:BBB...` with a different artifact and continue presenting version `1.1.0` as the same verified AIRbot.

## Update process

1. modify the package;
2. increment the AIRbot version;
3. rebuild/canonicalize the package;
4. calculate the package digest;
5. submit the new version;
6. validate and scan;
7. verify;
8. create the new verification record;
9. register the new version;
10. deploy the exact verified digest;
11. retain prior version and reputation history.

Credential rotation alone does not require a new AIRbot version when the credential contract is unchanged, because secret values are not part of the verified package.
