# Upstream: contributing to brenoperucchi/omabackup

Status ledger for the work Corey does on Breno Perucchi's OmaBackup, and for
the gates that decide whether hp-laptop ever migrates from Backstop to it.
This replaced the two hp-laptop Planka cards on 2026-09-27; update it here,
not on the board.

## Why this exists

Breno published a plugin named OmaBackup first (first commit 2026-08-24), so
the name is his. This plugin's display name became Backstop and the repo moved
to huey-holdings-llc/backstop (PR 30). Marketplace issue 7281 was withdrawn.
CLI, plugin id, units and paths are unchanged; hp-laptop runs 0.8.0 as is.

Breno made Corey a collaborator. The agreement is ongoing contribution: port
what Backstop has that his tool lacks, move his roadmap forward, improve his
docs. He reviews every PR, so work arrives in small pieces in his documented
phase order. Two PRs open at once, at most. Nothing quickshell-related runs
on the host; the test suite runs in the ob-trial container.

## Pull requests, as of 2026-10-22

| PR | What | State |
|---|---|---|
| 1 | Private-remote gate (his Phase 1, T89) | merged 2026-09-19, released 0.4.6 |
| 2 | collect no longer aborts with no foreign packages | merged 2026-09-20, released 0.4.7 |
| 3 | sync scans staging with the deny-list before publishing | merged 2026-10-22 after four rounds Breno pushed himself, released 0.4.8 |
| 4 | error veto covers every package list (asked for by Breno) | merged 2026-10-21, released 0.4.8 |
| 6 | the panel drives its own bundled CLI before PATH | open, awaiting review |
| 7 | the push refusal says where a secret is, never what (his open item from 2026-09-30) | open, awaiting review |

PR 5 is Breno's own (secret scan before the sync commit). He holds `main` at
each release commit until the marketplace verifies it, so open PRs wait for
that. Container baseline on his `main` at 8b6b15a (0.4.9): 1629 passed, 2
failed.

Queue after these, in order: `docs/help-lists-every-verb`, the credential
filename gate (his Phase 2), the trust record with non-GitHub blocking (rest
of Phase 1).

## Where the working material lives

* Clone: `~/projects/omabackup-breno`, with a local `CLAUDE.md` for his house style.
* Procedure: the `omabackup-contrib` skill in farmhouse-claude.
* Queue and per-PR detail: `~/.claude/plans/we-have-made-an-humble-whisper.md`.
* Original trial plan: `~/.claude/plans/i-have-seen-a-radiant-hare.md`.
* Trial report: farm-cluster vault, `121 comparison/comparison-omabackup-breno-trial`.

## Laptop migration gates

hp-laptop moves to his plugin only when all of these hold. Status 2026-10-22:

| Gate | Status |
|---|---|
| PRs 1 to 4 merged | met |
| Real-allowlist container run green, including `~/.local/bin` scripts | open |
| An answer for `/etc` (38 entries, unsupported upstream) | open |
| A custom groups file that survives his install | open |
| The `omabackup` command-name collision solved | open |
| A VM restore passed on warmachine | open |

Fallback if the trial disappoints: full rename of Backstop and maintenance mode.
