# acquisition-desk

> Équipe de due diligence automatisée pour l'évaluation d'actifs digitaux.
> Version 0.1 — Mai 2026

---

## Rôle dans l'architecture globale

```
teams/
├── discovery/          ← qualification d'opportunités produit
├── gtm/                ← go-to-market
├── opportunity-radar/  ← veille SaaS vertical (détection d'opportunités)
└── acquisition-desk/   ← due diligence rachats d'actifs digitaux  ◀ ici
```

`acquisition-desk` est déclenché **manuellement** — un clip ou PDF de listing
est soumis, l'équipe produit un rapport de due diligence structuré avec verdict
et prix de négociation. Elle ne génère pas de signaux : elle les évalue.

---

## Agents & dépendances

```
listing_parser
      │
      ├──────────────────────┐
      ▼                      ▼
financial_auditor      traffic_auditor
      │                      │
      └──────────┬───────────┘
                 ▼
         red_flag_detector
                 │
         ┌───────┴───────┐
         ▼               ▼
      valuator       fit_scorer
         │               │
         └───────┬───────┘
                 ▼
           deal_writer
                 │
                 ▼
   notes/deal-YYYY-MM-DD-[slug].md
```

| Agent | Tier | Rôle en une ligne |
|-------|------|-------------------|
| `listing_parser` | 0 | Extrait et normalise les données brutes du listing |
| `financial_auditor` | 1 | Audite revenus, marges, multiples et variance |
| `traffic_auditor` | 1 | Évalue qualité, sources et défendabilité du trafic |
| `red_flag_detector` | 2 | Détecte les patterns de manipulation croisés |
| `valuator` | 3 | Calcule valeur juste et prix de négociation |
| `fit_scorer` | 3 | Score fit personnel et A1 Cloud |
| `deal_writer` | 4 | Produit le rapport final + questions due diligence |

---

## Workflow modes

### `full_evaluation` — mode standard
Évaluation complète d'un listing soumis manuellement.
Les agents 1 et 3 tournent en parallèle pour réduire le temps de traitement.
Deux HITL checkpoints : après `red_flag_detector` si >= 2 flags critiques,
et systématiquement après `deal_writer` avant tout engagement.

### `quick_screen` — pré-qualification rapide
Exécute uniquement `listing_parser` + `financial_auditor` + `red_flag_detector`.
Produit un verdict binaire **Approfondir / Passer** avec 3 raisons max.
Utile pour trier un volume élevé de listings sans investir le temps d'un full eval.

### `revaluation` — mise à jour d'un deal existant
Reprend un rapport existant (`deal-*.md`) et le met à jour avec de nouvelles
informations (réponse vendeur, due diligence partielle, négociation en cours).
Ne re-exécute pas `listing_parser` — repart des données déjà structurées.

---

## HITL Checkpoints

| Moment | Condition | Action requise |
|--------|-----------|----------------|
| Après `red_flag_detector` | >= 2 flags critiques 🔴 | Lire les flags, décider si l'évaluation continue |
| Après `deal_writer` | Toujours | Valider le rapport avant tout contact vendeur |

---

## Double grille d'évaluation

Chaque actif est évalué selon deux prismes distincts :

**Grille personnelle** — objectif revenus passifs complémentaires.
Critères : budget, effort opérationnel (< 5h/sem idéal), courbe d'apprentissage.

**Grille A1 Cloud** — objectif actif stratégique pour le pivot SaaS B2B.
Critères : alignement pivot, levier stratégique (base clients, tech embarquable),
compatibilité image de marque.

Un actif peut scorer faiblement côté personnel et fortement côté A1 Cloud,
ou l'inverse — les deux verdicts sont toujours distincts dans le rapport final.

---

## Benchmarks de référence (multiples Flippa)

| Catégorie | Multiple standard |
|-----------|------------------|
| Site contenu / SEO | 2–3× profit annuel |
| Affiliate site | 2–3× profit annuel |
| E-commerce | 2–4× profit annuel |
| App mobile | 2–3× profit annuel |
| Micro-SaaS établi | 3–5× ARR |
| Business < 12 mois | Décote 40–50% sur le multiple |

---

## Bibliothèque de red flags

### 🔴 Critiques (workflow HITL si >= 2)
- **Pump before sell** — spike revenus 1–3 mois avant vente sans explication
- **Trafic géo suspect** — vendeur localisé dans pays source de trafic faible valeur
- **Dépenses cachées** — écart > 30% entre dépenses déclarées et implicites
- **Revenus non vérifiables** — screenshots uniquement, pas d'accès API natif
- **Actifs non transférables** — comptes affiliés bloqués par CGU partenaire
- **Google pénalisé** — Bing/Yandex dominent, Google "en réévaluation"

### 🟡 Attention (à mentionner, non bloquants seuls)
- **Flipper professionnel** — vendeur > 5 transactions, vend < 2 ans d'existence
- **Variance extrême** — ratio max/min > 5× sur 12 mois
- **Engagement catastrophique** — durée session < 30s, taux < 0.5%
- **Texte généré IA** — langage pompeux, incohérences factuelles internes
- **Spike saisonnier non signalé** — vente post-Noël/Black Friday sans disclaimer
- **Email list disproportionnée** — trop petite vs. CA annoncé

### ℹ️ Info (non bloquants)
- Business < 12 mois — résilience non prouvée
- Dépendance fournisseur unique
- Stack technique obsolète
- Support post-vente < 30 jours

---

## Format de sortie

Tous les rapports sont archivés dans `notes/` du vault selon la convention :
```
notes/deal-YYYY-MM-DD-[asset-slug].md
```

Frontmatter obligatoire :
```yaml
---
title: "Deal — [Nom de l'actif]"
date: YYYY-MM-DD
tags: [projet-perso, a-approfondir]
status: draft
source: URL
verdict: ACQUÉRIR | NÉGOCIER | PASSER
prix_juste: $X
prix_negociation: $X
---
```

---

## Historique des évaluations

| Date | Actif | Verdict | Prix juste |
|------|-------|---------|------------|
| 2026-05-12 | ForCar.org (quick_screen) | — | — |

*Mettre à jour après chaque run.*
