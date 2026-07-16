# Installed Cursor Plugins

Cursor stores its installed-plugin registry internally, so this manifest is the source of truth for reproducing the setup on a new machine. Install each via Settings -> Plugins (or ask the agent to walk through them), then reload the window.

## Marketplace plugins (cursor-public)

- cloudflare
- compound-engineering
- context7-plugin
- continual-learning
- cursor-team-kit
- figma
- functions
- parallel
- supabase
- superpowers

## Other marketplaces

- fullstory/fullstory (marketplace: github.com/fullstorydev/fullstory-skills)

## Local modifications (re-apply after plugin updates)

Five files in `compound-engineering` and `cursor-team-kit` carry small merged-in additions (~30 lines) that plugin updates will silently revert:

| File | Addition |
|---|---|
| `compound-engineering/skills/ce-debug/SKILL.md` | Core principle 5: never ship a workaround you don't understand |
| `compound-engineering/skills/ce-commit/SKILL.md` | Step 3: refactor/behavior-change separation + bisect/blame rationale |
| `compound-engineering/skills/ce-simplify-code/references/personas/code-quality-reviewer.md` | Checks 10-12: premature abstraction, defensive noise, scope creep |
| `compound-engineering/skills/ce-commit-push-pr/references/pr-description-writing.md` | Step C: reviewer-facing content block (verify steps, risks, non-goals) |
| `cursor-team-kit/skills/verify-this/SKILL.md` | Completion-Claim Gate section + "before claiming complete" trigger |

To check whether the edits are still present, grep the plugin cache for "Completion-Claim Gate" and "Premature abstraction and speculative generality".
