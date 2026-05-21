---
title: "How to Build Production-Ready AI Agents: MCP, CLI, and Skills — the Right Tool for the Right Job"
date: 2026-05-21
tags: [veille-tech, medium, agent-ia, architecture, a-approfondir]
status: active
source: "https://medium.com/agentic-builders/how-to-build-production-ready-ai-agents-mcp-cli-and-skills-the-right-tool-for-the-right-job-701dc102863f"
author: "Ana Bildea, PhD"
---

## Résumé

En 2026, les agents IA entrent en production à grande échelle. Ana Bildea décrit le "Connectivity Stack" moderne composé de trois couches complémentaires : les **Skills** (instructions réutilisables en markdown, portables entre clients), le **CLI** (exécution locale via outils Unix, efficace en tokens ~200 tokens/réponse), et le **MCP** (protocole d'intégration avec sémantique riche, OAuth, audit trails, mais coûteux en tokens à la naïve). Pour contrer l'explosion de tokens, deux techniques clés émergent : la **Progressive Discovery** (chargement différé des outils selon le besoin, réduction par 5 de la consommation de contexte) et le **Programmatic Tool Calling / Code Mode** (le modèle écrit un script d'orchestration dans un REPL plutôt que d'effectuer des appels séquentiels). Le message central : les meilleurs agents combinent Skills, MCP et CLI de manière contextuelle. Le MCP reste essentiel en contexte enterprise pour la gouvernance et la sécurité. Article très pertinent pour la mise en place d'agents de production dans le cadre du pivot SaaS.

## Points clés

- **Le triptyque Skills/CLI/MCP est complémentaire, non concurrent** : les Skills apportent le contexte métier, le CLI l'exécution légère et token-efficiente (~200 tokens/réponse), le MCP les intégrations enterprise avec gouvernance, OAuth et audit trails. Ne pas choisir entre eux — les combiner selon le contexte.
- **Progressive Discovery** : charger les outils à la demande via `tool_search` plutôt qu'en une seule fois réduit la consommation de contexte par un facteur 5 — pattern indispensable pour éviter la saturation du contexte dans les agents complexes (44 000–55 000 tokens en chargement naïf).
- **Code Mode (Programmatic Tool Calling)** : donner au modèle un environnement REPL (sandbox Python ou V8 isolate) pour qu'il écrive un script d'orchestration au lieu d'appels séquentiels réduit drastiquement la latence et le nombre de tours LLM nécessaires.
- **Concevoir pour les agents dès le départ** : les MCP servers ne doivent pas être de simples wrappers REST 1:1 — penser intention claire, sandbox d'exécution exposable, et possibilité de livrer des ressources UI (HTML/JS/CSS) directement via MCP.
- **Roadmap 2026 à surveiller** : Stateless Transport (déploiement Kubernetes/Cloud Run simplifié), Cross-App SSO via identity provider, et Skills over MCP (`skills/list`, `skills/get`) pour distribuer le contexte métier avec les outils.

## Notes liées

[[personal-harness-llm-wiki-obsidian]], [[4-lines-every-claude-md-needs]], [[opportunity-radar-agent-team]]

---

*Article original clipé dans [[_inbox/Ana Bildea, PhD – How to Build Production-Ready AI Agents_ MCP, CLI, and Skills — the Right Tool for the Right Job]]*
