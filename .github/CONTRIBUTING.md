# Contributing

Keep each skill focused on one reusable workflow. Put the required `SKILL.md` in `skills/<skill-name>/`, match its frontmatter `name` to that directory, and keep optional references beside their owning skill.

Before opening a pull request:

- Run `git diff --check`.
- When available, run `skills-ref validate skills/<skill-name>` for each changed skill. `skills-ref` is a reference validator, not a runtime dependency.
- For changed descriptions, consider positive and negative prompts that show when the skill should and should not activate.
- Report checks run and their results in the pull request description.

See [Repository Guidelines](../AGENTS.md) for the complete format and packaging rules. The `Validate Agent Skills` workflow runs on pull requests to `main` and pushes to `main`.
