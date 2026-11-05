---
tags: [ia, anthropic, claude, glossaire]
created: 2026-11-03
updated: 2026-11-05
---
# Glossaire et mindmap Anthropic

Glossaire du cours Anthropic « Claude Platform 101 » (Claude Certification, Developer Foundation). Il se suffit à lui-même : un terme que définit aussi un autre cours a ici sa propre entrée, telle que ce cours le définit. Définitions en anglais, résumées du cours ; traduction française entre parenthèses, vérifiée sur des sources françaises de l'IA et de l'informatique (documentation des éditeurs, terminologie officielle, recherche).

Schémas, avec un sommaire et une légende pour chacun : [mindmap.md](mindmap.md).

---

## Glossaire

### Claude Platform *(Claude Platform)*

Anthropic's infrastructure for building with Claude programmatically. Instead of chatting with Claude in a browser, you send structured requests from your code and get structured responses back, with control over every detail: which model to use, how many tokens to spend, what tools Claude can use, and what system instructions it follows. It is made up of a few pieces: a REST API you can call from any language, SDKs for different programming languages, command line interfaces (CLIs), and a console where you manage [API keys](#api-key-clé-api), monitor usage, deploy managed agents, and test prompts (the [Claude Console](#claude-console-claude-console)). Your API-level access to Claude's models, tools, and infrastructure: it takes you from asking Claude questions to making Claude part of your product, and with [managed agents](#managed-agents-agents-gérés) it can run your agents for you. It exists to close the gap between chatting with Claude in a browser tab and building Claude into something you ship: a chat answers a question and the thread ends there, while an application sends Claude structured requests, hands it tools, lets it act on real systems, and runs that loop for one user or a million. A different skill from prompting. Picture it as three layers stacked on top of each other, [primitives](#primitives-primitives), [infrastructure](#infrastructure-infrastructure) and [controls](#controls-pilotage); the shorthand: build with primitives, scale on infrastructure, run with control.

→ [schéma des trois couches](mindmap/three-layers.png)

### Claude Console *(Claude Console)*

The console of the [Claude Platform](#claude-platform-claude-platform), where you manage [keys](#api-key-clé-api), monitor usage, deploy [managed agents](#managed-agents-agents-gérés), and test prompts. The platform's structure is reflected in it: it's where the [infrastructure](#infrastructure-infrastructure) and [control](#controls-pilotage) layers live, with sections for building, managing agents, and analytics.

→ [schéma des trois couches](mindmap/three-layers.png)

### Primitives *(Primitives)*

The API building blocks tuned to Claude, the pieces you actually call from your code: the [Messages API](#messages-api-api-messages), tool use, files, web search, code execution, MCP servers, skills. What you build with. One of the three layers of the [Claude Platform](#claude-platform-claude-platform).

→ [schéma des trois couches](mindmap/three-layers.png)

### Infrastructure *(Infrastructure)*

What you need to build and scale agentic systems past a prototype: [managed agents](#managed-agents-agents-gérés), retries, queues, observability (the diagram adds prompt caching and memory), the plumbing that keeps things running when one Claude call becomes a thousand. What you scale on. It lives, with [controls](#controls-pilotage), in the [Claude Console](#claude-console-claude-console). One of the three layers of the [Claude Platform](#claude-platform-claude-platform).

→ [schéma des trois couches](mindmap/three-layers.png)

### Controls *(Pilotage)*

The tools for running agentic systems in production, like dashboards and evals (the diagram also lists workspaces, usage and spend limits, request logs), the dials your team uses once it's live. What you run with. It lives, with [infrastructure](#infrastructure-infrastructure), in the [Claude Console](#claude-console-claude-console). One of the three layers of the [Claude Platform](#claude-platform-claude-platform).

→ [schéma des trois couches](mindmap/three-layers.png)

### Messages API *(API Messages)*

One of the [primitives](#primitives-primitives), and a perfect use case for a help desk feature that drafts a reply from the contents of a ticket, following your team's tone and guidelines. The flow: define a client, retrieve the ticket, call `messages.create`, return the response to render. A single `messages.create` call gives you full control over the model, response length, [system prompt](#system-prompt-prompt-système), and user input: `model` (which model handles the request: Haiku, since drafting a reply is a simple task), `max_tokens` (caps how long Claude's response can be), `system` (the system prompt), `messages` (an array of objects: the user role tells Claude this is user input, and the ticket content goes there). Enough to wire Claude into an existing feature: you're adding Claude into a product that already exists, and the API is how you wire it in. Every API call goes through the `messages.create` function: you specify a model (which Claude model handles the request), a max tokens limit (a cap on how long the response can be), and a list of messages (objects with either user or assistant roles, structured similarly to how you'd have a conversation with Claude elsewhere). Its [response content](#response-content-contenu-de-la-réponse) is an array of blocks. In a real product, the same `messages.create` shape is the engine behind something like a summarize endpoint: pull a meeting transcript out of the database, hand it to Claude with a system prompt that says "extract insights and risks", save the result back on the row, and return it to the UI; the same call, just wrapped in a route handler. From here, everything builds on this pattern.

→ [schéma des trois couches](mindmap/three-layers.png) · [schéma du premier appel API](mindmap/first-api-call.png)

### System prompt *(Prompt système)*

The `system` parameter of a `messages.create` call ([Messages API](#messages-api-api-messages)): where you define the role Claude plays. In the help desk example, the relevant tone and guidelines go there. Through the [Claude Platform](#claude-platform-claude-platform), you control what system instructions Claude follows. Add a system prompt to shape Claude's behavior: it's where you shape the persona (a terse senior reviewer, not a chatty one, in the code review example).

→ [schéma des trois couches](mindmap/three-layers.png) · [schéma du premier appel API](mindmap/first-api-call.png)

### Managed agents *(Agents gérés)*

When your product needs agents, the [Claude Platform](#claude-platform-claude-platform) doesn't just hand you the model: with managed agents, it runs them for you. They are part of the [infrastructure](#infrastructure-infrastructure) layer, and you deploy them from the [Claude Console](#claude-console-claude-console). A managed agent is sandboxed: Anthropic runs the loop and reports back, and you consume its event stream.

→ [schéma des trois couches](mindmap/three-layers.png)

### API key *(Clé API)*

What you grab first, from platform.claude.com, before your first `messages.create` call ([Messages API](#messages-api-api-messages)); you'll need to purchase some credits beforehand. The [Claude Console](#claude-console-claude-console) shows a newly created key with a Copy key button and a warning: it won't be viewable again. Store it in a `.env.local` file so it stays out of your version control: hardcoding keys in source files is how they end up leaked on GitHub, so keep them in environment files instead. Next, install the SDK (`npm install @anthropic-ai/sdk`).

→ [schéma du premier appel API](mindmap/first-api-call.png)

### Response content *(Contenu de la réponse)*

What a `messages.create` call ([Messages API](#messages-api-api-messages)) returns in its `content`: an array of blocks, not a string. For a basic text reply there's usually just one block of type `text`, but Claude can return multiple blocks (text, tool calls, thinking), so you always loop and check each block's type.

→ [schéma du premier appel API](mindmap/first-api-call.png)
