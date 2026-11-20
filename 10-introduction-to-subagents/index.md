---
tags: [ia, anthropic, claude, glossaire]
created: 2026-11-20
updated: 2026-11-20
---

# Glossaire et mindmap Anthropic

Glossaire du cours Anthropic « Introduction to subagents » (Claude Certification, Developer Foundation). Il se suffit à lui-même : un terme que définit aussi un autre cours a ici sa propre entrée, telle que ce cours le définit. Définitions en anglais, résumées du cours ; traduction française entre parenthèses, vérifiée sur des sources françaises de l'IA et de l'informatique (documentation des éditeurs, terminologie officielle, recherche).

Schémas, avec un sommaire et une légende pour chacun : [mindmap.md](mindmap.md).

---

## Glossaire

### Subagent *(Sous-agent)*

A specialized assistant that Claude Code can delegate tasks to: think of it as a focused helper. Each one runs in its own conversation context window, does its work, and returns a summary to the main thread; the intermediate steps (all the file reads, searches, and tool calls) stay isolated and never clutter your main conversation. Subagents answer the filling of the [main context window](#main-context-window-fenêtre-de-contexte-principale) by spinning up a separate context window. A subagent's starting context includes a custom system prompt from your configuration file, which defines its role and behavior, and a task description written by the parent agent based on what you asked for. The subagent then works on its own: it reads files, runs searches, edits code, whatever it needs to do. When it's done, only a summary comes back to your main conversation; Claude Code saves the rest of the subagent's conversation in a separate transcript file. Your main context stays clean: you get the answer without all the noise of the journey it took to find it. The tradeoff: your main conversation doesn't see how the subagent reached its conclusions. Say you want to know which service handles refunds in an unfamiliar codebase: you ask the question, the Explore subagent spins up, does all the digging in its own context, and hands back a focused answer. Subagents give you three main benefits: they break work into focused pieces, letting each subagent concentrate on a specific task; they keep your main context window clean by isolating all the intermediate work; they bring back just the information you need as a concise summary. Claude Code ships with [built-in subagents](#built-in-subagents-sous-agents-intégrés), and you can create a [custom subagent](#custom-subagent-sous-agent-personnalisé) of your own. Either way, they're a practical way to get more out of longer Claude Code sessions.

### Main context window *(Fenêtre de contexte principale)*

The context window of your main conversation with Claude Code. Every time you chat with Claude Code, you're adding to it: every tool call, every file read, every search result gets stored there. That space is finite, and once it fills up, Claude starts losing track of earlier parts of the conversation. Exploring an unfamiliar codebase without a [subagent](#subagent-sous-agent), Claude might read 15 files, run several searches, and trace through multiple function calls, and all of that fills your context window, even though you only needed one fact; with a subagent, your main context window only records the question and the summary, not the files read along the way. The less noise in your main context, the longer and more effectively you can work.

### Built-in subagents *(Sous-agents intégrés)*

The [subagents](#subagent-sous-agent) Claude Code ships with, which you can use right away: the general purpose subagent, for multi-step tasks that require both exploration and action; Explore, for fast searching and navigation of codebases; Plan, used during plan mode for research and analysis of your codebase before presenting a plan. Beyond these built-in options, you can create a [custom subagent](#custom-subagent-sous-agent-personnalisé).

### Custom subagent *(Sous-agent personnalisé)*

A [subagent](#subagent-sous-agent) you create yourself, beyond the [built-in options](#built-in-subagents-sous-agents-intégrés), with a custom system prompt and tool access: a specialized agent tailored to your workflow, such as a code reviewer, a test writer, a documentation generator, or anything else you need. You build one with the /agents command.
