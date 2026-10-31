---
tags: [ia, anthropic, ai-fluency, glossaire]
created: 2026-10-28
updated: 2026-10-31
---
# Glossaire et mindmap Anthropic

Glossaire du cours Anthropic « AI Fluency for Builders » (Claude Certification, Developer Foundation). Il se suffit à lui-même : un terme que définit aussi un autre cours a ici sa propre entrée, telle que ce cours le définit. Définitions en anglais, résumées du cours ; traduction française entre parenthèses, vérifiée sur des sources françaises de l'IA et de l'informatique (documentation des éditeurs, terminologie officielle, recherche).

Schémas, avec un sommaire et une légende pour chacun : [mindmap.md](mindmap.md).

---

## Glossaire

### Builder *(Builder)*

Someone who owns the full arc from customer problem to shipped solution: figuring out what problem was actually worth solving, making hundreds of small decisions about how it should work, then getting it into people's hands and learning from what happened next. Writing code is only a small part of the job: a builder owns the full building process, not just the coding slice in the middle. Builders (product people, engineers, designers and makers) are uniquely positioned to leverage AI to amplify what they create, but only if they can approach it intentionally, with clear judgment and purpose; AI is changing almost every part of that process. Their AI collaboration skills are the [4D Framework](#4d-framework-cadre-4d) applied to real builder tasks, from framing a customer problem to shipping a product, integrating AI responsibly across the full arc of building. Every builder carries a [toolkit](#builders-toolkit-boîte-à-outils-du-builder) of six capabilities. The builders who thrive in this era won't be the ones who prompt the fastest: they will be the ones who frame problems clearly, who know what good looks like before they start, and who can tell the difference between code that runs and code that matters. The builder is the translator at every step of the [Description Chain](#description-chain-chaîne-de-description), and builders who carefully describe all aspects of the problem get the best results with AI. The builder's job isn't to defend the software: it's to serve the user. The builders who will do the most interesting things with AI in the next few years aren't the ones who automate the most: they know when to delegate, and when to stay in the loop, and care enough about their users to not just ship something because it compiles.

→ [schéma des 4D du builder](mindmap/builder-4ds.png)

### AI Fluency *(AI Fluency)*

The ability to work with AI systems in ways that are effective, efficient, ethical, and safe. It isn't a prompt library: it's a set of interconnected competencies (the [4D Framework](#4d-framework-cadre-4d)) that empower you to make great decisions regardless of the model or feature at your disposal. Writing better prompts to get better code is useful, but not enough to develop lasting AI Fluency: you need to know what to build in the first place, and to evaluate whether what AI produced is actually right, not just technically functional, but solving the real problem, working with real users, and not creating unexpected new problems. Think of AI as a capable but very literal collaborator: fast, knowledgeable, it doesn't get tired, but it needs clear tasks, real context about why you're building something, and specific feedback when it gets something wrong. Managing that collaborator well (knowing when to step in, when to let it run, how to give it the right brief) is the core skill the course develops: approaching AI with confidence and intentionality, moving faster without losing the judgment that makes what a [builder](#builder-builder) builds actually good.

→ [schéma des 4D du builder](mindmap/builder-4ds.png)

### 4D Framework *(Cadre 4D)*

The framework at the center of the course, developed by professors Joseph Feller and Rick Dakan in collaboration with Anthropic. It consists of four competencies: [Delegation](#delegation-délégation), [Description](#description-description), [Discernment](#discernment-discernement) and [Diligence](#diligence-diligence), the four competencies behind every productive AI collaboration. Think of them as the operating system underneath every collaboration you have with AI; they anchor every lesson of the course. Most AI failures trace back to Description, Discernment, or Diligence failures made earlier. Two modes of interaction: the [inner loop](#inner-loop-boucle-interne) (Description and Discernment) guides daily AI interactions; the [outer loop](#outer-loop-boucle-externe) (Delegation and Diligence) guides bigger decisions about when and how to use AI. The 4Ds come alive when you use them together; the framework is about making you more effective at the work that matters, work that requires human judgment, creativity, and deep understanding of your context. The 4Ds are dynamic, not a sequence: you'll move from Delegation to Description, back to Discernment, and realize you want to delegate differently; moving fluidly between them as you build is what fluency looks like in practice. The competencies of [AI Fluency](#ai-fluency-ai-fluency).

→ [schéma des 4D du builder](mindmap/builder-4ds.png)

### Delegation *(Délégation)*

Decomposing a problem into parts and deciding what role AI plays at each stage: if, when and where to delegate to AI in the builder process, and defining done before you write a line of code. Delegating [implementation](#implementation-implémentation) to AI is usually fine (safe); delegating [judgment](#judgment-jugement), the call about whether something is actually good and ready, is usually not advised. The best builders know the difference. Delegation means deciding what AI handles and what stays with you: what work should be done by humans, what work should be done by AI, and how to distribute tasks between them. Good Delegation starts with understanding the work itself (a routine status update where AI can handle a first draft, or a sensitive negotiation where tone and nuance need to come directly from you), and you need to understand your tools as well (with confidential data, the privacy and security features of the AI system you're using); then you can thoughtfully split tasks to leverage the strengths of each. In the builder sense, imagine yourself as the lead on a project and AI as your team: a great lead doesn't just assign tasks; they frame the problem so everyone understands what they're solving, set goals so the team knows what good looks like, decide what to tackle first, and know which decisions to make themselves and which ones to hand off. It starts well before any code gets written: decomposing the problem first, then deciding what AI handles at each step, across the [builder's toolkit](#builders-toolkit-boîte-à-outils-du-builder). Good Delegation in practice: spending real time at the beginning of a project getting clear on who you're building for and defining what success means ([acceptance tests](#acceptance-test-test-dacceptation)), inspecting the results skeptically, and keeping judgment calls in your own hands. Break the problem down: the parts of the work that genuinely benefit from AI (implementation, scaffolding, boilerplate, first drafts of specs) are strong candidates; the judgment calls, the understanding of who your user actually is and what they might be struggling with, and the decision about whether the thing you built is actually the right thing belong to you. Resist the temptation, once you have a tool that can write code instantly, to skip straight to building and treat empathy and design work as overhead. With Diligence, it forms the [outer loop](#outer-loop-boucle-externe). One of the competencies of the [4D Framework](#4d-framework-cadre-4d).

→ [schéma des 4D du builder](mindmap/builder-4ds.png)

### Description *(Description)*

A builder's ability to ensure that every input, from user voice to product requirements to technical specs, makes it into the implementation. Code built where the test passes is important, but insufficient (most AI training hyper-focuses on it). Any missing input or context cascades downstream: a user complains that the tool doesn't work for them, you trace it back, and you discover the issue wasn't in the code, but in how you understood and described the user problem. Builders must own every aspect of Description. Description means communicating clearly what you need and how you want AI to approach it: it goes beyond writing good prompts, starting with defining what you want (your outputs, format, audience, and style); you can also define how the AI approaches your request (the steps, the order of operations, the reasoning approach) and shape the AI's behavior during your collaboration. Description skills are the ones people pick up most naturally. Most AI training treats Description as prompt engineering; but Description is a high-level competency that will remain relevant, outlasting tips and tricks that may change from model to model, and the [Description Chain](#description-chain-chaîne-de-description) maps all its aspects, from user voice to AI instruction (prompt engineering is only one link). The more thoughtful the Description, the better the output. [Acceptance tests](#acceptance-test-test-dacceptation) are a form of Description too, its most precise form. With Discernment, it forms the [inner loop](#inner-loop-boucle-interne). One of the competencies of the [4D Framework](#4d-framework-cadre-4d).

→ [schéma des 4D du builder](mindmap/builder-4ds.png)

### Discernment *(Discernement)*

How you evaluate what AI gives you: not just does it run, but does it run well? Does it solve the right problem? Is it actually good to use, and is it responsible? You evaluate AI output against what actually matters: correctness, quality, fit, experience, and responsibility. AI has real blind spots: it can produce code that's locally correct, but breaks under load, or generate UX that's functional, but confusing. Discernment is the skill of catching those gaps before your users do. Apply it before shipping: AI output often passes « Does it work? » but stumbles on « Is it the right thing? », and those gaps are where your judgment matters most. Sometimes AI builds the thing you describe, but not the thing that solves the problem; or it builds the thing that works, but one that people don't want to use. Discernment means evaluating what AI gives back before acting on it, thoughtfully and critically: start with the output itself, then look at how AI got there. It doesn't just mean accepting or rejecting AI outputs: it involves iteration to get where you want to go. While most people describe what they want fairly naturally, Discernment is much rarer: questioning AI's reasoning, checking facts, and identifying missing context were among the least common behaviors observed. Its structure: the [Five Lenses of Discernment](#five-lenses-of-discernment-cinq-angles-du-discernement), five questions to ask of anything that AI builds. With Description, it forms the [inner loop](#inner-loop-boucle-interne). One of the competencies of the [4D Framework](#4d-framework-cadre-4d).

→ [schéma des 4D du builder](mindmap/builder-4ds.png) · [schéma des cinq angles du Discernement](mindmap/five-lenses.png)

### Diligence *(Diligence)*

Full ownership of the outcome, not just the output: taking full ownership of what you build with AI. [Shipping](#shipping-livraison) is a skill with its own technical realities that AI rarely surfaces proactively: migrations, rate limiting, monitoring. What happens when something breaks at 2 a.m. and you're the one who built it? Prototype freely, ship selectively, and be willing to veto something you built when the evidence says it isn't right: sunk effort is one of the hardest things to walk away from, but the builder's job isn't to defend the software, it's to serve the user. Before anything goes to users, ask: « Do I understand what this does? » Can I explain it? Is there a way to know if it's working? Diligence means owning the final result fully, regardless of AI's role: taking responsibility for how you use AI, being thoughtful about which AI systems you use and how you interact with them, being honest about AI's role in your work with the people who need to know, and verifying and vouching for the outputs you use or share. You're always accountable for the final result. In the builder model, Diligence is full ownership: you're responsible for the product from whether it should exist to whether it's serving users after launch. You own the outcome, not the output: « AI wrote it » explains nothing and excuses nothing. In the 4D Framework, it means taking responsibility for what you build with AI, making sure your use of AI is transparent, ethical, and accountable: being transparent about your AI use and disclosing it, taking ownership of the outputs that AI creates, verifying work before you ship, considering the impact of what you built on others, and honoring policies, privacy, and professional standards that govern AI use in your organization or industry. With AI, you can end up being the owner of code you didn't write: Diligence is how you catch up to your own code, through three [habits](#habits-of-diligence-habitudes-de-la-diligence). Cheap code creates value only when paired with honest evaluation, and deprecating your own work is an underrated skill. Access is a design decision: check who your assumptions exclude before you call something shipped. With Delegation, it forms the [outer loop](#outer-loop-boucle-externe). One of the competencies of the [4D Framework](#4d-framework-cadre-4d).

→ [schéma des 4D du builder](mindmap/builder-4ds.png) · [schéma des habitudes de la Diligence](mindmap/diligence-habits.png)

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

### Builder's toolkit *(Boîte à outils du builder)*

The six capabilities every [builder](#builder-builder) carries, maybe without knowing it, and can reach for at any moment in a build: [Empathy](#empathy-empathie), [Design](#design-design), [Architecture](#architecture-architecture), [Implementation](#implementation-implémentation), [Judgment](#judgment-jugement) and [Shipping](#shipping-livraison). AI can help with all six, but it's much stronger at some than others, and knowing the difference is a key part of AI fluency for builders. Implementation sits right in the middle, and that's where AI is the strongest; empathy, judgment, and shipping sit at the edges, and that's where AI is the weakest. The key insight of the course: AI is the strongest in the middle of the toolkit, and weakest at the edges; the edges are where the human work lives, and where the value is: AI can't feel what your user feels, and can't tell whether what you shipped actually made a difference. Delegate implementation freely; keep empathy, judgment, and shipping in your hands. The faster AI makes implementation, the more your value shifts to everything around it: framing problems and raising the bar. [Delegation](#delegation-délégation) decides what AI handles at each step. The four steps of the [Description Chain](#description-chain-chaîne-de-description) are directly tied to its capabilities.

→ [schéma de la boîte à outils du builder](mindmap/builders-toolkit.png)

### Empathy *(Empathie)*

The first capability of the [builder's toolkit](#builders-toolkit-boîte-à-outils-du-builder): understanding who you're building for. What does the person we're building for actually need? Not what they said that they want, but what will truly help their work. This is where you talk to users and observe what frustrates them. AI can surface data and personas, and help you organize what you learn, but it can't feel the gap: it can't sit with a clinic receptionist and notice that she checks her phone 40 times a day because patients keep calling to ask about wait times. That observation is all you. In the [Description Chain](#description-chain-chaîne-de-description), your own empathy observes what goes unsaid in [user voice](#user-voice-voix-de-lutilisateur), and the judgment calls of a [product requirement](#product-requirement-exigence-produit) rest on what you learned in your empathy work. At the edges of the toolkit, where AI is the weakest (the course's widget: « AI weak »).

→ [schéma de la boîte à outils du builder](mindmap/builders-toolkit.png)

### Design *(Design)*

The second capability of the [builder's toolkit](#builders-toolkit-boîte-à-outils-du-builder): what should we build, and why? Translating user needs into an experience worth having. This is where you weigh trade-offs, make bets, and decide what matters (a text message or a web page? exact wait times or ranges?): those are judgment calls. AI generates options and patterns quickly, but the judgment about which option fits is yours: you bring taste and context. The course's widget: « AI moderate ». Treating empathy and design work as overhead, once a tool can write code instantly, is a temptation to resist.

→ [schéma de la boîte à outils du builder](mindmap/builders-toolkit.png)

### Architecture *(Architecture)*

The third capability of the [builder's toolkit](#builders-toolkit-boîte-à-outils-du-builder): how should the thing be structured? What are the pieces, and how do they fit together? Structuring a system that holds up under real conditions. AI knows patterns: it's seen a thousand systems like the one you're sketching, but it doesn't know your constraints, your team skills, or what you need to change six months from now; your constraints are yours to specify. « Human plus AI » works really well here. The course's widget: « AI moderate ».

→ [schéma de la boîte à outils du builder](mindmap/builders-toolkit.png)

### Implementation *(Implémentation)*

The fourth capability of the [builder's toolkit](#builders-toolkit-boîte-à-outils-du-builder): writing the actual code (write, debug, and iterate on code). It sits right in the middle of the toolkit, where AI is the strongest: once you know what you're building, and how it should be structured, AI can write working code effectively. The capability you should delegate most aggressively (the widget: « AI strong », « delegate freely here »); delegating implementation to AI is usually safe, delegating [judgment](#judgment-jugement) is usually not. If you've entered this stage without clearly defined tests and success checkpoints ([acceptance tests](#acceptance-test-test-dacceptation)), you've probably skipped a step. The faster AI makes implementation, the more your value shifts to everything around it. Before implementation, you have to define the user need ([Description Chain](#description-chain-chaîne-de-description)): very clear, concrete criteria help AI do its job better when it gets to the implementation step.

→ [schéma de la boîte à outils du builder](mindmap/builders-toolkit.png)

### Judgment *(Jugement)*

The fifth capability of the [builder's toolkit](#builders-toolkit-boîte-à-outils-du-builder): deciding what's right, good enough, and worth shipping. Does it actually work? Is it actually good? Would you put your name on it? AI will tell you the code runs, but it won't tell you if the experience feels right, whether the edge cases matter, or whether you've solved a real problem at hand; AI can list options, it can't own the call. Judgment requires your expertise, standards, and perspective. Delegating judgment, the call about whether something is actually good and ready, is usually not advised: good [Delegation](#delegation-délégation) keeps judgment calls in your own hands. At the edges of the toolkit, where AI is the weakest (the widget: « AI weak »).

→ [schéma de la boîte à outils du builder](mindmap/builders-toolkit.png)

### Shipping *(Livraison)*

The last capability of the [builder's toolkit](#builders-toolkit-boîte-à-outils-du-builder): getting it to real users and learning from what happens, getting it in front of users and iterating. This means communication, measurement, iteration. AI can draft release notes and automate steps, but it can't read the room when your user hesitates before clicking: responsibility is yours. Shipping is a skill with its own technical realities that AI rarely surfaces proactively (migrations, rate limiting, monitoring: [Diligence](#diligence-diligence)). It has its own technical vocabulary (migrations, versioning, rate limits, feature flags) that AI will not surface unless you ask. The video puts it at the edges of the toolkit, where AI is the weakest; the course's widget rates it « AI moderate ».

→ [schéma de la boîte à outils du builder](mindmap/builders-toolkit.png)

### Acceptance test *(Test d'acceptation)*

A test written before code, that defines done before a single line of code exists: acceptance tests give you and AI a shared definition of done. If you've entered [implementation](#implementation-implémentation) without clearly defined tests and success checkpoints, you've probably skipped a step. Part of good [Delegation](#delegation-délégation): spending real time at the beginning of a project getting clear on who you're building for, and defining what success means. Acceptance tests are a form of [Description](#description-description) too, maybe the most powerful kind, and its most precise form: a well-written test is a description of intent that can't be misread, because it either passes, or it doesn't. Handed to AI alongside your prompt, tests tell it not just what to build, but how you'll know if it succeeded, and that changes what you get back: they tell AI exactly what success looks like ([AI instruction](#ai-instruction-instruction-pour-lia): the test it has to pass). A passing test with an unhappy user means you described the wrong intent ([Description failure](#description-failure-erreur-de-description)).

→ [schéma de la boîte à outils du builder](mindmap/builders-toolkit.png) · [schéma de la chaîne de Description](mindmap/description-chain.png)

### Description Chain *(Chaîne de Description)*

The full path from a messy human need to a precise instruction AI can act on, with the [builder](#builder-builder) as the translator at every step: it connects [user voice](#user-voice-voix-de-lutilisateur) to [product requirement](#product-requirement-exigence-produit) to [technical spec](#technical-spec-spécification-technique) to [AI instruction](#ai-instruction-instruction-pour-lia). Most AI training teaches you to write better prompts, and treats [Description](#description-description) as prompt engineering: that's necessary but not sufficient for building great products; prompt engineering is only one link. Four steps directly tied to the capabilities in the [builder's toolkit](#builders-toolkit-boîte-à-outils-du-builder): before [implementation](#implementation-implémentation), you have to define the user need. Every step involves judgment calls the previous phase did not make for you. AI can't hear what the user didn't say: your job is to carry what you know intact as you describe what you need to the AI. Robust description means following the full chain, all the way to tests: user voice to requirement to spec to AI instruction to tests; a failure at any link cascades downstream. When the translation breaks, you get a [Description failure](#description-failure-erreur-de-description): find which link broke upstream.

→ [schéma de la chaîne de Description](mindmap/description-chain.png)

### User voice *(Voix de l'utilisateur)*

The first step of the [Description Chain](#description-chain-chaîne-de-description): what a real person actually says (for example, "I want to see wait times before I go to the clinic"). Its tone and emotion carry context the speaker didn't say out loud: that it's been two hours already, a kid in the car, a choice between this clinic and urgent care across town. Use your own [empathy](#empathy-empathie) to connect and observe what goes unsaid by the user. User voice is just raw material: it's true, and it's not yet buildable. Never really hearing what the user needed in the first place is a user understanding failure ([Description failure](#description-failure-erreur-de-description)).

→ [schéma de la chaîne de Description](mindmap/description-chain.png)

### Product requirement *(Exigence produit)*

The second step of the [Description Chain](#description-chain-chaîne-de-description): where you take the raw user need and scope it into something measurable (for example, patients can view estimated wait times via a mobile-friendly webpage, perhaps updated every five minutes). Each decision (mobile-friendly, not an app; estimated, not exact; every five minutes, not real time) is a key judgment call, made from what you learned in your own [empathy](#empathy-empathie) work; AI can't make it (it can't decide that estimated is the right requirement, because exact times would make the clinic staff anxious about being held to them). Very clear, concrete criteria help AI do its job better when it gets to the [implementation](#implementation-implémentation) step. Hearing the user, but scoping the need wrong, is a requirement failure ([Description failure](#description-failure-erreur-de-description)).

→ [schéma de la chaîne de Description](mindmap/description-chain.png)

### Technical spec *(Spécification technique)*

The third step of the [Description Chain](#description-chain-chaîne-de-description), where you get into the real building (for example, a web app that takes wait data from a clinic API and displays it with a responsive UI, refreshing on a five-minute interval). It is implementable: an engineer could read it and start building, and so could an AI. But it still leaves room: which stack? How do errors get handled? What happens when the API goes down? A right requirement whose technical translation lost something is a spec failure ([Description failure](#description-failure-erreur-de-description)).

→ [schéma de la chaîne de Description](mindmap/description-chain.png)

### AI instruction *(Instruction pour l'IA)*

The fourth step of the [Description Chain](#description-chain-chaîne-de-description): specific, contextualized with constraints, with edge cases clearly defined: the stack you're using and the shape of the data, what to do when there's no data, the test it has to pass. Give the AI specific things it can verify: it helps it work more effectively, and for longer. Handing AI a set of [acceptance tests](#acceptance-test-test-dacceptation) alongside your prompt tells it not just what to build, but how you'll know if it succeeded. Everything upstream solid, but the AI instructed poorly: a prompt failure ([Description failure](#description-failure-erreur-de-description)).

→ [schéma de la chaîne de Description](mindmap/description-chain.png)

### Description failure *(Erreur de Description)*

Code that works, but a product that doesn't: the test might pass, but the user is still frustrated. That's not a bug: the translation along the [Description Chain](#description-chain-chaîne-de-description) broke, and the failure usually lives upstream of the prompt; it cascades. So a big part of a [builder](#builder-builder)'s job is forensic: when what you built misses the mark, trace it back to the link that broke. A user understanding failure ([user voice](#user-voice-voix-de-lutilisateur): you never really heard what they needed in the first place), a requirement failure ([product requirement](#product-requirement-exigence-produit): you heard them, but scoped it wrong), a spec failure ([technical spec](#technical-spec-spécification-technique): the requirement was right, but the technical translation lost something), or a prompt failure ([AI instruction](#ai-instruction-instruction-pour-lia): everything upstream was solid, and you instructed the AI poorly). A passing test with an unhappy user means you described the wrong intent: your test described the wrong thing, and now you know exactly where in the chain to look. Most AI failures trace back to Description, Discernment, or Diligence failures made earlier ([4D Framework](#4d-framework-cadre-4d)).

→ [schéma de la chaîne de Description](mindmap/description-chain.png)

### Five Lenses of Discernment *(Cinq angles du Discernement)*

A structure for the judgment of [Discernment](#discernment-discernement): five lenses and five questions to ask of anything that AI builds, to evaluate AI-generated work across correctness, quality, fit, experience, and responsibility. A working product and a good product are not always the same thing: when AI can spin up a working product in minutes, "working" stops being the bar, and your ability to tell the difference becomes the most valuable skill in the room. In order: [functional integrity](#functional-integrity-intégrité-fonctionnelle) (Does it work?), [production readiness](#production-readiness-préparation-à-la-production) (Does it work well?), [problem fit](#problem-fit-adéquation-au-besoin) (Is it the right thing?), [experience quality](#experience-quality-qualité-de-lexpérience) (Is it good?) and [responsible impact](#responsible-impact-impact-responsable) (Is it responsible?). Lens 1 is easy to test: run it and see; by lens 5, you're making judgment calls AI can't make for you. Most engineering education stops at the first two lenses, but [builders](#builder-builder) need all five: the biggest problems are almost never at lens 1. AI is good at producing code that runs; it needs your oversight to produce a product that matters. Code that runs can still fail: the default AI output is technically complete but often misses the point.

→ [schéma des cinq angles du Discernement](mindmap/five-lenses.png)

### Functional integrity *(Intégrité fonctionnelle)*

Lens 1 of the [Five Lenses of Discernment](#five-lenses-of-discernment-cinq-angles-du-discernement): does it actually work? Bugs, errors, security holes. It checks that the code produces correct output for real inputs, not just test data; its common AI failure: code that passes unit tests but breaks on real data the prompt never covered. This is where most code review stops: it's necessary, but it's not close to sufficient. Consider the full gamut of functional tests: unit tests, integration tests, regression tests, edge cases, end-to-end. AI should be building tests alongside the code, not after it: when you prompt, ask it to write test cases in the very same pass, then build in regular checkpoints. A test suite that hasn't been run is not a safety net: it's just a false sense of security.

→ [schéma des cinq angles du Discernement](mindmap/five-lenses.png)

### Production readiness *(Préparation à la production)*

Lens 2 of the [Five Lenses of Discernment](#five-lenses-of-discernment-cinq-angles-du-discernement): does it actually work well? Performance, scalability, reliability: what happens under load, when hundreds of people try to refresh at the same time? It checks that the code handles concurrent users without race conditions; its common AI failure: smooth in dev, broken under load or behind a real infrastructure stack. AI has specific blind spots here: predictable ones in concurrency, security, and anything that only breaks at scale, technical blind spots that surface in production but not in development. A few concrete moves: ask AI to stress test its own output, have it generate production scenarios, and check how the code handles them; ask it explicitly, "What production assumptions does this code make?", to surface things that were missed in the first pass. When an API call takes five seconds too long, does the display freeze, show stale data, or fail gracefully? AI doesn't think about that: that's with you.

→ [schéma des cinq angles du Discernement](mindmap/five-lenses.png)

### Problem fit *(Adéquation au besoin)*

Lens 3 of the [Five Lenses of Discernment](#five-lenses-of-discernment-cinq-angles-du-discernement): is it the right thing? Does it solve the user's actual problem, or the problem the user thinks they have? Those can diverge. It checks that it solves the user's actual need, not just the literal spec you wrote; its common AI failure: a technically complete feature that addresses the prompt but misses the underlying need. For example, a patient asked about wait times, and AI can build an estimated wait time display, but what the patient really needed to know was if there was a pediatrician available in the next 20 minutes, to assess if their child's fever is critical or not. AI solved the stated problem: you need to check whether that's the real problem (what goes unsaid in [user voice](#user-voice-voix-de-lutilisateur)).

→ [schéma des cinq angles du Discernement](mindmap/five-lenses.png)

### Experience quality *(Qualité de l'expérience)*

Lens 4 of the [Five Lenses of Discernment](#five-lenses-of-discernment-cinq-angles-du-discernement): is it actually good? Is the experience clear, intuitive, [accessible](#accessibility-accessibilité)? It checks that users can complete the core task without help or instruction; its common AI failure: generic UI patterns that technically work but feel uninvested, and confused or frustrated users. AI doesn't have [taste](#taste-goût), it has patterns: it will give you a competent interface that no one enjoys using. For a clinical wait time tool, that's not just an aesthetic problem, it's a patient safety issue. It's your job as the builder to notice this, and translate it into something concrete and fixable.

→ [schéma des cinq angles du Discernement](mindmap/five-lenses.png)

### Responsible impact *(Impact responsable)*

Lens 5 of the [Five Lenses of Discernment](#five-lenses-of-discernment-cinq-angles-du-discernement): is it responsible? Bias? Privacy? Unintended consequences? Who could this harm? What does it assume about the user that might not be true? It checks that the product is transparent about AI's role, and doesn't present generated content as verified fact; its common AI failure: AI-generated content presented as authoritative, or a demographic left out by default. If the historical data a model is trained on reflects existing bias (systemic inequities contributing to longer wait times for certain demographics, for example), the model may reproduce that same pattern: it won't flag it, it will just display a number. Build guardrails, ask AI to name its bias as it builds, and, most importantly, question all assumptions.

→ [schéma des cinq angles du Discernement](mindmap/five-lenses.png)

### Taste *(Goût)*

What AI doesn't have: it has patterns, and will give you a competent interface that no one enjoys using. Taste is a [builder](#builder-builder) skill: AI delivers functional; making it worth using is on you. When AI can spin up a working product in minutes, "working" stops being the bar: you build the taste that AI doesn't have ([experience quality](#experience-quality-qualité-de-lexpérience)).

→ [schéma des cinq angles du Discernement](mindmap/five-lenses.png)

### UX principles *(Principes d'UX)*

The principles that matter most when working with AI: as AI speeds up implementation, design becomes the differentiator. You don't need to become a designer, but you do need to recognize good experience, spec for it, and iterate towards it. Four, in order: [clarity](#clarity-clarté), [hierarchy](#hierarchy-hiérarchie) (with [progressive disclosure](#progressive-disclosure-divulgation-progressive)), [accessibility](#accessibility-accessibilité) and [feedback](#feedback-feedback) (with responsiveness). The course shows each one on a screen with common UX problems AI generates by default. Applying them is part of [design literacy](#design-literacy-culture-du-design).

→ [schéma des principes d'UX](mindmap/ux-principles.png)

### Clarity *(Clarté)*

Every element should instantly communicate its purpose: users shouldn't have to guess what a button does or what a field means. If users can't tell what your product does, or how to get started, they're gone. Clarity means unifying form and function while respecting people's mental models: users arrive with expectations, shaped by other software and by the world. Keep it simple and map your interface to concepts they recognize: a patient checking wait times expects it to work like every other status checker. One of the [UX principles](#ux-principles-principes-dux).

→ [schéma des principes d'UX](mindmap/ux-principles.png)

### Hierarchy *(Hiérarchie)*

Visual weight should match information priority: the most important thing should look the most important. Make it easy for people to scan and find the information that is needed; don't overwhelm them. Use text size and weight to create good headers. It goes with [progressive disclosure](#progressive-disclosure-divulgation-progressive). One of the [UX principles](#ux-principles-principes-dux).

→ [schéma des principes d'UX](mindmap/ux-principles.png)

### Progressive disclosure *(Divulgation progressive)*

Paired with [hierarchy](#hierarchy-hiérarchie): cut the amount of unneeded elements (the video says « Minify » [sic]), and allow people to find the information they need as they need it instead of cramming it all into one space.

→ [schéma des principes d'UX](mindmap/ux-principles.png)

### Accessibility *(Accessibilité)*

A baseline, not a nice to have. Screen reader compatibility, color contrast, keyboard navigation: ask the AI for these explicitly every single time, and build test cases to validate. About 1 in 5 people has a disability (visual, cognitive, or neurological); AI generates for the median user, and small text, color-only signals, and jargon quietly exclude everyone else. AI does not get accessibility right by default: specify it, then audit what you get back. One of the [UX principles](#ux-principles-principes-dux).

→ [schéma des principes d'UX](mindmap/ux-principles.png)

### Feedback *(Feedback)*

With responsiveness: when the user does something, the interface should acknowledge it, not lead the user to question if something might be broken. Loading states, confirmations, and error messages that explain what to do next, all in simple human language, help build trust. When something breaks, users need to know what happened, what to do next, and how to get help: a raw error code answers none of those questions. One of the [UX principles](#ux-principles-principes-dux).

→ [schéma des principes d'UX](mindmap/ux-principles.png)

### Design literacy *(Culture du design)*

A core [builder](#builder-builder) skill: when implementation is fast, experience is the differentiator. « Make it look good » is a wish, not a spec: describe experience with the same precision as a function (« Put the wait time in the largest text on the page, use a single color to indicate status, and make the refresh time visible so the patient knows how stale the number is » is an actionable, strong [Description](#description-description)). A good critique and an actionable AI description are different artifacts: « This feels cluttered » is a fair critique, but useless instruction for AI. Part of design literacy is learning how to translate your own [taste](#taste-goût) into something that is executable. This is Description and [Discernment](#discernment-discernement) working together: you describe the experience precisely, AI builds it; you evaluate what comes back against what you intended; you describe the gap, repeat.

→ [schéma des principes d'UX](mindmap/ux-principles.png)

### Habits of Diligence *(Habitudes de la Diligence)*

With AI, you can end up being the owner of code you didn't write: [Diligence](#diligence-diligence) is how you catch up to your own code. Understand it, stress it, test it, and put the systems in place that catch what you miss. Three habits, from an engineer's day-to-day: [verification](#verification-vérification) (seek out edge cases & assumptions), [transparency](#transparency-transparence) (tell people AI wrote it) and [understanding](#understanding-compréhension) (consciously understand how the code works). With them, [safety nets](#safety-nets-filets-de-sécurité): tests on one end, [observability](#observability-observabilité) on the other. None of this is new to engineering: AI is just a new tool under your belt to get there.

→ [schéma des habitudes de la Diligence](mindmap/diligence-habits.png)

### Verification *(Vérification)*

Seek out edge cases & assumptions. When you write code yourself, it becomes apparent as you go that there are things you hadn't thought of: some edge case, some decision you hadn't realized needed to be made. With AI, those sometimes end up getting decided without ever being surfaced to you: recreate that step on purpose, and get those questions out in the open where you can weigh in. When an edge case pops into your head, say it to the model (« Can you double check that users can't view other users' files? »); after Claude builds something substantial, ask directly: « What assumptions and trade-offs did you make? » What security risks should I be aware of? That ensures you're looped in on the important decisions. One of the [habits of Diligence](#habits-of-diligence-habitudes-de-la-diligence).

→ [schéma des habitudes de la Diligence](mindmap/diligence-habits.png)

### Transparency *(Transparence)*

Tell people AI wrote it: being transparent about your AI use and disclosing it. When Claude writes most of a pull request, say so in the Description, not as a disclaimer, as information: AI makes a different shape of mistake than humans do (deprecated APIs used confidently, code that's locally clean but inconsistent with the codebase, invented behavior for cases you never specified), and a reviewer who knows that can better tailor their review. One of the [habits of Diligence](#habits-of-diligence-habitudes-de-la-diligence).

→ [schéma des habitudes de la Diligence](mindmap/diligence-habits.png)

### Understanding *(Compréhension)*

Consciously understand how the code works. It's easy to feel out of your depth when AI does the building: you can end up with working code you don't understand, which wasn't really possible before. It's not that you can't understand it: it's just a separate step now, and AI can help with that too. Claude is more than happy to sit with you and patiently explain; it takes a bit of time, but that's what puts you back in the loop. One of the [habits of Diligence](#habits-of-diligence-habitudes-de-la-diligence).

→ [schéma des habitudes de la Diligence](mindmap/diligence-habits.png)

### Safety nets *(Filets de sécurité)*

What lets you move fast safely. The engineering best practices that existed before AI still apply after, maybe even more so: now you're shipping faster, and you understand a smaller fraction of what you shipped. Tests on one end: still the easiest way to make sure you don't break something while moving this fast; a solid test suite pins down the behavior you care about, so you can keep iterating without fear. Tests become your safety net the moment something is live: they make post-launch iteration safe, and the test-first habit is why you can keep changing things confidently (see [acceptance tests](#acceptance-test-test-dacceptation)). [Observability](#observability-observabilité) on the other end. With the [habits of Diligence](#habits-of-diligence-habitudes-de-la-diligence).

→ [schéma des habitudes de la Diligence](mindmap/diligence-habits.png)

### Observability *(Observabilité)*

Some things only show up when real users have it: so you want logs, error tracking, dashboards. You find out from your own data, not from a user email. And feature flags remain useful for when something does slip through. With tests, one of the [safety nets](#safety-nets-filets-de-sécurité).

→ [schéma des habitudes de la Diligence](mindmap/diligence-habits.png)
