---
name: capability-consumer
description: Demonstrates consuming a capability without depending on a provider Skill name.
---

# Capability Consumer

## Requirement

This Skill requires the capability:

- `greeting`

## Discovery rule

Do not assume or name a particular provider Skill.

When `greeting` is needed:

1. Inspect the available Skills and their declared capabilities.
2. Find a Skill that provides `greeting`.
3. Read that Skill's public entry instructions.
4. Use the public entry to fulfill the requirement.

If no provider can be discovered, report that the capability is unavailable rather than inventing a provider.
