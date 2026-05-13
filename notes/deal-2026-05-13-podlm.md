---
title: "Deal — PODLM (AI Podcast Maker iOS App)"
date: 2026-05-13
tags: [projet-perso, a-approfondir]
status: draft
source: https://flippa.com/12791061-ai-podcast-maker-podlm
verdict: APPROFONDIR
workflow: quick_screen
---

## Résumé exécutif

Application iOS (Flutter/Firebase) de création de podcasts IA, lancée en octobre 2024 (~7 mois d'existence). 28 800 téléchargements, revenus déclarés ~$400/mo de profit, prix demandé $6 500 (1,35× profit annualisé). Pas de domaine web identifiable — Ahrefs non applicable. Des incohérences dans les données financières déclarées méritent vérification. Pas de flag critique bloquant. **Verdict : ✅ APPROFONDIR** avec des due diligences spécifiques à l'App Store.

---

## Audit financier

| Métrique | Valeur |
|---|---|
| Profit mensuel déclaré | $400 /mo (range : $300–600) |
| Revenus mensuels déclarés | $300–600 /mo (~$600 récemment) |
| Dépenses mensuelles | ~$10–15 /mo (serverless) |
| Revenus annuels déclarés (12 mois) | $4 600 |
| Lifetime proceeds | $5 470 |
| Profit annualisé (moyenne déclarée) | ~$4 800 |
| Prix demandé | $6 500 |
| **Multiple calculé** | **1,35× profit annuel** |
| Benchmark app mobile < 12 mois | ~1–1,5× (décote 40–50% sur 2–3×) |
| Trend | Stable à légère croissance selon vendeur |
| Score fiabilité | **Faible** (pas de table mensuelle, incohérences internes) |

**Variance :** Aucune table mensuelle fournie dans le clip — impossible d'évaluer un éventuel spike.

**⚠️ Incohérence interne détectée :**
- Le vendeur déclare "Annual revenue over the past 12 months is approximately $4,600"  
- Or l'app a été lancée en **octobre 2024**, soit seulement ~7 mois avant le clip (mai 2026)  
- $4,600 sur 7 mois = ~$657/mo de moyenne, mais le claim actuel est "$300–600/mo"  
- Lifetime proceeds = $5,470 pour ~7 mois → $781/mo de moyenne lifetime  
- Ces trois chiffres ($400/mo, $4 600 annuel, $5 470 lifetime) ne sont pas réconciliables sans table détaillée  

---

## Audit trafic — Ahrefs

**Non applicable.** PODLM est une application iOS pure, sans site web identifié. Aucun domaine retrouvé via recherche web. Les métriques de distribution sont App Store uniquement.

**Métriques App Store (déclarées par le vendeur) :**

| Métrique | Valeur déclarée |
|---|---|
| Téléchargements totaux | 28 800+ |
| Téléchargements mensuels | ~1 000 /mo |
| Impressions App Store | 558 000+ |
| Conversion product page | 7,31% |
| Sessions par device actif | 3,36 |
| % acquisition organique | 78% (App Store Search 37,7% + App Referrer 40,3%) |
| Géographie principale | US (8 114), Taiwan (4 274), Germany (1 669) |

Score qualité trafic : **Non évaluable via Ahrefs.** Les métriques App Store semblent cohérentes (conversion 7,31% est raisonnable), mais nécessitent vérification directe via App Store Connect.

---

## Red flags

### 🟡 ATTENTION
- **Incohérences financières internes :** Trois métriques financières clés ($400/mo, $4 600 annual, $5 470 lifetime) ne sont pas réconciliables sans table mensuelle. Peut être de la rédaction approximative ou un signe d'embellissement.
- **Business < 12 mois :** Lancé en octobre 2024 (~7 mois). Les benchmarks exigent une décote significative, et la track record est trop courte pour valider la durabilité.
- **Dépendance SaaS multiple critique :** Le produit repose sur Gemini API, ChatGPT API, Google Cloud TTS, Firebase, et Adapty. Un changement de pricing de l'un de ces fournisseurs peut détruire les marges immédiatement. Les dépenses de $10–15/mo semblent très basses si l'app génère $600/mo — à vérifier (est-ce que les API costs sont réellement inclus ?).
- **Vendeur basé en Turquie :** Non critique en soi, mais la gestion de transition et le support post-vente peuvent être compliqués selon les zones légales/timezone.

### ℹ️ INFO
- **Absence de présence web :** Aucun site web, aucune présence SEO — Android reste entièrement à développer (travail significatif).
- **iOS uniquement :** Concentration du risque sur un seul marketplace soumis aux règles Apple (changement d'App Store Review Guidelines, commission 30%).
- **Stack Flutter cross-platform :** L'Android est théoriquement plus simple à déployer, mais nécessite une campagne ASO et test dédiés.

---

## Sources consultées

- Clip Flippa : `_inbox/AI Podcast Maker - PODLM - iOS App listed on Flippa.md`
- Ahrefs : non applicable (app mobile sans domaine web identifié)
- Web search : App Store links confirmés (aucun site web officiel trouvé)

---

## Verdict quick_screen

### ✅ APPROFONDIR

Prix bas (1,35×) pour une app à croissance organique forte sur App Store. Pas de flag critique bloquant. Cependant, le profil de risque est élevé : product très jeune, dépendances SaaS multiples, incohérences financières à clarifier.

**Lancer full_evaluation pour aller plus loin :** Demander accès à App Store Connect (courbe de téléchargements et revenus mois par mois), dashboard Adapty (MRR réel, churn), et décomposition des coûts API réels. Vérifier que les $10–15/mo de dépenses incluent bien les API costs à l'échelle actuelle.
