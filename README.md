# ai-kb-compiler
AI Knowledge Compiler using single source of truth

The term "Knowledge Compiler" is apt because, much like a software compiler transforms source code into an executable, this pipeline would transform source code and engineering artifacts into a structured, versioned, queryable knowledge model. That framing is more distinctive than a generic "RAG pipeline" and highlights the core innovation.

## Proposed architecture
```plaintext
GitHub
Rally/Jira
SharePoint
Confluence
CI/CD
ADR Repository
OpenAPI Specs
       │
       ▼
Knowledge Compiler
-----------------------------
• AST Parser
• Git Diff Analyzer
• Architecture Extractor
• API Extractor
• Release Comparator
• AI Summarizer
• Knowledge Graph Builder
-----------------------------
       │
       ▼
Versioned Knowledge Store
       │
       ▼
MCP Server
       │
       ▼
ChatGPT / Claude / VS Code / Cursor
```

## What large engineering companies do internally
Several companies are working on pieces of this problem, but none appears to solve exactly what you're describing: a release-versioned product knowledge base generated automatically from GitHub and related engineering systems.

Many large software companies have built proprietary systems that resemble parts of your vision:

- Google indexes code, design docs, bugs, code reviews, and ownership into internal developer search systems.
- Microsoft uses AI over GitHub, Azure DevOps, and engineering documentation to help developers navigate large codebases.
- Meta has internal code intelligence and dependency analysis tools that power developer workflows.
- Uber, Airbnb, and Netflix have internal developer portals and metadata catalogs to help engineers discover services and architecture.


```plaintext
| Company/Product                                                 | What they do                                                                           | Gap compared to your idea                                                                                                            |
| --------------------------------------------------------------- | -------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **[Glean](https://www.glean.com?utm_source=chatgpt.com)**       | Enterprise search across Slack, GitHub, Jira, Confluence, Google Drive with AI answers | Excellent enterprise search, but not a versioned product knowledge pipeline. ([Reuters][1])                                          |
| **[Graphora](https://graphora.io/?utm_source=chatgpt.com)**     | Converts documents into knowledge graphs                                               | Focuses on documents rather than understanding evolving software releases. ([graphora.io][2])                                        |
| **[KnowGraph](https://knowgraph.io/?utm_source=chatgpt.com)**   | Automatically captures GitHub, Slack, Zoom, PRs into a living knowledge graph          | Very close conceptually, but centers on organizational knowledge rather than release-aware product architecture. ([knowgraph.io][3]) |
| **[Kluris](https://kluris.io/?utm_source=chatgpt.com)**         | Git-backed knowledge for AI agents with human-reviewed entries                         | Relies on curated knowledge instead of deriving it from source code. ([Kluris][4])                                                   |
| **[DocBrain](https://docbrainapi.com/?utm_source=chatgpt.com)** | Builds documentation from PRs, Slack, CI, and IDE activity                             | Strong documentation automation, but not a full versioned software digital twin. ([DocBrain][5])                                     |
| **[Engram](https://engram-kb.org/?utm_source=chatgpt.com)**     | Persistent knowledge base for AI agents using Markdown                                 | Focuses on agent memory rather than software lifecycle knowledge. ([Engram][6])                                                      |

[1]: https://www.reuters.com/technology/us-enterprise-ai-search-startup-glean-raises-200-million-plans-hiring-spree-2024-02-27/?utm_source=chatgpt.com "US enterprise AI search startup Glean raises $200 million, plans hiring spree"
[2]: https://graphora.io/?utm_source=chatgpt.com "Graphora | Generative AI & Knowledge Graphs"
[3]: https://knowgraph.io/?utm_source=chatgpt.com "KnowGraph - AI-Powered Knowledge Base for Engineering Teams"
[4]: https://kluris.io/?utm_source=chatgpt.com "Kluris — The SME your team never had | AI agent knowledge base"
[5]: https://docbrainapi.com/?utm_source=chatgpt.com "DocBrain · Your organization's living knowledge graph"
[6]: https://engram-kb.org/?utm_source=chatgpt.com "Engram — Persistent Knowledge Base for AI Agents"


```

## Where current products stop

Most solutions follow this pattern:
```plaintext
GitHub
Slack
Confluence
Jira
SharePoint
      │
      ▼
Search + RAG
      │
      ▼
AI Chat
```
The AI retrieves documents but doesn't deeply understand how the software evolves.

Your proposed pipeline goes further:
```plaintext
GitHub (Source of Truth)
        │
        ▼
Release Event
        │
        ▼
Code Analysis
AST Analysis
Dependency Analysis
Architecture Extraction
API Discovery
Business Flow Extraction
        │
        ▼
Knowledge Graph
        │
        ▼
Release Snapshot
(v2.4)
        │
        ▼
AI Knowledge Base
```

