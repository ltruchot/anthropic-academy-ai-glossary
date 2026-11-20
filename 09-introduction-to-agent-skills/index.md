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

A markdown file that teaches Claude how to do something once; Claude then applies that knowledge automatically whenever it's relevant. Skills fix repeating yourself: explaining your team's coding standards to Claude, re-describing how you want feedback structured on every PR review, reminding Claude of your preferred commit message format. Skills are folders of instructions and resources that Claude Code can discover and use to handle tasks more accurately. Each skill lives in a SKILL.md file with a name and description in its frontmatter; below the frontmatter go the actual instructions (a review checklist, formatting preferences, whatever Claude needs to know for that task). To create one, make a directory named after the skill inside the skills folder, then a SKILL.md file inside it, in two parts separated by frontmatter dashes: the name identifies the skill; the description tells Claude when to use it, its matching criteria; everything after the second set of dashes is the instructions Claude follows when the skill is activated. The description is how Claude decides whether to use the skill: Claude reads your request, compares it to all available skill descriptions, and activates the ones that match; the terminal shows the skill load. How the match works: [skill matching](#skill-matching-correspondance-des-skills). Skills are unique among Claude Code's ways to customize behavior because they're automatic and task-specific. CLAUDE.md files load into every conversation (if you want Claude to always use TypeScript's strict mode, that goes in CLAUDE.md); skills load on demand when they match your request. Claude only loads their name and description initially, so they don't fill up your entire context window: a PR review checklist doesn't need to be in context while you're debugging, and loads when you actually ask for a review. Slash commands require you to explicitly type them; skills don't: Claude applies them when it recognizes the situation. Skills work best for specialized knowledge that applies to specific tasks: code review standards your team follows, commit message formats you prefer, brand guidelines for your organization, documentation templates for specific types of docs, debugging checklists for particular frameworks. The rule of thumb: if you find yourself explaining the same thing to Claude repeatedly, that's a skill waiting to be written. Skills are stored in different places depending on who needs them: [personal skills](#personal-skills-skills-personnels) and [project skills](#project-skills-skills-de-projet). To update a skill, edit its SKILL.md file; to remove one, delete its directory. Claude Code watches your skills directories, so a new skill or a change is picked up in the current session, without a restart; if the .claude/skills folder in your home directory didn't exist when the session started, Claude Code isn't watching it yet: run /reload-skills, and again after each later change. The available skills list shows whether a skill is available. Two skills with the same name: [skill priority](#skill-priority-priorité-des-skills).

### Personal skills *(Skills personnels)*

The [skills](#skill-skill) that go in the `.claude/skills` folder in your home directory (on Windows too, in your user folder). They follow you across all your projects: your commit message style, your documentation format, how you like code explained.

### Project skills *(Skills de projet)*

The [skills](#skill-skill) that go in `.claude/skills` inside the root directory of your repository. Anyone who clones the repo gets them automatically. This is where team standards live, like your company's brand guidelines, preferred fonts, and colors for web design. They get committed to version control alongside your code, so the whole team shares them.

### Skill matching *(Correspondance des skills)*

How Claude picks the [skill](#skill-skill) for a request. When Claude Code starts, it scans several locations for skills but only loads the name and description of each, not the full content. When you send a request, Claude compares your message against the descriptions of all available skills, using semantic matching: "explain what this function does" would match a skill described as "explain code with visual diagrams" because the intent overlaps. Once a match is found, Claude reads the complete SKILL.md file and follows its instructions. A skill with only a name, description, and instructions loads without asking you; if a skill pre-approves tools or adds hooks, Claude Code may ask you to approve it first, depending on your permission mode.

### Skill priority *(Priorité des skills)*

Which [skill](#skill-skill) wins when two have the same name, as when you clone a repository that has a skill with the same name as one of your personal skills. The order: Enterprise (managed settings, highest priority), then [personal skills](#personal-skills-skills-personnels) (your home directory), then [project skills](#project-skills-skills-de-projet) (the .claude/skills directory inside a repository). This lets organizations enforce standards through enterprise skills while still allowing individual customization: if your company has an enterprise "code-review" skill and you create a personal "code-review" skill, the enterprise version takes precedence. Skills from installed plugins sit outside this order: they're namespaced as /plugin-name:skill-name, so a plugin skill and another skill with the same name both load. To avoid conflicts, use descriptive names: "frontend-review" or "backend-review" rather than just "review".
