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

### MCP _(MCP)_

Model Context Protocol, an open-source standard for connecting AI applications to external systems: a protocol for connecting Claude to external services and data sources without manually writing tool schemas. Using MCP, AI applications like Claude or ChatGPT can connect to data sources (local files, databases), tools (search engines, calculators) and workflows (specialized prompts), to access key information and perform tasks. Think of it like a USB-C port for AI applications: just as USB-C provides a standardized way to connect electronic devices, MCP provides a standardized way to connect AI applications to external systems. Its benefits depend on where you sit: developers spend less development time and complexity when building, or integrating with, an AI application or agent; AI applications or agents get access to an ecosystem of data sources, tools and apps; end-users get more capable AI applications or agents that can access their data and take actions on their behalf when necessary. An open protocol supported across a wide range of clients and servers (Claude, ChatGPT, Visual Studio Code, Cursor, MCPJam and many others): build once and integrate everywhere. [MCP servers](#mcp-server-serveur-mcp) expose tools, resources and prompts, and [MCP clients](#mcp-client-client-mcp) consume them.

### MCP server _(Serveur MCP)_

What exposes [tools](#tool-outil), [resources](#resource-ressource) and [prompts](#prompt-prompt), the three basic components of an MCP server, to the [MCP clients](#mcp-client-client-mcp) that consume them. Tools are intended to be consumed by language models; resources allow a server to share data with clients; prompts provide pre-built instructions to language models.

### MCP client _(Client MCP)_

The side that communicates with [MCP servers](#mcp-server-serveur-mcp) and consumes the [tools](#tool-outil), [resources](#resource-ressource) and [prompts](#prompt-prompt) they expose.

### Tool _(Outil)_

One of the three basic components of an [MCP server](#mcp-server-serveur-mcp): intended to be consumed by language models. Search engines and calculators are examples of tools an AI application can connect to through [MCP](#mcp-mcp).

### Resource _(Ressource)_

One of the three basic components of an [MCP server](#mcp-server-serveur-mcp): resources allow a server to share data with clients, for direct data access (resources for exposing data).

### Prompt _(Prompt)_

One of the three basic components of an [MCP server](#mcp-server-serveur-mcp): prompts provide pre-built instructions to language models, for pre-defined workflows. Specialized prompts are the page's example of the workflows an AI application can connect to through [MCP](#mcp-mcp).
