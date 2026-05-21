---
title: "Anthropic's Engineer Said Kill Markdown. Here's What He Actually Meant."
date: 2026-05-21
tags: [veille-tech, medium, agent-ia, architecture]
status: active
source: "https://medium.com/generative-ai/anthropics-engineer-said-kill-markdown-here-s-what-he-actually-meant-36bee00c0ca2"
author: "Yanli Liu"
---

## Résumé

Thariq Shihipar, ingénieur lead chez Anthropic sur Claude Code, a déclenché un débat viral en affirmant que Markdown est un reliquat de l'ère de rareté des tokens et qu'HTML offre une meilleure expérience pour les sorties d'agents. Yanli Liu analyse calmement les deux camps et propose un framework de décision simple : le format doit suivre le lecteur, pas la mode. Si un humain lit (rapport stakeholder, code review), HTML offre navigation, sections repliables et visualisations interactives. Si seul un agent consomme le résultat, Markdown reste optimal : léger, parseable, diffable. Si les deux lisent, la combinaison gagnante est Markdown source versionnable + artifact HTML pour les lecteurs humains. L'overhead de 3-5x en tokens est réel à grande échelle (~$513/mois pour 100 rapports/jour sur Sonnet), mais souvent inférieur au coût du temps ingénieur gaspillé à naviguer dans un mur de texte. Les risques HTML à adresser : XSS dans le JS généré par IA, accessibilité WCAG et diffs bruités.

## Points clés

- **Framework de décision en 3 cas** : Humain lit → HTML (navigable, partageable). Agent uniquement → Markdown (léger, parseable, diffable). Les deux → Markdown source + artifact HTML. La décision suit le lecteur, pas le format.
- **Le Token Trap** : débat souvent mal cadré. À l'échelle individuelle, la différence est négligeable (~$0.17/rapport sur Sonnet). À 100 rapports/jour, c'est ~$513/mois supplémentaires. Mais le coût du temps humain à parser un mur Markdown ($19-38 par ingénieur/session) dépasse souvent l'économie réalisée.
- **Markdown est « promu », pas mort** : il passe du rôle de format d'affichage à celui de protocole machine-readable. C'est son vrai rôle dans l'ère agentique — source versionnable et diffable, pas interface finale pour les humains.
- **Risques HTML à ne pas ignorer** : XSS via JS généré par IA (imposer contrainte no-external-CDN, no-network-calls-at-runtime), manque d'accessibilité WCAG par défaut (à prompter explicitement), diffs bruités (solution : template HTML fixe + payload JSON pour les données variables).
- **Incitations à surveiller** : Anthropic bénéficie directement du switch vers HTML (plus de tokens = plus de revenus API) — ce qui ne invalide pas l'argument mais mérite d'être conscient lors de l'adoption wholesale.

## Notes liées

[[4-lines-every-claude-md-needs]], [[personal-harness-llm-wiki-obsidian]]

---

*Article original clipé dans [[_inbox/Yanli Liu – Anthropic's Engineer Said Kill Markdown. Here's What He Actually Meant.]]*
