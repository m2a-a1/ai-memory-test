---
title: "The Method That Replaces Spec-Driven Development — IDSD"
date: 2026-06-01
tags: [veille-tech, medium, agent-ia, architecture]
status: active
source: "https://medium.com/activated-thinker/the-method-that-replaces-spec-driven-development-idsd-66e921f6cdf7"
author: "Kapil Viren Ahuja"
---

## Résumé

Ahuja dresse un constat sévère du SDD : les specs ont toujours des trous, et les agents IA les remplissent avec leurs propres hypothèses — générant des rework coûteux (il cite 3 jours perdus à ~$985). Sa réponse : IDSD (Intent-Driven Software Development), basé sur le cadre ICE — Intent, Context, Expectations. L'Intent est le primitif central : 5 éléments (objectif, contraintes, scénarios d'échec, scénarios de succès, connexions). Le Context est géré par le harness (outils), pas par l'humain. Les Expectations restent sous la propriété du demandeur. L'argument clé : OpenAI a produit sa spec Symphony de 2169 lignes *après* avoir fait tourner le système, pas avant — l'industrie vend l'output d'un processus comme si c'était la méthode. Directement applicable pour piloter des agents sur des projets clients réels, avec la discipline de rester dans la boucle pendant l'exécution.

## Points clés

- **SDD échoue car on ne peut pas tout spécifier à l'avance** : OpenAI a écrit sa spec Symphony (2169 lignes) *après* que le système tournait déjà — l'industrie présente cet output rétrospectif comme une méthode prospective.
- **ICE : Intent + Context + Expectations** — trois artefacts distincts avec des propriétaires humains clairs ; l'Intent est ce qu'on veut, le Context est comment (géré par le harness), les Expectations définissent "done" en termes métier.
- **L'Intent n'est pas une spec déguisée** : test : deux implémentations différentes peuvent-elles toutes deux satisfaire l'Intent ? Si oui → Intent valide ; si non → spec en déguisement.
- **Harness ≠ méthode** : spec-kit, BMAD, Agent OS sont des outils d'exécution — adopter le harness sans la méthode ICE produit les mêmes échecs à plus grande échelle, sur la facture du client.
- **La présence dans la boucle est une métrique** : rester actif pendant l'exécution de l'agent (pas seulement reviewer le diff final) est la seule défense contre la génération de code "qui a l'air juste mais ne l'est pas".

## Notes liées

[[4-lines-every-claude-md-needs]], [[production-ready-ai-agents-mcp-cli-skills]]

---

*Article original clipé dans [[_inbox/Kapil Viren Ahuja – The Method That Replaces Spec-Driven Development — IDSD]]*
