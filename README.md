# lambdasec skills

Agent Skills for four tools: three open-source projects (Frame, adaptive-classifier and PTS) and the mlx-optiq package for Apple Silicon, plus rsi-skill, which measures and improves prompts. Each skill is a folder with a `SKILL.md` in the open [Agent Skills](https://agentskills.io) format, so it works in any agent that reads skills: Claude Code, Codex, Cursor, OpenCode, Gemini CLI, GitHub Copilot and others.

| Skill | What it does | Tool |
|---|---|---|
| [frame-security-scan](skills/frame-security-scan) | Scan Python, JavaScript/TypeScript, Java, C# and C/C++ code for vulnerabilities, triage the findings, generate and verify fixes, re-scan | [lambdasec/frame](https://github.com/lambdasec/frame) |
| [adaptive-classifier](skills/adaptive-classifier) | Build text classifiers that learn new examples and new classes without retraining, and evaluate them honestly | [codelion/adaptive-classifier](https://github.com/codelion/adaptive-classifier) |
| [pts-pivotal-token-search](skills/pts-pivotal-token-search) | Find the tokens, sentences and latent concepts that change whether a model solves a task, and turn them into datasets | [codelion/pts](https://github.com/codelion/pts) |
| [optiq-local-models](skills/optiq-local-models) | Pick, serve and check a quantized model on an Apple Silicon Mac with an OpenAI-compatible endpoint | [mlx-optiq](https://mlx-optiq.com) |
| [rsi-skill](skills/rsi-skill) | Score a prompt on your own test cases, then hill-climb it to a measurably better version with any open model. [GSM8K example: 17% to 92% on held-out problems](skills/rsi-skill/references/example-gsm8k.md) | [OptiQ Cloud](https://cloud.mlx-optiq.com), a local `optiq serve`, or any OpenAI-compatible API |

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

The `frame-security-scan` plugin also connects the [frame MCP server](https://github.com/lambdasec/frame-mcp) (`uvx frame-mcp`, needs [uv](https://docs.astral.sh/uv/)), so Frame's scan, verify and fix are available as tools. Outside Claude Code: `claude mcp add frame -- uvx frame-mcp` or `uvx frame-mcp` in any MCP client.

Or copy a folder from `skills/` into your agent's skills directory, such as `.claude/skills/` or `.agents/skills/`.

## What the skills will and won't do

The skills are plain Markdown with no bundled scripts, except rsi-skill, which ships one standard-library Python script (`scripts/rsi.py`) that sends your prompt and test cases to the model endpoint you choose. They do not install software: each one checks that its tool is already installed and points to the tool's own install steps if it is not. The one exception is the `frame-security-scan` plugin's MCP server entry: when Claude Code starts it, uv downloads `frame-mcp` and Frame from PyPI. They ask before anything downloads model weights or datasets, sends code to a network endpoint, changes files, or publishes to the Hugging Face Hub. Numbers quoted in the skills come from each project's README, with its caveats.

## License

Apache-2.0. See [LICENSE](LICENSE).
