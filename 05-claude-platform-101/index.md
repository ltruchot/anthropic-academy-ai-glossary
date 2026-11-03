---
tags: [ia, anthropic, claude, glossaire]
created: 2026-11-03
updated: 2026-11-03
---
# Glossaire et mindmap Anthropic

Glossaire du cours Anthropic « Claude Platform 101 » (Claude Certification, Developer Foundation). Il se suffit à lui-même : un terme que définit aussi un autre cours a ici sa propre entrée, telle que ce cours le définit. Définitions en anglais, résumées du cours ; traduction française entre parenthèses, vérifiée sur des sources françaises de l'IA et de l'informatique (documentation des éditeurs, terminologie officielle, recherche).

Schémas, avec un sommaire et une légende pour chacun : [mindmap.md](mindmap.md).

---

## Glossaire

### Claude Platform *(Claude Platform)*

Anthropic's infrastructure for building with Claude programmatically: a REST API, SDKs for different programming languages, CLIs (command line interfaces), and a console where you manage keys, monitor usage, deploy managed agents, and test prompts (the [Claude Console](#claude-console-claude-console)). It's where developers send structured requests, get structured responses, and control every detail: which model, how many tokens, what tools Claude can use, and what system instructions it follows. Your API-level access to Claude's models, tools, and infrastructure: it takes you from asking Claude questions to making Claude part of your product, and with [managed agents](#managed-agents-agents-gérés) it can run your agents for you. It exists to close the gap between chatting with Claude in a browser tab and building Claude into something you ship: a chat answers a question and the thread ends there, while an application sends Claude structured requests, hands it tools, lets it act on real systems, and runs that loop for one user or a million. A different skill from prompting. Think of it as three layers, [primitives](#primitives-primitives), [infrastructure](#infrastructure-infrastructure) and [controls](#controls-pilotage); the shorthand: build with primitives, scale on infrastructure, run with control.

→ [schéma des trois couches](mindmap/three-layers.png)

### Claude Console *(Claude Console)*

The console of the [Claude Platform](#claude-platform-claude-platform), where you manage keys, monitor usage, deploy [managed agents](#managed-agents-agents-gérés), and test prompts. The platform's structure is reflected in it: it's where the [infrastructure](#infrastructure-infrastructure) and [control](#controls-pilotage) layers live, with sections for building, managing agents, and analytics.

→ [schéma des trois couches](mindmap/three-layers.png)

### Primitives *(Primitives)*

The API building blocks tuned to Claude, the pieces you actually call: the [Messages API](#messages-api-api-messages), tool use, files, web search, code execution, MCP servers, skills. What you build with. One of the three layers of the [Claude Platform](#claude-platform-claude-platform).

→ [schéma des trois couches](mindmap/three-layers.png)

### Infrastructure *(Infrastructure)*

What you need to build and scale agentic systems past just a prototype: [managed agents](#managed-agents-agents-gérés), retries, queues, observability (the slide adds prompt caching and memory), the plumbing that keeps things running when one Claude call becomes a thousand. What you scale on. It lives, with [controls](#controls-pilotage), in the [Claude Console](#claude-console-claude-console). One of the three layers of the [Claude Platform](#claude-platform-claude-platform).

→ [schéma des trois couches](mindmap/three-layers.png)

### Controls *(Pilotage)*

For running agentic systems in production: dashboards, evals (the slide also lists workspaces, usage and spend limits, request logs), the dials your team uses once it's live. What you run with. It lives, with [infrastructure](#infrastructure-infrastructure), in the [Claude Console](#claude-console-claude-console). One of the three layers of the [Claude Platform](#claude-platform-claude-platform).

→ [schéma des trois couches](mindmap/three-layers.png)

### Messages API *(API Messages)*

One of the [primitives](#primitives-primitives), and a perfect use case for a help desk feature that drafts a reply from the contents of a ticket, following your team's tone and guidelines. The flow: define a client, retrieve the ticket, call `messages.create`, return the response to render. A single `messages.create` call gives you full control over the model, response length, [system prompt](#system-prompt-prompt-système), and user input: `model` (which model handles the request: Haiku, since drafting a reply is a simple task), `max_tokens` (caps how long Claude's response can be), `system` (the system prompt), `messages` (an array of objects: the user role tells Claude this is user input, and the ticket content goes there). Enough to wire Claude into an existing feature: you're adding Claude into a product that already exists, and the API is how you wire it in.

→ [schéma des trois couches](mindmap/three-layers.png)

### System prompt *(Prompt système)*

The `system` parameter of a `messages.create` call ([Messages API](#messages-api-api-messages)): where you define the role Claude plays. In the help desk example, the relevant tone and guidelines go there. Through the [Claude Platform](#claude-platform-claude-platform), you control what system instructions Claude follows.

→ [schéma des trois couches](mindmap/three-layers.png)

### Managed agents *(Agents gérés)*

When your product needs agents, the [Claude Platform](#claude-platform-claude-platform) doesn't just hand you the model: with managed agents, it runs them for you. They are part of the [infrastructure](#infrastructure-infrastructure) layer, and you deploy them from the [Claude Console](#claude-console-claude-console). A managed agent is sandboxed: Anthropic runs the loop and reports back, and you consume its event stream.

→ [schéma des trois couches](mindmap/three-layers.png)
