---
title: "Deal — Hauszi Media Network (hauszi.de + 5 sites)"
date: 2026-05-14
tags: [projet-perso, a-approfondir]
status: draft
source: https://flippa.com/12794987-hauszi-pinterest-powered-home-decor-media-network-6-sites-22m-reach-1-5k-mo-multi-language-brand-with-strong-growth-potential?elinktoken=263591767
verdict: À APPROFONDIR
workflow: quick_screen
---

## Résumé exécutif

Réseau de 6 sites de décoration d'intérieur (hauszi.de principal + .nl, .fr, .es, .it, .net) monétisé via display ads et alimenté exclusivement par Pinterest. Le vendeur déclare ~$1,500/mo de revenus et $992/mo de profit (marge 99%). Prix de réserve $29,999 soit 2.5x le profit annuel déclaré — un multiple raisonnable pour un site de contenu. La principale inconnue bloquante est l'impossibilité de vérifier indépendamment le trafic Pinterest, qui constitue 100% des visites.

## Audit financier

| Métrique                   | Valeur                                                                           |
| -------------------------- | -------------------------------------------------------------------------------- |
| Revenus déclarés           | ~$1,500/mo (moyenne)                                                             |
| Profit déclaré             | $992/mo (moyenne)                                                                |
| Marge déclarée             | 99%                                                                              |
| Profit annualisé           | $11,904                                                                          |
| Starting bid               | $9,999                                                                           |
| Réserve                    | $29,999                                                                          |
| Multiple (réserve)         | 2.52× profit annuel                                                              |
| Multiple (starting bid)    | 0.84× profit annuel                                                              |
| Benchmark contenu/SEO      | 2–3× profit annuel                                                               |
| Trend 3 mois               | Inconnu — aucun tableau mensuel fourni                                           |
| Score fiabilité financière | **Faible** — aucune décomposition mensuelle, revenus via Google Drive uniquement |

**Points critiques :**
- Aucun tableau mois par mois disponible dans le clip → impossible de détecter un spike pré-vente ou une variance extrême
- Marge de 99% est suspicieuse : sur 6 domaines, les seules dépenses visibles seraient les renouvellements de domaines (~$60-100/an) et l'hébergement. Si la production de contenu est entièrement externalisée à une IA, cela pourrait être réel, mais cela crée une dépendance à signaler.
- Revenus accessibles uniquement via Google Drive (liens fournis dans la description). Pas d'accès API Stripe, PayPal ou réseau publicitaire.

## Audit trafic — vendeur vs. Ahrefs

| Métrique | Déclaré (vendeur) | Ahrefs (hauszi.de) |
|---|---|---|
| Trafic mensuel | 50,120 page views via Pinterest | 0 organique Google |
| Impressions | 22M monthly Pinterest impressions | N/A (Pinterest non indexé) |
| DR | Authority Score 2 (Semrush) | DR 24 |
| Keywords actifs | 47 (Semrush) | 2 (positions 49–87, 0 trafic réel) |
| Referring domains | 11 (Semrush) | 12 (Ahrefs) |
| Backlinks | 192 (Semrush) | — |
| Trend organique 24 mois | — | 0 sur toute la période |
| DR trend | — | Stable à 24 (après montée de 0.8 → 24 sur 12 mois) |

**Analyse :**
- Le delta Ahrefs/vendeur sur le trafic organique Google (0 vs. 50K pages vues) est **cohérent** avec le modèle déclaré : les visites viennent de Pinterest, pas de Google. Pas de flag critique sur ce point.
- Le DR de 24 en 12 mois est honnête et résulte d'une croissance organique régulière des refdomains (0 → 12 sans spike).
- En revanche, le trafic Pinterest est **entièrement non vérifiable** par des outils tiers. L'acheteur devra demander l'accès aux analytics Pinterest Business et Google Analytics avant toute décision.

## Red flags

**🔴 CRITIQUE (1) :**
- **Revenus non vérifiables** : les preuves de revenus sont uniquement via des liens Google Drive (info + earnings). Pas d'accès à un tableau de bord publicitaire (Google AdSense, Ezoic, Mediavine, etc.) ou à un outil de vérification externe. Sans cela, les chiffres ne peuvent pas être confirmés indépendamment.

**🟡 ATTENTION (3) :**
- **Absence de tableau financier mensuel** : impossible de vérifier s'il y a eu un spike de revenus dans les 1–3 mois précédant la vente. Demander au vendeur l'historique complet mois par mois.
- **Dépendance canal unique (Pinterest)** : 100% du trafic vient de Pinterest. Un changement d'algorithme Pinterest ou une suspension de compte peut effacer la totalité des revenus du jour au lendemain.
- **Marge 99% non justifiée** : sans détail des dépenses, impossible de valider. Demander la liste complète des outils, hébergements, domaines, et coûts de production de contenu.

**ℹ️ INFO :**
- Business d'environ 12 mois (borderline pour la décote 40–50%)
- Stack technique inconnue (aucune mention de CMS, hébergement, ou outils utilisés)

## Sources consultées

- Clip Flippa : `_inbox/Hauszi Media Network - Website listed on Flippa.md`
- Ahrefs : `site-explorer-metrics`, `site-explorer-metrics-history`, `site-explorer-domain-rating-history`, `site-explorer-organic-keywords`, `site-explorer-refdomains-history` (target: hauszi.de, mode: subdomains)
- Web search : "hauszi.de flippa review scam complaint" → aucun résultat spécifique à ce listing

## Verdict quick_screen

**🟡 À APPROFONDIR**

Le seul flag critique (revenus non vérifiables) n'est pas rédhibitoire en soi — c'est le standard Flippa pour les petits listings. Le multiple de 2.5x est raisonnable. Le trafic Pinterest à 22M impressions est **potentiellement réel** (le modèle est cohérent et le DR Ahrefs est honnête), mais **entièrement non vérifiable** sans accès aux outils du vendeur.

**À faire avant toute décision :**
1. Exiger accès en lecture au compte Pinterest Business Analytics (impressions, clics, audience)
2. Exiger accès en lecture au tableau de bord publicitaire (AdSense/réseau) avec 12 mois d'historique
3. Demander le tableau financier mensuel complet (12 mois)
4. Vérifier les autres domaines du réseau (hauszi.nl, .fr, .es, .it, .net) avec Ahrefs
5. Clarifier la stack technique et les coûts d'hébergement réels

Lancer `full_evaluation` si les données d'accès partagées confirment les chiffres.
