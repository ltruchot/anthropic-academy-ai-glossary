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

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### MCP server *(Serveur MCP)*

What exposes [tools](#tool-outil), [resources](#resource-ressource) and [prompts](#prompt-prompt), the three basic components of an MCP server (MCP's three core primitives), to the [MCP clients](#mcp-client-client-mcp) that consume them. Tools are intended to be consumed by language models; resources allow a server to share data with clients; prompts provide pre-built instructions to language models. MCP servers provide access to data or functionality implemented by outside services: they act as specialized interfaces that expose tools, prompts and resources in a standardized way. The MCP Server for GitHub wraps up tons of functionality around GitHub as a standardized set of tools (like get_repos()), connects directly to GitHub's API and handles all the GitHub-specific implementation details. It provides tool schemas and functions already defined for you: to call an API directly, you would author those tool definitions on your own. Anyone can create an MCP server implementation; often, service providers make their own official MCP implementations (AWS might release one with tools for its various services). On a normal project, you typically implement either a client or an MCP server: a real project might author just an MCP server, to distribute to the world and allow developers to access a service you have built up. Building an MCP server becomes much simpler with the official [MCP Python SDK](#mcp-python-sdk-sdk-python-de-mcp).

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### MCP client *(Client MCP)*

The side that communicates with [MCP servers](#mcp-server-serveur-mcp) and consumes the [tools](#tool-outil), [resources](#resource-ressource) and [prompts](#prompt-prompt) they expose. In the basic architecture, the MCP client is your server, connecting to MCP servers; your application connects to an MCP server instead of implementing everything from scratch. It serves as the communication bridge between your server and MCP servers: your access point to all the tools an MCP server provides, handling the message exchange and protocol details so your application doesn't have to. In the course's project, the MCP client consists of two main components: a custom class you create to make using the session easier, and the [client session](#client-session-session-client) it wraps, the actual connection to the server; your code uses the client at two key points, to get a list of available tools to send to Claude and to execute tools when Claude requests them. MCP is [transport agnostic](#transport-agnostic-indépendant-du-transport): the most common setup runs the client and the server on the same machine, over [standard input/output](#standard-inputoutput-entréesortie-standard). Once connected, they exchange message types defined in the MCP specification, mainly [ListToolsRequest/ListToolsResult](#listtoolsrequestlisttoolsresult-listtoolsrequestlisttoolsresult) and [CallToolRequest/CallToolResult](#calltoolrequestcalltoolresult-calltoolrequestcalltoolresult). The client doesn't actually run a tool: it sends a CallToolRequest to the MCP server, which executes it. In the flow of a user query ("What repositories do I have?"): your server asks the MCP client for the available tools (a ListToolsRequest to the MCP server, a ListToolsResult back), sends the user's query plus those tools to Claude; Claude decides it needs to call a tool; your server asks the MCP client to run the tool Claude specified; the MCP client sends a CallToolRequest to the MCP server, which makes the actual GitHub API call; the data flows back through the MCP server as a CallToolResult; your server sends the tool results back to Claude, which formulates a final answer, and delivers it to the user. Many steps, but each component has a clear responsibility: the MCP client abstracts away the complexity of server communication, letting you focus on your application logic. On a normal project, you typically implement either a client or an MCP server: a project might make only an MCP client, to connect to outside MCP servers already implemented by other engineers.

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### Tool *(Outil)*

One of the three basic components of an [MCP server](#mcp-server-serveur-mcp): intended to be consumed by language models. Search engines and calculators are examples of tools an AI application can connect to through [MCP](#mcp-mcp). Each tool is a schema and a function: without MCP, your server holds them and you write, test and maintain them; with MCP, the MCP server defines and executes them. Claude calls them through [tool use](#tool-use-utilisation-doutils). With the [MCP Python SDK](#mcp-python-sdk-sdk-python-de-mcp), you define a tool with a [decorator](#decorator-décorateur) on a Python function, instead of writing its JSON schema by hand. A [resource](#resource-ressource), by contrast, lets clients fetch information without the complexity of tool calls.

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### Resource *(Ressource)*

One of the three basic components of an [MCP server](#mcp-server-serveur-mcp): resources allow a server to share data with clients, for direct data access (resources for exposing data). Like GET request handlers in a typical HTTP server, they expose data to clients: perfect when you need to fetch information rather than perform actions, a clean way to expose read-only data from your MCP server without the complexity of tool calls. They follow a request-response pattern: when your client needs data, it sends a [ReadResourceRequest](#readresourcerequestreadresourceresult-readresourcerequestreadresourceresult) with a URI that identifies the resource; the MCP server processes the URI, runs the appropriate function and returns the data in a ReadResourceResult. Your code requests a resource from the [MCP client](#mcp-client-client-mcp), which forwards the request to the MCP server. You usually define one resource for each distinct read operation. Two types: [direct resources](#direct-resource-ressource-directe) (a static URI) and [templated resources](#templated-resource-ressource-paramétrée) (parameters in their URI). With the [MCP Python SDK](#mcp-python-sdk-sdk-python-de-mcp), a resource is a Python function under a [decorator](#decorator-décorateur), `@mcp.resource(…)`, that gives its URI and its mime_type. A resource can return any type of data (strings, JSON, binary data); the mime_type parameter gives clients a hint about the kind of data returned (its [MIME type](#mime-type-type-mime)): "application/json" for structured data, "text/plain" for plain text, "application/pdf" for binary files. The SDK automatically serializes your return values: you return the data structure, not a JSON string, and the client deserializes it. The [MCP Inspector](#mcp-inspector-mcp-inspector) lists them in two sections, Resources (direct/static) and Resource Templates (templated); click one to test it, and the inspector shows the exact response structure your client will receive, with the MIME type and the serialized data. The course's example: a document mention feature (@document_name), one resource listing all available documents for an autocomplete, another fetching a document's contents, which your system injects into the prompt sent to Claude, so Claude needs no tool to fetch it. Resources expose information that can be directly included in prompts, rather than requiring tool calls to access data: a more efficient way to provide context to AI models. The resource content becomes part of the initial context, allowing for immediate responses about the data, a much smoother user experience than the AI model making separate tool calls. To access them, the MCP client implements a `read_resource` function: it requests the resource from the MCP server and processes the response based on its MIME type.

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### Prompt *(Prompt)*

One of the three basic components of an [MCP server](#mcp-server-serveur-mcp): prompts provide pre-built instructions to language models, for pre-defined workflows. Specialized prompts are the page's example of the workflows an AI application can connect to through [MCP](#mcp-mcp).

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### uv *(uv)*

An extremely fast Python package and project manager, written in Rust: the course manages its project with the UV CLI, which needs a local Python installation. A single tool to replace pip, pip-tools, pipx, poetry, pyenv, twine, virtualenv and more; 10-100x faster than pip. It provides comprehensive project management, with a universal lockfile; runs scripts, with support for inline dependency metadata; installs and manages Python versions; runs and installs tools published as Python packages; includes a pip-compatible interface; supports Cargo-style workspaces; is disk-space efficient, with a global cache for dependency deduplication. Installable without Rust or Python via curl or pip, on macOS, Linux and Windows. Backed by Astral, the creators of Ruff.

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### Tool use *(Utilisation d'outils)*

How Claude actually calls tools. [MCP servers](#mcp-server-serveur-mcp) and tool use are complementary but different concepts: MCP servers provide tool schemas and functions already defined for you, while tool use is about how Claude calls those tools. Saying [MCP](#mcp-mcp) is just the same as tool use is a common misconception. The key difference is who does the work: with MCP, someone else has already implemented the tools for you.

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### Transport agnostic *(Indépendant du transport)*

One of MCP's key strengths: a fancy way of saying the [MCP client](#mcp-client-client-mcp) and the [MCP server](#mcp-server-serveur-mcp) can communicate over different protocols depending on your setup. The most common setup runs both on the same machine, communicating through [standard input/output](#standard-inputoutput-entréesortie-standard); you can also connect them over HTTP, WebSockets or various other network protocols.

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### Standard input/output *(Entrée/sortie standard)*

How an [MCP client](#mcp-client-client-mcp) and an [MCP server](#mcp-server-serveur-mcp) communicate in the most common setup, both running on the same machine (the GitHub MCP server "running locally" of the course's slide). The way the course sets them up later. MCP being [transport agnostic](#transport-agnostic-indépendant-du-transport), it is one protocol among others (HTTP, WebSockets).

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### ListToolsRequest/ListToolsResult *(ListToolsRequest/ListToolsResult)*

One of the main message types the [MCP client](#mcp-client-client-mcp) and the [MCP server](#mcp-server-serveur-mcp) exchange, defined in the MCP specification. With a ListToolsRequest, the client asks the server "what tools do you provide?"; with a ListToolsResult, it gets back a list of available [tools](#tool-outil). Your server needs that list to send it to Claude, along with the user's query.

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### CallToolRequest/CallToolResult *(CallToolRequest/CallToolResult)*

One of the main message types the [MCP client](#mcp-client-client-mcp) and the [MCP server](#mcp-server-serveur-mcp) exchange, defined in the MCP specification. With a CallToolRequest, the client asks the server to run a specific [tool](#tool-outil) with given arguments; with a CallToolResult, it receives the results. Sent once Claude has decided to call a tool and your server has asked the MCP client to run it: the MCP server makes the actual call (to GitHub's API, in the course's example), and the data flows back through it as a CallToolResult.

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### MCP Python SDK *(SDK Python de MCP)*

The official Python SDK that makes building an [MCP server](#mcp-server-serveur-mcp) much simpler: instead of writing complex JSON schemas by hand, you define [tools](#tool-outil) with [decorators](#decorator-décorateur) and let the SDK handle the heavy lifting. It makes server creation straightforward: you can initialize a server with just one line (`mcp = FastMCP("DocumentMCP", log_level="ERROR")`, after `from mcp.server.fastmcp import FastMCP`). Instead of writing JSON schemas manually, you use Python [type hints](#type-hints-indications-de-type) and field descriptions: the SDK automatically generates the proper schema that Claude can understand. The Field class from Pydantic provides argument descriptions that help Claude understand what each parameter expects. Key benefits of the approach: no manual JSON schema writing required; type hints provide automatic validation; clear parameter descriptions help Claude understand tool usage; error handling integrates naturally with Python exceptions (a tool raises a ValueError when a document is not found); tool registration happens automatically through decorators. It transforms tool creation from a complex schema-writing exercise into simple Python function definitions, which makes MCP servers much easier to build and maintain while ensuring Claude receives properly formatted tool specifications. It includes a built-in browser-based inspector, the [MCP Inspector](#mcp-inspector-mcp-inspector), to test a server without connecting it to a full application. The course's example: a document management server with two core tools, one to read documents and another to update them (a simple find-and-replace), the documents existing in memory as a simple dictionary where keys are document IDs and values are the content.

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### Decorator *(Décorateur)*

What the [MCP Python SDK](#mcp-python-sdk-sdk-python-de-mcp) uses to define [tools](#tool-outil): `@mcp.tool(…)` above a Python function. The decorator specifies the tool name and description, while the function parameters define the required arguments. Tool registration happens automatically through decorators. A [resource](#resource-ressource) is defined the same way, with `@mcp.resource(…)`: its URI and its mime_type.

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### Type hints *(Indications de type)*

The types written on a Python function's parameters (`doc_id: str`). With the [MCP Python SDK](#mcp-python-sdk-sdk-python-de-mcp), you use Python type hints and field descriptions instead of writing JSON schemas manually, and the SDK automatically generates the proper schema that Claude can understand. Type hints provide automatic validation.

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### MCP Inspector *(MCP Inspector)*

The built-in browser-based inspector of the [MCP Python SDK](#mcp-python-sdk-sdk-python-de-mcp) (the course's overview calls it the built-in MCP Server Inspector): it lets you debug and test your [MCP server](#mcp-server-serveur-mcp) in real-time, without connecting to a full application. With your Python environment activated (the project's README gives the exact command), you run it with `mcp dev mcp_server.py`: this starts a development server and gives you a local URL to open in your browser. Its interface is actively being developed, so it may look different, but the core functionality remains consistent: a Connect button to start your MCP server (the connection status changes from "Disconnected" to "Connected"), navigation tabs for Resources, Tools, Prompts and other features, a tools listing and testing panel. In the Tools section, "List Tools" shows all available [tools](#tool-outil) from your server; select one, and the right panel shows its details and input fields; "Run Tool" runs it, and the inspector shows both the success status and the actual returned data. You can test multiple tools in sequence to verify complex workflows: after an edit tool modifies a document, test the read tool to confirm the changes were applied. The inspector maintains your server state between tool calls, so edits persist. Instead of writing separate test scripts or connecting to full applications, you can quickly iterate on tool implementations, test edge cases and error conditions, verify tool interactions and state management, and debug issues in real-time: an immediate feedback loop that catches issues early.

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### Client session *(Session client)*

The actual connection to an [MCP server](#mcp-server-serveur-mcp), part of the [MCP Python SDK](#mcp-python-sdk-sdk-python-de-mcp). The [MCP client](#mcp-client-client-mcp) of the course's project consists of two main components: the MCP Client, a custom class you create to make using the session easier, and the client session. The client session requires careful resource management: connections must be properly cleaned up when you're done. That's why it is wrapped in your own class that handles all the cleanup automatically (the video: a very common practice, rather than using the client session directly). Through the session, the client implements its two essential functions: `list_tools()` accesses the session, calls its built-in `list_tools()` method and returns the [tools](#tool-outil) from the result; `call_tool()` passes the tool name and the input parameters (provided by Claude) to the server and returns the result (`await self.session().call_tool(tool_name, tool_input)`).

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### ReadResourceRequest/ReadResourceResult *(ReadResourceRequest/ReadResourceResult)*

The message types of a [resource](#resource-ressource) read, in its request-response pattern. When the [MCP client](#mcp-client-client-mcp) needs data, it sends a ReadResourceRequest with a URI to identify which resource it wants (the address of the resource, defined with the resource); the [MCP server](#mcp-server-serveur-mcp) processes the request, runs the function behind that URI and returns the data in a ReadResourceResult. In the course's example, the list of document names for an autocomplete: a ReadResourceRequest for `docs://documents`, a ReadResourceResult with the list of doc names. The result holds a contents list; the client accesses its first element, since it typically only needs one resource at a time. The response includes the actual content (text or data), a [MIME type](#mime-type-type-mime) that tells the client how to parse the content, and other metadata about the resource.

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### Direct resource *(Ressource directe)*

A [resource](#resource-ressource) whose URI is static and never changes, such as `docs://documents`: perfect for operations that don't need parameters. Also called a static resource; the [MCP Inspector](#mcp-inspector-mcp-inspector) lists direct/static resources under Resources. One of the two types of resources, with [templated resources](#templated-resource-ressource-paramétrée).

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### Templated resource *(Ressource paramétrée)*

A [resource](#resource-ressource) whose URI includes one or more parameters, such as `docs://documents/{doc_id}`: the Python SDK automatically parses them and passes them as keyword arguments to your function, each with the name it has in the URI (`doc_id`). For requests that need more selection or customization of what is asked for. The [MCP Inspector](#mcp-inspector-mcp-inspector) lists them under Resource Templates, where you provide values for the parameters. One of the two types of resources, with [direct resources](#direct-resource-ressource-directe).

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)

### MIME type *(Type MIME)*

A hint about what kind of data a [resource](#resource-ressource) returns. The server gives it with the mime_type parameter: "application/json" for structured data, "text/plain" for plain text, "application/pdf" for binary files. The [ReadResourceResult](#readresourcerequestreadresourceresult-readresourcerequestreadresourceresult) carries it, and the client checks it to determine how to process the content: if it's application/json, parse the text as JSON and return the parsed object; otherwise, return the raw text content. The [MCP Inspector](#mcp-inspector-mcp-inspector) shows it in each response, with the serialized data.

→ [schéma de l'architecture MCP](mindmap/mcp-architecture.png)
