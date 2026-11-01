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

Five properties that apply to Claude regardless of which feature you use: [responses vary](#responses-vary-les-réponses-varient), [confident tone is not a signal of accuracy](#confident-tone-is-not-a-signal-of-accuracy-un-ton-assuré-nest-pas-un-signe-dexactitude), [context is a budget](#context-is-a-budget-le-contexte-est-un-budget), [knowledge has a training boundary](#knowledge-has-a-training-boundary-les-connaissances-ont-une-date-limite), [configured procedures still produce varied outputs](#configured-procedures-still-produce-varied-outputs-les-procédures-configurées-produisent-quand-même-des-réponses-variées). Understand them before selecting entry points and models, and before building workflows with Claude: it prevents the most common sources of frustration and misaligned expectations.

→ [schéma des propriétés comportementales](mindmap/behavioral-properties.png)

### Responses vary *(Les réponses varient)*

Ask Claude the same question twice and you will get two different answers: both may be useful, but neither should be viewed as the "one correct response". This is how generative AI works: outputs are produced using probability, as opposed to retrieved from a fixed database. Plan for variation in any workflow that depends on consistent outputs, and build review into the process. A Skill does not remove it: [configured procedures still produce varied outputs](#configured-procedures-still-produce-varied-outputs-les-procédures-configurées-produisent-quand-même-des-réponses-variées). One of the [behavioral properties](#behavioral-properties-propriétés-comportementales).

→ [schéma des propriétés comportementales](mindmap/behavioral-properties.png)

### Confident tone is not a signal of accuracy *(Un ton assuré n'est pas un signe d'exactitude)*

Claude writes with consistent fluency regardless of whether the answer is actually correct: a fabricated statistic reads with the same assurance as a verified one. Without verification habits, fluency signals nothing about accuracy. One of the [behavioral properties](#behavioral-properties-propriétés-comportementales).

→ [schéma des propriétés comportementales](mindmap/behavioral-properties.png)

### Context is a budget *(Le contexte est un budget)*

Every Claude conversation holds a working-memory limit. As a conversation approaches its limit, claude.ai automatically summarizes earlier messages so the session can continue (on paid plans with Code Execution enabled). Summaries compress detail, which is why instructions followed at the start of a two-hour session can lose force by the end. The strategies for managing it: when to restart, when to summarize, when to persist. One of the [behavioral properties](#behavioral-properties-propriétés-comportementales).

→ [schéma des propriétés comportementales](mindmap/behavioral-properties.png)

### Knowledge has a training boundary *(Les connaissances ont une date limite)*

Claude's training data has a cutoff date. Information after that date is outside Claude's reliable knowledge unless you connect a current source, turn on web search in chat, or use Research. This affects recent events, current regulations, and up-to-date market data. When relevance matters, verify or connect a source. One of the [behavioral properties](#behavioral-properties-propriétés-comportementales).

→ [schéma des propriétés comportementales](mindmap/behavioral-properties.png)

### Configured procedures still produce varied outputs *(Les procédures configurées produisent quand même des réponses variées)*

A Skill set up to run the same procedure every time reduces output variance but does not eliminate it: even a well-configured workflow produces different outputs each time it's run ([responses vary](#responses-vary-les-réponses-varient)). Configuration reduces variation, but it does not remove the need to check the output: review stays in your workflow regardless of how carefully a Skill is built. One of the [behavioral properties](#behavioral-properties-propriétés-comportementales).

→ [schéma des propriétés comportementales](mindmap/behavioral-properties.png)
