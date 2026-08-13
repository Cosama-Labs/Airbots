# A2A Agent Card

Every marketplace-eligible AIRbot MUST include or immutably reference an A2A Agent Card.

The Agent Card is not a replacement for `airbot.manifest.json`.

- **A2A Agent Card:** discovery, supported interfaces, capabilities/skills, interaction and authentication metadata.
- **AIRbot Manifest:** purpose, tasks, workflows, input/output contracts, model policy, package digest, security/governance rules, credential contract, deployment, and AIRbot-specific version/verification metadata.

The Agent Card is part of the verified AIRbot package boundary. Changing it changes the package digest and requires a new AIRbot version and verification cycle.

The Agent Card MUST NOT contain secrets.

Deployments SHOULD expose the Agent Card using the discovery mechanism required by the A2A version they implement.
