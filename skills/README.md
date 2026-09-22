# skills/

Skill packages published by this repository, in the conventional
`skills/<name>/SKILL.md` layout that git-based skill installers look for.

- [`agent-reach/`](agent-reach/) — the Agent Reach routing skill
  (`SKILL.md`, `SKILL_en.md`, `references/*.md`).

## Installing

```bash
# skills CLI (plural) — clones the repo and installs into your agents' skill dirs
npx skills add https://github.com/Panniantong/Agent-Reach.git

# skill CLI (singular) — downloads the files into ./.codebuddy/skills/agent-reach/
SKILL_BASE_URL=https://github.com/Panniantong/Agent-Reach/tree/main \
  npx skill skills/agent-reach

# or, once the agent-reach CLI is installed
agent-reach skill --install
```

`npx skill add <git-url>` does not exist — the singular `skill` CLI has no `add`
subcommand and takes a `skills/<name>` package name rather than a git URL.

## Note for maintainers

This directory is the **single source of truth** for the skill files. Wheels
re-publish the same files at `agent_reach/skill/` via the `force-include` entry
in `pyproject.toml`, so `importlib.resources` keeps working for installed users.
Edit the files here, never a copy inside `agent_reach/`.
