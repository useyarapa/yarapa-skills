# Yarapa Agent Skills

Portable skills for repository audits and GitHub issue and pull request workflows. Each skill lives in `skills/<name>/SKILL.md` and follows the [Agent Skills specification](https://agentskills.io/specification). The root `plugin.json` packages the collection as a portable Agent Plugin.

## Install Skills into Another Repository

Use the [Skills CLI](https://github.com/vercel-labs/skills) from the repository where the skills should be available. This CLI accepts a local skills directory or a GitHub repository and installs skills at project scope.

```sh
# List skills from a local clone
npx skills add /path/to/yarapa-skills/skills --list

# Install one skill from a local clone
npx skills add /path/to/yarapa-skills/skills --skill audit-repository --agent codex

# Install from GitHub after the skills are committed and pushed
npx skills add useyarapa/yarapa-skills --skill audit-repository --agent codex
```

Use `--skill '*'` to install the full collection or repeat `--skill` to select several skills. Replace the local path with the path to this repository's `skills/` directory.

## Codex and ChatGPT Plugin Distribution

This repository packages its skills as a portable plugin, with `plugin.json` at the root and skills in `skills/`. The Skills CLI commands above install individual skills. To test or share the complete plugin through a Codex repo or personal marketplace, follow the [official plugin and marketplace setup guide](https://developers.openai.com/plugins/build/plugins); marketplace distribution is separate from public listing. To publish in the universal Codex and ChatGPT Plugins Directory, submit the package through the [official plugin submission process](https://developers.openai.com/plugins/deploy/submission). OpenAI reviews submissions and approves them before publication.

## Included Skills

- `audit-repository` — evidence-based, read-only repository audits.
- `create-github-issue` — draft or create issues using repository templates and policies.
- `create-github-pr` — prepare or create pull requests using branch changes and repository guidance.

## Contributing

See [contribution guidance](.github/CONTRIBUTING.md) and the [pull request template](.github/PULL_REQUEST_TEMPLATE.md). Pull requests to `main` run skill metadata and whitespace validation.
