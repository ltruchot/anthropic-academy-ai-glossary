---
tags: [ia, anthropic, claude, glossaire]
created: 2026-11-12
updated: 2026-11-14
---
# Glossaire et mindmap Anthropic

Glossaire du cours Anthropic « Claude Code 101 » (Claude Certification, Developer Foundation). Il se suffit à lui-même : un terme que définit aussi un autre cours a ici sa propre entrée, telle que ce cours le définit. Définitions en anglais, résumées du cours ; traduction française entre parenthèses, vérifiée sur des sources françaises de l'IA et de l'informatique (documentation des éditeurs, terminologie officielle, recherche).

Schémas, avec un sommaire et une légende pour chacun : [mindmap.md](mindmap.md).

---

## Glossaire

### Claude Code *(Claude Code)*

An agentic coding tool that understands your codebase, edits your files, runs commands, and integrates with your existing developer tools to help you get things done faster. It's available in your terminal, Visual Studio Code, the Claude Desktop app, on the web, and in JetBrains IDEs. Unlike Claude.ai, it has direct access to your files, your terminal, and your entire codebase: instead of copying and pasting code back and forth, it goes in and does the work itself, because it works as an [AI agent](#ai-agent-agent-ia). In practice it can read and understand your codebase (explain a feature, trace a bug), edit files across your project (refactor a function and update every file that references it), run terminal commands (execute your build script, run your tests, install packages, and use the output to decide what to do next) and search the web (documentation, the latest API references). Three concepts to keep in mind to use it effectively: the [context window](#context-window-fenêtre-de-contexte), its [permission modes](#permission-modes-modes-de-permission), and the fact that it can make mistakes: it might misunderstand your intent, introduce a bug, or over-engineer a solution, and staying in the loop helps you catch these early. It combines several agentic concepts: an [agentic loop](#agentic-loop-boucle-agentique), a managed [context window](#context-window-fenêtre-de-contexte), [tools](#tool-outil), and configurable [permission modes](#permission-modes-modes-de-permission), all inside your terminal: it can read your codebase, take action, and verify its own work. That's what makes it fundamentally different from a chat window. Whatever directory you run `claude` in, it has access to that directory and all of its subfolders. To install it, on macOS, Linux, or WSL the curl command does it in one go; Homebrew and winget work too but don't auto-update by default. Where to use it: the terminal is the best bet to stay on the cutting edge, since features ship there first; the IDE integrations offer a nearly identical experience, more intertwined with your code editor; Desktop lets Claude run in the background, work in a specific folder, change permissions, or work in a cloud environment; the web is restricted to GitHub repositories and suits remote work.

### AI agent *(Agent IA)*

Software that can interact with its environment and perform actions to complete a defined goal. At its core, it works by having a large language model operating in a loop in real time. AI agents can have access to [tools](#tool-outil), external services, or even other AI agents to help reach their goals. The key differentiator of [Claude Code](#claude-code-claude-code): it works as an AI agent.

### Agentic loop *(Boucle agentique)*

How [Claude Code](#claude-code-claude-code) is best explained. You enter a prompt; Claude gathers the context it needs by interacting with the model, which returns text or a [tool](#tool-outil) call that Claude Code can execute; it takes action, for example editing a file or running a command; it verifies the results and determines whether they achieve what your prompt set out to do. If they do, Claude finishes and waits for the next prompt; if they don't, it loops back and tries again until the results are complete and verifiable. Throughout this loop, you can add context, interrupt, or steer the model to help guide it toward your goal.

### Context window *(Fenêtre de contexte)*

Claude's working memory. It can hold a lot, but not everything at once. This is where the "agentic" aspect of [Claude Code](#claude-code-claude-code) comes in: Claude finds strategic ways to locate answers within your codebase without loading the entire thing into context. Every file it reads, every command it runs and every message you send takes up space in it, and since the space is finite, it becomes important to optimize how you use it (see [context management](#context-management-gestion-du-contexte)). It determines how much of your conversation, file contents, command outputs, and more Claude can store and reference. Once you reach that limit, Claude Code [compacts](#compaction-compaction) your conversation.

### Compaction *(Compaction)*

What [Claude Code](#claude-code-claude-code) does once you reach the limit of the [context window](#context-window-fenêtre-de-contexte): it compacts your conversation, automatically determining what it can remove or summarize to bring the context window back down to a usable size. Compaction summarizes important details and removes unnecessary tool call results to free up space; this process can potentially lose details. You can also run it manually with the [/compact command](#context-commands-commandes-de-contexte).

### Context commands *(Commandes de contexte)*

Three commands to act on the [context window](#context-window-fenêtre-de-contexte) of [Claude Code](#claude-code-claude-code). `/compact` runs [compaction](#compaction-compaction) manually: it compacts everything up to that point, which is handy to free up context space while keeping a memory of what you previously worked on. `/clear` starts completely from scratch, with no memory of the previous session: it removes everything. `/context` checks the state of your context: a high-level overview of your context size, the categories taking up the most space, and a visual graphic showing the breakdown.

### Context management *(Gestion du contexte)*

Keeping the [context window](#context-window-fenêtre-de-contexte) of [Claude Code](#claude-code-claude-code) useful. A general rule of thumb: use `/compact` when you're working on a specific feature and running up against the context limit but need to continue, because keeping the context relevant to your current feature is important; use `/clear` when you want to start a new feature, because you don't want the previous conversation to introduce bias into something new (see [context commands](#context-commands-commandes-de-contexte)). For things you want Claude to remember across sessions, put them in your [CLAUDE.md file](#claudemd-file-fichier-claudemd). To save context space: be specific (a vague prompt might seem smaller, but it costs more context in the long run, since without clear instructions Claude is forced to explore your codebase more and do its own reasoning); manage your [MCP servers](#mcp-server-serveur-mcp), turning off those unrelated to the current project; and use [subagents](#subagent-sous-agent) for tasks where you only need the answer.

### Tool *(Outil)*

The backbone of how agents work. Most AI assistants simply take text in and return text out; tools let [Claude Code](#claude-code-claude-code) determine when to execute code to get closer to completing a task. This could be a file-reading tool, a web search tool, or any number of other capabilities. Claude Code uses semantic understanding to determine when to call a tool and how to use the output.

### MCP *(MCP)*

Model Context Protocol, an open standard that lets [Claude Code](#claude-code-claude-code) connect to external tools and data sources. When you ask a question, Claude automatically understands when it should use those [tools](#tool-outil) to better handle your query. A lot of your context lives outside your codebase, in databases, productivity apps or public repositories: MCP bridges that gap. For example, a Linear [MCP server](#mcp-server-serveur-mcp) brings in the details of your specific issues, and a docs MCP server like Context7 provides up-to-date documentation for a dependency.

### MCP server *(Serveur MCP)*

What connects [Claude Code](#claude-code-claude-code) to external tools and data sources through [MCP](#mcp-mcp). You add one with the claude mcp add command; it is an [HTTP server](#http-server-serveur-http) or a [stdio server](#stdio-server-serveur-stdio), and it has a [scope](#mcp-server-scopes-portées-des-serveurs-mcp). You manage your servers with /mcp inside a Claude Code session: see what's connected, check status, and disable servers you don't need. By default, a connected MCP server loads only its tool names and instructions into the context, and Claude loads a [tool](#tool-outil)'s full details when it needs that tool ([tool search](#tool-search-recherche-doutils)). It adds them even when you're not actively using it, and each server still takes some space, so if you have servers configured for things unrelated to the current project, consider turning them off (see [context management](#context-management-gestion-du-contexte)). If a tool has a CLI equivalent (like gh for GitHub or aws for AWS), the CLI is more context-efficient because it doesn't add a listing for each tool. You might also pair an MCP server with a [skill](#skill-skill) that teaches Claude how to use the server's tools well.

### HTTP server *(Serveur HTTP)*

A type of [MCP server](#mcp-server-serveur-mcp) for remote services. It is hosted by the service provider and connects over the network. The other main type is the [stdio server](#stdio-server-serveur-stdio).

### Stdio server *(Serveur stdio)*

A type of [MCP server](#mcp-server-serveur-mcp) for local processes that run on your machine. The other main type is the [HTTP server](#http-server-serveur-http).

### MCP server scopes *(Portées des serveurs MCP)*

An [MCP server](#mcp-server-serveur-mcp) can be scoped in three ways. Local: only available in the current project, just for you. User: available across all your projects. Project: uses a .mcp.json file that you check into version control, so anyone on the codebase gets the exact same servers automatically.

### Tool search *(Recherche d'outils)*

On by default: Claude Code keeps the full definition of each [MCP server](#mcp-server-serveur-mcp) tool out of your context until Claude needs it.

### Permission modes *(Modes de permission)*

What lets you choose how hands-on to be with [Claude Code](#claude-code-claude-code): it can ask you before running commands or making changes, or run in [auto mode](#auto-mode-mode-auto). You're always in control, whether you prefer a hands-on or hands-off approach. Claude Code has several: [manual](#manual-mode-mode-manuel), [auto-accept](#auto-accept-acceptation-automatique), [plan mode](#plan-mode-mode-plan) and [auto mode](#auto-mode-mode-auto). You can use Shift and Tab to toggle between modes (the page says cycle). There is no right or wrong choice: it is whatever you are comfortable with. All of this can be configured in your settings file. Be cautious when skipping permissions: giving Claude Code free rein to run commands means a mistake could be harder to catch before it happens.

### Manual mode *(Mode manuel)*

A [permission mode](#permission-modes-modes-de-permission) of [Claude Code](#claude-code-claude-code) in which Claude asks for explicit permission before editing a file or running a shell command. The video calls it the default behavior; which mode a new session starts in depends on your Claude Code version and settings.

### Auto-accept *(Acceptation automatique)*

A [permission mode](#permission-modes-modes-de-permission) of [Claude Code](#claude-code-claude-code) in which files are edited without asking, and common filesystem commands like mkdir, mv, and rm run without asking too. Other commands still require approval.

### Plan mode *(Mode Plan)*

A [permission mode](#permission-modes-modes-de-permission) of [Claude Code](#claude-code-claude-code) in which Claude reads files and runs shell commands to explore, without editing your source files, and compiles a plan of action before starting any work. It takes your prompt, then analyzes your codebase and researches your suggested implementation; it asks clarifying questions along the way, then returns a detailed plan it can execute. It is great for planning complex changes or doing a safe code review, and excels at multi-step implementations toward a feature. After reviewing the plan, if it looks good, you accept it and let Claude work through it; depending on your permission mode, it may check in with you along the way. Reviewing the plan is the best place to course-correct, because no code is written yet; the [explore subagent](#subagent-sous-agent) can also give a general summary of your codebase without plan mode. It is the fastest way to handle the [Explore and Plan](#explore-plan-code-commit-workflow-flux-de-travail-explore-plan-code-commit) steps.

### Auto mode *(Mode auto)*

A [permission mode](#permission-modes-modes-de-permission) of [Claude Code](#claude-code-claude-code) in which a background safety check screens most actions instead of asking you before each one. Claude works without routine permission prompts while a classifier checks most actions in the background, targeted at blocking actions that are irreversible, destructive, or aimed outside your environment. When something is blocked, Claude usually finds a safer approach or asks you for the go-ahead.

### Explore, Plan, Code, Commit workflow *(Flux de travail Explore, Plan, Code, Commit)*

The workflow the course says to take away: Explore, Plan, Code, and Commit. Without it, most people jump straight to asking Claude to write code, which means more course-correcting later on. Explore gives Claude the relevant context it needs for your project. Plan creates a plan of action that Claude uses to measure success; [plan mode](#plan-mode-mode-plan) is the fastest way to handle these first two steps. Code is the back and forth between you and Claude before settling on the final outcome: define a success criteria, add tools (for web UIs, the Claude in Chrome extension so [Claude Code](#claude-code-claude-code) can test the UI directly), and include a test suite that is a reliable source of truth to avoid false positives. If Claude keeps running into the same issues, ask it to save the solution to its CLAUDE.md file. Commit helps you review and push your code: test the changes yourself, run a [subagent](#subagent-sous-agent) code reviewer, then get Claude to generate a commit message in your style.

### Subagent *(Sous-agent)*

A reviewer or helper that [Claude Code](#claude-code-claude-code) runs apart from the main agent. A subagent gets a fresh pair of eyes on the codebase: it doesn't carry the bias the main agent might have from the session. The course uses one as a code reviewer before you commit, and the explore subagent to get a general summary of your codebase without being in [plan mode](#plan-mode-mode-plan) and without intending to make changes afterward. A subagent runs in parallel with your main agent but has a completely separate context window: for tasks where you only need the answer, it does the work and returns just a summary to your main agent, keeping your primary context clean (see [context management](#context-management-gestion-du-contexte)). Claude can delegate tasks to subagents that break them down and run component tasks in parallel, each in its own isolated context window: what Claude discovers while exploring, such as tool calls reading your codebase or running web searches, isn't always relevant to the main feature you're developing. Claude spawns a subagent to handle a task like “explore this codebase for me”; once finished, it summarizes its findings and returns that summary back to Claude, so you get the answer without the entire journey it took to get there cluttering your main context. The subagent receives two inputs, a custom system prompt from its configuration file and a task description written by the parent agent based on what you ask for; it then works autonomously, none of its file reads, edits or tool use appears in the main conversation, only a summary is returned, and its whole conversation is discarded. The trade-off: the main window loses visibility into how the subagent reaches its conclusions and what it discovered along the way. Claude Code includes [built-in subagents](#built-in-subagents-sous-agents-intégrés), and you can create a [custom subagent](#custom-subagent-sous-agent-personnalisé) of your own.

### Custom subagent *(Sous-agent personnalisé)*

A [subagent](#subagent-sous-agent) you create yourself, with a custom system prompt and tool access. It is defined in a Markdown file with YAML frontmatter; the easiest way to get started is to let Claude generate one for you: describe the subagent you want and where to save it, and Claude generates a name, description and prompt for it. A subagent in `.claude/agents/` works in the current project, and one in `.claude/agents/` in your home directory works in all your projects. If the folder you chose didn't exist when your session started, restart [Claude Code](#claude-code-claude-code) to load the new subagent. It can be customized further: persistent memory lets it retain memory across conversations, which is great if you're using it consistently on the same projects, and you can preload [skills](#skill-skill) into it by adding the skills key and listing skills by name; unlike skills in your main conversation, the entire skill is loaded into context here.

### Built-in subagents *(Sous-agents intégrés)*

The [subagents](#subagent-sous-agent) that [Claude Code](#claude-code-claude-code) includes and you can use immediately. The general-purpose subagent is used for multi-step tasks that require both exploration and action; the explore subagent, for fast searching of codebases; the plan subagent, during [plan mode](#plan-mode-mode-plan), for research and analysis of your codebase before presenting a plan. You can also create your own, with custom system prompts and tool access (see [custom subagent](#custom-subagent-sous-agent-personnalisé)).

### CLAUDE.md file *(Fichier CLAUDE.md)*

A Markdown file you add to the root of your project: it gives [Claude Code](#claude-code-claude-code) persistent memory about your project, and Claude Code reads it automatically every time you start a session. Without one, it starts fresh every time: it has to re-explore your codebase, figure out what dependencies are needed and understand what features are already implemented, and sometimes it makes assumptions, which makes it harder to steer Claude in the right direction. Think of it as an onboarding script for your codebase: its contents are appended to your prompt. It is where to put what you want Claude to remember across sessions, so it doesn't have to rediscover things from scratch. Start with your stack, your preferences and your commands, then build from there as you go. You can (and should) commit it to version control so your team benefits from it; there is a hierarchy of memory files depending on who they're for: the [project-level CLAUDE.md](#project-level-claudemd-claudemd-au-niveau-du-projet) and the [user-level CLAUDE.md](#user-level-claudemd-claudemd-au-niveau-utilisateur). Save corrections to memory: if you find yourself correcting Claude repeatedly, explicitly ask it to save that rule to memory (if Claude keeps running into the same issues, ask it to save the solution to its CLAUDE.md file), and next time you open the project it will know. To have Claude reference project docs, use the @ symbol with the file path. Start without one, so you can see where you constantly have to course-correct the model: this keeps your CLAUDE.md compact and focused on only the necessary information. See [context management](#context-management-gestion-du-contexte) and the [/init command](#init-command-commande-init).

### Project-level CLAUDE.md *(CLAUDE.md au niveau du projet)*

The [CLAUDE.md file](#claudemd-file-fichier-claudemd) that lives in the root directory of your project. It is shared with the team.

### User-level CLAUDE.md *(CLAUDE.md au niveau utilisateur)*

The [CLAUDE.md file](#claudemd-file-fichier-claudemd) that lives in your configuration folder. It is just for you and applies across all your projects: put your personal preferences here.

### /init command *(Commande /init)*

When you're ready for a [CLAUDE.md file](#claudemd-file-fichier-claudemd), run `/init` to have Claude generate one for you.

### Diff *(Diff)*

The before-and-after of a change: the lines removed and the lines added, file by file. The `/diff` command opens an interactive viewer of your uncommitted changes in that form, and it can also show what each of Claude's turns changed (the up and down arrows move between files, Enter opens one). `/diff` and `/code-review` read git's record of what changed, so your project needs to be in a git repository. Read the actual diff before you trust Claude's summary alone, and look for changes you didn't ask for, tests that got weaker (skipped, deleted, or loosened until they passed), and new packages and hard-coded values (a dependency added for only one function, a URL or a key written straight into the code). See the [/code-review command](#code-review-command-commande-code-review).

### /code-review command *(Commande /code-review)*

A second reviewer for a change, before you keep it: it reviews the change in a clean context, with none of your session's history, and reports what it finds ([findings](#finding-constat)). It edits nothing unless you ask it to. A long session carries everything it has read and decided, which is exactly the history you don't want in a reviewer (see [context management](#context-management-gestion-du-contexte)). The review runs in the background, anywhere from seconds to a few minutes, and counts against your usage like any other task, so save it for changes that deserve a second look. An effort level goes after the command: `/code-review low` reports only the findings it's most confident about, `/code-review high` casts a wider net and may include findings it's less sure of; the level you type is remembered for later reviews until you type a different one. It is not Claude Code Review, a separate product for teams: an Owner of your Claude organization turns it on for a GitHub repository, and it posts its findings on pull requests. See also [diff](#diff-diff).

### Finding *(Constat)*

What a [/code-review](#code-review-command-commande-code-review) reports: a file location, a tag (correctness or style) and a one-line summary. Sort each finding into one of three piles. Fix now: a real problem, it matters, and it must be fixed. Ask why: findings you can't quite verify or that seem off, since reviewers reading code changes cold can also miss things; quote the finding back to Claude and ask Claude to check again. Leave it: a real problem but small or inconsequential, which can often be batched into a group of fixes covered in one future session. Whenever you ask for a fix, ask for evidence with it; if a fix grows into a large change of its own, run the review again. A human review and a Claude review pay off when a change is bigger than you could hold in your head, when it touches something sensitive or does something destructive, and before you hand the work to a teammate; a simple, one-line change often needs only a quick glance at the [diff](#diff-diff).

### /rewind command *(Commande /rewind)*

The way back when the whole change is wrong: run `/rewind` (or press Esc twice on an empty prompt), pick the prompt that produced it, and choose Restore code and conversation. One limit: files changed by shell commands Claude ran, such as a package install, aren't rolled back. It works on a different version control system too, because Claude tracks its own edits. See the [diff](#diff-diff).

### Skill *(Skill)*

A markdown file that teaches Claude how to do something once, and Claude applies that knowledge automatically whenever it's relevant. Skills fix having to explain your team's coding standards, how you want feedback structured on a PR review or your preferred commit message format every time. Agent skills are folders of instructions, scripts and resources that Claude can discover and use to do things more accurately and efficiently. In Claude Code, a skill has a SKILL.md file, and its description is how Claude decides whether to use the skill: it matches your request against the available skill descriptions and activates the ones that match. Skills are unique among the ways to customize Claude Code because they are automatic and task specific: unlike a [CLAUDE.md file](#claudemd-file-fichier-claudemd), which loads into every conversation (so a rule Claude should always follow, such as TypeScript strict mode, goes there), a skill loads on demand when it matches your request. Only its name and description are loaded, so it doesn't fill up your context window (see [context window](#context-window-fenêtre-de-contexte)): a PR review checklist is not in the context while you're debugging, and loads when you ask for a review. Slash commands require you to type them; skills don't, Claude applies them when it recognizes the situation. Skills work best for specialized knowledge that applies to specific tasks: code review standards your team follows, commit message formats that you prefer, your organization's brand guidelines. If you find yourself explaining the same thing to Claude repeatedly, that's a skill waiting to be written. A [custom subagent](#custom-subagent-sous-agent-personnalisé) can preload skills. Skills are stored as [personal skills](#personal-skills-skills-personnels) or [project skills](#project-skills-skills-de-projet), depending on who needs them.

### Personal skills *(Skills personnels)*

The [skills](#skill-skill) that go in the `.claude/skills` folder in your home directory and follow you across all your projects. They hold your preferences: your commit message style, your documentation format, how you like code explained.

### Project skills *(Skills de projet)*

The [skills](#skill-skill) that go in `.claude/skills` inside the root directory of your repository. Anyone who clones the repository gets them automatically. This is where team standards live, like your company's brand guidelines, and the preferred fonts and colors that you use for web design.

### Hook *(Hook)*

A command that runs at a specific point in [Claude Code](#claude-code-claude-code)'s lifecycle. The key difference between hooks and everything else covered in the course is that hooks are deterministic: they always run. You can tell Claude in your [CLAUDE.md file](#claudemd-file-fichier-claudemd) to run Prettier after every file edit, and most of the time it will, but sometimes it won't; a hook makes it happen every single time, no exceptions. Common use cases: auto-formatting after file edits, logging all executed commands for compliance, blocking dangerous operations like modifying production files, and sending yourself notifications when Claude finishes a task. Hooks are configured in your settings.json: you pick a [hook event](#hook-event-événement-de-hook), optionally set a [matcher](#matcher-matcher) for which tools it applies to, and provide a command to run. You configure them by editing settings.json directly; the [/hooks command](#hooks-command-commande-hooks) opens a read-only list of your configured hooks. Hooks configured in .claude/settings.json are project-level and can be checked into your repo, so your entire team gets the same hooks automatically; their commands use [CLAUDE_PROJECT_DIR](#claude_project_dir-claude_project_dir) to reference scripts stored in your project. If something needs to happen every time without fail, don't put it in a prompt: put it in a hook.

### Hook event *(Événement de hook)*

The point in [Claude Code](#claude-code-claude-code)'s lifecycle at which a [hook](#hook-hook) runs; you pick one for each hook. Some of the most common: PreToolUse runs before a tool call; PostToolUse runs after a tool call completes; UserPromptSubmit runs when you submit a prompt, before Claude processes it; Stop runs when Claude finishes responding; Notification runs when Claude sends a notification. These are just a few of the events you can hook into: Claude Code supports many more (the hooks reference lists them all). Use PostToolUse for auto-formatting and logging, and PreToolUse to block dangerous operations (see [exit codes](#exit-codes-codes-de-sortie)).

### Matcher *(Matcher)*

The optional part of a [hook](#hook-hook)'s configuration that sets which tools it applies to. The most common hook, auto-formatting after edits, is a PostToolUse [hook event](#hook-event-événement-de-hook) with a matcher of "Edit|Write", so it fires after Claude uses the Edit or Write tool. Its command checks the file extension and runs the appropriate formatter: Prettier for TypeScript, gofmt for Go, whatever your project uses.

### Exit codes *(Codes de sortie)*

What decides the behavior of a PreToolUse [hook](#hook-hook), which can block tool calls before they execute; it receives the tool name and input as JSON on stdin. Exit code 0: proceed normally. Exit code 2: block the action, and the stderr message gets fed back to Claude as feedback, so it knows why it was blocked and can adjust. Any other exit code: a non-blocking error that gets shown to you but doesn't stop anything. This is how you enforce hard rules: block writes to a production config directory, block bash commands that contain rm -rf, block commits to main, whatever your team needs to be guaranteed, not suggested.

### /hooks command *(Commande /hooks)*

The command inside [Claude Code](#claude-code-claude-code) that opens a read-only list of your configured [hooks](#hook-hook), so you can check that a new one shows up. It doesn't edit them: you configure hooks by editing settings.json directly.

### CLAUDE_PROJECT_DIR *(CLAUDE_PROJECT_DIR)*

The environment variable to use in a [hook](#hook-hook)'s commands to reference scripts stored in your project, so they work regardless of Claude's current working directory. It goes in the commands of hooks configured in .claude/settings.json, which are project-level and can be checked into your repo.
