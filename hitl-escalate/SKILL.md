---
name: hitl-escalate
description: Escalate blocked runs to a human. Use when you hit a missing credential, a destructive action needing approval, or some other issue that you can't solve yourself.
when_to_use: the task hit a missing credential, a destructive action needing approval, or some other issue that you can't solve yourself
---

# Human-in-the-Loop Escalate

Agents fail in a specific way when they meet a question they can't answer: they guess. The guess ships, later work builds on it, and by the time a human looks the divergence is three commits deep. Or worse: they waste time going round in circles or down the wrong path. This skill is the release valve — when the agent is stuck, it stops and asks, cleanly, in a shape the human can act on.

## Trigger — escalate when any of these are true

- **Ambiguous spec.** The task description admits two implementations and the choice changes user-visible behavior.
- **Missing credential.** A required env var, API key, or config file is absent, and there is no sanctioned way for the agent to create one.
- **Destructive action needing approval.** Dropping a table, force-pushing, deleting user data, spending money, sending mail to real recipients.
- **3+ consecutive failed attempts at the same fix.** You are thrashing. Stop and get a human eye before the fourth attempt.
- **External dependency down.** A third-party service the feature needs is unreachable and no offline path exists.

If none of the above hold, do not escalate. Guessing is bad; escalating on a solvable problem is also bad (it trains humans to ignore the channel).

## How to escalate

Stop working and put the question to the user directly, with exactly these four parts:

```
Question: <one sentence, answerable with a short reply>

Context: <what feature, which file, which commit, why now — 3-6 lines>

Attempted: <bulleted list of what you tried and why each fell short>

Choices:
- A) <option> — <consequence>
- B) <option> — <consequence>
- C) <option> — <consequence>
```

Do not continue with other speculative work on the blocked task while waiting. If there is genuinely independent work in the same request, say so and proceed only on that.

## Anti-patterns — do not do these

- **Do not fabricate an answer.** "I'll assume the user meant X" is how divergence starts. Assume nothing under ambiguity — escalate.
- **Do not loop endlessly.** After the third consecutive failure of the same fix, escalate. The fourth attempt is not going to succeed by the same reasoning that failed thrice.
- **Do not silently swallow the missing credential.** Do not commit a placeholder, do not disable the feature, do not "TODO" the auth. Ask.
- **Do not escalate for questions the repo already answers.** Read the project docs (AGENTS.md, README, the task description) and the last three commits first. Escalation is expensive human attention — spend it on real ambiguity.
- **Do not bury the question in a wall of text.** The four-part shape exists so the human can answer in one line.

## Pairs with

- `adversarial-verify` — the source of the 3-failure trigger.
