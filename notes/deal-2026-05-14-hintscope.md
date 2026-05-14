---
title: "Deal — Hintscope.com (AI sports predictions SaaS)"
date: 2026-05-14
tags: [projet-perso, a-approfondir]
status: draft
source: https://flippa.com/12800955-this-is-an-ai-sports-prediction-and-live-score-provider-providing-sports-predictions-betting-tips-match-statistics-and-real-time-sports-data-for-bettors
verdict: PASSER
workflow: quick_screen
---

## Résumé exécutif

SaaS de prédictions sportives IA (pay-per-use) et scores en direct, 3 mois d'existence, 24 abonnés actifs. Revenus: $0 (fév) → $120 (mars) → $234 (avril), expenses déclarées à $20/mo. Demande $5,599 (réduit de $6,999). Deux flags critiques bloquants : les comptes affiliés sportsbook (1xBet, Stake) sont personnels et non-transférables par nature, et les revenus ne couvrent que 2 mois sans vérification indépendante. Un pic de referring domains anormalement rapide (0 → 70 en 3 mois) renforce le signal de prudence.

## Audit financier

| Mois | Revenus | Dépenses | Profit |
|---|---|---|---|
| Fév 2026 | $0 | $0 | $0 |
| Mars 2026 | $120 | $20 | $100 |
| Avr 2026 | $234 | $20 | $214 |

| Métrique | Valeur |
|---|---|
| Profit moyen (3 mois) | $104.67/mo |
| Profit médian | $100/mo |
| Profit annualisé (moy. 2 derniers mois) | $1,884 |
| ARR basé sur Avr 2026 | $2,808 |
| Asking price | $5,599 |
| Multiple (ARR) | 1.99× ARR |
| Benchmark SaaS | 3–5× ARR (avec décote 40–50% < 12 mois → 1.5–3×) |
| Multiple vs. benchmark décoté | Dans la fourchette haute acceptable |
| Spike détecté | Non déterminable (seulement 2 mois de données) |
| Trend 3 mois | Croissance ($100 → $214 profit) |
| Score fiabilité financière | **Faible** — 2 mois de données, pas de vérification externe |

**Points critiques :**
- Le listing est affiché "réduit 20%" ($6,999 → $5,599). Signal possible que le listing stagne.
- Les $20/mo de dépenses déclarées couvrent uniquement cloud ($10/mo) + domaine prorata. L'API sports data est déclarée "Free" et l'IA est "per-report" (donc variable, non incluse dans les dépenses fixes). Cela signifie que les marges réelles seront inférieures à mesure que les volumes augmentent.
- Les sources de revenus sont mixtes : crédits AI (pay-per-use) + affiliés sportsbook. La part respective n'est pas précisée.

## Audit trafic — vendeur vs. Ahrefs

| Métrique | Déclaré (vendeur) | Ahrefs (hintscope.com) |
|---|---|---|
| Trafic organique | 1,594 page views/mo | 145 visites/mo (organique Google) |
| DR | Authority Score 0 (Semrush) | DR 0.9 |
| Keywords actifs | Non précisé | 6 (positions 11–50, 145 visites via 1 keyword) |
| Referring domains | 1 (Semrush) | 70 (Ahrefs — écart majeur) |
| Backlinks | 1 (Semrush) | — |
| Trend trafic | Démarrage | Uniquement depuis mai 2026 |
| DR trend | — | 0 → 0.9 (2 mois) |
| Score qualité trafic | **Faible** |

**Anomalie critique — refdomains :**
- Semrush (embed listing Flippa) : 1 refdomain
- Ahrefs : 70 refdomains en mai 2026
- Historique Ahrefs : 0 (nov–fév) → 17 (mars) → 40 (avr) → 70 (mai)
- Cette accélération de +17→+40→+70 sur 3 mois consécutifs est **anormale pour un site de 3 mois**. Cela correspond au pattern classique de link building artificiel (PBN ou achat de liens) avant une mise en vente. Le fait que Semrush en voit seulement 1 alors qu'Ahrefs en détecte 70 suggère que les liens viennent de domaines de faible qualité non indexés par Semrush mais crawlés par Ahrefs.

**Keyword principal :** "nepal national cricket team vs united arab emirates national cricket team match scorecard" (209K vol.) → position 26, génère 145 visites/mo. Trafic très dépendant d'un seul event sportif, non pérenne.

## Red flags

**🔴 CRITIQUE (2) :**

1. **Actifs potentiellement non transférables** : les comptes affiliés 1xBet et Stake sont des comptes personnels par définition. Les CGU 1xBet Affiliates indiquent explicitement que le compte est personnel ("belonging to an Affiliate") avec responsabilité exclusive du titulaire. Une cession de site ne transfère pas automatiquement les accès affiliés — le nouvel acquéreur devra créer ses propres comptes, potentiellement refuser son application, et repartir de zéro sur les commissions déjà générées. De plus, 1xBet opère dans une zone grise légale dans de nombreux pays européens (France, Allemagne) ce qui représente un risque réglementaire additionnel.

2. **Revenus non vérifiables** : seulement 2 mois de données de revenus ($120 + $234). Aucune preuve de connexion API Stripe/PayPal/Analytics mentionnée dans le listing. Le PayPal est "intégré" (pour les paiements) mais les captures d'écran des revenus ne sont pas fournies dans le clip. Historique insuffisant pour toute évaluation fiable.

**🟡 ATTENTION (2) :**

- **Pic de referring domains avant vente** : 0 → 17 → 40 → 70 en 3 mois, avec incohérence Semrush/Ahrefs (1 vs. 70). Signal fort de link building artificiel (PBN ou liens achetés) destiné à gonfler la présence SEO avant la vente.
- **Multiple inacceptable pour la maturité** : avec la décote standard de 50% pour les < 12 mois, la valorisation devrait être ~$1,400–$4,200. À $5,599, on est dans la fourchette haute voire au-dessus sur la base de 2 mois de données.

**ℹ️ INFO :**
- Business < 12 mois (3 mois) — historique trop court pour toute évaluation fiable
- Niche sportsbook/betting — risque réglementaire en Europe, conformité ARJEL/DGCCRF en France
- Dépendance fournisseur données sportives ("Free API" — à vérifier si pérenne)
- Support post-vente 3 mois inclus (positif)

## Sources consultées

- Clip Flippa : `_inbox/Hintscope - SaaS listed on Flippa.md`
- Ahrefs : `site-explorer-metrics`, `site-explorer-metrics-history`, `site-explorer-domain-rating-history`, `site-explorer-organic-keywords`, `site-explorer-refdomains-history` (target: hintscope.com, mode: subdomains)
- Web search : "hintscope.com flippa review scam complaint" → aucun résultat spécifique
- Web search : "1xBet affiliate account transfer non-transferable terms of service" → CGU 1xBet confirment nature personnelle du compte affilié
- Wayback Machine : non consulté (flags critiques de type non-transférabilité, pas pump-before-sell)

## Verdict quick_screen

**❌ PASSER**

2 flags critiques confirmés : comptes affiliés 1xBet/Stake non transférables (risque de perdre la principale source de revenus affiliate dès l'acquisition) + revenus non vérifiables sur seulement 2 mois. Le pic de refdomains (×70 en 3 mois) est un signal supplémentaire préoccupant sur la qualité du SEO. Le business a une stack technique solide (Next.js 15, Prisma, ClickHouse) mais l'actif commercial ne survivrait pas à une acquisition propre.
