---
title: "How to Build Production-Ready AI Agents: MCP, CLI, and Skills — the Right Tool for the Right Job"
author:
  - "Ana Bildea"
  - "PhD"
published: 2026-05-02
source: "https://medium.com/agentic-builders/how-to-build-production-ready-ai-agents-mcp-cli-and-skills-the-right-tool-for-the-right-job-701dc102863f"
image: "https://miro.medium.com/v2/resize:fit:1200/1*erWJQjhet4xM3YWGgANdmw.png"
created: 2026-05-18
tags:
  - "veille-tech"
  - "medium"
  - "agent-ia"
  - "architecture"
  - "a-approfondir"
status: "active"
---
---
title: "How to Build Production-Ready AI Agents: MCP, CLI, and Skills — the Right Tool for the Right Job"
author:
  - "[[Ana Bildea, PhD]]"
published: 2026-05-02T12:33:58Z
source: "https://medium.com/agentic-builders/how-to-build-production-ready-ai-agents-mcp-cli-and-skills-the-right-tool-for-the-right-job-701dc102863f"
image: "https://miro.medium.com/v2/resize:fit:1200/1*erWJQjhet4xM3YWGgANdmw.png"
created: 2026-05-18T09:19:47+02:00
tags:
  - "veille-tech"
  - "medium"
status: draft
---
![How to Build Production-Ready AI Agents: MCP, CLI, and Skills — the Right Tool for the Right Job](https://miro.medium.com/v2/resize:fit:1200/1*erWJQjhet4xM3YWGgANdmw.png)

> A step-by-step guide to the 2026 connectivity stack that powers enterprise agents at 110M monthly downloads.

---

## Mes notes

En 2026, les agents IA entrent en production à grande échelle. Ana Bildea décrit le "Connectivity Stack" moderne composé de trois couches complémentaires : les **Skills** (instructions réutilisables en markdown, portables entre clients), le **CLI** (exécution locale via outils Unix, efficace en tokens ~200 tokens/réponse), et le **MCP** (protocole d'intégration avec sémantique riche, OAuth, audit trails, mais coûteux en tokens à la naïve). Pour contrer l'explosion de tokens, deux techniques clés émergent : la **Progressive Discovery** (chargement différé des outils selon le besoin, réduction par 5 de la consommation de contexte) et le **Programmatic Tool Calling / Code Mode** (le modèle écrit un script d'orchestration dans un REPL plutôt que d'effectuer des appels séquentiels). Le message central : les meilleurs agents combinent Skills, MCP et CLI de manière contextuelle. Le MCP reste essentiel en contexte enterprise pour la gouvernance et la sécurité. Article très pertinent pour la mise en place d'agents de production dans le cadre du pivot SaaS.

**Notes liées :** [[personal-harness-llm-wiki-obsidian]], [[4-lines-every-claude-md-needs]], [[opportunity-radar-agent-team]]

## Points clés

- **Le triptyque Skills/CLI/MCP est complémentaire, non concurrent** : les Skills apportent le contexte métier, le CLI l'exécution légère et token-efficiente (~200 tokens/réponse), le MCP les intégrations enterprise avec gouvernance, OAuth et audit trails. Ne pas choisir entre eux — les combiner selon le contexte.
- **Progressive Discovery** : charger les outils à la demande via `tool_search` plutôt qu'en une seule fois réduit la consommation de contexte par un facteur 5 — pattern indispensable pour éviter la saturation du contexte dans les agents complexes (44 000–55 000 tokens en chargement naïf).
- **Code Mode (Programmatic Tool Calling)** : donner au modèle un environnement REPL (sandbox Python ou V8 isolate) pour qu'il écrive un script d'orchestration au lieu d'appels séquentiels réduit drastiquement la latence et le nombre de tours LLM nécessaires.
- **Concevoir pour les agents dès le départ** : les MCP servers ne doivent pas être de simples wrappers REST 1:1 — penser intention claire, sandbox d'exécution exposable, et possibilité de livrer des ressources UI (HTML/JS/CSS) directement via MCP.
- **Roadmap 2026 à surveiller** : Stateless Transport (déploiement Kubernetes/Cloud Run simplifié), Cross-App SSO via identity provider, et Skills over MCP (`skills/list`, `skills/get`) pour distribuer le contexte métier avec les outils.

---

## Article complet

## A step-by-step guide to the 2026 connectivity stack that powers enterprise agents at 110M monthly downloads.

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*erWJQjhet4xM3YWGgANdmw.png)

In 2024, we built demos. In 2025, we built coding agents. In 2026, we are putting general knowledge workers into production.

According to David Soria Parra from Anthropic, the Model Context Protocol (MCP) has reached a staggering 110 million monthly downloads — achieving this milestone faster than React. But as we scale agents to handle complex enterprise workflows across multiple SaaS applications and shared drives, a critical realisation has emerged: connectivity is not one thing.

If someone tells you there is a single solution to all your connectivity problems — be it computer use, MCP, or CLI — they are wrong. Top-tier agents don’t choose between tools — they use the entire connectivity stack simultaneously and effortlessly.

Here is the step-by-step guide to mastering the 2026 Connectivity Stack: Skills, MCP, and CLI.

## Understand the Connectivity Stack

Before writing code, you must understand the three distinct layers of modern agent connectivity. What exactly are Skills, CLI, and MCP, and how are they formed?

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*Wv6e4G50i225wZ5mSryhLQ.png)

- **Skills (Domain Knowledge)**: Reusable procedural instructions and markdown files that teach the model how to use tools. They are portable across clients and provide the necessary context for complex tasks. Skills are typically written by humans or generated by agents, and are loaded from local `.claude/skills/` directories or remote repositories. I love [superpowers](https://github.com/obra/superpowers) & [everything-claude-code](https://github.com/affaan-m/everything-claude-code).
- **CLI / Computer Use (Local Execution)**: The Unix-style approach to connectivity. It is highly composable, token-efficient (~200 tokens per response), and leverages the model’s pre-training on existing tools like `git`, `gh`, and `curl`. CLI tools are formed by installing standard binaries via package managers.
- **MCP (The Connective Tissue)**: The integration protocol that provides rich semantics, platform independence, and crucial enterprise features like OAuth, governance policies, and audit trails. MCP servers are formed by defining tools, resources, and prompts in code (e.g., `server.py ` or `server.ts`) and communicating via JSON-RPC 2.0 over HTTP or SSE.

## Executing a Task with MCP

When you need rich semantics, authorisation, and platform independence, MCP is the right tool for the job. It provides a schema-first, deterministic approach to tool selection.

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*E4qJxpmdHxh1cvzXHqmKOA.png)

MCP provides a deterministic, schema-first approach with built-in governance and audit trails.

However, this comes with a trade-off. In a naive implementation, loading all tool schemas upfront can consume massive amounts of context (e.g., 44,000–55,000 tokens). The response is a full, typed JSON object that is excellent for programmatic parsing but can be heavy on tokens.

**Pro Tip for Server Authors**:

> Always use descriptive function names, parameter names, and annotate parameters with descriptions. LLMs will be faster and more successful if they know exactly what is expected.

```c
# Annotated Tool Definitions
from typing import Annotated
from datetime import date
from enum import Enum

class Category(str, Enum):
    TRAVEL = "travel"
    MEALS = "meals"
    OFFICE = "office"

def submit_expense(
    amount: Annotated[float, "The expense amount in USD"],
    date: Annotated[date, "Date of the expense in YYYY-MM-DD format"],
    category: Annotated[Category, "The expense category"]
) -> str:
    """Submits a new expense report for approval."""
    pass
```

## Executing a Task with CLI

When the tool is already in the model’s pre-training data (like GitHub CLI or Git), CLI execution is incredibly powerful. It allows the model to compose commands using pipes and redirects, iterating on errors in a token-efficient manner.

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*bOwaJxZeHf3GGdgtZHDYvA.png)

CLI execution leverages pre-trained knowledge for token-efficient, composable workflows.

Instead of returning a massive JSON payload, the model can use tools like `jq` to filter exactly what it needs, returning a compact response of ~200 tokens.

## Progressive Discovery

The number one improvement we must make to our agent harnesses is **Progressive Discovery.** Instead of dumping all tools into the context window, we defer tool loading until the model actually needs them.

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*FXH5DXF7KnArFbqx6lN7AQ.png)

Progressive discovery reduces context bloat by loading tools on demand via tool search.

By providing a `tool_search` capability, the model can look up tools dynamically. This pattern can reduce context usage by a factor of 5.

## Programmatic Tool Calling (Code Mode)

If you want the model to orchestrate multiple tools, do not force it to make sequential tool calls. Sequential calls rely on inference latency for every step of the orchestration.

Instead, use `Programmatic Tool Calling` (or `Code Mode`). Provide the model with a `REPL` `(Read-Eval-Print Loop) ` environment — like a V8 isolate or a Python sandbox — and let it write a script to compose the tools together.

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*DP8In1gJHhQ5XBIcytt_oQ.png)

Code Mode allows the model to write orchestration scripts, drastically reducing latency.

```c
// Programmatic Tool Calling (Code Mode)
// Instead of multiple sequential LLM turns, the model writes this script once:
const issue = await mcp.call_tool("linear_get_issue", { id: "ENG-5121" });
const prs = await mcp.call_tool("github_list_prs", { repo: "frontend" });

// Use structured output to enforce types
const expectedType = z.object({ title: z.string(), status: z.string() }).passthrough();
const typedIssue = await extract("claude-haiku-4-5", expectedType, issue);py
```

## Build for Agents

As server authors, we must stop taking REST APIs and mapping them 1:1 into MCP servers. We need to design for agents from the ground up.

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*L_FOl3RYNdhabOkLOurD0Q.png)

Design tools with clear intent, expose sandboxes for orchestration, and ship UI resources.

> **Design for the Agent:** Build tools with clear intent, just as you would design an interface for a human.
> 
> **Reach for Code Mode:** Expose execution environments (like the Cloudflare MCP) so the model can orchestrate complex workflows.
> 
> **Ship an MCP App:** Use the rich semantics of MCP to ship UI resources (HTML + JS + CSS) directly through the wire, allowing the server to render its own interface in the client.

## MCP this year — What’s Coming

The MCP ecosystem is evolving rapidly to address enterprise needs and scale.

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*mjFcvbDtWOvEce8xWSjgCQ.png)

The 2026 roadmap includes stateless transport, cross-app access, and Skills over MCP.

- **Improved Core**: A new Stateless Transport protocol (proposed by Google) will make it easier to deploy MCP servers to Kubernetes and Cloud Run. Expect TypeScript and Python SDK v2.0 releases.
- **Integrate Everywhere:** Cross-App Access will allow single sign-on (SSO) across MCP servers using your company’s identity provider. Server discovery will be automated via `.well-known/mcp-server-card/server.json.`
- **Pushing the Boundary:** Skills over MCP will allow servers to ship domain knowledge alongside tools using `skills/list` and `skills/get endpoints`.

Choosing between MCP, CLI, and Skills based on context and requirements. Below is the end to end flow.

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*2pnDFTb8HAPFerhb-_iMJQ.png)

## Take Aways

The evolution of agent connectivity in 2026 proves that there is no silver bullet. The debate between MCP and CLI is a false dichotomy; the reality is that production-grade agents require a nuanced, multi-layered approach.

MCP’s criticisms — token overhead, auth gaps, and server quality — are real but solvable engineering challenges, not existential threats. The ecosystem is already self-correcting. Techniques like Progressive Discovery and Programmatic Tool Calling (Code Mode) drastically reduce token bloat and latency, proving that we can optimize the standard without abandoning it.

Furthermore, abandoning MCP in enterprise contexts introduces worse problems: auth fragmentation, zero audit trails, and vendor lock-in. The connective tissue provided by MCP is essential for governance and security at scale.

The future belongs to agents that seamlessly blend the domain knowledge of Skills, the secure connectivity of MCP, and the token-efficient execution of the CLI. The best agents will use all of it.

Thank you for reading. See you in the next one.

If this was useful, the clap button helps more people find it ❤️.

I write about agentic AI governance, agent architecture, optimisation and the infrastructure decisions that separate production systems  
from demos → [Subscribe](https://medium.com/subscribe/@anna.bildea)

Deploying long-running agents in a regulated environment? Let’s talk → [LinkedIn](https://www.linkedin.com/in/ana-bildea-phd-2339b728/)

---

**Source :** [How to Build Production-Ready AI Agents: MCP, CLI, and Skills — the Right Tool for the Right Job](https://medium.com/agentic-builders/how-to-build-production-ready-ai-agents-mcp-cli-and-skills-the-right-tool-for-the-right-job-701dc102863f)  
**Auteur :** Ana Bildea, PhD  
**Clipé le :** 2026-05-18T09:19:47+02:00
