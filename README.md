# 🚩 Git The Flag — About

> *A game where the challenge is the repository itself.*

---

## The problem with learning git

Git is everywhere. Every developer uses it every day. And yet most developers only know five commands: `clone`, `add`, `commit`, `push`, `pull`. The moment something goes wrong — a lost commit, a leaked secret, a broken merge — they are lost.

The gap is not in documentation. Git has excellent documentation. The gap is **experience**. There is no safe, structured environment where developers can practice the commands that matter most, under realistic conditions, with something at stake.

The result: developers spend years using git as a save button, never discovering the forensic tools that would make them genuinely good at it.

---

## The idea

**Git The Flag** is a mystery-forensics CTF — a genre that did not previously exist for git learning.

The core mechanic: **the repo is the puzzle. Git commands are how you read it. Flags are what you find.**

Players clone a real repository to their own machine. They investigate using real git commands in their own terminal. They find hidden flags and submit them via GitHub Issues. An automated bot validates each submission instantly and explains the real-world significance of the command they just used.

No web app. No simulation. No sandboxed environment. The player interacts with an actual git repository exactly as they would on a real job.

---

## Why GitHub-native

Every piece of this game runs on GitHub's free tier:

- **Repos** store the crafted git histories that hide the flags
- **Issues** receive flag submissions from players
- **GitHub Actions** validate submissions and respond in seconds
- **Discussions** host the community and leaderboard
- **Pull Requests** are the final task for each case

There are no servers to maintain, no databases to manage, no costs to sustain. The game is as permanent as GitHub itself.

---

## The "why it matters" principle

Every correct flag submission triggers a bot comment. That comment does two things: confirms the flag is correct, and explains the real-world consequence of the command the player just used.

Example, after finding a flag in a deleted file:

> **What you learned:** Deleting a file in git only removes it from the working directory. The file still exists in every previous commit. This is how API keys get leaked — someone commits them by accident, panics, deletes the file, but the secret lives on in history forever. Always use `.gitignore` before committing sensitive files.

This turns a puzzle into a lesson. The player does not just learn the command — they learn *why the command exists* and *when they will need it at work*.

---

## How flags are hidden

Each case hides flags in a different location within the git repository. Players must discover both the hiding spot and the command to reveal it. The flags are not tricks — every hiding technique reflects a real git scenario.

| Technique | Command | Real-world scenario |
|-----------|---------|---------------------|
| Commit message | `git log --oneline` | Reading the history of a codebase you inherited |
| Deleted file | `git show <hash>` | Auditing what a developer "cleaned up" before a code review |
| Annotated tag | `git show <tagname>` | Finding undocumented release notes |
| Hidden ref | `git ls-remote` · `git fetch` | Finding non-standard refs a developer left on the remote |
| Stash | `git stash list` | Finding work-in-progress a developer left behind |
| Reflog | `git reflog` | Recovering a branch that was force-pushed away |

---

## The learning progression

The cases form a complete curriculum. A player who completes all cases will have used every meaningful git skill used in professional development.

| Case | Level | Theme | What you learn |
|------|-------|-------|----------------|
| Case 01 — Welcome to the Team | 🟢 Beginner | First day at a new job | `clone` · `branch` · `checkout` · `log` · `diff` |
| Case 02 — The Vanishing Feature | 🟡 Rookie | A feature disappeared | `log` forensics · `show` · `tag` · `ls-remote` |
| Case 03 — The Rewritten Past | 🔴 Mid | History was changed | `stash` · `reflog` · `rebase` · `cherry-pick` |
| Case 04 — The Inside Job | ⚫ Advanced | Someone made a mistake — find out who, when, and why | `bisect` · `blame` · merge conflicts · internals |

Each case adds one layer of depth. Case 01 is safe, welcoming, and guided. Case 04 requires thinking like a senior engineer conducting a forensic incident review.

---

## Who it is for

**Students and beginners** — Case 01 teaches git from zero. It explains what cloning is, what a branch is, what a commit is. Every command has context. Every step makes sense. If you have never used git, you are exactly who this was built for.

**Junior developers** — You know the basics but not the investigative side. Cases 02 and 03 give you the tools you have been missing. These are the commands that matter when something breaks at 2am.

**Seniors and teachers** — Use this as a structured exercise for onboarding, training, or university courses. The cases are self-contained, self-grading, and require no setup on your part. Students clone a repo and play. You watch the Discussions leaderboard fill up.

---

## The design rule

The game must never lie. Every file in a case repo looks like something a real developer would have written. Every commit message is plausible. Every branch name makes sense. The history tells a coherent story of a team that existed and worked on something real.

Players who investigate carefully will not just find flags — they will feel like they are reading someone's actual code. That authenticity is what makes the commands feel meaningful rather than arbitrary.

---

*Git The Flag is built and maintained by [mrpiay](https://github.com/mrpiay).*
*Start playing: [github.com/GitTheFlag/case-01](https://github.com/GitTheFlag/case-01)*
