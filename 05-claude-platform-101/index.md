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

The tools for running agentic systems in production, like dashboards and [evals](#evaluation-évaluation) (the diagram also lists workspaces, usage and spend limits, request logs), the dials your team uses once it's live. What you run with. It lives, with [infrastructure](#infrastructure-infrastructure), in the [Claude Console](#claude-console-claude-console). One of the three layers of the [Claude Platform](#claude-platform-claude-platform).

→ [schéma des trois couches](mindmap/three-layers.png)

### Messages API *(API Messages)*

One of the [primitives](#primitives-primitives), and a perfect use case for a help desk feature that drafts a reply from the contents of a ticket, following your team's tone and guidelines. The flow: define a client, retrieve the ticket, call `messages.create`, return the response to render. A single `messages.create` call gives you full control over the model, response length, [system prompt](#system-prompt-prompt-système), and user input: `model` (which model handles the request, one of the [model tiers](#model-tiers-gammes-de-modèles): Haiku, since drafting a reply is a simple task), `max_tokens` (caps how long Claude's response can be), `system` (the system prompt), `messages` (an array of objects: the user role tells Claude this is user input, and the ticket content goes there). Enough to wire Claude into an existing feature: you're adding Claude into a product that already exists, and the API is how you wire it in. Every API call goes through the `messages.create` function: you specify a model (which Claude model handles the request), a max tokens limit (a cap on how long the response can be), and a list of messages (objects with either user or assistant roles, structured similarly to how you'd have a conversation with Claude elsewhere). Its [response content](#response-content-contenu-de-la-réponse) is an array of blocks. In a real product, the same `messages.create` shape is the engine behind something like a summarize endpoint: pull a meeting transcript out of the database, hand it to Claude with a system prompt that says "extract insights and risks", save the result back on the row, and return it to the UI; the same call, just wrapped in a route handler. From here, everything builds on this pattern.

→ [schéma des trois couches](mindmap/three-layers.png) · [schéma du premier appel API](mindmap/first-api-call.png)

### System prompt *(Prompt système)*

The `system` parameter of a `messages.create` call ([Messages API](#messages-api-api-messages)): where you define the role Claude plays. In the help desk example, the relevant tone and guidelines go there. Through the [Claude Platform](#claude-platform-claude-platform), you control what system instructions Claude follows. Add a system prompt to shape Claude's behavior: it's where you shape the persona (a terse senior reviewer, not a chatty one, in the code review example).

→ [schéma des trois couches](mindmap/three-layers.png) · [schéma du premier appel API](mindmap/first-api-call.png)

### Managed agents *(Agents gérés)*

When your product needs agents, the [Claude Platform](#claude-platform-claude-platform) doesn't just hand you the model: with managed agents, it runs them for you. They are part of the [infrastructure](#infrastructure-infrastructure) layer, and you deploy them from the [Claude Console](#claude-console-claude-console). A managed agent is sandboxed: Anthropic runs the loop and reports back, and you consume its event stream. When you don't want to own the [agent loop](#agent-loop-boucle-dagent), managed agents run this exact loop for you on Anthropic's infrastructure.

→ [schéma des trois couches](mindmap/three-layers.png) · [schéma de la boucle d'agent](mindmap/agent-loop.png)

### API key *(Clé API)*

What you grab first, from platform.claude.com, before your first `messages.create` call ([Messages API](#messages-api-api-messages)); you'll need to purchase some credits beforehand. The [Claude Console](#claude-console-claude-console) shows a newly created key with a Copy key button and a warning: it won't be viewable again. Store it in a `.env.local` file so it stays out of your version control: hardcoding keys in source files is how they end up leaked on GitHub, so keep them in environment files instead. Next, install the SDK (`npm install @anthropic-ai/sdk`).

→ [schéma du premier appel API](mindmap/first-api-call.png)

### Response content *(Contenu de la réponse)*

What a `messages.create` call ([Messages API](#messages-api-api-messages)) returns in its `content`: an array of blocks, not a string. For a basic text reply there's usually just one block of type `text`, but Claude can return multiple blocks (text, tool calls, thinking), so you always loop and check each block's type.

→ [schéma du premier appel API](mindmap/first-api-call.png)

### Model tiers *(Gammes de modèles)*

Anthropic currently offers four model tiers, and you choose between them with the `model` parameter in your API call ([Messages API](#messages-api-api-messages)): [Fable](#fable-fable), [Opus](#opus-opus), [Haiku](#haiku-haiku) and [Sonnet](#sonnet-sonnet) (the video, recorded before Fable was generally available, names three). Each model has different trade-offs, and picking the right one affects both quality and cost: if you default to the smartest one, your API bill will surprise you; pick the cheapest one, and the output might not hold up. The right model is the cheapest one whose output you'd actually ship: find it with an [evaluation](#evaluation-évaluation), from Haiku upward. Opus for hard problems, Sonnet for daily work, and Haiku for volume. In a real app, you'd route different kinds of work to different models inside the same endpoint, instead of picking one model for everything: in an operations dashboard with a document processing route, every incoming file gets classified with Haiku, client updates get drafted with Sonnet, and only RFP responses reach for Opus. One queue, three models, picked per task.

→ [schéma du choix du modèle](mindmap/choosing-a-model.png)

### Fable *(Fable)*

The most capable model yet: a new tier that sits above [Opus](#opus-opus), built for your toughest challenges. It comes at a significantly higher cost than Opus, so reserve it for work where that extra capability is worth paying for. At the time of the course, it was not generally available: the video does not show it. One of the [model tiers](#model-tiers-gammes-de-modèles).

→ [schéma du choix du modèle](mindmap/choosing-a-model.png)

### Opus *(Opus)*

The most capable of the three core model families, but also the slowest and highest cost of the three (the slide: most intelligent, slowest, highest cost). Use it for deep reasoning, complex analysis, multi-step coding, and nuanced writing: hard problems. Only reach for it when the task needs it: for drafting a regulatory response, you'd probably end up on Opus; in the routing example, only RFP responses reach for it. Side by side, it takes the longest and reads the most polished, but for a two-sentence definition, that polish is wasted. One of the [model tiers](#model-tiers-gammes-de-modèles).

→ [schéma du choix du modèle](mindmap/choosing-a-model.png)

### Haiku *(Haiku)*

The fastest and lowest cost, optimized for speed and cost efficiency rather than maximum intelligence (the slide: less intelligent, fastest, lowest cost). Use it for high-volume, low-complexity work like classification, extraction, and routing: volume. Run your [evaluation](#evaluation-évaluation)'s examples through it first: if the quality holds, you're done, and you just saved a lot of money. Side by side, it comes back often in under a second with a very competent two-sentence answer: for a definition, Haiku is plenty. In the routing example, every incoming file gets classified with it. One of the [model tiers](#model-tiers-gammes-de-modèles).

→ [schéma du choix du modèle](mindmap/choosing-a-model.png)

### Sonnet *(Sonnet)*

The sweet spot: a balanced combination of intelligence, speed, and cost that works well for most production work (the slide: capable, fast; the video: the middle tier on cost). Daily work. Step up to it when [Haiku](#haiku-haiku)'s quality doesn't hold in your [evaluation](#evaluation-évaluation). Side by side, it tightens the writing up a little; in the routing example, client updates get drafted with it. One of the [model tiers](#model-tiers-gammes-de-modèles).

→ [schéma du choix du modèle](mindmap/choosing-a-model.png)

### Evaluation *(Évaluation)*

A simple evaluation, set up before you write production code: a set of example inputs that you run through each model and score against what good output means for your use case. You don't need anything fancy: 20 or 30 representative examples from your actual workload is enough to start. Then work your way up the [tiers](#model-tiers-gammes-de-modèles): run your examples through [Haiku](#haiku-haiku) first; if the quality holds, you're done; if it doesn't, step up to [Sonnet](#sonnet-sonnet); only reach for [Opus](#opus-opus) when the task needs it. You land on the cheapest model that still does the job. The eval is the same shape every single time. To compare the tiers side by side, send the same prompt through each model: the loop swaps the `model` field on each request (same prompt, same max tokens, only the model changes), and you watch the latency and the [input and output tokens](#input-and-output-tokens-tokens-dentrée-et-de-sortie). Evals are also one of the [controls](#controls-pilotage).

→ [schéma du choix du modèle](mindmap/choosing-a-model.png)

### Input and output tokens *(Tokens d'entrée et de sortie)*

What `response.usage` gives you straight back from the API, after a `messages.create` call ([Messages API](#messages-api-api-messages)): the input and output tokens, which is what your bill is calculated on. With the latency, they are how you compare the [model tiers](#model-tiers-gammes-de-modèles) on the same prompt ([evaluation](#evaluation-évaluation)).

→ [schéma du choix du modèle](mindmap/choosing-a-model.png)

### Agentic workflows *(Flux de travail agentiques)*

A single API call ([Messages API](#messages-api-api-messages)) only returns one response. If you want to automate a workflow, Claude needs to act, look at the result, decide what's next, and keep going: that pattern is what people mean when they talk about agentic workflows. An [agent](#agent-agent) runs it, in the [agent loop](#agent-loop-boucle-dagent).

→ [schéma de la boucle d'agent](mindmap/agent-loop.png)

### Agent *(Agent)*

An autonomous version of Claude, running both sides of the messaging loop without a human in the middle. An agent receives a task, picks a tool, and executes code in a loop until Claude decides the task is done (the video: "until Claude deems the task done"). Claude in a loop: observe, decide, act, repeat. You own the [loop](#agent-loop-boucle-dagent) and the tools; Claude owns the reasoning. When you don't want to own the loop, [managed agents](#managed-agents-agents-gérés) run this exact loop for you on Anthropic's infrastructure.

→ [schéma de la boucle d'agent](mindmap/agent-loop.png)

### Agent loop *(Boucle d'agent)*

The loop an [agent](#agent-agent) runs. The easiest way to implement it: send a message to Claude with tools available (the [tools array](#tools-array-tableau-tools)); Claude responds with either a final answer or a request to use a tool you defined; your code executes that tool; you send the result back to Claude; repeat until the [stop reason](#stop-reason-raison-darrêt) is `end_turn`. Think of it as a conversation where the turns alternate: the user kicks things off, the agent calls a tool, the tool returns a result, and the agent keeps going until it has an answer. Each iteration sends the messages to Claude ([Messages API](#messages-api-api-messages)) and switches on the response's stop reason. On `end_turn`, Claude is done: print the final text and break. On `tool_use`, find the tool use blocks in the [response content](#response-content-contenu-de-la-réponse), run each one, push the assistant's response and your tool results back into messages, and loop again so Claude can answer. In the course's demo (a fake `get_weather` tool, and "What should I wear in Austin today?": Claude has no way to know the weather on its own), two turns: two API calls, one tool execution, one final answer. That's the entire loop: everything you build with the Claude API is going to be similar to this. The same loop shape scales from a mock weather demo to a production compliance agent (an auto-review endpoint that reads a structural report, looks up the relevant building codes via a tool, and writes risk findings back to the database one by one as it works): only the tools and plumbing change (real tools instead of a mock weather lookup, results streamed back to the UI as server-sent events, findings persisted to a risk-finding table). You own the loop and the tools, Claude owns the reasoning; when you don't want to own the loop, [managed agents](#managed-agents-agents-gérés) run this exact loop for you on Anthropic's infrastructure.

→ [schéma de la boucle d'agent](mindmap/agent-loop.png)

### Stop reason *(Raison d'arrêt)*

The response's stop reason, on which each iteration of the [agent loop](#agent-loop-boucle-dagent) switches. `tool_use`: Claude requests a tool you defined; find the tool use blocks, run each one, push the assistant's response and your tool results back into messages, and loop again. `end_turn`: Claude is done; print the final text and break. The loop repeats until the stop reason is `end_turn`.

→ [schéma de la boucle d'agent](mindmap/agent-loop.png)

### Tools array *(Tableau tools)*

Tells Claude what's available: for each tool, a name, a description, and a JSON schema for the inputs. Sent with the messages on each call of the [agent loop](#agent-loop-boucle-dagent). Claude only requests a tool: your code executes it (in the course's demo, `run_tool` is just a hardcoded lookup; in a real app, this would hit your database, an API, whatever).

→ [schéma de la boucle d'agent](mindmap/agent-loop.png)
