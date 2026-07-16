# agent_setup

Personal Cursor agent setup, synced across machines. This repo lives directly in `~/.cursor/skills/` so skills are edited in place and synced with plain git.

## Contents

- `<skill-name>/SKILL.md` — Cursor Agent Skills (loaded globally, in every project)
- `AGENTS.md` — baseline AI assistant guidance, copied into new projects
- `CLAUDE.md` — pointer to AGENTS.md for tools that look for CLAUDE.md

## Setup on a new machine

```powershell
git clone https://github.com/learkonas/agent_setup "$env:USERPROFILE\.cursor\skills"
```

If `~/.cursor/skills` already exists with content, clone elsewhere and merge manually, or move the existing folder aside first.

## Syncing

- After adding or editing a skill: commit and push from `~/.cursor/skills`
- On other machines: `git pull`
