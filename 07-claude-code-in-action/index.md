---
tags: [ia, anthropic, claude, glossaire]
created: 2026-11-15
updated: 2026-11-15
---
# Glossaire et mindmap Anthropic

Glossaire du cours Anthropic « Claude Code in Action » (Claude Certification, Developer Foundation). Il se suffit à lui-même : un terme que définit aussi un autre cours a ici sa propre entrée, telle que ce cours le définit. Définitions en anglais, résumées du cours ; traduction française entre parenthèses, vérifiée sur des sources françaises de l'IA et de l'informatique (documentation des éditeurs, terminologie officielle, recherche).

Schémas, avec un sommaire et une légende pour chacun : [mindmap.md](mindmap.md).

---

## Glossaire

### Plan mode *(Mode Plan)*

The way to scope the work before Claude starts, the first of the two habits of a long session (the second: steer it while it runs). Before Claude writes a single line, it lays out a plan: in plan mode, Claude does its research without editing your source files. It reads the code, figures out what needs to change, and hands you a plan to review. Actually read it, don't skim it: the more thorough the plan, the fewer surprises once Claude starts executing. If something's off or missing, ask Claude to add it where you want: iterating on a plan is much faster than letting Claude run and hoping for the best, then cleaning up the mess.

### Compaction *(Compaction)*

The first way to steer Claude while it works. Compact summarizes your conversation, uses that summary as the new context, and deletes the old messages: this frees up your context window so Claude can keep going. The risk is that something important gets dropped in the summary, and Claude drifts off course. So don't just run `/compact` on its own: add instructions after the command to tell Claude how to summarize (`/compact Focus on the --version flag implementation`). Anything you write after the command shapes what the summary keeps: direct your compaction so the summary keeps what matters.

### Checkpoint *(Checkpoint)*

What every user prompt creates: a point of the session you can revert to with the [rewind menu](#rewind-menu-menu-de-rembobinage).

### Rewind menu *(Menu de rembobinage)*

The way to course correct when Claude heads down the wrong path, instead of prompting your way back out: rewind takes you to your last [checkpoint](#checkpoint-checkpoint). To open the menu, double tap escape on an empty prompt. Its options: Restore code and conversation (roll back both together), Restore conversation (just the chat), Restore code (just the files), Summarize from here (summarizes everything after the checkpoint: great after a side conversation, to free up some space), Summarize up to here (summarizes everything before the checkpoint: great to compress a long setup phase and keep the implementation parts intact).

### /goal command *(Commande /goal)*

A way to let Claude run more autonomously than hands-on steering. Goal sets a completion condition: you describe what "done" looks like, and Claude keeps working across turns until a fast evaluator confirms those conditions are met, instead of stopping the first time it thinks it's finished. For example: `/goal all tests in src/billing pass, and the type checker reports zero errors`. To cancel it, run `/goal clear`. The evaluator only reads the transcript, so the condition has to be checkable from the output Claude actually produces, like the results of a test run. Set a goal when you can describe "done" better than you can describe the steps. The other autonomous way: the [/loop command](#loop-command-commande-loop).

### /loop command *(Commande /loop)*

The other way, with the [/goal command](#goal-command-commande-goal), to let Claude run more autonomously. Loop runs a prompt on an interval between turns, either fixed or self-paced: use it to poll something external, like a CI run or a deploy, and act when the state changes. To stop a self-paced loop while it waits for its next run, press escape; a loop on a fixed interval keeps running until you ask Claude to cancel it or seven days pass.

### Worktree *(Worktree)*

The way to run parallel work: when you're running multiple agents on the same codebase, two Claude sessions fighting over the same files leads to conflicts (two steering wheels in one car). With worktrees, each session gets its own independent file tree, so they can't clobber each other's changes. When a session exits, a clean worktree is automatically removed. A `.worktreeinclude` file at the repo root lists git-ignored files to copy into each worktree: useful for an environment variable file or a local config that you need in every worktree but don't want to commit to version control.
