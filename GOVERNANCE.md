# AIRbot Governance

AIRbot governance exists at two layers:

1. **Package governance** — immutable rules shipped with an AIRbot version.
2. **Registry governance** — external decisions about verification, marketplace eligibility, suspension, revocation, reputation, and policy profiles.

Package governance MAY require human approval, evidence retention, jurisdiction rules, restricted actions, data boundaries, audit logging, escalation paths, and compliance obligations.

A runtime MAY enforce stricter policy than the package declares. It MUST NOT silently relax mandatory package governance while claiming to execute the verified AIRbot unchanged.

Changes to package governance require a new AIRbot version and verification cycle.
