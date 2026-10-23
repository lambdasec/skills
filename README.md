# lambdasec skills

Agent Skills for four open-source tools. Each skill is a folder with a `SKILL.md` in the open [Agent Skills](https://agentskills.io) format, so it works in any agent that reads skills: Claude Code, Codex, Cursor, OpenCode, Gemini CLI, GitHub Copilot and others.

| Skill | What it does | Tool |
|---|---|---|
| [frame-security-scan](skills/frame-security-scan) | Scan Python code for vulnerabilities, triage the findings, generate and verify fixes, re-scan | [lambdasec/frame](https://github.com/lambdasec/frame) |
| [adaptive-classifier](skills/adaptive-classifier) | Build text classifiers that learn new examples and new classes without retraining, and evaluate them honestly | [codelion/adaptive-classifier](https://github.com/codelion/adaptive-classifier) |
| [pts-pivotal-token-search](skills/pts-pivotal-token-search) | Find the tokens, sentences and latent concepts that change whether a model solves a task, and turn them into datasets | [codelion/pts](https://github.com/codelion/pts) |
| [optiq-local-models](skills/optiq-local-models) | Pick, serve and check a quantized model on an Apple Silicon Mac with an OpenAI-compatible endpoint | [mlx-optiq](https://mlx-optiq.com) |

## Install

With the [skills CLI](https://skills.sh), for any supported agent:

```bash
npx skills add lambdasec/skills
npx skills add lambdasec/skills --skill frame-security-scan   # just one
```

As a Claude Code plugin marketplace:

```
/plugin marketplace add lambdasec/skills
/plugin install frame-security-scan@lambdasec-skills
```

Or copy a folder from `skills/` into your agent's skills directory, such as `.claude/skills/` or `.agents/skills/`.

## What the skills will and won't do

The skills are plain Markdown with no bundled scripts. They do not install software: each one checks that its tool is already installed and points to the tool's own install steps if it is not. They ask before anything downloads model weights or datasets, sends code to a network endpoint, changes files, or publishes to the Hugging Face Hub. Numbers quoted in the skills come from each project's README, with its caveats.

## License

Apache-2.0. See [LICENSE](LICENSE).
