---
tags: [ia, anthropic, claude, glossaire]
created: 2026-11-15
updated: 2026-11-18
---
# Glossaire et mindmap Anthropic

Glossaire du cours Anthropic « Claude Code in Action » (Claude Certification, Developer Foundation). Il se suffit à lui-même : un terme que définit aussi un autre cours a ici sa propre entrée, telle que ce cours le définit. Définitions en anglais, résumées du cours ; traduction française entre parenthèses, vérifiée sur des sources françaises de l'IA et de l'informatique (documentation des éditeurs, terminologie officielle, recherche).

Schémas, avec un sommaire et une légende pour chacun : [mindmap.md](mindmap.md).

---

## Glossaire

### Plan mode *(Mode Plan)*

The way to scope the work before Claude starts, the first of the two habits of a long session (the second: steer it while it runs). Before Claude writes a single line, it lays out a plan: in plan mode, Claude does its research without editing your source files. It reads the code, figures out what needs to change, and hands you a plan to review. Actually read it, don't skim it: the more thorough the plan, the fewer surprises once Claude starts executing. If something's off or missing, ask Claude to add it where you want: iterating on a plan is much faster than letting Claude run and hoping for the best, then cleaning up the mess. One of the [permission modes](#permission-modes-modes-de-permission): reads run freely, and when [auto mode](#auto-mode-mode-auto) is available, auto's [classifier](#classifier-classifieur) reviews the commands Claude runs to explore and lets the approved ones run without a prompt.

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

### CLAUDE.md *(CLAUDE.md)*

Not enforced configuration: guidance. Every line competes with every other line for Claude's attention, so the longer the file gets, the more it competes with itself, and the less reliably Claude follows any single rule. The goal is to keep the file tight: the leaner the file, the more of it Claude actually follows. Before writing a rule, ask whether it belongs in CLAUDE.md at all: a hard rule like "never push to main" belongs in a [pre-tool-use hook](#pre-tool-use-hook-hook-pretooluse); CLAUDE.md handles the softer conventions. It can live in four places, the [CLAUDE.md locations](#claudemd-locations-emplacements-de-claudemd), and a long one can be split with [imports](#import-import). Whether Claude obeys a rule comes down to how you phrase it: specific and checkable ("Put new API routes in src/api/handlers, one per file", not "Follow best practices for API routes"); naming the replacement ("Use named exports, not default exports", not just "Don't use default exports"); emphasis ("IMPORTANT", "YOU MUST") as a budget, spent on the two or three rules that really hurt when they get broken, since it raises a rule's priority only relative to everything quieter around it. The file is never finished: when Claude does the wrong thing, treat it as a bug report against your CLAUDE.md (tell Claude "add that to the CLAUDE.md file", and it'll write the rule). Treat it like production code: if you can't justify a line, delete it.

### Pre-tool-use hook *(Hook PreToolUse)*

Where a hard rule belongs instead of [CLAUDE.md](#claudemd-claudemd), for a line that must never be crossed ("never push to main"): in CLAUDE.md, Claude respects it most of the time, and "most of the time" isn't good enough for something that dangerous. A hook is code that runs before Claude takes an action, and it can actually block the action: even if Claude does try to push to main, the hook stops it. Real enforcement, not a polite request. The [hook](#hook-hook) on PreToolUse, the [hook event](#hook-event-événement-de-hook) that fires before a tool call: the enforcement primitive, where the real power is, because it can block a tool call before it runs. It talks back to Claude by printing JSON and exiting zero. The key field is permissionDecision, and it takes one of three values: allow (let the call through), deny (stop the call), ask (hand it back to the user to decide). There's technically a fourth value, defer, but it only applies to non-interactive -p runs where a calling process pauses the tool and resumes it later. Instead of blocking a call, it can return [updatedInput](#updatedinput-updatedinput) to rewrite it. As a guardrail on the Bash tool, the matcher picks the tool to watch, and an optional if clause can narrow it to a specific command.

### CLAUDE.md locations *(Emplacements de CLAUDE.md)*

The four places a [CLAUDE.md](#claudemd-claudemd) can live. Claude loads all of them together at launch: nothing gets dropped, and they stack. [Managed policy](#managed-policy-politique-gérée): the org-level file your platform team controls. User: your personal preferences that follow you across every project on your machine. Project: the file shared with your team, checked into the repo. Local: ignored by git, your personal notes for this one repository only (say you're refactoring off in your own branch and want Claude to hold some architectural decisions in mind: that goes in local, not in the shared project file where it'd affect your whole team).

### Managed policy *(Politique gérée)*

The org-level [CLAUDE.md](#claudemd-claudemd) file your platform team controls. You can't exclude it, so org policy is always in play. One of the [CLAUDE.md locations](#claudemd-locations-emplacements-de-claudemd).

### Import *(Import)*

The path-to-file import syntax splits a long [CLAUDE.md](#claudemd-claudemd) into pieces: instead of one wall of text, you point to other files (`@.claude/conventions/testing.md`). When Claude launches, it expands those imported files inline, right where you referenced them. So imports help you keep things tidy, but everything still loads up front: they do not reduce the amount of context Claude has to read. Use imports to organize, not to shrink the load.

### Skill *(Skill)*

A folder with a SKILL.md inside it: a name, a description that triggers it, and the procedure itself. Only the descriptions load into context until a skill is needed, so there's little cost to packaging every procedure you repeat; the rule of thumb: if you've typed the same multi-step instruction twice, that's a skill. The folder can carry more than instructions: a reference.md next to SKILL.md for detailed material, linked from SKILL.md, which Claude reads only when it needs that depth; and scripts, which Claude executes rather than loading their contents into context, so a skill can carry its own tooling (a check.sh that runs all the gates). Keep SKILL.md itself lean and push the heavy material into side files. Checked into your project's .claude/skills, the whole team inherits it. Of the three places to put instructions, procedures and reference material tied to a particular kind of task belong in a skill; conventions that apply all the time belong in [CLAUDE.md](#claudemd-claudemd); a rule Claude must not be able to skip belongs in a [hook](#hook-hook), because CLAUDE.md and skills are both instructions that Claude follows, while a hook is code that actually runs. The skill worth building first: a [verification skill](#verification-skill-skill-de-vérification).

### Verification skill *(Skill de vérification)*

The [skill](#skill-skill) worth building first. Without it, checking Claude's work depends on you remembering to ask for it: skip that step once and bad code slips through. When Claude finishes a change that matches the skill's description, the skill fires on its own and walks the same steps every time: it runs the test suite, reads the diff, checks that no test was weakened just to make things pass, and reports pass or fail, with the evidence attached. Seeing green isn't enough: a test can be quietly loosened so it passes no matter what. "Done" isn't "the code looks right" from reading the diff alone: done is the gates being run and observed, with the results stated explicitly. The same shape carries any procedure your team repeats: a release checklist, a migration recipe, a pre-PR check.

### Permission modes *(Modes de permission)*

They let you decide once what Claude is allowed to run without stopping to ask you: instead of approving every action one prompt at a time, you pick a mode that matches the job and let Claude work at the level of trust you're comfortable with. Each mode draws a different line between what runs freely and what needs your sign-off. The six: Manual reads only, without prompting, and everything else asks first. Accept edits runs reads, file edits, and common file system bash commands without asking: for iterating on code that you review after the fact. [Plan](#plan-mode-mode-plan) researches and proposes changes without editing anything. [Auto](#auto-mode-mode-auto) accepts everything, with a separate [classifier](#classifier-classifieur) model reviewing most actions before they run. [Don't ask](#dont-ask-dont-ask) allows file reads inside your working directories and pre-approved tools; anything that would prompt is auto-denied. [Bypass permissions](#bypass-permissions-bypass-permissions) skips all checks. Press shift-tab to cycle through the everyday ones: manual, accept edits, plan, and auto; the status bar at the bottom always shows which mode you're currently in. Match the mode to the job.

### Auto mode *(Mode auto)*

The hands-off [permission mode](#permission-modes-modes-de-permission), the one to reach for when you leave the everyday, hands-on work. Claude runs on its own, but before most actions execute, a separate [classifier](#classifier-classifieur) model reviews them. The classifier checks intent, not correctness, so pair auto mode with a [stop hook](#stop-hook-hook-stop) that runs your tests: auto mode watches what Claude is trying to do while it runs, the stop hook confirms the code actually runs once Claude finishes. One guards intent before most actions, the other guards correctness after. Auto mode's guardrails are still evolving: check the docs for the current block and allow lists.

### Classifier *(Classifieur)*

The separate model that reviews most actions before they run in [auto mode](#auto-mode-mode-auto). It guards intent: it's watching for moves that escalate beyond what you actually asked for. The kind of thing it's designed to block: production deploys and migrations; force pushing, or piping downloaded code straight into a shell; sending sensitive data to external endpoints; irreversibly destroying files that existed before the session. It waves through the everyday work: local edits in your project, installing dependencies from your lock file, read-only requests, and pushing to your own branch. It won't catch whether the code actually works: if Claude writes broken authentication, the classifier waves it through, because broken isn't dangerous. When auto mode is available, it also reviews the commands Claude runs to explore in [plan mode](#plan-mode-mode-plan).

### Stop hook *(Hook Stop)*

A hook that runs your tests once Claude finishes: it confirms the code actually runs. Paired with [auto mode](#auto-mode-mode-auto), whose [classifier](#classifier-classifieur) checks intent, not correctness: one guards intent before most actions, the other guards correctness after. Like the [pre-tool-use hook](#pre-tool-use-hook-hook-pretooluse), code that actually runs. The [hook](#hook-hook) on Stop, the [hook event](#hook-event-événement-de-hook) that fires when Claude wants to end its turn: you can refuse and say "no, you're not done yet" if some condition isn't met; [exit code](#exit-code-code-de-sortie) 2 can block Stop, which is how you tell Claude it's not done. Gate the turn with Stop. There's a matching SubagentStop for when a sub-agent finishes.

### Don't ask *(Don't ask)*

The [permission mode](#permission-modes-modes-de-permission) for unattended runs, the right move whenever no human is around to approve prompts: CI pipelines, scheduled jobs, overnight batches. Claude still runs what needs no approval in Manual mode, such as file reads inside your working directories, plus the tools you pre-approved. Anything that would otherwise prompt gets auto-denied: your pipeline keeps moving instead of hanging on an approval no one is there to give.

### Bypass permissions *(Bypass permissions)*

The [permission mode](#permission-modes-modes-de-permission) that skips all checks: the equivalent of the dangerously-skip-permissions flag. Only run it inside an isolated container or virtual machine.

### Hook *(Hook)*

Deterministic code that runs at a fixed point in the loop, so it can guarantee behavior instead of hoping for it. Telling Claude to do something in a [CLAUDE.md](#claudemd-claudemd) file is a request, not a guarantee: write "always format after editing" and Claude will usually listen, but on a long run you're not watching, "usually" isn't good enough. A hook turns a rule from "Claude usually listens" into "Claude can't skip it": it hangs code on a [hook event](#hook-event-événement-de-hook). It talks back to Claude by printing JSON (the [pre-tool-use hook](#pre-tool-use-hook-hook-pretooluse)'s decision), or, when it doesn't speak JSON, with its [exit code](#exit-code-code-de-sortie). Reach past auto-formatting: guard tools with PreToolUse, gate the turn with Stop (the [stop hook](#stop-hook-hook-stop)), and preserve state across a compact (the [SessionStart hook](#sessionstart-hook-hook-sessionstart)). The setup takes a little effort up front, but it pays back the first time it catches something on a run you weren't even watching.

### Hook event *(Événement de hook)*

A moment of the session a [hook](#hook-hook) can hang code on. Claude Code fires around 30 hook events over the course of a session; a small handful you'll reach for again and again, and they line up with points in the agentic loop where you'd want to step in: a session starts, prompts come in, tools get called, and the turn eventually ends. PreToolUse fires before a tool call: the enforcement primitive, the one that can stop something before it happens (the [pre-tool-use hook](#pre-tool-use-hook-hook-pretooluse)). PostToolUse fires after a successful tool call: usually where auto-formatting or an auto-lint goes; it fires after the tool already ran, so blocking there is too late to stop the call, though it can still feed text back to Claude. Stop fires when Claude wants to end its turn (the [stop hook](#stop-hook-hook-stop)); SubagentStop, when a sub-agent finishes. PreCompact and PostCompact fire before and after [compaction](#compaction-compaction): to re-inject context after compaction, don't use PostCompact, use SessionStart with the compact matcher. InstructionsLoaded fires when a CLAUDE.md or rule file loads: handy for auditing what actually made it into context. SessionStart fires at the start and primes the environment (the [SessionStart hook](#sessionstart-hook-hook-sessionstart)). The video's slide places them in the loop: Session Start, UserPromptSubmit, then the agentic loop (PreToolUse, PermissionRequest, the tool executing, PostToolUse / PostToolUseFailure, PostToolBatch, SubagentStart / SubagentStop, TaskCreated, TaskCompleted, back to PreToolUse), Stop / StopFailure at the end of each turn, then TeammateIdle, PreCompact, PostCompact, SessionEnd; beside them, Setup, UserPromptExpansion, PermissionDenied, Elicitation, ElicitationResult, Notification, ConfigChange, WorktreeCreate, WorktreeRemove, CwdChanged, FileChanged, InstructionsLoaded and MessageDisplay.

### updatedInput *(updatedInput)*

What a [pre-tool-use hook](#pre-tool-use-hook-hook-pretooluse) returns to rewrite a tool call instead of blocking it: the lesser-known and more interesting move than returning deny. That's how you strip a secret out of a command and still let it run, instead of just refusing: Claude is asked to run a command that includes a live-looking secret; the hook intercepts it, spots the sk_live_ pattern, and swaps it for a placeholder before the command ever executes. The command still ran, the work still got done, but the secret never made it through: the difference between blocking and redacting. One catch: updatedInput replaces the whole input object, so you have to echo back the fields you aren't changing, or you'll lose them.

### Exit code *(Code de sortie)*

How a [hook](#hook-hook) that doesn't return JSON talks back: for simpler hooks, exit codes do the job, and three numbers matter. 0 is success: if standard out is JSON, Claude parses it; plain text is ignored on most events, but on SessionStart, UserPromptSubmit and UserPromptExpansion it gets added to context, which is what makes a state-preserver hook work (the [SessionStart hook](#sessionstart-hook-hook-sessionstart)). 2 is a blocking error: standard error gets fed back to Claude as context; the blocking exit code almost everywhere (the video names the lone exception, WorktreeCreate, which aborts on any non-zero code). Anything else is non-blocking: standard error gets logged, and Claude carries on. Exit code 1 catches people out: it feels like an error, but it does not block, and Claude runs the command anyway; if you meant to stop something, exit 2, not 1. Exit 2 can even block Stop, which is how you tell Claude it's not done (the [stop hook](#stop-hook-hook-stop)). On PostToolUse, blocking is too late to stop the call, since the tool already ran, though it can still feed text back to Claude. A few events ignore blocking entirely, like Notification and SessionStart: SessionStart shows your standard error to you only, Notification ignores it, and both carry on regardless.

### SessionStart hook *(Hook SessionStart)*

The [hook](#hook-hook) on SessionStart, the [hook event](#hook-event-événement-de-hook) that fires at the start and primes the environment; use the startup source if you only want it on fresh starts. With the compact matcher, it runs right after [compaction](#compaction-compaction), and it is the one to re-inject context after compaction, not PostCompact: it actually gets its output back into the conversation. When Claude compacts a long conversation, it drops a lot of detail: have the hook print a short summary of the files you've been working on. That summary goes back into context (plain text from a hook that exits 0 is added to context on SessionStart: see [exit code](#exit-code-code-de-sortie)), so Claude picks up where it left off instead of starting cold. It ignores blocking: it shows your standard error to you only, and carries on.
