<div align="center">

<img src="assets/cosmo-airbots.jpg" alt="Cosmo — AIRbot Standard mascot" width="320" />

# AIRbot Standard

### The Open Standard for Registered, Verified AI Agents

**AIRbot = AI Registered Bot**

Purpose-built • Registered • Security-scanned • Verified • Versioned • Governed

[**airbots.co**](https://airbots.co) · [Specification](SPECIFICATION.md) · [Conformance](CONFORMANCE.md) · [Security](SECURITY.md) · [Governance](GOVERNANCE.md)

**Draft v0.2.0** · Part of the **AROS — Agentic Registry Open Standard** family

</div>

---

## An AI model is not an AIRbot

An **AIRbot** is a purpose-built, self-contained AI agent developed for a defined role or task — such as an Instagram agent, social-media agent, financial-planning agent, support agent, research agent, or procurement agent.

An AI model may power an AIRbot, but the model itself is not the agent.

An AIRbot packages the behavior and controls required to perform its role in a form that can be inspected, registered, security-scanned, verified, deployed, versioned, and governed.

> **AIRbot:** A registered, versioned, purpose-built AI agent with predefined tasks, skills, workflows, input requirements, output requirements, model policy, security controls, credential-protection rules, governance requirements, an A2A Agent Card, declared deployment methods, and immutable verification of each approved version.

## The defining rule

> **A verified AIRbot version is immutable.**

Verification applies to an exact package digest. Once a version has passed standards validation, security scanning, governance checks, and registration, its verified contents MUST NOT change.

Any change to code, prompts, workflows, skills, dependencies, permissions, model policy, input/output contracts, Agent Card, deployment definition, or other behavior-affecting content requires a **new AIRbot version** and a new verification cycle.

## What makes an AIRbot

A conforming AIRbot defines:

- **Purpose** — the specific role the agent exists to perform.
- **Tasks** — the predefined jobs it may execute.
- **Skills** — tools, APIs, MCP servers, functions, knowledge interfaces, and internal capabilities.
- **Workflows** — controlled execution paths.
- **Input contracts** — required/optional inputs, types, validation, and constraints.
- **Output contracts** — response schemas, artifacts, side effects, and result requirements.
- **Model policy** — model-agnostic or model-specific requirements.
- **Security controls** — permissions, isolation, network policy, data handling, and execution restrictions.
- **Credential protection** — credential requirements and secure runtime injection; secrets are never embedded.
- **Governance** — approval gates, audit requirements, restricted actions, retention, and policy rules.
- **A2A Agent Card** — agent-to-agent discovery and interoperability metadata.
- **Deployment declaration** — e.g. Vercel, Cloudflare Worker, container, Kubernetes, managed runtime, private enterprise runtime.
- **Package integrity** — cryptographic digest identifying the exact reviewed artifact.
- **Registration** — persistent AIRbot identity and version history.
- **Verification** — scan/validation evidence and verified badge bound to one exact version/digest.
- **Reputation history** — operational history, incidents, ratings, and trust signals maintained separately from verification.

## AIRbot vs. model

```text
AI MODEL
GPT / Claude / Gemini / Llama / other model
        │
        │ may power
        ▼
AIRBOT
Purpose-built agent package
Tasks + skills + workflows + I/O contracts
Security + governance + credential policy
A2A Agent Card + deployment declaration
        │
        │ registered / verified by
        ▼
REGISTRY (for example AROS)
Identity + versions + scan evidence + badge
Reputation + incidents + lifecycle history
        │
        ▼
MARKETPLACE / ENTERPRISE CATALOG / PRIVATE DEPLOYMENT
```

A model is a dependency or execution resource. It does not become an AIRbot merely because it can answer prompts or call tools.

## Three separate objects

The standard deliberately separates:

1. **AIRbot Package** — the self-contained, versioned artifact that is scanned and deployed.
2. **AIRbot Manifest** — the machine-readable contract describing that package.
3. **AIRbot Registry Record** — the external record holding registration, verification, reputation, lifecycle, and version history.

The verified package is immutable. The registry record continues to evolve as reputation, incidents, suspensions, deployments, and newer versions are recorded.

## Verification lifecycle

```text
DEVELOPMENT
   ↓
SUBMITTED
   ↓
FORMAT + STANDARDS VALIDATION
   ↓
SECURITY SCAN
   ↓
GOVERNANCE / POLICY REVIEW
   ↓
DIGEST LOCK
   ↓
VERIFIED + REGISTERED
   ↓
MARKETPLACE ELIGIBLE
   ↓
DEPLOYED
   ↓
REPUTATION / AUDIT / INCIDENT HISTORY
```

A changed digest invalidates verification for that version.

## Cosmo

**Cosmo is the official mascot of the AIRbot Standard.**

His job is simple: make a serious agent standard recognizable without making it boring.

## Project links

- **Website:** [airbots.co](https://airbots.co)
- **Canonical specification:** [SPECIFICATION.md](SPECIFICATION.md)
- **Conformance:** [CONFORMANCE.md](CONFORMANCE.md)
- **Security:** [SECURITY.md](SECURITY.md)
- **Governance:** [GOVERNANCE.md](GOVERNANCE.md)
- **Versioning:** [VERSIONING.md](VERSIONING.md)
- **Terminology:** [TERMINOLOGY.md](TERMINOLOGY.md)

## Repository structure

```text
Airbots/
├── README.md
├── SPECIFICATION.md
├── CONFORMANCE.md
├── SECURITY.md
├── GOVERNANCE.md
├── VERSIONING.md
├── TERMINOLOGY.md
├── NOTICE.md
├── VERSION
├── assets/
│   └── cosmo-airbots.jpg
├── schemas/
│   ├── airbot-manifest.schema.json
│   ├── registry-record.schema.json
│   └── verification-record.schema.json
└── docs/
    └── a2a-agent-card.md
```

---

<div align="center">

**AIRbot Standard — Define the agent. Verify the artifact. Trust the version.**

[airbots.co](https://airbots.co)

</div>
