---
tags: [ia, anthropic, claude, glossaire]
created: 2026-11-01
updated: 2026-11-01
---
# Glossaire et mindmap Anthropic

Glossaire du cours Anthropic « Claude Platform and Model Foundations » (Claude Certification, Developer Foundation). Il se suffit à lui-même : un terme que définit aussi un autre cours a ici sa propre entrée, telle que ce cours le définit. Définitions en anglais, résumées du cours ; traduction française entre parenthèses, vérifiée sur des sources françaises de l'IA et de l'informatique (documentation des éditeurs, terminologie officielle, recherche).

Schémas, avec un sommaire et une légende pour chacun : [mindmap.md](mindmap.md).

---

## Glossaire

### Behavioral properties *(Propriétés comportementales)*

Five properties that apply to Claude regardless of which feature you use: [responses vary](#responses-vary-les-réponses-varient), [confident tone is not a signal of accuracy](#confident-tone-is-not-a-signal-of-accuracy-un-ton-assuré-nest-pas-un-signe-dexactitude), [context is a budget](#context-is-a-budget-le-contexte-est-un-budget), [knowledge has a training boundary](#knowledge-has-a-training-boundary-les-connaissances-ont-une-date-limite), [configured procedures still produce varied outputs](#configured-procedures-still-produce-varied-outputs-les-procédures-configurées-produisent-quand-même-des-réponses-variées). Understand them before selecting [entry points](#entry-points-points-dentrée) and [models](#model-tiers-gammes-de-modèles), and before building workflows with Claude: it prevents the most common sources of frustration and misaligned expectations.

→ [schéma des propriétés comportementales](mindmap/behavioral-properties.png)

### Responses vary *(Les réponses varient)*

Ask Claude the same question twice and you will get two different answers: both may be useful, but neither should be viewed as the "one correct response". This is how generative AI works: outputs are produced using probability, as opposed to retrieved from a fixed database. Plan for variation in any workflow that depends on consistent outputs, and build review into the process. A Skill does not remove it: [configured procedures still produce varied outputs](#configured-procedures-still-produce-varied-outputs-les-procédures-configurées-produisent-quand-même-des-réponses-variées). One of the [behavioral properties](#behavioral-properties-propriétés-comportementales).

→ [schéma des propriétés comportementales](mindmap/behavioral-properties.png)

### Confident tone is not a signal of accuracy *(Un ton assuré n'est pas un signe d'exactitude)*

Claude writes with consistent fluency regardless of whether the answer is actually correct: a fabricated statistic reads with the same assurance as a verified one. Without verification habits, fluency signals nothing about accuracy. One of the [behavioral properties](#behavioral-properties-propriétés-comportementales).

→ [schéma des propriétés comportementales](mindmap/behavioral-properties.png)

### Context is a budget *(Le contexte est un budget)*

Every Claude conversation holds a working-memory limit. As a conversation approaches its limit, claude.ai automatically summarizes earlier messages so the session can continue (on paid plans with [Code Execution](#code-execution-exécution-de-code) enabled). Summaries compress detail, which is why instructions followed at the start of a two-hour session can lose force by the end. The strategies for managing it ([context management](#context-management-gestion-du-contexte)): when to [restart](#restart-repartir-à-neuf), when to [summarize](#summarize-résumer), when to [persist](#persist-pérenniser). Long conversations degrade as context fills: managing context deliberately is more efficient than working around drift after it has accumulated. One of the [behavioral properties](#behavioral-properties-propriétés-comportementales).

→ [schéma des propriétés comportementales](mindmap/behavioral-properties.png)

### Knowledge has a training boundary *(Les connaissances ont une date limite)*

Claude's training data has a cutoff date. Information after that date is outside Claude's reliable knowledge unless you connect a current source, turn on web search in [chat](#chat-chat), or use [Research](#research-research). This affects recent events, current regulations, and up-to-date market data. When relevance matters, verify or connect a source. One of the [behavioral properties](#behavioral-properties-propriétés-comportementales).

→ [schéma des propriétés comportementales](mindmap/behavioral-properties.png)

### Configured procedures still produce varied outputs *(Les procédures configurées produisent quand même des réponses variées)*

A [Skill](#skills-skills) set up to run the same procedure every time reduces output variance but does not eliminate it: even a well-configured workflow produces different outputs each time it's run ([responses vary](#responses-vary-les-réponses-varient)). Configuration reduces variation, but it does not remove the need to check the output: review stays in your workflow regardless of how carefully a Skill is built. Every Claude feature, including configured Skills, produces different outputs run to run: variation is inherent; review is structural. One of the [behavioral properties](#behavioral-properties-propriétés-comportementales).

→ [schéma des propriétés comportementales](mindmap/behavioral-properties.png)

### Entry points *(Points d'entrée)*

The four distinct working entry points that Claude's one interface offers: [Chat](#chat-chat), [Projects](#projects-projets), [Artifacts](#artifacts-artefacts), and [Research](#research-research) Mode. Which entry point to use is the first of the four decisions (the second: the [capability layer](#capability-layer-couche-de-fonctionnalités)) at the front of every Claude interaction: choosing the right one before starting work determines how efficiently the session runs and whether the context you build today carries forward to tomorrow. Select the entry point before writing the prompt: the entry-point decision shapes every subsequent choice in the session. Selection logic: a one-off question or quick task, no plan to reuse → Chat; recurring work with stable context requirements → Project; output is a deliverable the recipient will open and read → Artifact; deep multi-source investigation or synthesis → Research (quick current-information lookups: web search in Chat).

→ [schéma des points d'entrée](mindmap/entry-points.png)

### Chat *(Chat)*

The default entry point, an unstructured conversation. A Chat is saved to your history and can be continued later, and [Memory](#memory-mémoire) plus past-chat search can carry key context into new sessions; what Chat does not give you is a Project's deliberate persistence, [standing instructions](#standing-instructions-instructions-de-projet) and a curated [knowledge base](#knowledge-base-base-de-connaissances). Regular Chat can search the web: web search is available on all Claude plans as a per-chat toggle in the chat input (on Team and Enterprise plans, an Owner or Primary Owner must first enable it for the workspace). Use Chat for one-off questions, quick drafts, exploratory prompting, and tasks you will not repeat: any task where the work starts and ends in that session. When you open a new Chat by pasting the same background paragraph you pasted last week, that workstream has outgrown Chat. One of the [entry points](#entry-points-points-dentrée).

→ [schéma des points d'entrée](mindmap/entry-points.png)

### Projects *(Projets)*

Persistent workspaces. A Project holds three things: [standing instructions](#standing-instructions-instructions-de-projet), a [knowledge base](#knowledge-base-base-de-connaissances), and a conversation history, its own conversation list, separate from your global conversation history. Conversations within a Project share the Project's instructions and knowledge base, but they do not share context with each other. Projects solve the most common productivity drain in AI-assisted professional work, re-explaining the same background every session: set the context once, and every conversation that follows starts with that context already in place. Worth building when any two of three conditions hold: the task recurs, the background context is stable (the same across sessions), the output format is consistent; the setup time is then recovered within two or three sessions. One of the [entry points](#entry-points-points-dentrée).

→ [schéma des points d'entrée](mindmap/entry-points.png)

### Standing instructions *(Instructions de projet)*

What Claude should know and do consistently across every conversation in a [Project](#projects-projets) (in the course's example, the report format and the escalation thresholds). With the [knowledge base](#knowledge-base-base-de-connaissances), where you set the context once. One of the three things a Project holds.

→ [schéma des points d'entrée](mindmap/entry-points.png)

### Knowledge base *(Base de connaissances)*

Documents, policies, and reference files uploaded once into a [Project](#projects-projets), so Claude can draw on them without re-uploading each session (in the course's example, the project background, the team structure, and the stakeholder list). Every conversation in the Project shares it. One of the three things a Project holds; a curated one is what [Chat](#chat-chat) does not give you.

→ [schéma des points d'entrée](mindmap/entry-points.png)

### Artifacts *(Artefacts)*

The right output format when the result is a deliverable rather than a conversational reply: an Artifact appears as a separate, editable block alongside the chat rather than flowing into the conversation thread. Use Artifacts for draft documents, data tables, formatted reports, and code; use inline responses for answers you will act on within the conversation. One of the [entry points](#entry-points-points-dentrée).

→ [schéma des points d'entrée](mindmap/entry-points.png)

### Research *(Research)*

Deep multi-source synthesis (available on paid plans). Research goes further than web search in [Chat](#chat-chat): it runs multi-step searches across multiple sources and synthesizes them. Use it when the task needs deep investigation across a range of sources, or synthesis of current information beyond a quick lookup. One way past [the training boundary](#knowledge-has-a-training-boundary-les-connaissances-ont-une-date-limite). One of the [entry points](#entry-points-points-dentrée).

→ [schéma des points d'entrée](mindmap/entry-points.png)

### Capability layer *(Couche de fonctionnalités)*

[Entry points](#entry-points-points-dentrée) determine where you work; the capability layer determines what Claude can do within that entry point. Which capability features to activate is the second of the four decisions at the front of every Claude interaction. Three features extend Claude's default text-generation behavior in ways that matter for professional work: [Skills](#skills-skills) for consistent procedures, [Code Execution](#code-execution-exécution-de-code) for verified computation, and [Memory](#memory-mémoire) for continuity across sessions. With [Projects](#projects-projets), they make the [four-layer model](#four-layer-model-modèle-à-quatre-couches).

→ [schéma de la couche de fonctionnalités](mindmap/capability-layer.png)

### Four-layer model *(Modèle à quatre couches)*

The relationship between four layers: [Projects](#projects-projets) carry context (what background knowledge and standing instructions apply to this workstream), [Skills](#skills-skills) define procedures (how a specific task should be executed, consistently, every time), [Code Execution](#code-execution-exécution-de-code) verifies computations (when the result must be correct, not merely plausible), [Memory](#memory-mémoire) persists continuity (relevant facts carry forward across sessions without re-entry). The layers are independent: use any combination based on what the task requires. A one-off question needs none of them, while a recurring analytical workflow might use all four.

→ [schéma de la couche de fonctionnalités](mindmap/capability-layer.png)

### Skills *(Skills)*

Reusable procedures. Anthropic provides built-in Skills for common professional tasks (creating, editing, and analyzing Excel spreadsheets, Word documents, PowerPoint decks, and PDFs); custom Skills can be added via settings for task-specific workflows. Skills live at the account level, not inside any one [Project](#projects-projets), and Claude invokes them automatically when relevant in any conversation, inside or outside a Project: a Project's own configuration is its [standing instructions](#standing-instructions-instructions-de-projet) and [knowledge base](#knowledge-base-base-de-connaissances); an active Skill tells Claude to follow a defined procedure for that task type, consistently, wherever it applies. Skills reduce variance, but they do not eliminate it: review stays in your workflow ([configured procedures still produce varied outputs](#configured-procedures-still-produce-varied-outputs-les-procédures-configurées-produisent-quand-même-des-réponses-variées)). Skills require a trust evaluation: a Skill has access to whatever you give Claude access to during the session, so review a third-party Skill's source and the permissions it requests before enabling it; Anthropic-provided Skills and Skills approved by your organization are the lower-risk starting point. One of the three features of the [capability layer](#capability-layer-couche-de-fonctionnalités).

→ [schéma de la couche de fonctionnalités](mindmap/capability-layer.png)

### Code Execution *(Exécution de code)*

Claude's sandboxed computation environment: Claude writes and runs code internally, then returns the result; you do not write the code yourself. Claude generates prose by producing the most probable next sequence of text: this works well for language tasks, but for computation it produces plausible-looking numbers that may or may not be accurate. Code Execution produces a verified result by running the calculation. Use it instead of asking Claude to calculate when any numeric output will be used or reported, when data needs to be transformed or cleaned, or when the output needs to be a chart or visualization, or a real downloadable file. One of the three features of the [capability layer](#capability-layer-couche-de-fonctionnalités).

→ [schéma de la couche de fonctionnalités](mindmap/capability-layer.png)

### Memory *(Mémoire)*

Retains work-relevant facts across sessions, removing the need to re-enter the same context each time (for example: recurring role context, preferences for output format, names of frequent collaborators, standing constraints that apply across projects). Memory is most useful when [actively curated](#memory-curation-entretien-de-la-mémoire): a memory that was accurate last quarter and has not been reviewed since can be actively misleading. Review stored memories periodically (at least once per month for active users), delete or update entries that no longer hold, and keep the stored set focused on information that genuinely recurs across sessions. Project-scoped Memory keeps Memory contexts separate for each [Project](#projects-projets): set up separate Projects for separate workstreams, and Memory follows the same boundaries. [Incognito mode](#incognito-mode-mode-incognito) keeps a session out of it. In [Chat](#chat-chat), Memory plus past-chat search can carry key context into new sessions. One of the three features of the [capability layer](#capability-layer-couche-de-fonctionnalités).

→ [schéma de la couche de fonctionnalités](mindmap/capability-layer.png)

### Incognito mode *(Mode incognito)*

Keeps a session out of [Memory](#memory-mémoire) and chat history; it applies to standalone chats, outside [Projects](#projects-projets). Use it for sensitive conversations or exploratory work with confidential inputs that shouldn't surface in history or Memory. It does not override your organization's underlying data retention.

→ [schéma de la couche de fonctionnalités](mindmap/capability-layer.png)

### Model tiers *(Gammes de modèles)*

The [capability layer](#capability-layer-couche-de-fonctionnalités) determines what Claude does; the model determines how well Claude does it, and at what cost in speed. Which model to select is the third of the four decisions at the front of every Claude interaction. Different model tiers in the Claude family span a range from efficient-and-fast to thorough-and-capable: [Haiku](#haiku-haiku), [Sonnet](#sonnet-sonnet) and [Opus](#opus-opus). Model tiers reflect a speed-capability trade-off. Matching the tier to the task avoids both over-engineering routine work and under-resourcing high-stakes analysis. The decision logic: routine, structured extraction or classification at volume → Haiku; most professional drafting, synthesis, and analysis → Sonnet; complex judgment, high-stakes output, ambiguous or multi-layered inputs → Opus. On metered or usage-budgeted plans (including API access), the speed-versus-capability trade-off also becomes a per-call cost trade-off: "efficiency" means cost as well as speed. On the standard claude.ai subscription surface, treat efficiency (speed and usage headroom) as the practical proxy for cost. The decision logic applies regardless of which tiers are available to you.

→ [schéma des gammes de modèles](mindmap/model-tiers.png)

### Haiku *(Haiku)*

The fastest and most efficient model in the Claude family. It handles structured tasks well: classification, extraction, formatting, straightforward summarization, and high-volume routine work where speed matters and the cost of an imperfect output is low. When a task runs at volume across hundreds of items in sequence, its speed advantage compounds. Use it where volume and speed are the primary requirements and the task has clear structure. One of the [model tiers](#model-tiers-gammes-de-modèles).

→ [schéma des gammes de modèles](mindmap/model-tiers.png)

### Sonnet *(Sonnet)*

The balanced tier. It handles the full range of professional tasks with strong quality across task types: drafting, synthesis, analysis, research assistance, and document review. For most knowledge-worker work, Sonnet is the right starting point: if quality is falling short for a complex task, upgrade to [Opus](#opus-opus); if speed and volume are the primary requirements and the task is structured, consider [Haiku](#haiku-haiku). One of the [model tiers](#model-tiers-gammes-de-modèles).

→ [schéma des gammes de modèles](mindmap/model-tiers.png)

### Opus *(Opus)*

A higher-capability tier, offering more advanced performance than [Sonnet](#sonnet-sonnet) and [Haiku](#haiku-haiku). Use it for tasks that require nuanced judgment, complex multi-step reasoning, ambiguous inputs that require interpretation, or any work where quality outranks speed (client-facing deliverables, complex document analysis, strategic planning, high-stakes synthesis across multiple sources). It produces better output on complex tasks, with the tradeoff of running slower, and consumes more usage per call than Haiku or Sonnet. Reserve it for work where the quality ceiling genuinely matters. One of the [model tiers](#model-tiers-gammes-de-modèles).

→ [schéma des gammes de modèles](mindmap/model-tiers.png)

### Context management *(Gestion du contexte)*

[Model selection](#model-tiers-gammes-de-modèles) and capability configuration (the [capability layer](#capability-layer-couche-de-fonctionnalités)) determine what Claude can do in a session; context management determines how long it can do it well. How to manage context across a session is the fourth of the four decisions at the front of every Claude interaction. Every Claude conversation has a finite working-memory budget ([context is a budget](#context-is-a-budget-le-contexte-est-un-budget)), and that budget runs down as the conversation grows (its [context window](#context-window-fenêtre-de-contexte) fills); deliberate context management keeps sessions coherent through long or complex work. Signs a conversation needs intervention: Claude stops following instructions it followed correctly earlier in the same session; responses address only the most recent exchange without reference to earlier decisions or context; accuracy drops in ways that are consistent with missing early-session context. Three responses when context degrades: [restart](#restart-repartir-à-neuf), [summarize](#summarize-résumer), [persist](#persist-pérenniser). For intensive tasks, plan ahead around the [usage limits](#usage-limits-limites-dutilisation).

→ [schéma de la gestion du contexte](mindmap/context-management.png)

### Context window *(Fenêtre de contexte)*

The working-memory limit of a Claude conversation. As messages and uploaded documents accumulate, it fills; as it fills toward the limit, claude.ai automatically summarizes earlier messages to make room (on paid plans with [Code Execution](#code-execution-exécution-de-code) enabled), and the full history remains available for reference. Detail can compress when earlier context is summarized: detailed instructions given at the start of a long session may produce responses later that don't follow them, not because Claude is ignoring them. What to do about it: [context management](#context-management-gestion-du-contexte).

→ [schéma de la gestion du contexte](mindmap/context-management.png)

### Restart *(Repartir à neuf)*

Start a new conversation. The [Project](#projects-projets)'s [standing instructions](#standing-instructions-instructions-de-projet) and [knowledge base](#knowledge-base-base-de-connaissances) carry forward automatically; the conversation thread does not. Restarting is the right call when the current session has drifted beyond recovery, or when you are beginning a genuinely new task within the same workstream. One of the three responses when context degrades ([context management](#context-management-gestion-du-contexte)); [summarize](#summarize-résumer) before it to keep the thread.

→ [schéma de la gestion du contexte](mindmap/context-management.png)

### Summarize *(Résumer)*

Before starting a new conversation ([restart](#restart-repartir-à-neuf)), ask Claude to produce a summary of the current state: decisions made, work in progress, and open questions; paste that summary at the start of the new conversation as context. This preserves thread continuity without carrying a degraded [context window](#context-window-fenêtre-de-contexte) into the next session. For intensive tasks, restart from a summary rather than extending a single session indefinitely ([usage limits](#usage-limits-limites-dutilisation)). One of the three responses when context degrades ([context management](#context-management-gestion-du-contexte)).

→ [schéma de la gestion du contexte](mindmap/context-management.png)

### Persist *(Pérenniser)*

For information that should be available across all future sessions: save it to [Memory](#memory-mémoire) or update the [Project](#projects-projets) [knowledge base](#knowledge-base-base-de-connaissances). Saving the right information at the right moment is more efficient than re-entering it repeatedly; a well-maintained Project with current knowledge base entries reduces the impact of individual session context limits. One of the three responses when context degrades ([context management](#context-management-gestion-du-contexte)).

→ [schéma de la gestion du contexte](mindmap/context-management.png)

### Memory curation *(Entretien de la mémoire)*

[Memory](#memory-mémoire) is most useful when actively curated, and serves best when it stays current: a memory entry that was accurate three months ago and has not been reviewed since can be actively misleading. Treat Memory like a working file: review it on a regular cadence (at least once per month for active users), delete entries that have expired, and update facts that have changed; keep the stored set focused on information that genuinely recurs across sessions. The accuracy of stored memories matters more than the volume.

→ [schéma de la gestion du contexte](mindmap/context-management.png) · [schéma de la couche de fonctionnalités](mindmap/capability-layer.png)

### Usage limits *(Limites d'utilisation)*

Claude's usage limits operate on more than one time window: a short rolling session window, plus weekly limits on paid plans that apply across models (with a separate weekly pool for the highest [model tier](#model-tiers-gammes-de-modèles)); the specific windows and allowances vary by plan and change over time. Extended sessions on higher-tier models may reach a limit before the work is complete. For intensive tasks, planning ahead is more efficient than working around an interrupted session: break large tasks into segments, save interim progress to the [knowledge base](#knowledge-base-base-de-connaissances), and [restart](#restart-repartir-à-neuf) from a [summary](#summarize-résumer) rather than extending a single session indefinitely.

→ [schéma de la gestion du contexte](mindmap/context-management.png)
