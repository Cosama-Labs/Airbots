# AIRbot Standard Specification

**Version:** Draft 0.2.0  
**Standard:** AIRbot — AI Registered Bot  
**Standard family:** AROS — Agentic Registry Open Standard

## 1. Scope

This specification defines the portable package, manifest, verification, registration, versioning, and marketplace-conformance requirements for an **AIRbot (AI Registered Bot)**.

An AIRbot is a **purpose-built AI agent** designed to execute a defined role or bounded set of tasks. It is not an AI model, foundation model, chatbot session, prompt by itself, tool by itself, or generic model endpoint.

An AIRbot MAY use one or more AI models. It MAY be model-agnostic or model-specific. Model choice is part of AIRbot execution policy, not its category definition.

## 2. Normative language

The terms **MUST**, **MUST NOT**, **REQUIRED**, **SHOULD**, **SHOULD NOT**, and **MAY** are normative.

## 3. AIRbot definition

A conforming AIRbot MUST be a versioned, self-contained agent package with a declared purpose and the behavior/security contracts required by this specification.

Each AIRbot version MUST declare:

1. persistent AIRbot identity;
2. semantic version;
3. publisher/owner;
4. purpose and operational boundaries;
5. predefined tasks;
6. skills/capabilities;
7. workflows;
8. input contracts;
9. output contracts;
10. model policy;
11. security controls;
12. credential requirements and protection policy;
13. governance rules;
14. A2A Agent Card location;
15. deployment method(s);
16. package digest and digest algorithm.

Marketplace verification additionally requires external registration and verification records.

## 4. What is not an AIRbot

The following are not AIRbots by themselves:

- foundation or language models;
- model API endpoints;
- raw prompts/system prompts;
- individual tools, plugins, MCP servers, or API integrations;
- unbounded chat sessions;
- workflow fragments without an agent package;
- registry records with no corresponding agent artifact.

These MAY be dependencies or components of an AIRbot.

## 5. AIRbot package

A distributable AIRbot package MUST include:

```text
airbot-package/
├── airbot.manifest.json
├── agent-card.json
├── workload/
└── NOTICE
```

It SHOULD include when applicable:

```text
├── workflows/
├── schemas/
├── policies/
├── tests/
├── sbom/
└── docs/
```

A registry MAY support an immutable external workload artifact if its digest is included in the manifest and can be independently verified.

**Self-contained** means the package contains or immutably identifies everything necessary to determine what is being verified: code/configuration, prompts, workflows, skills, dependencies, model policy, permissions, security policy, and external interfaces.

Runtime secrets MUST NOT be embedded.

## 6. AIRbot manifest

The canonical filename is `airbot.manifest.json`.

The manifest is part of the verified package and becomes immutable after verification.

## 7. Purpose and boundaries

`purpose` MUST describe the specific role of the AIRbot. Examples include Instagram content publishing, social-media management, financial-planning assistance, support-ticket intake, procurement research, or invoice triage.

The manifest SHOULD declare `out_of_scope` behaviors. A verified AIRbot MUST NOT silently expand its declared role.

## 8. Tasks

`tasks` defines the predefined jobs the AIRbot is designed to perform.

Each task MUST have a stable identifier and description. Tasks SHOULD identify risk level and human-approval requirements.

A verified AIRbot MUST NOT execute a materially new task absent from the verified manifest.

## 9. Skills

Skills are callable capabilities used by tasks or workflows. A skill MAY represent an internal function, API, MCP tool/server, A2A peer capability, database interface, knowledge source, browser capability, or connector.

Skill declarations MUST NOT contain credentials.

## 10. Workflows

Workflows define controlled execution paths and SHOULD declare associated tasks, required skills, execution steps or graph, approval gates, retry/failure behavior, termination conditions, and side effects.

Dynamic behavior MUST remain bounded by constraints contained in the verified package.

## 11. Input and output contracts

AIRbots MUST declare external input and output contracts. Structured contracts SHOULD use JSON Schema.

Inputs MAY define required data, validation, content types, size limits, sensitivity classes, and preprocessing rules.

Outputs MAY define returned data, artifacts, text, files, events, API side effects, or state changes.

## 12. Model policy

Each AIRbot MUST declare one model mode:

- `model_agnostic` — a compliant runtime may select models satisfying declared requirements;
- `model_specific` — the AIRbot requires explicitly declared model/provider constraints.

A model-agnostic AIRbot SHOULD declare minimum capabilities such as tool calling, structured output, modality, context size, or other requirements.

Changing model policy or required model constraints requires a new AIRbot version.

## 13. Security

An AIRbot MUST declare relevant security requirements including permissions, denied scopes, network policy, storage/filesystem policy, isolation requirements, data restrictions, allowed external services, sandbox requirements, code-execution policy, approval rules, and action/rate limits where applicable.

Permissions MUST follow least privilege.

Capability does not imply permission.

## 14. Credentials and secrets

Verified AIRbot packages MUST NOT contain production credentials, private keys, API tokens, passwords, session cookies, refresh tokens, or reusable secrets.

The manifest MUST declare `embedded_secrets_allowed: false`.

Credential requirements MAY describe provider/service, type, scopes, tenancy, and secure runtime binding.

Credentials MUST be supplied out of band by the runtime or deployment environment.

## 15. Governance

An AIRbot MUST declare applicable governance rules. These MAY include human approvals, prohibited actions, data handling, retention, audit logging, incident reporting, jurisdiction/compliance constraints, escalation behavior, and usage limits.

Package governance is part of the verified artifact. Changing it requires a new version.

## 16. A2A Agent Card

Every marketplace-eligible AIRbot MUST include or immutably reference an A2A Agent Card as `agent-card.json`.

The Agent Card and AIRbot manifest serve different purposes: the Agent Card supports agent discovery/interoperability; the AIRbot manifest defines AIRbot package, security, governance, model, deployment, credential, version, and verification semantics.

Changing the Agent Card changes the AIRbot package digest and requires a new verification cycle.

## 17. Deployment

An AIRbot MUST declare one or more supported deployment methods, such as Vercel, Cloudflare Worker, OCI/container image, Kubernetes, serverless, managed AIRbot runtime, private enterprise runtime, or local/on-prem deployment.

A deployment claiming verified AIRbot status MUST run the exact verified package or artifact digest.

## 18. Package integrity and immutability

Every submitted AIRbot version MUST have a cryptographic package digest. SHA-256 is REQUIRED for Draft 0.2 baseline interoperability.

Once a version reaches verified status, every artifact covered by verification MUST be immutable.

Changes to code, prompts/system instructions, model constraints, tasks, skills, workflows, I/O schemas, permissions, governance/security policy, Agent Card, dependencies, deployment artifact/reference, or execution/trust metadata invalidate the existing verified artifact.

A registry MUST NOT move a verified badge to a different digest while retaining the same version.

## 19. Versioning

AIRbot versions SHOULD use Semantic Versioning.

Any change to a verified package requires a new version. The new version MUST be submitted, scanned, validated, verified, registered, and logged independently.

Prior versions MUST remain historically resolvable, even if retired or revoked, subject to legitimate legal/privacy constraints.

## 20. Registration

Registration creates or updates the external AIRbot Registry Record.

A registry record MUST contain AIRbot identity, publisher/owner, version history, package digest per version, verification state, lifecycle state, verification-evidence references, reputation history or reference, and incident/revocation history where applicable.

Registration alone does not imply verification.

## 21. Verification

A marketplace-verified AIRbot version MUST pass at least:

1. schema/format validation;
2. package integrity calculation;
3. security scan appropriate to package type;
4. dependency/SBOM or dependency-risk inspection where applicable;
5. secret/credential scan;
6. permission and network-policy review;
7. governance conformance validation;
8. A2A Agent Card validation;
9. workload integrity check;
10. registry identity/publisher checks required by the registry.

Higher-risk AIRbots MAY require stronger controls and sandbox/dynamic testing.

## 22. Verified badge

A Verified AIRbot badge MUST be bound to:

- `airbot_id`;
- `version`;
- `package_digest`;
- verification profile/version;
- verification timestamp;
- verifier/registry identity.

A badge MUST NOT transfer to modified code or another version.

Verification means the exact version met the declared verification profile at review time. It is not a guarantee of future safety, correctness, legality, or fitness for purpose.

## 23. Marketplace eligibility

A marketplace claiming AIRbot Marketplace Conformance MUST NOT label an AIRbot version verified unless it has a conforming manifest, valid A2A Agent Card, current verification record for the exact digest, non-revoked status, required deployment metadata, credential/security conformance, and resolvable registry identity/version history.

Unverified agents MAY be listed, but MUST NOT be presented as Verified AIRbots.

## 24. Reputation

Reputation is separate from verification.

Reputation MAY include successful task history, failure rates, ratings, incidents, policy violations, uptime, disputes, verified deployment history, and publisher reputation.

A registry MUST preserve material negative history and MUST NOT reset reputation merely because a new version is released.

## 25. Lifecycle

Recommended states:

`development`, `submitted`, `validating`, `security_scanning`, `governance_review`, `verified`, `active`, `suspended`, `revoked`, `retired`.

`verified` means a verification record exists for the exact digest. `active` means the version is permitted for use/listing under registry policy.

## 26. Registry neutrality

AIRbot is a portable standard. AROS MAY implement it as a reference registry, but conforming AIRbot packages MUST NOT require one marketplace, model provider, cloud provider, runtime framework, or registry vendor unless explicitly declared as a package dependency.

## 27. Extensions

Extensions MUST use namespaced keys and MUST NOT weaken core security, immutability, credential, or verification requirements.
