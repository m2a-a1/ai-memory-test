---
title: "Deal — Sentinel AI (sentinel-ai.dev)"
date: 2026-05-14
tags: [projet-perso, a-approfondir, agent-ia, saas]
status: draft
source: https://flippa.com/12843544-enterprise-ai-control-plane-for-evals-security-testing-observability-release-governance-and-sso-built-product-best-suited-for-the-right-acquirer
verdict: APPROFONDIR
workflow: quick_screen
---

## Résumé exécutif

Sentinel est une plateforme SaaS enterprise de contrôle IA (prompt management, évaluations, red-teaming, observabilité, SSO/SCIM) construite en 3 mois par un développeur hongrois. **Zéro revenu** : c'est une vente d'actif (codebase), pas une acquisition de business. Demande $9 900 pour la totalité du produit. Le code est décrit comme substantiel et production-ready. L'alignement avec le profil de Marc-Antoine (Cloud/DevOps/IA enterprise) est fort — verdict **APPROFONDIR**.

---

## Audit financier

| Métrique | Valeur |
|---|---|
| Modèle | SaaS enterprise — vente d'actif (pre-revenue) |
| Revenus mensuels | $0 (non commercialisé, déclaré par le vendeur) |
| Dépenses déclarées | Non communiquées |
| Profit moyen | $0 |
| Profit médian | $0 |
| Asking price | $9 900 |
| Multiple calculé | N/A (pas de revenu) |
| Multiple benchmark | N/A — vente de codebase |
| Spike détecté | N/A |
| Trend 3 derniers mois | N/A |
| Score fiabilité financière | **N/A** — vente d'actif, aucune donnée financière à auditer |

**Note :** La structure de cette vente est clairement celle d'une cession de codebase, pas d'une acquisition de business avec flux de trésorerie. Le prix de $9 900 rémunère l'ingénierie réalisée. Le vendeur est transparent sur l'absence de revenus. Il n'y a pas d'anomalie à détecter sur ce point.

**Subscribers :** 10 actifs, 0% churn déclaré. Impossible de déterminer si ces comptes sont payants ou gratuits (démo incluse dans le produit).

---

## Audit trafic — vendeur vs. Ahrefs

| Métrique | Déclaré (vendeur) | Ahrefs |
|---|---|---|
| Authority Score / DR | 0 (via Semrush Flippa widget) | **7.0** (stable avr–mai 2026) |
| Referring Domains | 10 | **66** (mai 2026) |
| Backlinks | 10 | Non mesuré (cohérent avec 66 refdomains) |
| Trafic organique | Non communiqué | **0** (0 keywords rankés) |
| Keywords rankés | Non communiqué | **0** |
| Trafic payant | 0 | **0** |

**Historique referring domains (Ahrefs) :**

| Période | Refdomains |
|---|---|
| Avant mars 2026 | 0 |
| Mars 2026 | 19 |
| Avril 2026 | 32 |
| Mai 2026 | 66 |

**Historique Domain Rating :** Apparu à 7.0 en avril 2026, stable à 7.0 en mai 2026. Aucune chute.

**Analyse :** La croissance rapide des refdomains (0→66 en 3 mois) est cohérente avec un nouveau produit lancé via GitHub, ProductHunt, HackerNews ou blogs tech. Elle n'est pas anormale pour un lancement agressif d'un produit developer-first. Le DR 7 est faible mais attendu pour un domaine de 3 mois. L'absence totale de trafic organique est normale (aucun effort SEO visible, produit enterprise vendu en direct/inbound).

**Delta vendeur vs. Ahrefs :** Le vendeur déclare 10 referring domains (via Semrush) vs. 66 constatés par Ahrefs — les deux outils mesurent différemment, pas de signal de manipulation.

**Score qualité trafic :** **Faible** (0 organique) — mais cohérent avec un SaaS enterprise B2B pré-commercial.

---

## Red flags

### 🔴 Critiques

Aucun flag critique détecté.

### 🟡 Attention

- **Pic de referring domains avant vente :** 0 → 66 refdomains en 3 mois. Non bloquant si lié à un lancement GitHub/PH/HN, mais à vérifier lors d'une full evaluation (quelles sont les sources exactes ?).
- **Revenus non vérifiables :** Par nature de la vente (pre-revenue). Le vendeur est transparent, mais un acheteur ne peut pas valider de flux de trésorerie réels.

### ℹ️ Info

- **Business < 12 mois :** 3 mois seulement. Décote logique sur la valeur, mais ici c'est une vente de codebase, pas un business multiple.
- **Question de motivation :** Pourquoi vendre à $9 900 après 3 mois sans essayer de monétiser ? Le vendeur dit "best suited for the right acquirer" — soit il manque de réseau commercial enterprise, soit il a rencontré une résistance marché non déclarée. À clarifier.
- **10 subscribers actifs :** Sans pricing ni accès dashboard, impossible de savoir si ce sont des comptes démo, beta gratuits ou payants.

### 🔍 Web search (non déclenché)

Aucun flag critique → web search non effectué selon le protocole.

---

## Analyse stratégique (hors protocole, ajoutée pour pertinence)

Le produit Sentinel couvre un espace réel et croissant (AI governance / LLMOps enterprise). La stack technique est moderne et pertinente : Next.js 15, PostgreSQL, ClickHouse, Redis, pnpm monorepo, Docker Compose. La feature list (SAML/OIDC SSO, SCIM, prompt registry, eval suites, red-team packs, audit logs, TypeScript SDK) est substantielle pour 3 mois de développement.

**Alignement profil Marc-Antoine :** Fort. Un opérateur avec une base clients enterprise Cloud/DevOps peut offrir ce produit en upsell ou en bundle. L'espace "AI control plane" est en émergence et peu d'outils open-source matures existent (LangFuse, Helicone sont les plus proches).

**Risques principaux :**
1. Qualité réelle du code non vérifiée (full code review nécessaire)
2. Saturation potentielle par les outils open-source concurrents
3. Go-to-market enterprise = cycle de vente long, nécessite un réseau existant
4. Le vendeur n'a pas validé le product-market fit

---

## Sources consultées

- Clip Flippa : `_inbox/Sentinel - SaaS listed on Flippa.md`
- Ahrefs : `site-explorer-metrics`, `site-explorer-metrics-history`, `site-explorer-domain-rating-history`, `site-explorer-organic-keywords`, `site-explorer-refdomains-history` (tous sur `sentinel-ai.dev`)
- Web search : non effectué (aucun flag critique)
- Wayback Machine : non effectué (aucun flag critique)

---

## Verdict quick_screen

### ✅ APPROFONDIR

**Aucun flag critique détecté.** Vente d'actif transparente, codebase bien décrit, alignement fort avec le profil acquéreur de Marc-Antoine (Cloud/DevOps/IA enterprise).

**Raison principale :** Le $9 900 demandé est un prix d'actif (pas de multiple de revenu), potentiellement justifiable si la qualité du code est au niveau annoncé. La vraie question est la faisabilité go-to-market depuis la base clients existante.

**Lancer une full_evaluation pour aller plus loin**, avec accès au code source, vérification des 10 subscribers, liste exacte des refdomains, et discussion avec le vendeur sur les raisons de la cession.
