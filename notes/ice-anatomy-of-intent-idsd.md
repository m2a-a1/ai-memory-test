---
title: "The Anatomy of Intent (ICE in IDSD)"
date: 2026-06-01
tags: [veille-tech, medium, agent-ia, architecture]
status: active
source: "https://medium.com/activated-thinker/the-anatomy-of-intent-ice-in-idsd-built-from-where-spec-driven-breaks-1597e5a16659"
author: "Kapil Viren Ahuja"
---

## Résumé

Suite directe de l'article IDSD, Ahuja détaille l'anatomie précise d'un Intent dans le cadre ICE. Un Intent bien formé contient trois éléments : **Goal** (l'outcome voulu en une phrase, sans "et", sans mention d'implémentation), **Constraints** (les qualités non-fonctionnelles en langage métier), et **Failure Conditions** (les vérifications binaires exécutables après coup). La distinction critique : si une règle influence le design du builder, c'est une contrainte ; si elle ne peut être vérifiée qu'après, c'est une failure condition. Le compartimentage est intentionnel : le builder ne voit pas les failure conditions pour éviter le reward hacking. Les success scenarios appartiennent aux Expectations, pas à l'Intent. L'auteur reconnaît se tromper lui-même régulièrement sur ces distinctions. Le modèle est universel (code, e-commerce, tout domaine). Très structurant pour écrire des prompts d'agents robustes.

## Points clés

- **Goal en une phrase, sans "et"** : dès qu'une conjonction apparaît, ce sont deux goals — la solution est de splitter, jamais d'ajouter des détails ; la méthode scale en multipliant les intents, pas en les alourdissant.
- **Contraintes = qualités non-fonctionnelles en langage métier** : "p99 < 200ms" est valide ; "utiliser Redis pour le cache" est une spec déguisée — les choix technologiques vont dans le Context, géré par le harness.
- **Failure Conditions doivent être binaires et observables** : chaque condition doit être évaluable par un script ou eval sans intervention humaine — c'est la ligne de séparation entre builder (qui exécute) et validator (qui vérifie).
- **Compartimentage anti-reward-hacking** : le builder ne voit pas les failure conditions — sinon il optimise pour passer les tests plutôt que pour l'outcome réel ; les success scenarios sont dans les Expectations pour la même raison.
- **L'Intent est la seule partie irréductible à l'humain** : le harness gère le Context, les Expectations peuvent être générées — mais l'Intent reste la responsabilité que personne d'autre ne peut assumer à ta place.

## Notes liées

[[4-lines-every-claude-md-needs]], [[production-ready-ai-agents-mcp-cli-skills]], [[idsd-intent-driven-software-development]]

---

*Article original clipé dans [[_inbox/Kapil Viren Ahuja – The Anatomy of Intent (ICE in IDSD). Built from Where Spec-Driven Breaks.]]*
