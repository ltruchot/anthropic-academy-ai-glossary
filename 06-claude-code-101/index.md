---
tags: [ia, anthropic, claude, glossaire]
created: 2026-11-12
updated: 2026-11-13
---
# Glossaire et mindmap Anthropic

Glossaire du cours Anthropic « Claude Code 101 » (Claude Certification, Developer Foundation). Il se suffit à lui-même : un terme que définit aussi un autre cours a ici sa propre entrée, telle que ce cours le définit. Définitions en anglais, résumées du cours ; traduction française entre parenthèses, vérifiée sur des sources françaises de l'IA et de l'informatique (documentation des éditeurs, terminologie officielle, recherche).

Schémas, avec un sommaire et une légende pour chacun : [mindmap.md](mindmap.md).

---

## Glossaire

### Claude Code *(Claude Code)*

An agentic coding tool that understands your codebase, edits your files, runs commands, and integrates with your existing developer tools to help you get things done faster. It's available in your terminal, Visual Studio Code, the Claude Desktop app, on the web, and in JetBrains IDEs. Unlike Claude.ai, it has direct access to your files, your terminal, and your entire codebase: instead of copying and pasting code back and forth, it goes in and does the work itself, because it works as an [AI agent](#ai-agent-agent-ia). In practice it can read and understand your codebase (explain a feature, trace a bug), edit files across your project (refactor a function and update every file that references it), run terminal commands (execute your build script, run your tests, install packages, and use the output to decide what to do next) and search the web (documentation, the latest API references). Three concepts to keep in mind to use it effectively: the [context window](#context-window-fenêtre-de-contexte), its [permission modes](#permission-modes-modes-de-permission), and the fact that it can make mistakes: it might misunderstand your intent, introduce a bug, or over-engineer a solution, and staying in the loop helps you catch these early. It combines several agentic concepts: an [agentic loop](#agentic-loop-boucle-agentique), a managed [context window](#context-window-fenêtre-de-contexte), [tools](#tool-outil), and configurable [permission modes](#permission-modes-modes-de-permission), all inside your terminal: it can read your codebase, take action, and verify its own work. That's what makes it fundamentally different from a chat window. Whatever directory you run `claude` in, it has access to that directory and all of its subfolders. To install it, on macOS, Linux, or WSL the curl command does it in one go; Homebrew and winget work too but don't auto-update by default. Where to use it: the terminal is the best bet to stay on the cutting edge, since features ship there first; the IDE integrations offer a nearly identical experience, more intertwined with your code editor; Desktop lets Claude run in the background, work in a specific folder, change permissions, or work in a cloud environment; the web is restricted to GitHub repositories and suits remote work.

### AI agent *(Agent IA)*

Software that can interact with its environment and perform actions to complete a defined goal. At its core, it works by having a large language model operating in a loop in real time. AI agents can have access to [tools](#tool-outil), external services, or even other AI agents to help reach their goals. The key differentiator of [Claude Code](#claude-code-claude-code): it works as an AI agent.

### Agentic loop *(Boucle agentique)*

How [Claude Code](#claude-code-claude-code) is best explained. You enter a prompt; Claude gathers the context it needs by interacting with the model, which returns text or a [tool](#tool-outil) call that Claude Code can execute; it takes action, for example editing a file or running a command; it verifies the results and determines whether they achieve what your prompt set out to do. If they do, Claude finishes and waits for the next prompt; if they don't, it loops back and tries again until the results are complete and verifiable. Throughout this loop, you can add context, interrupt, or steer the model to help guide it toward your goal.

### Context window *(Fenêtre de contexte)*

Claude's working memory. It can hold a lot, but not everything at once. This is where the "agentic" aspect of [Claude Code](#claude-code-claude-code) comes in: Claude finds strategic ways to locate answers within your codebase without loading the entire thing into context. It determines how much of your conversation, file contents, command outputs, and more Claude can store and reference. Once you reach that limit, Claude Code [compacts](#compaction-compaction) your conversation.

### Compaction *(Compaction)*

What [Claude Code](#claude-code-claude-code) does once you reach the limit of the [context window](#context-window-fenêtre-de-contexte): it compacts your conversation, automatically determining what it can remove or summarize to bring the context window back down to a usable size.

### Tool *(Outil)*

The backbone of how agents work. Most AI assistants simply take text in and return text out; tools let [Claude Code](#claude-code-claude-code) determine when to execute code to get closer to completing a task. This could be a file-reading tool, a web search tool, or any number of other capabilities. Claude Code uses semantic understanding to determine when to call a tool and how to use the output.

### Permission modes *(Modes de permission)*

What lets you choose how hands-on to be with [Claude Code](#claude-code-claude-code): it can ask you before running commands or making changes, or run in [auto mode](#auto-mode-mode-auto). You're always in control, whether you prefer a hands-on or hands-off approach. Claude Code has several: [manual](#manual-mode-mode-manuel), [auto-accept](#auto-accept-acceptation-automatique), [plan mode](#plan-mode-mode-plan) and [auto mode](#auto-mode-mode-auto). You can use Shift and Tab to toggle between modes (the page says cycle). There is no right or wrong choice: it is whatever you are comfortable with. All of this can be configured in your settings file. Be cautious when skipping permissions: giving Claude Code free rein to run commands means a mistake could be harder to catch before it happens.

### Manual mode *(Mode manuel)*

A [permission mode](#permission-modes-modes-de-permission) of [Claude Code](#claude-code-claude-code) in which Claude asks for explicit permission before editing a file or running a shell command. The video calls it the default behavior; which mode a new session starts in depends on your Claude Code version and settings.

### Auto-accept *(Acceptation automatique)*

A [permission mode](#permission-modes-modes-de-permission) of [Claude Code](#claude-code-claude-code) in which files are edited without asking, and common filesystem commands like mkdir, mv, and rm run without asking too. Other commands still require approval.

### Plan mode *(Mode Plan)*

A [permission mode](#permission-modes-modes-de-permission) of [Claude Code](#claude-code-claude-code) in which Claude reads files and runs shell commands to explore, without editing your source files, and compiles a plan of action before starting any work. It takes your prompt, then analyzes your codebase and researches your suggested implementation; it asks clarifying questions along the way, then returns a detailed plan it can execute. It is great for planning complex changes or doing a safe code review, and excels at multi-step implementations toward a feature. After reviewing the plan, if it looks good, you accept it and let Claude work through it; depending on your permission mode, it may check in with you along the way.

### Auto mode *(Mode auto)*

A [permission mode](#permission-modes-modes-de-permission) of [Claude Code](#claude-code-claude-code) in which a background safety check screens most actions instead of asking you before each one. Claude works without routine permission prompts while a classifier checks most actions in the background, targeted at blocking actions that are irreversible, destructive, or aimed outside your environment. When something is blocked, Claude usually finds a safer approach or asks you for the go-ahead.
