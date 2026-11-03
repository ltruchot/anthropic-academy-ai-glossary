---
tags: [ia, anthropic, claude, glossaire]
created: 2026-11-03
updated: 2026-11-03
---
# Glossaire et mindmap Anthropic

Glossaire du cours Anthropic « Choosing the right Claude model » (Claude Certification, Developer Foundation). Il se suffit à lui-même : un terme que définit aussi un autre cours a ici sa propre entrée, telle que ce cours le définit. Définitions en anglais, résumées du cours ; traduction française entre parenthèses, vérifiée sur des sources françaises de l'IA et de l'informatique (documentation des éditeurs, terminologie officielle, recherche).

Schémas, avec un sommaire et une légende pour chacun : [mindmap.md](mindmap.md).

---

## Glossaire

### Claude models *(Modèles de Claude)*

Claude comes in four models, [Haiku](#haiku-haiku), [Sonnet](#sonnet-sonnet), [Opus](#opus-opus) and [Fable](#fable-fable): think of them as different tools designed for different jobs. Each is built for different kinds of work, and each uses your [rate limit](#rate-limit-limite-dutilisation) differently: using Opus on a task Haiku could handle costs you tokens for no gain and slows you down in the process. Which models you have and how high your limit is both depend on your Claude account plan. On some biology and security topics, Claude may switch to a different model than the one you picked, and it tells you when it does. To pick one, consider what kind of output you're looking for and choose accordingly: if you're not sure, start with Sonnet; move to Opus for problems Sonnet struggled with, and to Fable for problems Opus struggled with. To test a choice, run a task you already know well with Haiku, then with Sonnet in a new chat, and compare where the answers differ, not how long they are: if Haiku's summary covers everything you would have flagged yourself, the task is Haiku-shaped. Each new model brings its own strengths: when one comes out, try more ambitious tasks that may have hit a ceiling in the past.

→ [schéma des quatre modèles](mindmap/four-models.png)

### Haiku *(Haiku)*

Fast and lightweight: the fastest model, built for everyday requests. When you need quick answers to simple questions, basic summaries, or synthesis, it gets it done instantly, and it is the most efficient with your [rate limit](#rate-limit-limite-dutilisation) (the lightest). Use it for simple, straightforward questions with short answers, a quick lookup or categorization, extracting specific information from text, simple summarization or synthesis: anything you want done instantly without complex reasoning (summarizing articles, for example). One of the [Claude models](#claude-models-modèles-de-claude).

→ [schéma des quatre modèles](mindmap/four-models.png)

### Sonnet *(Sonnet)*

The daily driver: strong reasoning for the kind of work you do every day (coding, writing, analysis, research, complex problem-solving), responsive enough for real-time collaboration and capable enough that most problems won't outgrow it. It also handles computer use, vision tasks, and document and spreadsheet creation well: a versatile default across a wide range of work. Its use of the [rate limit](#rate-limit-limite-dutilisation) is moderate. Use it for writing and content creation, coding tasks (debugging, writing new code, refactoring), analysis that needs reasoning but isn't extremely complex, customer support chatbots with context and nuance, multi-step problems and workflows. If you're not sure which model to pick, start here. One of the [Claude models](#claude-models-modèles-de-claude).

→ [schéma des quatre modèles](mindmap/four-models.png)

### Opus *(Opus)*

A large reasoning specialist, exceptional for specialized complex tasks requiring advanced reasoning: built for problems that genuinely need deep thinking over time. It uses more of your [rate limit](#rate-limit-limite-dutilisation) (heavy), because it does more reasoning: reserve it for tasks that really need it. Use it for deep research and analysis you'll question, redirect, and build on as you go; complex work you're doing in a live, back-and-forth session, where you want each answer sooner; problems where you've tested with [Sonnet](#sonnet-sonnet) and it struggled (analyzing complex research papers, for example). One of the [Claude models](#claude-models-modèles-de-claude).

→ [schéma des quatre modèles](mindmap/four-models.png)

### Fable *(Fable)*

The go-to for your largest, most important projects: the most capable model, built for long, complex tasks. It can work through tasks more autonomously with fewer mid-task check-ins: describe the outcome you want, and it plans the steps and checks its own work along the way. It takes time to think through problems before answering, so responses take longer, and it uses the most of your [rate limit](#rate-limit-limite-dutilisation). Use it for specialized tasks where accuracy is critical, long horizon tasks with many connected steps, outputs from dense source material (long documents, charts, technical diagrams), work where you'd rather describe the outcome and let Claude plan the steps, and problems you've tested with [Opus](#opus-opus) and it struggled (building a working project from a rough idea, for example). One of the [Claude models](#claude-models-modèles-de-claude).

→ [schéma des quatre modèles](mindmap/four-models.png)

### Rate limit *(Limite d'utilisation)*

Your rate limit caps how many tokens you can use in a given time window; how high it is depends on your Claude account plan. The [Claude models](#claude-models-modèles-de-claude) consume tokens at different rates: [Haiku](#haiku-haiku) is the lightest, [Sonnet](#sonnet-sonnet) is moderate, [Opus](#opus-opus) is heavy, and [Fable](#fable-fable) uses the most. Haiku and Sonnet are more "efficient" with your limit (you can ask more with fewer tokens); Opus and Fable use more tokens because they do more reasoning, so using them on a task Sonnet or Haiku could handle may use more of your limit unnecessarily. To balance rate limits with efficiency, consider what kind of output you're looking for and choose your model accordingly; the [Effort setting](#effort-setting-niveau-deffort) also helps.

→ [schéma des quatre modèles](mindmap/four-models.png)

### Effort setting *(Niveau d'effort)*

In the model picker, it adjusts the depth of reasoning Claude applies to a problem (thinking and effort controls customize that depth). The default level is the right balance for most work; lower it for quicker answers that use less of your [rate limit](#rate-limit-limite-dutilisation); save the highest setting for your hardest problems, since deeper thinking takes more time and uses more of your limit.

→ [schéma des quatre modèles](mindmap/four-models.png)
