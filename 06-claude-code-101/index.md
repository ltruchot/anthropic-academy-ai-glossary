---
tags: [ia, anthropic, claude, glossaire]
created: 2026-11-12
updated: 2026-11-12
---
# Glossaire et mindmap Anthropic

Glossaire du cours Anthropic « Claude Code 101 » (Claude Certification, Developer Foundation). Il se suffit à lui-même : un terme que définit aussi un autre cours a ici sa propre entrée, telle que ce cours le définit. Définitions en anglais, résumées du cours ; traduction française entre parenthèses, vérifiée sur des sources françaises de l'IA et de l'informatique (documentation des éditeurs, terminologie officielle, recherche).

Schémas, avec un sommaire et une légende pour chacun : [mindmap.md](mindmap.md).

---

## Glossaire

### Claude Code *(Claude Code)*

An agentic coding tool that understands your codebase, edits your files, runs commands, and integrates with your existing developer tools to help you get things done faster. It's available in your terminal, Visual Studio Code, the Claude Desktop app, on the web, and in JetBrains IDEs. Unlike Claude.ai, it has direct access to your files, your terminal, and your entire codebase: instead of copying and pasting code back and forth, it goes in and does the work itself, because it works as an [AI agent](#ai-agent-agent-ia). In practice it can read and understand your codebase (explain a feature, trace a bug), edit files across your project (refactor a function and update every file that references it), run terminal commands (execute your build script, run your tests, install packages, and use the output to decide what to do next) and search the web (documentation, the latest API references). Three concepts to keep in mind to use it effectively: the [context window](#context-window-fenêtre-de-contexte), its [permission modes](#permission-modes-modes-de-permission), and the fact that it can make mistakes: it might misunderstand your intent, introduce a bug, or over-engineer a solution, and staying in the loop helps you catch these early.

### AI agent *(Agent IA)*

Software that can interact with its environment and perform actions to complete a defined goal. At its core, it works by having a large language model operating in a loop in real time. AI agents can have access to tools, external services, or even other AI agents to help reach their goals. The key differentiator of [Claude Code](#claude-code-claude-code): it works as an AI agent.

### Context window *(Fenêtre de contexte)*

Claude's working memory. It can hold a lot, but not everything at once. This is where the "agentic" aspect of [Claude Code](#claude-code-claude-code) comes in: Claude finds strategic ways to locate answers within your codebase without loading the entire thing into context.

### Permission modes *(Modes de permission)*

What lets you choose how hands-on to be with [Claude Code](#claude-code-claude-code): it can ask you before running commands or making changes, or run in [auto mode](#auto-mode-mode-auto). You're always in control, whether you prefer a hands-on or hands-off approach.

### Auto mode *(Mode auto)*

A [permission mode](#permission-modes-modes-de-permission) of [Claude Code](#claude-code-claude-code) in which a background safety check screens most actions instead of asking you before each one.
