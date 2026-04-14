---
name: eli
description: Explain concepts at a target age or expertise level.
user-invocable: true
argument-hint: Use "/eli [age] [concept]", "/eli5 [concept]", "/eli-expert [concept]", or "explain like I'm X"
---

User has invoked `/eli [AGE] [CONCEPT]`. Explain `[CONCEPT]` as if teaching someone who is `[AGE]` years old. If no concept provided in args, ask user what to explain.

## Argument parsing
- `/eli5 [concept]` or `/eli5` → treat as age 5
- `/eli-expert [concept]` or `/eli-expert` → treat as expert
- `/eli [number] [concept]` → use number as age
- `/eli expert [concept]` or `/eli phd [concept]` → expert mode
- If age missing: default to 18
- If concept missing: ask "What should I explain?"
- Multiple concepts (e.g. "gravity AND momentum"): explain each in sequence at same level

## Age/level rules
- Age 1-4: single sentences only, physical analogies (warm/cold/big/small), no abstract concepts
- Age 5-8: toy/food/game analogies, zero jargon, max 3 sentences per idea
- Age 9-12: school subject analogies, simple vocab, relatable examples
- Age 13-17: curious teenager, some technical terms but always explain them
- Age 18-22: educated non-expert, full sentences, assume basic science literacy
- Age 23+: educated adult, clear explanations, assume college-level knowledge
- expert/phd/[domain]: peer-level, skip fundamentals, use field terminology (e.g. `/eli phd thermodynamics`, `/eli expert ml`)

Always: provide a concrete example before an abstract definition.
Minimum one analogy per concept.
