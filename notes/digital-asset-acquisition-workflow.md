---
title: "Workflow d'évaluation — Rachat d'actifs digitaux"
date: 2026-05-12
tags: [agent-ia, architecture, projet-perso]
status: draft
source: "personnel"
---

> Design du workflow d'évaluation automatisé pour les opportunités d'acquisition
> sur Flippa et plateformes similaires. S'appuie sur les patterns d'analyse déjà établis
> dans le projet "Rachats actifs digitaux".

---

## Objectif du workflow

Transformer un clip ou PDF de listing Flippa en rapport de due diligence structuré,
avec verdict d'achat, prix de négociation justifié, et liste de questions à poser au vendeur —
le tout en moins de 10 minutes, sans intervention manuelle.

**Double grille d'évaluation systématique :**
- Fit **personnel** (budget perso, compétences, objectif revenus passifs)
- Fit **A1 Cloud** (alignement stratégique avec le pivot SaaS, image de marque)

---

## Architecture — Vue d'ensemble

```
INPUT : clip _inbox/ ou PDF uploadé
          │
          ▼
┌─────────────────────┐
│   listing_parser    │  ← Tier 0 : extraction structurée
└─────────────────────┘
          │
    ┌─────┴──────┐
    ▼            ▼
┌────────────┐ ┌────────────┐
│  financial │ │  traffic   │  ← Tier 1 : audit parallèle
│  auditor   │ │  auditor   │
└────────────┘ └────────────┘
    │            │
    └─────┬──────┘
          ▼
┌─────────────────────┐
│  red_flag_detector  │  ← Tier 2 : détection croisée
└─────────────────────┘
          │
    ┌─────┴──────┐
    ▼            ▼
┌────────────┐ ┌────────────┐
│  valuator  │ │ fit_scorer │  ← Tier 3 : décision parallèle
└────────────┘ └────────────┘
    │            │
    └─────┬──────┘
          ▼
┌─────────────────────┐
│    deal_writer      │  ← Tier 4 : rapport final
└─────────────────────┘
          │
          ▼
  notes/deal-YYYY-MM-DD-[nom].md
  [HITL : validation avant toute action]
```

---

## Profils d'agents

### `listing_parser`
**Rôle :** Extrait et structure toutes les données brutes du listing.
Produit un JSON normalisé que tous les agents suivants consomment.
Élimine le bruit (navigation, ads, recommandations Flippa).

**Ce qu'il extrait :**
- Modèle de monétisation déclaré (AdSense, affiliate, SaaS, e-commerce, CPA…)
- Table financière complète (revenus/dépenses/profit mois par mois)
- Métriques trafic (sources, géographie, engagement si disponibles)
- Stack technique (langages, CMS, dépendances, hébergement)
- Actifs inclus dans la vente (domaine, code, BDD, comptes, email list…)
- Profil vendeur (ancienneté Flippa, nb de transactions, avis)
- Prix demandé, structure (enchère / BIN / négociation), deadline

**Output :** `listing.json` structuré

---

### `financial_auditor`
**Rôle :** Audite la réalité financière derrière les chiffres annoncés.
Cherche l'écart entre ce qui est présenté et ce qui est vérifiable.

**Méthodologie :**
1. **Analyse de variance** — calculer l'écart min/max/moyenne sur 12 mois, détecter les spikes récents (signal de pump before sell)
2. **Reconstruction des marges réelles** — dépenses annoncées vs. dépenses implicites dans les tableaux
3. **Calcul des multiples** — annualiser le profit, calculer le ratio prix/profit, comparer aux benchmarks Flippa par catégorie
4. **Trend analysis** — la trajectoire est-elle croissante, stable ou en compression ?
5. **Test de cohérence** — les revenus sont-ils cohérents avec le trafic annoncé ?

**Benchmarks Flippa par catégorie (référence interne) :**
- Site contenu/SEO : 2-3x profit annuel
- Affiliate site : 2-3x
- SaaS : 3-5x ARR
- E-commerce : 2-4x profit annuel
- App mobile : 2-3x profit annuel

**Red flags financiers à signaler :**
- Spike de revenus dans les 1-3 mois précédant la vente
- Dépenses inexpliquées (trou entre dépenses déclarées et dépenses visibles)
- Revenus à $0 pendant plusieurs mois consécutifs
- Multiple très supérieur au benchmark catégorie

**Output :** Section financière du rapport avec score de fiabilité (Haute / Moyenne / Faible)

---

### `traffic_auditor`
**Rôle :** Évalue la qualité, la stabilité et la défendabilité du trafic.
Un trafic fragile = un business fragile, quelle que soit la marge.

**Méthodologie :**
1. **Analyse des sources** — SEO organique > direct > email > social > paid. Classer par ordre de défendabilité
2. **Analyse géographique** — quelle part vient des marchés CPA/SaaS à haute valeur (US, UK, CA, AU) vs. marchés à faible valeur (IN, PH, KE) ?
3. **Engagement metrics** — durée de session, taux de rebond, pages vues. Seuils d'alerte : durée < 60s, rebond > 80%
4. **Concentration de trafic** — si > 80% d'une seule source, c'est une dépendance critique
5. **SEO health** — Authority Score, referring domains, age du domaine, keywords organiques

**Red flags trafic à signaler :**
- Trafic social > 80% (dépendance Meta/TikTok)
- Géographie incohérente avec le pitch commercial
- Vendeur géographiquement aligné avec les marchés "trafic de remplissage"
- Engagement catastrophique (< 30s, < 1% d'engagement)
- Google "en réévaluation" = potentiellement pénalisé

**Output :** Section trafic du rapport avec score de qualité (Haute / Moyenne / Faible)

---

### `red_flag_detector`
**Rôle :** Détecte les patterns de manipulation propres à Flippa et aux ventes d'actifs digitaux.
S'appuie sur les outputs de `financial_auditor` et `traffic_auditor` pour les croiser.

**Patterns surveillés :**

| Pattern | Signal | Niveau |
|---------|--------|--------|
| Pump before sell | Spike revenus 1-3 mois avant vente | 🔴 Critique |
| Flipper professionnel | Vendeur > 5 transactions, vend avant 2 ans | 🟡 Attention |
| Trafic géo suspect | Vendeur basé dans pays source du trafic faible valeur | 🔴 Critique |
| Dépenses cachées | Écart > 30% entre dépenses déclarées et réelles | 🔴 Critique |
| Texte généré IA | Langage marketing générique et pompeux, incohérences factuelles | 🟡 Attention |
| Google pénalité | "Re-evaluation phase", trafic Bing/Yandex dominant vs. Google | 🟡 Attention |
| Revenus non vérifiables | Screenshots uniquement, pas d'accès API AdSense/Stripe | 🔴 Critique |
| Actifs non transférables | Comptes affiliés non transférables selon CGU partenaire | 🔴 Critique |

**Output :** Liste ordonnée de red flags avec niveau de criticité

---

### `valuator`
**Rôle :** Calcule la valeur juste de l'actif et le prix de négociation recommandé.

**Méthodologie :**
1. Appliquer le multiple benchmark de la catégorie au profit annualisé réel (pas le profit "peak")
2. Appliquer une décote pour chaque red flag critique identifié (-10 à -20% par flag)
3. Calculer le prix plancher de négociation (80% de la valeur juste)
4. Comparer au prix demandé et formuler la stratégie : passer / négocier / acceptable

**Formule de base :**
```
Valeur juste = profit_annuel_moyen_12_mois × multiple_benchmark_catégorie × (1 - décotes_red_flags)
Prix négociation = valeur_juste × 0.80
```

**Output :** Valeur juste, prix de négociation, verdict prix (Sous-évalué / Juste / Sur-évalué / Inacceptable)

---

### `fit_scorer`
**Rôle :** Évalue l'adéquation de l'actif avec le profil et les objectifs.
Produit deux scores distincts : personnel et A1 Cloud.

**Grille personnelle :**
- Budget disponible (à calibrer par projet)
- Compétences nécessaires pour opérer l'actif (< 5h/semaine idéal)
- Niche cohérente avec l'expertise ou l'intérêt personnel
- Potentiel de revenus passifs (faible intervention = meilleur score)

**Grille A1 Cloud :**
- Alignement avec le pivot SaaS B2B (actif tech > actif contenu)
- Pas de conflit d'image de marque
- Levier stratégique possible (base clients, technologie réutilisable, distribution)
- Budget d'entreprise vs. budget personnel

**Output :** Score /10 pour chaque grille + commentaire de fit

---

### `deal_writer`
**Rôle :** Produit le rapport final structuré, prêt à archiver dans `notes/`.
Inclut obligatoirement une liste de questions de due diligence à poser au vendeur avant tout engagement.

**Structure du rapport :**
1. Résumé exécutif (3 phrases : modèle réel, verdict, prix juste)
2. Audit financier (avec tableau mois par mois reconstruit)
3. Audit trafic (sources, qualité, risques)
4. Red flags identifiés (classés par criticité)
5. Scoring fit (personnel + A1 Cloud)
6. Valuation (calcul détaillé)
7. Verdict final : Passer / Négocier à $X / Acceptable au prix demandé
8. **Questions due diligence** (10-15 questions précises à envoyer au vendeur)

**Format de sortie :** `notes/deal-YYYY-MM-DD-[nom-actif].md`

---

## Flux d'artefacts

```
clip _inbox/ ou PDF
       │
       ▼
listing_parser → listing.json
                      │
          ┌───────────┴───────────┐
          ▼                       ▼
  financial_auditor         traffic_auditor
          │                       │
          └───────────┬───────────┘
                      ▼
              red_flag_detector
                      │
          ┌───────────┴───────────┐
          ▼                       ▼
       valuator              fit_scorer
          │                       │
          └───────────┬───────────┘
                      ▼
                 deal_writer
                      │
                      ▼
         notes/deal-YYYY-MM-DD-[nom].md
                [HITL obligatoire]
```

---

## HITL Checkpoints

| Point | Déclencheur | Action |
|-------|-------------|--------|
| Post red_flag_detector | Flag critique 🔴 | Alerte immédiate — décision d'arrêt possible avant valuation |
| Post deal_writer | Toujours | Validation manuelle avant tout contact vendeur |

---

## Test du workflow — Run sur ForCar.org

Le clip `ForCar.org — VIN Decoder & Monroney Window Sticker Tool` en `_inbox/` est le
premier candidat pour valider ce workflow en conditions réelles.

Voir : [[opportunity-brief-2026-W20]] *(note à recréer avec la bonne grille)*

---

## Fichiers à créer (prochaine étape)

```
teams/deal-evaluator/
├── team.yaml           ← définition des 7 agents
├── TEAM.md             ← documentation + diagramme
├── benchmarks.yaml     ← multiples Flippa par catégorie
└── red-flags.yaml      ← bibliothèque de patterns de manipulation
```
