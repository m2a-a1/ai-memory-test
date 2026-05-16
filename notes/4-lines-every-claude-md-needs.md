---
title: "The 4 Lines Every CLAUDE.md Needs"
date: 2026-05-14
tags: [veille-tech, medium, agent-ia, a-approfondir]
status: active
source: "https://medium.com/gitconnected/the-4-lines-every-claude-md-needs-2717a46866f6"
author: "Yanli Liu"
---

## Résumé

Cet article analyse pourquoi quatre lignes comportementales dans un CLAUDE.md ont généré 60 000 étoiles GitHub — davantage que n'importe quel plugin ou framework. Inspirées du diagnostic d'Andrej Karpathy sur les modes d'échec des agents de code (suppositions non verbalisées, sur-engineering, modifications non sollicitées, absence de critères de succès), ces quatre lignes ciblent le comportement de l'agent plutôt que ses fonctionnalités : (1) ne pas supposer, exprimer ses incertitudes ; (2) coder le minimum nécessaire ; (3) ne toucher que ce qui est demandé ; (4) définir des critères de succès vérifiables et itérer. L'article pointe un "paradoxe de configuration" : au-delà d'un seuil (~12 000 chars au total dans Claude Code), plus de règles produisent un agent confus, pas discipliné. Les contraintes comportementales, transférables à tout projet et langage, surpassent les règles spécifiques. Directement actionnable : à appliquer au CLAUDE.md de ce vault.

## Points clés

- **Les 4 lignes ciblent le comportement, pas les fonctionnalités :** "Ne pas supposer / exprimer ses confusions", "Minimum de code", "Ne toucher que ce qui est demandé", "Définir des critères de succès" — chacune corrige un mode d'échec systématique des LLMs de code identifié par Karpathy.
- **Le paradoxe de configuration :** Claude Code plafonne à 6 000 chars par fichier de règles et 12 000 au total. Au-delà, les agents deviennent confus plutôt que disciplinés — analogie avec le manuel RH de 50 pages qu'on ne lit jamais vs. 4 principes qu'on retient.
- **La ligne 4 est un levier de capacité, pas seulement un garde-fou :** définir des critères de succès vérifiables + boucle d'itération exploite la capacité naturelle des LLMs à converger vers un objectif précis — c'est la seule des 4 lignes qui multiplie les capacités plutôt que de les contraindre.
- **Litmus test pour chaque règle :** "La supprimer ferait-elle commettre des erreurs irrecouvrables à l'agent ?" Si non, la retirer. Seules les règles comportementales transférables (indépendantes du stack) méritent leur place.
- **Ce qui ne doit PAS être dans CLAUDE.md :** patterns inférables du code existant, style guides redondants, listes de dépendances visibles dans package.json — l'agent lit le codebase, ne pas dupliquer ce qu'il peut déjà lire.

## Notes liées

Aucun lien identifié.

---

*Article original clipé dans [[Yanli Liu – The 4 Lines Every CLAUDE.md Needs]]*
