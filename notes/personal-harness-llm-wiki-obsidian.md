---
title: "Building a Complete Personal Harness: LLM Wiki + Developer's Second Brain in Obsidian"
date: 2026-05-14
tags: [veille-tech, medium, agent-ia, architecture]
status: active
source: "https://medium.com/@roanmonteiro/building-a-complete-personal-harness-llm-wiki-developers-second-brain-in-obsidian-d7b61c7398ff"
author: "Roan Brasil Monteiro"
---

## Résumé

Cet article propose un tutoriel pratique complet pour configurer un vault Obsidian comme base de connaissance maintenue par agent IA, combinant le pattern "LLM Wiki" de Karpathy avec un "second cerveau" orienté développeur (ADRs, débriefs, projets). L'architecture repose sur trois zones physiquement séparées : `raw/` (contenu curé, lecture seule pour l'agent), `wiki/` (maintenu autonomement par l'agent) et `dev/` (collaboration hybride). Le `CLAUDE.md` racine définit les règles d'accès par zone, tandis que des skills personnalisés encodent les patterns de travail spécifiques — ADRs au format MADR, débriefs blameless. Trois chemins d'intégration sont présentés : filesystem direct + skills officiels Obsidian (recommandé), MCP via Local REST API, ou plugin prépackagé. Particulièrement pertinent pour un dirigeant DevOps en pivot vers l'édition logicielle : le vault accumule décisions architecturales, veille technologique et leçons des incidents, formant un asset cognitif à valeur croissante.

## Points clés

- **Séparation des zones comme principe de sécurité :** raw/ (lecture seule), wiki/ (agent autonome), dev/ (collaboration) — la frontière physique prévient la corruption des données curées et donne à l'agent une politique d'accès non ambiguë.
- **Le CLAUDE.md est la colonne vertébrale :** il doit définir qui écrit où, les conventions de wikilinks, les limites strictes (jamais de suppression sans confirmation), et les workflows d'ingestion — relu à chaque session, c'est le seul fichier qui prime sur tout.
- **Skills personnalisés = patterns métier encapsulés :** les skills adr-writing et debrief-writing permettent à l'agent d'opérer avec cohérence dans dev/ sans avoir à réexpliquer les conventions à chaque session.
- **Défense en profondeur contre les erreurs agent :** Git snapshots quotidiens, `allowed-tools` restreints dans les slash commands, et règle "présenter le plan avant d'exécuter" pour les ingestions externes — l'auditabilité est au cœur du dispositif.
- **Valeur monotonique croissante :** le 30e article ingéré se connecte à 5 précédents, le 100e à 30 — un asset cognitif irréplicable par un chatbot stateless, directement applicable pour la mise en place du vault collectif d'équipe en Phase 2.

## Notes liées

Aucun lien identifié.

---

*Article original clipé dans [[_inbox/Roan Brasil Monteiro – Building a Complete Personal Harness_ LLM Wiki + Developer's Second Brain in Obsidian]]*
