---
name: weather-helper
description: Provides a weather greeting by collaborating with another Skill that can provide a general greeting.
---

# Weather Helper

## Capability

I can provide a `weather-greeting`.

To produce a weather greeting, I need a general `greeting` capability from another available Skill. Discover that capability by reading available Skills and use the provider's public entry. Do not depend on a specific provider Skill name.

## Public entry

When another Agent or Skill needs a weather greeting, use this public entry:

> Produce a weather greeting by first discovering and using an available Skill that provides `greeting`, then add a weather-related context to that greeting.

The caller should depend on the capability (`weather-greeting`), not on this Skill's name or internal implementation.
