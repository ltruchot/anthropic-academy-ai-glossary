---
tags: [ia, anthropic, claude, glossaire]
created: 2026-11-20
updated: 2026-11-20
---

# Glossaire et mindmap Anthropic

Glossaire du cours Anthropic « Introduction to agent skills » (Claude Certification, Developer Foundation). Il se suffit à lui-même : un terme que définit aussi un autre cours a ici sa propre entrée, telle que ce cours le définit. Définitions en anglais, résumées du cours ; traduction française entre parenthèses, vérifiée sur des sources françaises de l'IA et de l'informatique (documentation des éditeurs, terminologie officielle, recherche).

Schémas, avec un sommaire et une légende pour chacun : [mindmap.md](mindmap.md).

---

## Glossaire

### Skill *(Skill)*

A markdown file that teaches Claude how to do something once; Claude then applies that knowledge automatically whenever it's relevant. Skills fix repeating yourself: explaining your team's coding standards to Claude, re-describing how you want feedback structured on every PR review, reminding Claude of your preferred commit message format. Skills are folders of instructions and resources that Claude Code can discover and use to handle tasks more accurately. Each skill lives in a SKILL.md file with a name and description in its frontmatter; below the frontmatter go the actual instructions (a review checklist, formatting preferences, whatever Claude needs to know for that task). The description is how Claude decides whether to use the skill: Claude reads your request, compares it to all available skill descriptions, and activates the ones that match; the terminal shows the skill load. Skills are unique among Claude Code's ways to customize behavior because they're automatic and task-specific. CLAUDE.md files load into every conversation (if you want Claude to always use TypeScript's strict mode, that goes in CLAUDE.md); skills load on demand when they match your request. Claude only loads their name and description initially, so they don't fill up your entire context window: a PR review checklist doesn't need to be in context while you're debugging, and loads when you actually ask for a review. Slash commands require you to explicitly type them; skills don't: Claude applies them when it recognizes the situation. Skills work best for specialized knowledge that applies to specific tasks: code review standards your team follows, commit message formats you prefer, brand guidelines for your organization, documentation templates for specific types of docs, debugging checklists for particular frameworks. The rule of thumb: if you find yourself explaining the same thing to Claude repeatedly, that's a skill waiting to be written. Skills are stored in different places depending on who needs them: [personal skills](#personal-skills-skills-personnels) and [project skills](#project-skills-skills-de-projet).

### Personal skills *(Skills personnels)*

The [skills](#skill-skill) that go in the `.claude/skills` folder in your home directory (on Windows too, in your user folder). They follow you across all your projects: your commit message style, your documentation format, how you like code explained.

### Project skills *(Skills de projet)*

The [skills](#skill-skill) that go in `.claude/skills` inside the root directory of your repository. Anyone who clones the repo gets them automatically. This is where team standards live, like your company's brand guidelines, preferred fonts, and colors for web design. They get committed to version control alongside your code, so the whole team shares them.
