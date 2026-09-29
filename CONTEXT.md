# Yarapa Skills — Repository Context

## Project Overview

`yarapa-skills` is a repository of portable, reusable agent skills maintained by `useyarapa`. It provides specialized capabilities for coding agents:

- Evidence-based repository audits
- GitHub issue preparation and creation
- GitHub pull request drafting and creation

The repository serves two distribution channels:

1. **Agent Skills CLI**: Consumed via `@vercel/skills` (`npx skills add`) for project-level installation into AI agent workspaces.
2. **OpenAI / Codex Agent Plugin**: Packaged via root `plugin.json` following the portable Agent Plugins specification.

## Repository Structure

```text
.
├── .github/
│   ├── ISSUE_TEMPLATE/           # Issue templates for bug reports and feature requests
│   ├── workflows/
│   │   └── validate-skills.yml   # CI validation using skills-ref and git whitespace checks
│   ├── CONTRIBUTING.md           # Contribution guidelines
│   ├── PULL_REQUEST_TEMPLATE.md  # PR checklist and report format
│   └── SECURITY.md               # Security policy
├── skills/
│   ├── audit-repository/
│   │   ├── SKILL.md              # Entrypoint: read-only, standards-driven audits
│   │   ├── references/           # Detailed protocols, sources, framework selection, finding contract
│   │   └── tests/                # Pressure test scenarios
│   ├── create-github-issue/
│   │   ├── SKILL.md              # Entrypoint: issue drafting from repo templates & policies
│   │   └── tests/                # Pressure test scenarios
│   └── create-github-pr/
│       ├── SKILL.md              # Entrypoint: PR preparation from branch changes
│       └── tests/                # Pressure test scenarios
├── AGENTS.md                     # Universal agent instructions & packaging guidelines
├── CLAUDE.md                     # Claude Code guidance & common commands
├── CONTEXT.md                    # Repository context and architectural overview
├── LICENSE                       # Project license
├── README.md                     # User-facing installation and usage guide
└── plugin.json                   # Root plugin manifest (agent-plugins schema 1.0.0)
```

## Architectural Principles & Standards

### Agent Skills Specification

Every skill in `skills/<skill-name>/`:

- Main instruction file is named `SKILL.md`.
- Frontmatter requires `name` (1–64 characters, lowercase alphanumeric and single hyphens, matching parent directory) and `description` (explains capability and triggering condition).
- Instruction files must stay under 500 lines. Extended rules, matrices, or checklists must be moved to `references/` and referenced via one-level relative paths.
- Avoid runtime scripts unless deterministic execution or external tools require code; prefer clear natural language instructions.

### Agent Plugins Specification

- Root `plugin.json` adheres to `https://agent-plugins.org/schemas/1.0.0/plugin.schema.json`.
- Exposes plugin metadata, capabilities, default prompts, and OpenAI extensions (`com.openai`).

## Development & Validation Workflows

### Validation Commands

- **Install reference validator:** `python -m pip install "git+https://github.com/agentskills/agentskills.git@69ef37e9424c0a7ea9dd2293b559e43ec8176379#subdirectory=skills-ref"`
- **Validate single skill:** `skills-ref validate skills/<skill-name>`
- **Validate all skills:** `for s in skills/*/SKILL.md; do skills-ref validate "$(dirname "$s")"; done`
- **Check whitespace and formatting:** `git diff --check`

### Local Testing with Skills CLI

- **List skills in repo:** `npx skills add ./skills --list`
- **Install skill for target agent:** `npx skills add ./skills --skill <skill-name> --agent <codex|claude|cursor>`

## CI/CD Pipeline

The `.github/workflows/validate-skills.yml` action triggers on pushes and pull requests to `main`:

1. Sets up Python 3.13.
2. Installs pinned `skills-ref` validator.
3. Runs `skills-ref validate` on every skill in `skills/`.
4. Executes `git diff --check` to block trailing whitespace and formatting defects.

## Contribution & Commit Rules

- **Commits**: Concise imperative subject line.
- **Pull Requests**: Identify affected skills, outline manual and automated checks, and maintain README / metadata parity when changing skills.
