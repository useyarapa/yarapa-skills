# Create GitHub Issue

## Purpose

Prepare or create GitHub issues against a confirmed repository while following its reporting policy, templates, and routing rules.

## When to use

Use this skill when the user asks to draft, prepare, file, open, or create a GitHub issue for a bug, feature request, or other supported repository issue route.

## Behavior

The skill confirms the target repository, discovers applicable repository guidance and issue templates from the authoritative default branch, preserves the selected template as an output contract, and drafts only from verified evidence. Security reports are routed through verified private reporting paths rather than disclosed in public issues.

## Safety and write boundary

Drafting is read-only. The skill creates an issue only when the user explicitly asks to create or submit it. Labels, assignees, milestones, and projects are added only when requested and verified. It does not invent missing required facts, flatten incompatible YAML issue forms, or expose sensitive material.

## Files

- `SKILL.md` — authoritative agent workflow and creation contract.
- `tests/pressure-scenarios.md` — manual regression scenarios for routing, templates, activation, and portability.
