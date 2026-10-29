---
tags: [ia, anthropic, ai-fluency, glossaire]
created: 2026-10-24
updated: 2026-10-27
---
# Glossaire et mindmap Anthropic

Glossaire du cours Anthropic « AI Capabilities and Limitations » (Claude Certification, Developer Foundation) et de son annexe « AI Fluency Framework: Capabilities & Limitations ». Définitions en anglais, résumées du cours ; traduction française entre parenthèses, vérifiée sur des sources françaises de l'IA et de l'informatique (documentation des éditeurs, terminologie officielle, recherche).

Schémas, avec un sommaire et une légende pour chacun : [mindmap.md](mindmap.md).

---

## Glossaire

### AI Fluency *(AI Fluency)*

Fluent AI use: it isn't about memorizing every failure mode, it's about holding a small, clear model of the machine in your head ([mental model](#mental-model-modèle-mental)), so that when something goes wrong you can recognize which kind of wrong it is and respond accordingly. The Framework for AI Fluency (Dakan & Feller, 2025), the 4D Framework, describes the [human competencies](#human-competencies-compétences-humaines) you need to collaborate well with AI; this course's framework, the AI Capabilities & Limitations Framework, describes the machine properties those competencies are responding to ([AI properties](#ai-properties-propriétés-de-lia)). Its true essence: you don't trust the AI, but you don't distrust it either; you locate the task, and you set your habits accordingly ([calibrated trust](#calibrated-trust-confiance-calibrée)). Being honest about AI's role in your work, checking what it gives you, standing behind what you ship: that's all part of AI fluency.

→ [schéma des 4D](mindmap/four-properties.png)

### Mental model *(Modèle mental)*

What the course builds: a working mental model of the machine, of where AI outputs actually come from. Four [AI properties](#ai-properties-propriétés-de-lia) as continuums, characteristic failures as property intersections (a [hallucinated citation](#hallucination-hallucination), [long-conversation drift](#long-conversation-drift-dérive-au-fil-dune-longue-conversation)), and the training fingerprints: [pre-training](#pre-training-préentraînement) builds a document completer, [fine-tuning](#fine-tuning-réglage-fin) layers an assistant on top. The goal isn't to catalogue every possible error: it's a model that makes AI behavior predictable rather than surprising, clear enough that when something goes wrong you can recognize which kind of wrong it is, locate where on the continuum you've drifted, and respond accordingly ([calibrated trust](#calibrated-trust-confiance-calibrée)); a structure that lets you answer the next "Why does it do that?" yourself. Durable on purpose: it survives daily product updates and model releases, because the properties stay stable as models improve, only their boundaries shift. The model in your head gets sharper the more you test it against actual output: pay attention to where your predictions about AI behavior are right and where they're off. Part of [AI Fluency](#ai-fluency-ai-fluency).

→ [schéma des 4D](mindmap/four-properties.png)

### Human competencies *(Compétences humaines)*

The four skills of the AI Fluency Framework (the 4Ds) a person needs to collaborate well with AI: [Delegation](#delegation-délégation), [Description](#description-description), [Discernment](#discernment-discernement) and [Diligence](#diligence-diligence). They are the human side of one system; the [AI properties](#ai-properties-propriétés-de-lia) are the machine side. The two frameworks aren't separate things you have to juggle: the 4Ds are what you do, the four properties are what you're responding to when you do them. Two halves of one system, opposite sides of the same coin: the machine layer sharpens the human layer. Part of [AI Fluency](#ai-fluency-ai-fluency).

→ [schéma des 4D](mindmap/four-properties.png)

### Delegation *(Délégation)*

Deciding which work to hand to AI and which to keep. You can't delegate well without knowing where the model is strong and where it's weak; understanding the [context window](#context-window-fenêtre-de-contexte) changes how you delegate long tasks. Tasks deep in the [capability zone](#capability-zone-and-limitation-zone-zone-de-compétence-et-zone-des-limites) are safer handoffs; tasks near the edge deserve more of your attention on the back end. [Knowledge](#knowledge-connaissances) unevenness is core to Delegation: where the model is well-stocked versus thin tells you when to hand off, when to supply context yourself (context, documents, search), and when to go elsewhere. Tasks that need long reasoning chains or native numeric precision need either tighter human checkpoints or a different tool entirely ([steerability](#steerability-pilotabilité)). The same compound failure on the same kind of task is signal: it tells you which task types to restructure, which to break into smaller pieces, which to keep for yourself; the patterns you diagnose today shape how you delegate tomorrow. On the course slide, it faces [Steerability](#steerability-pilotabilité): understanding steerability makes you better at Delegation, because you know where control is high, and where it's less precise. One of the [human competencies](#human-competencies-compétences-humaines).

→ [schéma des 4D](mindmap/four-properties.png)

### Description *(Description)*

Telling AI clearly what you want: the goal, the expected output, the way to get there. Understanding that AI is a prediction engine ([next token prediction](#next-token-prediction-prédiction-du-token-suivant)) changes how you describe tasks to it. On the course slide, it faces [Working memory](#working-memory-mémoire-de-travail): working memory is what Description acts on, the mechanism that makes it work. Understanding working memory makes you better at Description, because you know context is leverage, and you stop assuming the model remembers everything. Everything you describe to an AI (your instructions, your constraints, your examples) has to live inside the [context window](#context-window-fenêtre-de-contexte) to have any effect; the window's size, its edges and its reset behavior tell you how to structure a prompt, when to restate critical context, and what's worth uploading. [Steerability](#steerability-pilotabilité) is what makes Description powerful and what bounds it (both the thing Description exploits and the constraint it operates inside): good Description narrows the gap between your words and your intent, and understanding that gap changes how you write prompts and where you insert checkpoints. One of the [human competencies](#human-competencies-compétences-humaines).

→ [schéma des 4D](mindmap/four-properties.png)

### Discernment *(Discernement)*

Judging the quality of what AI gives back. You can't assess an output without some picture of how it was produced and what to look out for. On the course slide, it faces [Next token prediction](#next-token-prediction-prédiction-du-token-suivant), its foundation: knowing the output was generated tells you exactly what kind of scrutiny to apply. Understanding next token prediction makes you better at Discernment, because you know that fluency and accuracy are independent variables. [Knowledge](#knowledge-connaissances) shapes it too: anything in the model's weak zone (recent, rare or local) warrants a second look. Diagnosing which [AI properties](#ai-properties-propriétés-de-lia) meet in a failure is Discernment applied: naming the property level failure turns vague dissatisfaction ("That wasn't quite right") into a targeted iteration ("I need to reground this in a source," "I need to invite pushback"); you evaluate better when you know what kind of wrong you're looking at. One of the [human competencies](#human-competencies-compétences-humaines).

→ [schéma des 4D](mindmap/four-properties.png)

### Diligence *(Diligence)*

Taking responsibility for AI-assisted work: being honest about AI's role in it, checking what AI gives you, standing behind what you ship. On the course slide, it faces [Knowledge](#knowledge-connaissances). One of the [human competencies](#human-competencies-compétences-humaines).

→ [schéma des 4D](mindmap/four-properties.png)

### Generative AI *(IA générative)*

AI that produces new content (text, images, code, audio, video) rather than classifying existing content. Most AI in the world isn't generative: spam filters, recommendations, fraud detection sort, rank, classify and predict. Generative AI is created in two stages, [pre-training](#pre-training-préentraînement) then [fine-tuning](#fine-tuning-réglage-fin): pretraining builds a document completer, fine-tuning layers an assistant on top, and every behavior you see, helpful or strange, traces back to one of those two fingerprints. At its core it is a prediction system ([next token prediction](#next-token-prediction-prédiction-du-token-suivant)). The course is about the transformer-based text models that produce new content one token at a time; much of its framework transfers to other kinds of generative AI. It isn't uniformly capable or uniformly unreliable: it is strong and weak along the four [AI properties](#ai-properties-propriétés-de-lia).

→ [schéma des 4D](mindmap/four-properties.png)

### Pre-training *(Préentraînement)*

The first stage that creates [generative AI](#generative-ai-ia-générative): the model is exposed to vast quantities of text and trained on a single task, predicting what comes next ([next token prediction](#next-token-prediction-prédiction-du-token-suivant)). What emerges isn't an assistant but a document completer: it continues a text in whatever direction seems statistically likely, with no concept of you and no concept of helping. Type "What is the capital of France?" and a raw, pre-trained model doesn't answer your question: it continues your document, maybe with more capital questions, because it has seen that pattern in quizzes. [Fine-tuning](#fine-tuning-réglage-fin) turns it into an assistant.

→ [schéma de la personnalité de l'IA](mindmap/ai-character.png)

### Fine-tuning *(Réglage fin)*

The second stage that creates [generative AI](#generative-ai-ia-générative): the document completer from [pre-training](#pre-training-préentraînement) is trained again to be broadly safe, ethical and helpful, first on curated examples of good assistant behavior, then with reward signals toward good, safe responses most people prefer. It learns to treat your input as a request, to answer rather than ramble, to decline harmful asks, to say "I'm not sure" when it isn't. That's where it picks up the habit of breaking tasks into steps and following the rules you set; format and length instructions are exactly what fine-tuning optimized for. The assistant behavior is a trained overlay on top of the document completer, shaped by human judgments; it is what makes the model steerable ([steerability](#steerability-pilotabilité)) and what makes generative AI usable and useful. Because it relies on human judgments about what good looks like, those judgments leave fingerprints on the models' personalities: the [shadow areas of AI's helpfulness](#shadow-areas-of-ais-helpfulness-la-part-dombre-dune-ia-serviable).

→ [schéma de la personnalité de l'IA](mindmap/ai-character.png)

### Shadow areas of AI's helpfulness *(La part d'ombre d'une IA serviable)*

The four fingerprints [fine-tuning](#fine-tuning-réglage-fin) leaves on an AI's personality, because it relies on human judgments about good responses: [sycophancy](#sycophancy-complaisance), [verbosity](#verbosity-verbosité), [over-caution](#over-caution-excès-de-prudence) and [loose confidence calibration](#loose-confidence-calibration-mauvaise-calibration-de-la-confiance). The same personality traits are often what make [generative AI](#generative-ai-ia-générative) so effective. They aren't bugs in one particular model: they show up in all AI models, and the quality and type of fine-tuning shapes how they manifest, likely differently from model to model. The behavior was built layer by layer, and sometimes the seams show: learning to spot them is part of using AI well.

→ [schéma de la personnalité de l'IA](mindmap/ai-character.png)

### Sycophancy *(Complaisance)*

When people prefer agreeable responses, the model learns to validate readily and back down under light pushback, even when it was right the first time. If your AI assistant caves the moment you push back, that's sycophancy: factor it in when assessing responses. This trained disposition meets [next token prediction](#next-token-prediction-prédiction-du-token-suivant) in agreeing with a [bad premise](#agreeable-bad-premises-prémisses-erronées-acceptées) (in the PDF annex; continuing your framing rather than challenging it). Listed with [hallucination](#hallucination-hallucination) among output quality problems. One of the [shadow areas of AI's helpfulness](#shadow-areas-of-ais-helpfulness-la-part-dombre-dune-ia-serviable).

→ [schéma de la personnalité de l'IA](mindmap/ai-character.png)

### Verbosity *(Verbosité)*

When thoroughness scores better during training, the model defaults to longer answers, even when brevity could serve you better for a specific situation. Getting essays when you want bullets is the verbosity default kicking in. One of the [shadow areas of AI's helpfulness](#shadow-areas-of-ais-helpfulness-la-part-dombre-dune-ia-serviable).

→ [schéma de la personnalité de l'IA](mindmap/ai-character.png)

### Over-caution *(Excès de prudence)*

When safety training leans conservative, the model can hedge heavily or refuse requests that are actually safe. Getting heavy caveats on a harmless question is over-caution. One of the [shadow areas of AI's helpfulness](#shadow-areas-of-ais-helpfulness-la-part-dombre-dune-ia-serviable).

→ [schéma de la personnalité de l'IA](mindmap/ai-character.png)

### Loose confidence calibration *(Mauvaise calibration de la confiance)*

The model's stated confidence is only loosely tied to its actual reliability. Confidence is genuinely hard to train, so it's particularly important to be vigilant here. Not the same as [calibrated trust](#calibrated-trust-confiance-calibrée) (locating your task on the continuum). One of the [shadow areas of AI's helpfulness](#shadow-areas-of-ais-helpfulness-la-part-dombre-dune-ia-serviable).

→ [schéma de la personnalité de l'IA](mindmap/ai-character.png)

### AI properties *(Propriétés de l'IA)*

The four core properties of [generative AI](#generative-ai-ia-générative): [next token prediction](#next-token-prediction-prédiction-du-token-suivant), [knowledge](#knowledge-connaissances), [working memory](#working-memory-mémoire-de-travail) and [steerability](#steerability-pilotabilité). The AI Capabilities & Limitations Framework: four properties that shape what AI can and can't do for you. The machine side of the system the [human competencies](#human-competencies-compétences-humaines) respond to. Each is a continuum with a [capability zone](#capability-zone-and-limitation-zone-zone-de-compétence-et-zone-des-limites), a limitation zone, and [product features](#product-features-fonctionnalités-produit) that push the edge further out; the same mechanism is always running, the only thing that changes is where your task lands on the line. The properties stay stable as models improve, only their boundaries shift: the specific numbers will change, the exact location of each edge will shift, but the shape of these properties holds. AI will keep being a predictor whose fluency may run ahead of its accuracy, keep having uneven knowledge with a cutoff, keep working inside a finite window, keep following your instructions despite a gap between words and intent. They don't operate in isolation: most real-world failures are two properties meeting at the same time ([hallucinated citations](#hallucination-hallucination), [agreeable bad premises](#agreeable-bad-premises-prémisses-erronées-acceptées), [stale context vs. trained knowledge](#stale-context-vs-trained-knowledge-contexte-obsolète-contre-connaissances-acquises-à-lentraînement), [confidently wrong reasoning](#confidently-wrong-reasoning-raisonnement-faux-mené-avec-assurance), [long-conversation drift](#long-conversation-drift-dérive-au-fil-dune-longue-conversation)), and once you can name which two, you know which fix to reach for: that's how you diagnose and adjust, not "What broke?" but "Which two things collided?". Ask which properties you're looking at with the task even before starting the conversation: the diagnosis determines the fix (a knowledge problem and a working memory problem can produce outputs that look similar on the surface, but they need completely different responses). On the course's collision diagram: next token prediction generates what sounds right, knowledge knows what it was trained on, working memory attends to what's nearby, steerability follows the loudest instruction.

→ [schéma des 4D](mindmap/four-properties.png)

### Steerability *(Pilotabilité)*

How much control your instructions give you: the model's ability to follow your directions. Specify a role, a tone, a format, a word limit, a set of rules, and the model applies them, often on the first try. [Fine-tuning](#fine-tuning-réglage-fin) makes the model follow a role, a tone, a format, rules; but steerability isn't the same as understanding: it follows them by continuing a pattern, via [next token prediction](#next-token-prediction-prédiction-du-token-suivant), the same pattern completion engine it uses for everything else. There's always a gap between the words you typed and the intent you had in mind, and most of the interesting failures live in that gap: the question to ask isn't "Did I write a good prompt?" but "How much room is there between what I typed and what I actually want?". Control is highest with short, concrete, verifiable instructions (format specs, length limits, explicit roles: the [capability zone](#capability-zone-and-limitation-zone-zone-de-compétence-et-zone-des-limites)) and degrades with long chains of reasoning, abstract or ambiguous instructions, or tasks needing native numerical or logical precision (arithmetic, formal logic). It enables precise control over format, style, length and tone, role-setting (a persona held across a whole conversation), multi-step task execution following a clear process, and iterative refinement ("make it shorter," "more specific here"); it characteristically fails in [reasoning drift](#reasoning-drift-dérive-du-raisonnement), [letter over spirit](#letter-over-spirit-la-lettre-plutôt-que-lesprit) and [prompt injection](#prompt-injection-injection-de-prompt) (the lesson's objectives also name brittle arithmetic). [Product features](#product-features-fonctionnalités-produit) (system prompts and custom instructions, code execution, visible reasoning, structured output modes) keep your intent from diluting. To stay in the capability zone: state the goal alongside the steps, break long chains with checkpoints, restate the goal rather than the instruction when one lands literally but uselessly (repeating it with more force won't close the gap), and keep concrete, verifiable instructions near the task (short and checkable beats long and ambiguous). What makes [Description](#description-description) powerful and what bounds it; it shapes [Delegation](#delegation-délégation) too. Meets [working memory](#working-memory-mémoire-de-travail) in [long-conversation drift](#long-conversation-drift-dérive-au-fil-dune-longue-conversation) (it follows whatever instructions are most salient now), [next token prediction](#next-token-prediction-prédiction-du-token-suivant) in [confidently wrong reasoning](#confidently-wrong-reasoning-raisonnement-faux-mené-avec-assurance), and [knowledge](#knowledge-connaissances) in [agreeable bad premises](#agreeable-bad-premises-prémisses-erronées-acceptées) (it defaults to following your framing, especially if you sound confident). One of the [AI properties](#ai-properties-propriétés-de-lia).

→ [schéma de la pilotabilité](mindmap/steerability.png)

### Working memory *(Mémoire de travail)*

What the AI is paying attention to right now: the AI model has a fixed [context window](#context-window-fenêtre-de-contexte) that it can attend to (your instructions, its prior responses, the documents you uploaded, the conversation), and nothing outside it; a lot like how working memory functions in humans. The window has a hard size limit and, by default, empties between sessions: a new chat starts from zero, unless a product feature, like memory or a CLAUDE.md file, has deliberately carried something forward. A continuum like the other properties: when your material fits comfortably, the session is current and you're supplying relevant context, you're in the [capability zone](#capability-zone-and-limitation-zone-zone-de-compétence-et-zone-des-limites); very long documents or conversations, expecting continuity across sessions, or burying critical info in the middle of long input slide toward the limitation zone. The property with the hardest edge: a cliff rather than a gradient (next token prediction degrades gradually, knowledge gets thinner gradually; working memory works right up until it doesn't). In the capability zone, context is leverage: rapid in-session adaptation (style guides, samples apply immediately, with no retraining), work with your material (your docs, your constraints), precision through specificity (the more relevant context you supply, the more tailored the output). It characteristically fails in [silent truncation](#silent-truncation-troncature-silencieuse) (hard length limits), [lost in the middle](#lost-in-the-middle-perte-au-milieu), no persistent memory by default (each session starts from zero) and no learning from you (corrections don't change the model, only the context: it only responds to what's currently in context). [Product features](#product-features-fonctionnalités-produit) (memory, compaction, projects, skills, multi-agent workflows, larger context windows) push the cliff further out. Signs you're approaching the edge: a very long conversation where quality has started to slip, a very long document where details from the middle aren't showing up, expecting the model to recall a prior session without a memory feature. To stay on the good side of the cliff: lead with what matters, chunk long work into passes, use features that save your context, and start fresh when quality degrades over a long conversation (often a context limit rather than a capability limit). What [Description](#description-description) acts on. Meets [steerability](#steerability-pilotabilité) in [long-conversation drift](#long-conversation-drift-dérive-au-fil-dune-longue-conversation), and [knowledge](#knowledge-connaissances) in [stale context vs. trained knowledge](#stale-context-vs-trained-knowledge-contexte-obsolète-contre-connaissances-acquises-à-lentraînement). One of the [AI properties](#ai-properties-propriétés-de-lia).

→ [schéma de la mémoire de travail](mindmap/working-memory.png)

### Next token prediction *(Prédiction du token suivant)*

Where AI answers come from: given everything written so far, the model predicts what comes next, one fragment at a time, [sampling](#sampling-échantillonnage) each new word. It writes an answer word by word, based on what tends to follow what, rather than looking one up: closer to a vastly sophisticated autocomplete than to a search engine. Familiar tasks (well-worn paths: summarize, reformat, explain common concepts) sit in the [capability zone](#capability-zone-and-limitation-zone-zone-de-compétence-et-zone-des-limites); novel or sparse ones, or telling a true fact from a plausible one, drift toward the edge. That single property gives both the fluency and the hallucination: it enables fluent text in virtually any style, rapid synthesis across distant fields, strong performance on tasks resembling what the model has seen, coherent continuation of any thread; it characteristically fails in [hallucination](#hallucination-hallucination), [confabulation](#confabulation-confabulation), [inconsistency](#inconsistency-variabilité-des-réponses) and [misplaced confidence](#misplaced-confidence-excès-de-confiance). Fabrication concentrates in specificity (names, dates, statistics, citations, URLs, quotes): the more precise a claim, the more it warrants verification; treat outputs as drafts to verify. [Product features](#product-features-fonctionnalités-produit) push this limitation further out. The foundation of [Discernment](#discernment-discernement). Generating what looks plausible over a [gap](#gap-lacune) in [knowledge](#knowledge-connaissances) gives a [hallucination](#hallucination-hallucination). Meets [steerability](#steerability-pilotabilité) in [confidently wrong reasoning](#confidently-wrong-reasoning-raisonnement-faux-mené-avec-assurance), and, in the PDF annex, [sycophancy](#sycophancy-complaisance) in agreeing with a [bad premise](#agreeable-bad-premises-prémisses-erronées-acceptées). One of the [AI properties](#ai-properties-propriétés-de-lia).

→ [schéma de la prédiction du token suivant](mindmap/next-token-prediction.png)

### Knowledge *(Connaissances)*

What the model learned from its training text, and the only way it knows things: through billions of rounds of "what comes next?", it builds internal representations of concepts, relationships and facts. It knows what it was exposed to during training, and only that: no real-time browsing by default, no lived experience, and a hard stop at the [knowledge cutoff](#knowledge-cutoff-date-limite-des-connaissances). Uneven in a predictable way: topics that appeared frequently, recently (within training) and consistently (mainstream topics, popular languages) sit in the [capability zone](#capability-zone-and-limitation-zone-zone-de-compétence-et-zone-des-limites); rare, post-cutoff, niche, local or contested ones drift toward the edge. The question to ask isn't "does the AI know this?" but "how well-represented was this in what it read?". It enables extraordinarily broad general knowledge, deep competence in well-represented domains, and connections across fields ([embeddings](#embeddings-embeddings)); it characteristically fails in [knowledge cutoff](#knowledge-cutoff-date-limite-des-connaissances), [staleness](#staleness-obsolescence-des-connaissances), [uneven coverage](#uneven-coverage-couverture-inégale), [inherited bias](#inherited-bias-biais-hérité) and [source amnesia](#source-amnesia-amnésie-de-la-source). Where it runs out, there is a [gap](#gap-lacune). [Product features](#product-features-fonctionnalités-produit) (web search, retrieval, tool use) patch these gaps by giving the model access to information it was never trained on. Core to [Delegation](#delegation-délégation); it also shapes [Discernment](#discernment-discernement). Broad, deep, frozen and imperfect all at once. Meets [next token prediction](#next-token-prediction-prédiction-du-token-suivant) in [hallucinated citations](#hallucination-hallucination), [steerability](#steerability-pilotabilité) in [agreeable bad premises](#agreeable-bad-premises-prémisses-erronées-acceptées), and [working memory](#working-memory-mémoire-de-travail) in [stale context vs. trained knowledge](#stale-context-vs-trained-knowledge-contexte-obsolète-contre-connaissances-acquises-à-lentraînement). One of the [AI properties](#ai-properties-propriétés-de-lia).

→ [schéma des connaissances](mindmap/knowledge.png)

### Capability zone and limitation zone *(Zone de compétence et zone des limites)*

The two ends of the continuum each of the [AI properties](#ai-properties-propriétés-de-lia) sits on. The same mechanism gives both: an AI writes compellingly because it's a prediction engine, and [hallucinates](#hallucination-hallucination) for the same reason. What varies is where your task lands on that line; the further toward the limitation zone, the more you should verify and compensate. Boundaries shift as models improve; the properties stay the same. Keep testing the edges: the models get better, the context windows get bigger, features close gaps that used to be open; the edges move, and you find them by pushing on them. Locating your task on that line is [calibrated trust](#calibrated-trust-confiance-calibrée).

→ [schéma des 4D](mindmap/four-properties.png)

### Calibrated trust *(Confiance calibrée)*

Locating your task on the continuum of each of the [AI properties](#ai-properties-propriétés-de-lia), from [capability zone to limitation zone](#capability-zone-and-limitation-zone-zone-de-compétence-et-zone-des-limites), rather than granting or withholding trust wholesale. The goal is neither to distrust AI nor to [delegate](#delegation-délégation) all your tasks to it. Its questions: is this well-trodden territory, or am I out near an edge? What are the stakes if I'm wrong? It gets talked about like an attitude, but it's actually a habit: locating your task on each continuum and matching your verification and context habits to where it sits. Before you hand something to an AI, you run a quick internal check: is this well-worn territory or sparse? Is this topic recent or stable? Does your material fit comfortably inside the window? Are your instructions concrete, or is there room between your words and your intent? And then you adjust: more verification, where fabrication can concentrate; more context, where the model can't guess what you mean; more checkpoints, when reasoning chains run too long; and you look for features that can help you extend the capabilities of the models ([product features](#product-features-fonctionnalités-produit)). You don't trust the AI, but you don't distrust it either: you locate the task, and you set your habits accordingly. That's the true essence of [AI Fluency](#ai-fluency-ai-fluency).

→ [schéma de la confiance calibrée](mindmap/calibrated-trust.png) · [schéma des 4D](mindmap/four-properties.png)

### Context window *(Fenêtre de contexte)*

The fixed-size workspace of [working memory](#working-memory-mémoire-de-travail): your instructions, uploaded documents, the system's prior responses and the running dialogue, any other info you've shared; one finite container, and the model can only attend to what's inside. Fixed because the model processes your entire context as a single block every time it generates a response, reading all of it, start to finish, to decide what to write next: there's a ceiling on how much it can hold and still produce a coherent reply. Even inside that ceiling, attention isn't uniform ([lost in the middle](#lost-in-the-middle-perte-au-milieu)). When a conversation or a document exceeds it, something falls off the edge, usually the oldest material, usually silently ([silent truncation](#silent-truncation-troncature-silencieuse)); in a long conversation, early context fades, which leads to [drift](#long-conversation-drift-dérive-au-fil-dune-longue-conversation). By default, it empties between sessions. Larger context windows push the cliff further out ([product features](#product-features-fonctionnalités-produit)).

→ [schéma de la mémoire de travail](mindmap/working-memory.png)

### Gap *(Lacune)*

A hole in the model's [knowledge](#knowledge-connaissances) that the model doesn't know is there. Met by [next token prediction](#next-token-prediction-prédiction-du-token-suivant), it leads to [hallucination](#hallucination-hallucination). Generative AI models have predictable knowledge gaps, most likely when the topic is time sensitive, the domain is niche, local or in a less-represented language, the question postdates the [knowledge cutoff](#knowledge-cutoff-date-limite-des-connaissances), you rely on the model's sense of typical or normal, or web search is turned off. [Product features](#product-features-fonctionnalités-produit) such as search and retrieval are there specifically to patch them.

→ [schéma des 4D](mindmap/four-properties.png)

### Sampling *(Échantillonnage)*

The act of picking a next word based on what you have so far, from a probability distribution of what comes next: the same term for a [Markov chain](#markov-chain-chaîne-de-markov) and for modern language models like Claude. In [next token prediction](#next-token-prediction-prédiction-du-token-suivant), each new word is sampled from a distribution shaped by everything the model learned in training. Because of it, the same prompt can yield different outputs: [inconsistency](#inconsistency-variabilité-des-réponses). Developers improve it with [sampling parameters](#sampling-parameters-paramètres-déchantillonnage).

→ [schéma de la prédiction du token suivant](mindmap/next-token-prediction.png)

### Sampling parameters *(Paramètres d'échantillonnage)*

Parameters developers use to improve [sampling](#sampling-échantillonnage) after the probabilities are generated: more or less the same sampling constraints developers pass to Claude. Temperature runs from focused to random. Tail trimming removes unlikely words entirely before sampling (top-k, top-p).

→ [schéma de la prédiction du token suivant](mindmap/next-token-prediction.png)

### Markov chain *(Chaîne de Markov)*

The 100% interpretable next-token generator, "trained" by tallying the connections between words. The finished map of connections between words is called a frequency table (the transition matrix); normalize each row and you get a probability distribution of what comes next. It reads the last word as context and looks up one row in the table; an LLM reads the entire conversation so far and runs a forward pass through billions of parameters. The output is the same, a probability distribution of likely next words or tokens, and [sampling](#sampling-échantillonnage) is the same; training is radically different. LLMs trade the explainability of tallying words for far more context and far greater capabilities. Markov published the idea in 1906; by 2010, n-gram models like it powered next-word prediction on phones, before neural networks replaced the table lookup with a learned function.

→ [schéma de la prédiction du token suivant](mindmap/next-token-prediction.png)

### Confabulation *(Confabulation)*

The model fills gaps with plausible material rather than flagging them. One of the characteristic failures of [next token prediction](#next-token-prediction-prédiction-du-token-suivant), with [hallucination](#hallucination-hallucination), [inconsistency](#inconsistency-variabilité-des-réponses) and [misplaced confidence](#misplaced-confidence-excès-de-confiance).

→ [schéma de la prédiction du token suivant](mindmap/next-token-prediction.png)

### Inconsistency *(Variabilité des réponses)*

[Sampling](#sampling-échantillonnage) means the same prompt can yield different outputs. One of the characteristic failures of [next token prediction](#next-token-prediction-prédiction-du-token-suivant), with [hallucination](#hallucination-hallucination), [confabulation](#confabulation-confabulation) and [misplaced confidence](#misplaced-confidence-excès-de-confiance).

→ [schéma de la prédiction du token suivant](mindmap/next-token-prediction.png)

### Misplaced confidence *(Excès de confiance)*

Smooth prose can wrap a guess: a confident tone does not signal accuracy; smoothness and correctness are independent variables. One of the characteristic failures of [next token prediction](#next-token-prediction-prédiction-du-token-suivant), with [hallucination](#hallucination-hallucination), [confabulation](#confabulation-confabulation) and [inconsistency](#inconsistency-variabilité-des-réponses).

→ [schéma de la prédiction du token suivant](mindmap/next-token-prediction.png)

### Product features *(Fonctionnalités produit)*

Features built into AI products to push the limitation of an AI property further out: each property's continuum has a capability zone, a limitation zone, and its product features. Part of [calibrated trust](#calibrated-trust-confiance-calibrée) is looking for features that can help you extend the capabilities of the models; features close gaps that used to be open. For [next token prediction](#next-token-prediction-prédiction-du-token-suivant), frontier labs built them because the underlying behavior is always generative next token prediction: citations and source grounding (trace what's backed vs. what's generated), trained uncertainty signaling (the model flags its own shakiness: "I'm not sure about this"), constrained generation and skills (narrow the space where fabrication can sneak in), generator-verifier loops (output meets checks from an outside source). The model can't reliably tell grounded from invented: if your tool offers citations or source grounding, use them. For [knowledge](#knowledge-connaissances), they patch its gaps by giving the model access to information it was never trained on: web search (current information at response time, working around the [knowledge cutoff](#knowledge-cutoff-date-limite-des-connaissances) for time-sensitive questions), retrieval (RAG) and MCPs (documents never trained on, like your company's wiki or a specialized database), tool use (real-time calculators, databases, APIs instead of absorbed patterns), explicit cutoff disclosure (you know what to double-check). Using them extends the model's knowledge at runtime; without them, you rely entirely on what it absorbed during training. For [working memory](#working-memory-mémoire-de-travail), products layer them on top of the raw [context window](#context-window-fenêtre-de-contexte) to soften its edges and push the cliff further out: memory (persists selected facts across sessions, so you're not starting from zero every time), compaction or summarization (condenses old turns of the conversation history to free room when a conversation runs long), projects and workspaces (standing documents reliably in context, without re-uploading), skills (keep instructions minimal until a specific task actually needs them), multi-agent workflows (multiple agents with different specialties and their own context windows, expanding the total amount of context the workflow can have), larger context windows. Use the features that save your context. For [steerability](#steerability-pilotabilité), they narrow the gap between your words and your intent and keep it from diluting: system prompts and custom instructions (standing directions that don't dilute as the conversation gets longer), code execution (offload math to an actual interpreter), visible reasoning (catch [drift](#reasoning-drift-dérive-du-raisonnement) at step two rather than discovering it in the final answer), structured output modes (JSON schemas, function calling: cut down on [letter-over-spirit](#letter-over-spirit-la-lettre-plutôt-que-lesprit) wandering).

→ [schéma de la prédiction du token suivant](mindmap/next-token-prediction.png) · [schéma des connaissances](mindmap/knowledge.png) · [schéma de la mémoire de travail](mindmap/working-memory.png) · [schéma de la pilotabilité](mindmap/steerability.png)

### Knowledge cutoff *(Date limite des connaissances)*

The date training ends: the model's knowledge was fixed at that moment, and everything that happened after it simply isn't there. Without tools, the model has no access to any information after that date. A question that postdates the cutoff is where a [gap](#gap-lacune) is most likely; web search works around the cutoff for time-sensitive questions, and explicit cutoff disclosure tells you what to double-check ([product features](#product-features-fonctionnalités-produit)). One of the characteristic failures of [knowledge](#knowledge-connaissances), with [staleness](#staleness-obsolescence-des-connaissances), [uneven coverage](#uneven-coverage-couverture-inégale), [inherited bias](#inherited-bias-biais-hérité) and [source amnesia](#source-amnesia-amnésie-de-la-source).

→ [schéma des connaissances](mindmap/knowledge.png)

### Staleness *(Obsolescence des connaissances)*

Information that was true at the time of training may have changed: true-at-training-time isn't true-now, and the model has no mechanism to know this. Verify anything time-sensitive (current events, recent research, who holds a position, what something costs) and assume the model may be out of date. One of the characteristic failures of [knowledge](#knowledge-connaissances), with [knowledge cutoff](#knowledge-cutoff-date-limite-des-connaissances), [uneven coverage](#uneven-coverage-couverture-inégale), [inherited bias](#inherited-bias-biais-hérité) and [source amnesia](#source-amnesia-amnésie-de-la-source).

→ [schéma des connaissances](mindmap/knowledge.png)

### Uneven coverage *(Couverture inégale)*

Frequent topics are handled well, rare topics poorly: minority languages, niche domains, local knowledge and recent developments suffer. Brilliance in one area doesn't transfer to the one next door: test before you trust in a new domain. One of the characteristic failures of [knowledge](#knowledge-connaissances), with [knowledge cutoff](#knowledge-cutoff-date-limite-des-connaissances), [staleness](#staleness-obsolescence-des-connaissances), [inherited bias](#inherited-bias-biais-hérité) and [source amnesia](#source-amnesia-amnésie-de-la-source).

→ [schéma des connaissances](mindmap/knowledge.png)

### Inherited bias *(Biais hérité)*

The model's sense of what's normal or default reflects its training data's blind spots: it shows up in assumptions about what a doctor looks like, what a family looks like, or what counts as a professional. Watch for default assumptions that reflect training data rather than reality. One of the characteristic failures of [knowledge](#knowledge-connaissances), with [knowledge cutoff](#knowledge-cutoff-date-limite-des-connaissances), [staleness](#staleness-obsolescence-des-connaissances), [uneven coverage](#uneven-coverage-couverture-inégale) and [source amnesia](#source-amnesia-amnésie-de-la-source).

→ [schéma des connaissances](mindmap/knowledge.png)

### Source amnesia *(Amnésie de la source)*

The model usually can't tell you where a piece of knowledge came from: "I read this somewhere" isn't a citation. One of the characteristic failures of [knowledge](#knowledge-connaissances), with [knowledge cutoff](#knowledge-cutoff-date-limite-des-connaissances), [staleness](#staleness-obsolescence-des-connaissances), [uneven coverage](#uneven-coverage-couverture-inégale) and [inherited bias](#inherited-bias-biais-hérité).

→ [schéma des connaissances](mindmap/knowledge.png)

### Embeddings *(Embeddings)*

Words and ideas mapped as points in a vast mathematical space where related concepts cluster together: the idea that meaning could be a place. Concepts that appear together in text end up near each other in the model's internal representation, which is how [knowledge](#knowledge-connaissances) makes connections across fields. An embedding model turns any string, three words or three paragraphs, into a single vector: a fixed-length list of numbers (real embedding models use around a thousand dimensions), the address where this text lives relative to everything else. This mapping of semantic space isn't manual but emergent from training data; so is the meaning of each dimension, which doesn't correspond to anything a human could name. [Similarity search](#similarity-search-recherche-de-similarité) is built on them.

→ [schéma des connaissances](mindmap/knowledge.png)

### Similarity search *(Recherche de similarité)*

Search by meaning rather than by string similarity: the question is mapped with the same logic as the documents, then the nearest k items, the most relevant, are retrieved. Multi-dimensional proximity replaces keyword matching and synonym tables; in practice, nearness is measured with [cosine similarity](#cosine-similarity-similarité-cosinus) rather than straight-line distance. Built on [embeddings](#embeddings-embeddings).

→ [schéma des connaissances](mindmap/knowledge.png)

### Cosine similarity *(Similarité cosinus)*

A measure of how similar two pieces of text are, based on the direction their vectors point rather than how far apart they sit: from -1 (opposite) through 0 (unrelated) to 1 (identical). What [similarity search](#similarity-search-recherche-de-similarité) uses in practice instead of straight-line distance.

→ [schéma des connaissances](mindmap/knowledge.png)

### Silent truncation *(Troncature silencieuse)*

The failure mode of the context window's hard size limit: once a conversation or a set of documents exceeds what the [context window](#context-window-fenêtre-de-contexte) can hold, something falls off, usually the oldest material, and usually silently. The model doesn't stop and announce that it dropped your first messages; it just keeps going with whatever's left. You won't always be warned: things work until they don't. One of the characteristic failures of [working memory](#working-memory-mémoire-de-travail), with [lost in the middle](#lost-in-the-middle-perte-au-milieu), no persistent memory by default and no learning from you. Larger context windows push the cliff further out ([product features](#product-features-fonctionnalités-produit)).

→ [schéma de la mémoire de travail](mindmap/working-memory.png)

### Lost in the middle *(Perte au milieu)*

Attention isn't uniform across the [context window](#context-window-fenêtre-de-contexte): research on long context behavior found a lost-in-the-middle effect, where material buried deep in the middle of a very long input tends to carry less weight than material at the beginning or the end. Large language models exhibit the same pattern as the [serial position effect](#serial-position-effect-effet-de-position-sérielle): in 2023, researchers at Stanford found accuracy highest when a key fact appeared at the very beginning or very end of a long context window, and down by more than 30% when it was buried in the middle. Structural, not a quirk: transformer attention patterns naturally weight the edges of the context window more heavily. Put your most important instructions at the beginning and end of the context; a constraint that absolutely must be followed: state it early in the system prompt and restate it near the end. Every piece of context you add pushes other pieces further into the middle, the attention dead zone: [context degradation](#context-degradation-dégradation-du-contexte). One of the characteristic failures of [working memory](#working-memory-mémoire-de-travail), with [silent truncation](#silent-truncation-troncature-silencieuse), no persistent memory by default and no learning from you.

→ [schéma de la mémoire de travail](mindmap/working-memory.png)

### Serial position effect *(Effet de position sérielle)*

A pattern of human memory that psychologists have studied for over a century: items at the beginning of a list benefit from primacy (they get rehearsed more), and items at the end benefit from recency (they're still fresh); the middle gets neither advantage. Recall follows a U-shaped curve. Large language models exhibit the same pattern: [lost in the middle](#lost-in-the-middle-perte-au-milieu).

→ [schéma de la mémoire de travail](mindmap/working-memory.png)

### Context degradation *(Dégradation du contexte)*

When more context makes things worse: the reason "just give it more context" is not always the answer. Every piece of context you add pushes other pieces further into the middle, the attention dead zone ([lost in the middle](#lost-in-the-middle-perte-au-milieu)). More context ≠ better results: the model's attention is finite. Curate ruthlessly, place strategically, and repeat what matters. The core tension of [context engineering](#context-engineering-ingénierie-du-contexte).

→ [schéma de la mémoire de travail](mindmap/working-memory.png)

### Context engineering *(Ingénierie du contexte)*

Structuring context so the model reliably understands what matters. Its core tension: not just what to include, but where to put it and what to leave out; leveraging where in the window information sits, what to include versus cut, and how to keep critical instructions from sliding into the dead zone ([context degradation](#context-degradation-dégradation-du-contexte)). The goal is always the same: make it obvious to Claude what you actually need.

→ [schéma de la mémoire de travail](mindmap/working-memory.png)

### Reasoning drift *(Dérive du raisonnement)*

Small errors compound over long chains of reasoning, and the model doesn't notice: a small mistake in step two quietly carries through steps three, four and five. A characteristic failure of [steerability](#steerability-pilotabilité), in its limitation zone (long chains of reasoning). Visible reasoning ([product features](#product-features-fonctionnalités-produit)) lets you catch drift at step two rather than discovering it in the final answer; break long chains with checkpoints: ask for an intermediate result you can verify before the model keeps going. See also [long-conversation drift](#long-conversation-drift-dérive-au-fil-dune-longue-conversation), where working memory meets steerability, and [confidently wrong reasoning](#confidently-wrong-reasoning-raisonnement-faux-mené-avec-assurance), where small errors compound under a confident tone.

→ [schéma de la pilotabilité](mindmap/steerability.png)

### Letter over spirit *(La lettre plutôt que l'esprit)*

The instruction is satisfied literally, but the intent is missed: honored literally but uselessly. The model honored what was said and missed what was meant: instructions are honored via pattern-matching, not understanding, and there's always room between your words and your intent. A characteristic failure of [steerability](#steerability-pilotabilité) (on the course slide: "Literal over nuanced"). Structured output modes ([product features](#product-features-fonctionnalités-produit)) cut down on letter-over-spirit wandering. When an instruction is followed literally but uselessly, restate the goal rather than the instruction: repeating it with more force won't close the gap (repeating "Be concise" louder doesn't fix a concision problem that was really an intent problem).

→ [schéma de la pilotabilité](mindmap/steerability.png)

### Prompt injection *(Injection de prompt)*

Instructions as an attack surface: because the model follows instructions embedded in text, a malicious instruction hidden inside a document or web page can be followed too (unwanted or unsafe instructions in documents). A characteristic failure of [steerability](#steerability-pilotabilité): more of a security concern than a daily one, but worth knowing exists.

→ [schéma de la pilotabilité](mindmap/steerability.png)

### Hallucination *(Hallucination)*

A fluent, plausible-looking output that is false, such as a hallucinated citation: [next token prediction](#next-token-prediction-prédiction-du-token-suivant) (generating what looks plausible) meeting a [gap](#gap-lacune) in [knowledge](#knowledge-connaissances). The plausible continuation isn't always the true one: hallucination comes from next token prediction, the same property as fluency. In hallucinated citations, next token prediction generates citation-shaped text (plausible titles, real-sounding journals, names that fit the field) over a knowledge gap the model doesn't know is there: it can't tell the difference between what it knows and what it's fabricating. Fix: verify specifics independently, or use source grounding so the model retrieves real documents rather than generating citation-shaped text ([product features](#product-features-fonctionnalités-produit)). One of its characteristic failures, with [confabulation](#confabulation-confabulation), [inconsistency](#inconsistency-variabilité-des-réponses) and [misplaced confidence](#misplaced-confidence-excès-de-confiance).

→ [schéma des 4D](mindmap/four-properties.png) · [schéma des collisions](mindmap/collisions.png)

### Agreeable bad premises *(Prémisses erronées acceptées)*

Agreeing with a bad premise: [knowledge](#knowledge-connaissances) (it might "know" better) meeting [steerability](#steerability-pilotabilité) (it defaults to following your framing). You state something incorrect in your prompt; the model's knowledge might "know" better, but steerability defaults to following your framing, especially if you sound confident. Fix: explicitly invite pushback ("Tell me if my assumption is wrong."). The PDF annex gives another pair: the trained disposition, [sycophancy](#sycophancy-complaisance), meeting [next token prediction](#next-token-prediction-prédiction-du-token-suivant) (continuing your framing rather than challenging it).

→ [schéma des collisions](mindmap/collisions.png)

### Stale context vs. trained knowledge *(Contexte obsolète contre connaissances acquises à l'entraînement)*

Answers that blend your document with the model's training: [knowledge](#knowledge-connaissances) (what it learned in training) meeting [working memory](#working-memory-mémoire-de-travail) (the document you supplied). Your working memory supplies a document that contradicts what knowledge learned in training; the model may blend both, producing answers that are neither faithful to your source nor to its training. Fix: be explicit about which source takes priority ("Use only the attached document" or "Use your training.").

→ [schéma des collisions](mindmap/collisions.png)

### Confidently wrong reasoning *(Raisonnement faux mené avec assurance)*

Fluent, confident-sounding chains of logic that are wrong: [next token prediction](#next-token-prediction-prédiction-du-token-suivant) (it generates fluent, confident-sounding chains of logic) meeting [steerability](#steerability-pilotabilité) (it dutifully follows your complex prompt step by step). Small errors compound ([reasoning drift](#reasoning-drift-dérive-du-raisonnement)), and the confident tone never wavers. Fix: use visible reasoning to catch drift early, or offload precise steps to code execution ([product features](#product-features-fonctionnalités-produit)). The lesson's objectives and the PDF annex call it confidently wrong math: a fluent, assured calculation that is wrong, next token prediction (fluency decoupled from truth) meeting steerability (no native sense of quantity, just patterns over digits).

→ [schéma des collisions](mindmap/collisions.png)

### Long-conversation drift *(Dérive au fil d'une longue conversation)*

The model gradually stops following what was set early in a long conversation: [working memory](#working-memory-mémoire-de-travail) (early context fading from the [context window](#context-window-fenêtre-de-contexte)) meeting [steerability](#steerability-pilotabilité) (later instructions overwriting earlier ones). Your early constraints fade as the conversation grows, either pushed out of the window or just receiving less attention than what you said recently; steerability follows whatever instructions are most salient now, so later messages quietly overwrite the earlier ones: working memory fading while steerability takes new instructions too literally. Fix: re-supply critical context, or, if the conversation has gotten unwieldy, start fresh with the essentials up front.

→ [schéma des 4D](mindmap/four-properties.png) · [schéma des collisions](mindmap/collisions.png)
