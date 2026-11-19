---
tags: [ia, anthropic, claude, glossaire]
created: 2026-11-19
updated: 2026-11-19
---

# Glossaire et mindmap Anthropic

Glossaire du cours Anthropic « Introduction to Model Context Protocol » (Claude Certification, Developer Foundation). Il se suffit à lui-même : un terme que définit aussi un autre cours a ici sa propre entrée, telle que ce cours le définit. Définitions en anglais, résumées du cours ; traduction française entre parenthèses, vérifiée sur des sources françaises de l'IA et de l'informatique (documentation des éditeurs, terminologie officielle, recherche).

Schémas, avec un sommaire et une légende pour chacun : [mindmap.md](mindmap.md).

---

## Glossaire

### MCP *(MCP)*

Model Context Protocol, an open-source standard for connecting AI applications to external systems: a protocol for connecting Claude to external services and data sources without manually writing tool schemas. Using MCP, AI applications like Claude or ChatGPT can connect to data sources (local files, databases), tools (search engines, calculators) and workflows (specialized prompts), to access key information and perform tasks. Think of it like a USB-C port for AI applications: just as USB-C provides a standardized way to connect electronic devices, MCP provides a standardized way to connect AI applications to external systems. Its benefits depend on where you sit: developers spend less development time and complexity when building, or integrating with, an AI application or agent; AI applications or agents get access to an ecosystem of data sources, tools and apps; end-users get more capable AI applications or agents that can access their data and take actions on their behalf when necessary. An open protocol supported across a wide range of clients and servers (Claude, ChatGPT, Visual Studio Code, Cursor, MCPJam and many others): build once and integrate everywhere. [MCP servers](#mcp-server-serveur-mcp) expose tools, resources and prompts, and [MCP clients](#mcp-client-client-mcp) consume them. A communication layer that provides Claude with context and tools without requiring you to write a bunch of tedious integration code: it shifts the burden of tool definitions and execution away from your server to specialized MCP servers. Without it, a chat app that lets users ask Claude about their GitHub data would need an incredible number of tool schemas and functions to cover GitHub's features, all integration code you write, test and maintain yourself. Not the same as [tool use](#tool-use-utilisation-doutils): the two are complementary.

### MCP server *(Serveur MCP)*

What exposes [tools](#tool-outil), [resources](#resource-ressource) and [prompts](#prompt-prompt), the three basic components of an MCP server, to the [MCP clients](#mcp-client-client-mcp) that consume them. Tools are intended to be consumed by language models; resources allow a server to share data with clients; prompts provide pre-built instructions to language models. MCP servers provide access to data or functionality implemented by outside services: they act as specialized interfaces that expose tools, prompts and resources in a standardized way. The MCP Server for GitHub wraps up tons of functionality around GitHub as a standardized set of tools (like get_repos()), connects directly to GitHub's API and handles all the GitHub-specific implementation details. It provides tool schemas and functions already defined for you: to call an API directly, you would author those tool definitions on your own. Anyone can create an MCP server implementation; often, service providers make their own official MCP implementations (AWS might release one with tools for its various services).

### MCP client *(Client MCP)*

The side that communicates with [MCP servers](#mcp-server-serveur-mcp) and consumes the [tools](#tool-outil), [resources](#resource-ressource) and [prompts](#prompt-prompt) they expose. In the basic architecture, the MCP client is your server, connecting to MCP servers; your application connects to an MCP server instead of implementing everything from scratch.

### Tool *(Outil)*

One of the three basic components of an [MCP server](#mcp-server-serveur-mcp): intended to be consumed by language models. Search engines and calculators are examples of tools an AI application can connect to through [MCP](#mcp-mcp). Each tool is a schema and a function: without MCP, your server holds them and you write, test and maintain them; with MCP, the MCP server defines and executes them. Claude calls them through [tool use](#tool-use-utilisation-doutils).

### Resource *(Ressource)*

One of the three basic components of an [MCP server](#mcp-server-serveur-mcp): resources allow a server to share data with clients, for direct data access (resources for exposing data).

### Prompt *(Prompt)*

One of the three basic components of an [MCP server](#mcp-server-serveur-mcp): prompts provide pre-built instructions to language models, for pre-defined workflows. Specialized prompts are the page's example of the workflows an AI application can connect to through [MCP](#mcp-mcp).

### uv *(uv)*

An extremely fast Python package and project manager, written in Rust: the course manages its project with the UV CLI, which needs a local Python installation. A single tool to replace pip, pip-tools, pipx, poetry, pyenv, twine, virtualenv and more; 10-100x faster than pip. It provides comprehensive project management, with a universal lockfile; runs scripts, with support for inline dependency metadata; installs and manages Python versions; runs and installs tools published as Python packages; includes a pip-compatible interface; supports Cargo-style workspaces; is disk-space efficient, with a global cache for dependency deduplication. Installable without Rust or Python via curl or pip, on macOS, Linux and Windows. Backed by Astral, the creators of Ruff.

### Tool use *(Utilisation d'outils)*

How Claude actually calls tools. [MCP servers](#mcp-server-serveur-mcp) and tool use are complementary but different concepts: MCP servers provide tool schemas and functions already defined for you, while tool use is about how Claude calls those tools. Saying [MCP](#mcp-mcp) is just the same as tool use is a common misconception. The key difference is who does the work: with MCP, someone else has already implemented the tools for you.
