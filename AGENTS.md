# Repository Guidelines

## Project Structure & Module Organization

This repository distributes reusable Agent Skills. Keep installable skills in `skills/<skill-name>/SKILL.md` and keep the portable plugin manifest at the repository root as `plugin.json`. Store optional references and assets inside their owning skill, with paths relative to that skill.

## Official Format & Packaging

Follow the [Agent Skills specification](https://agentskills.io/specification): `name` must be 1–64 lowercase letters, numbers, or hyphens, match the parent directory, and have no leading, trailing, or repeated hyphens. `description` must explain both the skill's job and when to use it. Keep frontmatter to standard fields for portability; use `agents/openai.yaml` for Codex-specific UI metadata. The root plugin uses the [portable Agent Plugins format](https://developers.openai.com/plugins/build/plugins), which discovers skills from `skills/`.

## Skill Writing & Validation

Keep each skill focused on one workflow. Write clear, ordered instructions with explicit inputs and outputs. Keep `SKILL.md` under 500 lines, move detailed or branch-specific material into focused `references/` files, and use one-level relative links. Prefer instructions over scripts unless deterministic behavior or external tooling requires code. When available, run `skills-ref validate skills/<skill-name>`; exercise descriptions with positive and negative prompts before publishing.

## Install & Develop

There is no package build or automated test suite. The `.github/workflows/validate-skills.yml` workflow validates skill metadata and changed-line whitespace on pull requests and pushes to `main`. From a consuming repository, the Vercel-maintained Skills CLI can list or install this collection with `npx skills add /path/to/yarapa-skills/skills --list` or `npx skills add /path/to/yarapa-skills/skills --skill audit-repository --agent codex`. Keep both local-path and GitHub examples in `README.md` accurate. Run `git diff --check` and review changed references and metadata.

## Commit & Pull Request Guidelines

Git history currently contains only `Initial commit`, so no commit format is established. Use a concise imperative subject. Pull requests should explain the change, identify affected skills, and report checks performed. Update the README when skill names, install steps, or package metadata change.
