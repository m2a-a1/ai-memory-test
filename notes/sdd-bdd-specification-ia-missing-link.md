---
title: "SDD Writing Specifications for AI: BDD as the Missing Link"
date: 2026-06-01
tags: [veille-tech, medium, agent-ia, architecture]
status: active
source: "https://medium.com/@wasowski.jarek/sdd-writing-specifications-for-ai-bdd-as-the-missing-link-spec-driven-development-ad1b540b7f75"
author: "Jaroslaw Wasowski"
---

## Résumé

En 2026, les ingénieurs ne codent plus — ils spécifient. Le SDD (Spec-Driven Development) fait consensus, mais la forme de la spécification reste ouverte. Les formats traditionnels (SRS, HLD, LLD) échouent comme contrats pour les agents IA : trop vagues ou trop détaillés. Le BDD (Behavior-Driven Development) serait le chaînon manquant — la syntaxe Given/When/Then opère exactement au bon niveau d'abstraction, lisible par le métier et exécutable par la machine. Un scénario BDD génère automatiquement 5 niveaux de tests (unit, intégration, E2E, UAT, régression), réduisant le coût de production d'une feature de 60 à 80 % (étude BMW/CRITICAL Software : €0.12/script). Le rituel "Three Amigos" — 30 min/semaine — permet d'intégrer cette pratique sans outils nouveaux ni validation hiérarchique. Très actionnable pour un contexte DevOps/Cloud en pivot SaaS où la rigueur de spécification conditionne la qualité des agents.

## Points clés

- **BDD comme spécification exécutable** : les scénarios Given/When/Then sont le seul format lisible par le métier *et* directement exploitable par un agent IA sans traduction — ils opèrent au bon niveau d'abstraction entre SRS (trop vague) et LLD (trop détaillé).
- **Un scénario = 5 niveaux de tests** : unit, intégration, E2E, UAT et régression générés depuis un seul artefact — réduction estimée à 60–80 % du coût par feature, validée empiriquement à €0.12/script (AutoUAT / BMW+CRITICAL Software).
- **Le rôle de l'ingénieur a changé** : de codeur (2015) → prompt engineer (2023–2025) → *facilitateur de contrats métier/machine* (2026) ; la spec est le nouvel artefact primaire dans le dépôt.
- **Three Amigos en 30 min/semaine** : PM + dev + testeur écrivent ensemble le `.feature` file, l'IA génère code et step definitions — zéro outil nouveau, ROI mesurable dès le premier sprint.
- **CLAUDE.md/AGENTS.md comme garde-fou** : fichier Markdown dans le repo qui porte les principes architecturaux persistants et évite de les répéter dans chaque prompt agent.

## Notes liées

[[4-lines-every-claude-md-needs]], [[production-ready-ai-agents-mcp-cli-skills]], [[personal-harness-llm-wiki-obsidian]]

---

*Article original clipé dans [[_inbox/Jaroslaw Wasowski – SDD Writing Specifications for AI_ BDD as the Missing Link — Spec-Driven Development]]*
