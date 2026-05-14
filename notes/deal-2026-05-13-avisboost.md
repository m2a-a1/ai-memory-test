---
title: Deal — AvisBoost (avisboost.net)
date: 2026-05-13
tags:
  - projet-perso
status: draft
source: https://flippa.com/12757441-saas-generateur-de-revenus-recurrents-base-sur-avis-google-et-fidelisation-client-automatise-scalable-pret-a-exploiter-immediatement
verdict: PASSER
workflow: quick_screen
---

## Résumé exécutif

AvisBoost est un SaaS B2B français de 4 mois visant les professionnels locaux (gestion d'avis Google, fidélisation, RDV, devis). Le listing ne présente **aucune donnée financière** (profit affiché : "-/mo") et aucun trafic vérifiable. Ahrefs confirme : DR=0, 0 trafic organique, 0 keyword ranké, et 67 referring domains constitués à 100% de liens spam (itxoft-*.site, fiverr-*.site). Demandé à $11 185 USD. **Verdict : ❌ PASSER** — deux flags critiques (revenus invérifiables + delta vendeur/Ahrefs sur l'existence même d'un business) et link building artificiel patent.

---

## Audit financier

| Donnée | Valeur |
|---|---|
| Mois disponibles | 0 (aucune donnée fournie) |
| Profit moyen / mois | null |
| Profit médian | null |
| MRR déclaré | non communiqué |
| Churn déclaré | 0% (vraisemblablement 0 client) |
| Asking price | $11 185 USD (indicatif, "open for negotiation") |
| Multiple demandé | ∞ (0 revenu déclaré) |
| Multiple benchmark SaaS < 12 mois | 1,5–2,5× ARR après décote 40–50% |
| Spike avant vente | N/A (aucune donnée) |
| Trend 3 mois | N/A |
| Score fiabilité financière | **FAIBLE** |

**Observations :** Le listing présente ce produit comme un « générateur de revenus récurrents » avec un modèle d'abonnement à 590 €/mois, mais aucun tableau financier, aucune capture de revenus, aucune donnée MRR n'est fourni. La section "Financials (monthly)" est vide et le profit mensuel affiché est littéralement "-". Il s'agit d'une vente de code/actif, pas d'une vente de business rentable.

---

## Audit trafic — vendeur vs. Ahrefs

| Métrique | Déclaré vendeur | Ahrefs (2026-05-13) | Delta |
|---|---|---|---|
| Trafic organique | non communiqué | **0** | N/A |
| Keywords rankés | non communiqué | **0** | N/A |
| Domain Rating | non communiqué | **0.0** | N/A |
| Referring domains | non communiqué | **67** (100% spam) | N/A |
| Trend trafic 24 mois | non communiqué | aucun historique | N/A |
| Score qualité trafic | — | **FAIBLE** | — |

**Évolution referring domains (Ahrefs) :**

| Période | Referring domains |
|---|---|
| Jan–Feb 2026 | 0 |
| Mars 2026 | 20 |
| Avril 2026 | 37 |
| Mai 2026 | 67 |

**Analyse qualitative des backlinks :** Les 15 premiers referring domains par DR sont tous marqués `is_spam: true` avec 0 trafic chacun. Les domaines suivent des patterns manifestes de PBN/spam Fiverr : `itxoft-proven-seo-strategies.site` (DR 76), `itxoft-organic-seo-growth.site` (DR 76), `fiverr-seo-for-small-businesses.site` (DR 73), etc. La montée de 0 à 67 domaines en 3 mois avant la vente est entièrement artificielle.

---

## Red flags

### 🔴 Flags critiques

**1. Revenus non vérifiables**
Aucune donnée financière fournie dans le listing. Le profit mensuel est affiché "-/mo", la section "Financials (monthly)" est vide. Le vendeur demande $11 185 pour un produit sans revenu prouvé. Pas d'accès Analytics, pas de capture de revenus, pas d'intégration Stripe ou équivalent mentionnée.

**2. Delta vendeur/Ahrefs — claim "SaaS générateur de revenus récurrents" vs. réalité**
Le titre et la description positionnent AvisBoost comme un business avec MRR établi ("revenus récurrents", "scalable", "prêt à exploiter immédiatement"). Ahrefs montre : DR=0, 0 trafic organique, 0 keyword ranké. Le 0% de churn déclaré est cohérent avec l'absence de clients plutôt qu'avec une rétention excellente. L'écart entre le discours commercial et les métriques réelles est total.

### 🟡 Flags attention

**3. Pic de referring domains avant vente — link building artificiel**
0 → 20 → 37 → 67 referring domains en 3 mois. 100% des backlinks sont des domaines spam Fiverr/PBN (is_spam=true, 0 trafic, patterns répétitifs : itxoft-*.site, fiverr-*.site). Objectif probable : gonfler artificiellement les métriques Ahrefs pour justifier la demande de prix.

**4. Business < 12 mois**
4 mois d'existence. Aucun historique de performance, aucun cycle saisonnier documenté, aucune preuve de product-market fit.

**5. Multiple de valorisation inacceptable**
$11 185 pour 0 revenu déclaré = multiple infini. Même en supposant un MRR de 590 €/mois (1 seul client), le multiple serait ~16× le profit annuel estimé — très largement au-dessus du benchmark SaaS early-stage (1,5–2,5× ARR après décote).

### ℹ️ Points d'information

- **Dépendances SaaS tierces :** Supabase (BDD) et n8n (automatisation) génèrent des coûts récurrents non chiffrés dans le listing. Ces comptes devront être transférés ou recréés.
- **Marché réel :** Le segment "avis Google + fidélisation PME" est concurrentiel (Google Business Profile natif, Trustpilot, Avis Vérifiés). La différenciation "tout-en-un" reste à prouver sur un marché qui existe déjà.

---

## Sources consultées

- **Clip Flippa :** `_inbox/AvisBoost - SaaS listed on Flippa.md`
- **Ahrefs — site-explorer-metrics** (avisboost.net, 2026-05-13, mode=subdomains)
- **Ahrefs — site-explorer-metrics-history** (2024-05-01 → 2026-05-13, monthly)
- **Ahrefs — site-explorer-domain-rating-history** (2024-05-01 → 2026-05-13, monthly)
- **Ahrefs — site-explorer-refdomains-history** (2024-05-01 → 2026-05-13, monthly)
- **Ahrefs — site-explorer-referring-domains** (top 15 par DR, mode=subdomains)
- **Web search :** `avisboost.net Flippa review scam complaint` → aucun résultat spécifique
- **Web search :** `"avisboost" Flippa acquisition avis` → aucun résultat spécifique
- Wayback Machine : non consulté (aucun flag "pump before sell" ou "Google pénalisé" au sens strict — le site est simplement inexistant en termes de trafic)

---

## Verdict quick_screen

### ❌ PASSER

Deux flags critiques cumulés : **revenus totalement invérifiables** (aucune donnée financière fournie) et **décalage total entre le discours vendeur ("SaaS générateur de revenus récurrents") et la réalité Ahrefs** (DR=0, 0 trafic, 0 keywords). Le pic de 67 referring domains en 3 mois constitués à 100% de liens spam Fiverr/PBN est un signal de manipulation délibérée des métriques avant vente.

Il s'agit d'une vente de code source pour un SaaS non validé commercialement, sans client prouvé, présentée comme un business établi. Le prix demandé ($11 185) n'est pas justifiable en l'état.
