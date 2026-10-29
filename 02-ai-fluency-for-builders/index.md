---
tags: [ia, anthropic, ai-fluency, glossaire]
created: 2026-10-28
updated: 2026-10-29
---
# Glossaire et mindmap Anthropic

Glossaire du cours Anthropic « AI Fluency for Builders » (Claude Certification, Developer Foundation). Il se suffit à lui-même : un terme que définit aussi un autre cours a ici sa propre entrée, telle que ce cours le définit. Définitions en anglais, résumées du cours ; traduction française entre parenthèses, vérifiée sur des sources françaises de l'IA et de l'informatique (documentation des éditeurs, terminologie officielle, recherche).

Schémas, avec un sommaire et une légende pour chacun : [mindmap.md](mindmap.md).

---

## Glossaire

### Builder *(Builder)*

Someone who owns the full arc from customer problem to shipped solution: figuring out what problem was actually worth solving, making hundreds of small decisions about how it should work, then getting it into people's hands and learning from what happened next. Writing code is only a small part of the job: a builder owns the full building process, not just the coding slice in the middle. Builders (product people, engineers, designers and makers) are uniquely positioned to leverage AI to amplify what they create, but only if they can approach it intentionally, with clear judgment and purpose; AI is changing almost every part of that process. Their AI collaboration skills are the [4D Framework](#4d-framework-cadre-4d) applied to real builder tasks, from framing a customer problem to shipping a product, integrating AI responsibly across the full arc of building.

→ [schéma des 4D du builder](mindmap/builder-4ds.png)

### AI Fluency *(AI Fluency)*

The ability to work with AI systems in ways that are effective, efficient, ethical, and safe. It isn't a prompt library: it's a set of interconnected competencies (the [4D Framework](#4d-framework-cadre-4d)) that empower you to make great decisions regardless of the model or feature at your disposal. Writing better prompts to get better code is useful, but not enough to develop lasting AI Fluency: you need to know what to build in the first place, and to evaluate whether what AI produced is actually right, not just technically functional, but solving the real problem, working with real users, and not creating unexpected new problems. Think of AI as a capable but very literal collaborator: fast, knowledgeable, it doesn't get tired, but it needs clear tasks, real context about why you're building something, and specific feedback when it gets something wrong. Managing that collaborator well (knowing when to step in, when to let it run, how to give it the right brief) is the core skill the course develops: approaching AI with confidence and intentionality, moving faster without losing the judgment that makes what a [builder](#builder-builder) builds actually good.

→ [schéma des 4D du builder](mindmap/builder-4ds.png)

### 4D Framework *(Cadre 4D)*

The framework at the center of the course, developed by professors Joseph Feller and Rick Dakan in collaboration with Anthropic. It consists of four competencies: [Delegation](#delegation-délégation), [Description](#description-description), [Discernment](#discernment-discernement) and [Diligence](#diligence-diligence), the four competencies behind every productive AI collaboration. Think of them as the operating system underneath every collaboration you have with AI; they anchor every lesson of the course. Most AI failures trace back to Description, Discernment, or Diligence failures made earlier. Two modes of interaction: the [inner loop](#inner-loop-boucle-interne) (Description and Discernment) guides daily AI interactions; the [outer loop](#outer-loop-boucle-externe) (Delegation and Diligence) guides bigger decisions about when and how to use AI. The 4Ds come alive when you use them together; the framework is about making you more effective at the work that matters, work that requires human judgment, creativity, and deep understanding of your context. The competencies of [AI Fluency](#ai-fluency-ai-fluency).

→ [schéma des 4D du builder](mindmap/builder-4ds.png)

### Delegation *(Délégation)*

Decomposing a problem into parts and deciding what role AI plays at each stage: if, when and where to delegate to AI in the builder process, and defining done before you write a line of code. Delegating implementation to AI is usually fine (safe); delegating judgment, the call about whether something is actually good and ready, is usually not advised. The best builders know the difference. Delegation means deciding what AI handles and what stays with you: what work should be done by humans, what work should be done by AI, and how to distribute tasks between them. Good Delegation starts with understanding the work itself (a routine status update where AI can handle a first draft, or a sensitive negotiation where tone and nuance need to come directly from you), and you need to understand your tools as well (with confidential data, the privacy and security features of the AI system you're using); then you can thoughtfully split tasks to leverage the strengths of each. With Diligence, it forms the [outer loop](#outer-loop-boucle-externe). One of the competencies of the [4D Framework](#4d-framework-cadre-4d).

→ [schéma des 4D du builder](mindmap/builder-4ds.png)

### Description *(Description)*

A builder's ability to ensure that every input, from user voice to product requirements to technical specs, makes it into the implementation. Code built where the test passes is important, but insufficient (most AI training hyper-focuses on it). Any missing input or context cascades downstream: a user complains that the tool doesn't work for them, you trace it back, and you discover the issue wasn't in the code, but in how you understood and described the user problem. Builders must own every aspect of Description. Description means communicating clearly what you need and how you want AI to approach it: it goes beyond writing good prompts, starting with defining what you want (your outputs, format, audience, and style); you can also define how the AI approaches your request (the steps, the order of operations, the reasoning approach) and shape the AI's behavior during your collaboration. Description skills are the ones people pick up most naturally. With Discernment, it forms the [inner loop](#inner-loop-boucle-interne). One of the competencies of the [4D Framework](#4d-framework-cadre-4d).

→ [schéma des 4D du builder](mindmap/builder-4ds.png)

### Discernment *(Discernement)*

How you evaluate what AI gives you: not just does it run, but does it run well? Does it solve the right problem? Is it actually good to use, and is it responsible? You evaluate AI output against what actually matters: correctness, quality, fit, experience, and responsibility. AI has real blind spots: it can produce code that's locally correct, but breaks under load, or generate UX that's functional, but confusing. Discernment is the skill of catching those gaps before your users do. Discernment means evaluating what AI gives back before acting on it, thoughtfully and critically: start with the output itself, then look at how AI got there. It doesn't just mean accepting or rejecting AI outputs: it involves iteration to get where you want to go. While most people describe what they want fairly naturally, Discernment is much rarer: questioning AI's reasoning, checking facts, and identifying missing context were among the least common behaviors observed. With Description, it forms the [inner loop](#inner-loop-boucle-interne). One of the competencies of the [4D Framework](#4d-framework-cadre-4d).

→ [schéma des 4D du builder](mindmap/builder-4ds.png)

### Diligence *(Diligence)*

Full ownership of the outcome, not just the output: taking full ownership of what you build with AI. Shipping is a skill with its own technical realities that AI rarely surfaces proactively: migrations, rate limiting, monitoring. What happens when something breaks at 2 a.m. and you're the one who built it? Prototype freely, ship selectively, and be willing to veto something you built when the evidence says it isn't right. Diligence means owning the final result fully, regardless of AI's role: taking responsibility for how you use AI, being thoughtful about which AI systems you use and how you interact with them, being honest about AI's role in your work with the people who need to know, and verifying and vouching for the outputs you use or share. You're always accountable for the final result. With Delegation, it forms the [outer loop](#outer-loop-boucle-externe). One of the competencies of the [4D Framework](#4d-framework-cadre-4d).

→ [schéma des 4D du builder](mindmap/builder-4ds.png)

### Inner loop *(Boucle interne)*

The 4D Framework's mode of interaction for engaging with AI effectively on a day-to-day basis: [Description](#description-description) and [Discernment](#discernment-discernement). You describe what you need, evaluate what you get, and then refine your Description based on that evaluation, like working with a human teammate, building a shared understanding through conversation. It guides daily AI interactions; critically important when learning AI, but not sufficient on its own: the [outer loop](#outer-loop-boucle-externe) completes it.

→ [schéma des 4D du builder](mindmap/builder-4ds.png)

### Outer loop *(Boucle externe)*

The 4D Framework's mode of interaction for everything that happens in your workplace, community, and life around the use of AI: [Delegation](#delegation-délégation) and [Diligence](#diligence-diligence). It guides bigger decisions about when and how to use AI: should you be using AI at all, and if you do, what are your ethical responsibilities to proceed intentionally and responsibly? The choices you make about what to delegate must be matched by ongoing responsibility for how you use AI, and your diligent practices inform smarter Delegation decisions over time. The other mode is the [inner loop](#inner-loop-boucle-interne).

→ [schéma des 4D du builder](mindmap/builder-4ds.png)

### Generative AI *(IA générative)*

AI systems that can create new content rather than just analyzing existing data: where traditional AI might classify emails as spam or not spam based on patterns, generative AI can write a completely new email. The first approach analyzes and categorizes; the second creates something new that didn't exist before, a fundamental shift in AI capabilities. [Large language models](#large-language-model-grand-modèle-de-langage) are a prominent type of it. Three characteristics make modern generative AI so powerful: its ability to process vast amounts of information during training, its [in-context learning](#in-context-learning-apprentissage-en-contexte) ability, and [emergent capabilities](#emergent-capabilities-capacités-émergentes). It is trained in two phases: [pre-training](#pre-training-préentraînement), then [fine-tuning](#fine-tuning-réglage-fin).

→ [schéma des trois piliers de l'IA générative](mindmap/three-pillars.png)

### Large language model *(Grand modèle de langage)*

LLM: a prominent type of [generative AI](#generative-ai-ia-générative), like Anthropic's Claude models. Called language models because they're trained to predict and generate human language, and large because they contain billions of parameters, mathematical values that determine how the model processes information, somewhat like synaptic connections in your brain. When you interact with one, you provide a prompt, a text the model reads and then continues from, based on patterns it learned during training: it isn't retrieving pre-written answers from a database, it's generating new text that statistically follows from what you've written. Three developments made modern LLMs possible: the [transformer architecture](#transformer-architecture-architecture-transformeur), vast training data, and massive compute. Current strengths include versatility across tasks, conversational fluency, and [tool use](#tool-use-utilisation-doutils); current limits include [knowledge cutoffs](#knowledge-cutoff-date-limite-des-connaissances), [hallucinations](#hallucination-hallucination), and unreliable complex reasoning.

→ [schéma des trois piliers de l'IA générative](mindmap/three-pillars.png)

### Transformer architecture *(Architecture transformeur)*

The architecture developed in 2017, a game changer among the algorithmic and architectural breakthroughs that fundamentally changed how AI systems learn (neural networks had been around conceptually for decades). It excels at processing sequences of text while maintaining relationships between words across long passages, which is critical for understanding language and context. One of the three developments that made modern [LLMs](#large-language-model-grand-modèle-de-langage) possible, with vast training data (the explosion of digital data: websites, code repositories, and other texts) and massive compute (GPUs, TPUs, and clusters). Their combination led to the [scaling laws](#scaling-laws-lois-déchelle).

→ [schéma des trois piliers de l'IA générative](mindmap/three-pillars.png)

### Scaling laws *(Lois d'échelle)*

An important discovery the combination of the three developments (the [transformer architecture](#transformer-architecture-architecture-transformeur), vast training data, and massive compute) led to: empirical findings showing that as models grew larger and trained on more data with more computing power, their performance improved in predictable ways. More surprisingly, [emergent capabilities](#emergent-capabilities-capacités-émergentes) appeared as models grew larger.

→ [schéma des trois piliers de l'IA générative](mindmap/three-pillars.png)

### Emergent capabilities *(Capacités émergentes)*

Entirely new capabilities that began to emerge as models grew larger: abilities no one explicitly programmed, like reasoning through problems step by step or adapting to new tasks with minimal instruction. They arise from scale and sometimes surprise even their creators. One of the three characteristics that make modern [generative AI](#generative-ai-ia-générative) so powerful; found alongside the [scaling laws](#scaling-laws-lois-déchelle).

→ [schéma des trois piliers de l'IA générative](mindmap/three-pillars.png)

### Pre-training *(Préentraînement)*

The first of the two phases [generative AI](#generative-ai-ia-générative) is trained in: LLMs like Claude analyze patterns across billions of text examples, not just to absorb information, but to understand the statistical relationships between words, phrases, and concepts, building something like a complex map of language and knowledge. It involves showing the model text and asking it to predict what comes next; through many iterations, the model gradually refines its predictions, learning the patterns that make language coherent and meaningful. At the end of pre-training, the model is a very competent literal document completer. [Fine-tuning](#fine-tuning-réglage-fin) follows.

→ [schéma des trois piliers de l'IA générative](mindmap/three-pillars.png)

### Fine-tuning *(Réglage fin)*

The second phase of training, after [pre-training](#pre-training-préentraînement): models learn to follow instructions, provide helpful responses, and importantly, avoid generating harmful content. It often involves human feedback to improve the model's performance, as well as reinforcement learning, which uses rewards and penalties to shape the model's behavior toward being more helpful, honest, and harmless (in the case of Anthropic's models).

→ [schéma des trois piliers de l'IA générative](mindmap/three-pillars.png)

### Context window *(Fenêtre de contexte)*

The practical limit to how much information an [LLM](#large-language-model-grand-modèle-de-langage) can consider at once: think of it as the AI's working memory. It includes your prompts, the AI's responses, and any other information you've shared in your conversation. AI companies continue to grow it, but these systems don't have unlimited access to information and cannot use content beyond their current context window without specialized tools like web search. If a conversation or document exceeds it, the AI won't be able to consider information that falls outside the window, usually on a first in, first out basis: depending on the model, this can limit its ability to process large documents or remember an entire conversation. One of the current limits of LLMs.

→ [schéma des trois piliers de l'IA générative](mindmap/three-pillars.png)

### In-context learning *(Apprentissage en contexte)*

The ability of modern [generative AI](#generative-ai-ia-générative) to adapt to new tasks from instructions or examples in your prompt. One of the three characteristics that make it so powerful, with its ability to process vast amounts of information during training and [emergent capabilities](#emergent-capabilities-capacités-émergentes). These models can shift between different tasks without needing additional training.

→ [schéma des trois piliers de l'IA générative](mindmap/three-pillars.png)

### Knowledge cutoff *(Date limite des connaissances)*

The date, based on when an [LLM](#large-language-model-grand-modèle-de-langage) was trained, after which it has no innate knowledge of the world: AI models are bounded by their training data (a model with a cutoff date of November 2024 wasn't trained on any data after that point), like someone who went into a retreat without internet access and wouldn't know about the events after they left. Models need tools like web search to learn about recent developments. One of the current limits of LLMs.

→ [schéma des trois piliers de l'IA générative](mindmap/three-pillars.png)

### Hallucination *(Hallucination)*

AI confidently stating something that sounds plausible but is actually incorrect, like a friend who tells a story with absolute confidence only to have the details completely wrong. The training process doesn't verify every fact in the training data: models can learn and reproduce inaccuracies present in it, and can make mistakes when trying to piece together information they've learned. Unlike search engines that simply retrieve existing documents, [LLMs](#large-language-model-grand-modèle-de-langage) generate responses based on statistical patterns, sometimes producing hallucinations. One of the current limits of LLMs.

→ [schéma des trois piliers de l'IA générative](mindmap/three-pillars.png)

### Non-deterministic *(Non déterministe)*

Somewhat unpredictable by default, as [LLMs](#large-language-model-grand-modèle-de-langage) are, unlike traditional software that produces identical outputs given the same inputs: ask the same question twice and you might get slightly different responses. This variability stems from how these models generate text, making probabilistic decisions about what text should come next based on patterns in their training data and settings developers can tweak. It can be great for brainstorming and generating diverse ideas, but requires awareness when consistency or accuracy are critical; [temperature](#temperature-température) controls it. One of the current limits of LLMs.

→ [schéma des trois piliers de l'IA générative](mindmap/three-pillars.png)

### Temperature *(Température)*

A setting some LLM interfaces offer to control the randomness of a [non-deterministic](#non-deterministic-non-déterministe) model when needed.

→ [schéma des trois piliers de l'IA générative](mindmap/three-pillars.png)

### Tool use *(Utilisation d'outils)*

One of the current strengths of [LLMs](#large-language-model-grand-modèle-de-langage), with versatility across tasks and conversational fluency: many modern LLMs can reach beyond their own knowledge by connecting to external tools and information sources, allowing them to search the web, process files, or even use other applications to enhance their capabilities, which dramatically expands what they can help with. They may still lack access to specific data sources or specialized tools needed for certain tasks, like a brilliant colleague who can't access your company's internal database.

→ [schéma des trois piliers de l'IA générative](mindmap/three-pillars.png)

### Retrieval augmented generation *(Génération augmentée par récupération)*

A technique researchers use to address current limitations of [generative AI](#generative-ai-ia-générative): it connects models to external knowledge and data sources (alongside expanding their ability to use tools and improving their reasoning capabilities). Some limitations will likely remain for the foreseeable future.

→ [schéma des trois piliers de l'IA générative](mindmap/three-pillars.png)
