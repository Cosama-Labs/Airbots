# AIRbot Terminology

**AIRbot** — AI Registered Bot; a purpose-built, versioned, self-contained AI agent package conforming to this standard.

**AI model** — a model used by an AIRbot. A model alone is not an AIRbot.

**AIRbot Package** — the versioned artifact inspected, scanned, verified, and deployed.

**AIRbot Manifest** — `airbot.manifest.json`, the immutable machine-readable behavior/security contract for one package version.

**Registry Record** — the external mutable history of identity, versions, verification, reputation, incidents, and lifecycle.

**Verification Record** — evidence that one exact package digest passed a declared verification profile.

**Verified Badge** — a resolvable visual/machine status bound to AIRbot ID + version + package digest.

**Task** — a predefined job the AIRbot is designed and permitted to perform.

**Skill** — a callable capability or integration used by tasks/workflows.

**Workflow** — constrained execution logic connecting tasks, skills, approvals, and outputs.

**Model-agnostic** — a runtime may select a model meeting declared requirements.

**Model-specific** — the package requires explicit model/provider constraints.

**Reputation** — operational history distinct from verification status.

**Cosmo** — mascot of the AIRbot Standard project.
