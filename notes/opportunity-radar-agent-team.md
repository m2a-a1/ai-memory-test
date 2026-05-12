---
title: "Opportunity Radar — Design de l'équipe d'agents"
date: 2026-05-12
tags: [agent-ia, architecture, projet-perso, veille-tech]
status: draft
source: "personnel"
---

## Contexte

Système automatisé de veille et d'analyse pour détecter les opportunités de SaaS vertical dans des
secteurs "ennuyeux" sous-équipés. S'inscrit dans le tier **Discovery** de l'architecture système
globale (discovery → GTM → ops).

Objectif : produire chaque semaine un brief classé d'opportunités avec scoring, preuves terrain,
et recommandation d'action — sans intervention manuelle sur la collecte.

---

## Architecture — Vue d'ensemble

```
TIER 0 — ORCHESTRATION
└── opportunity_radar_orchestrator

TIER 1 — COLLECTE (parallèle)
├── market_scanner
├── review_miner
└── trend_detector

TIER 2 — ANALYSE (séquentiel)
├── competitive_analyst
├── fit_scorer
└── opportunity_analyst

TIER 3 — SYNTHÈSE
└── brief_writer

[HITL] → Validation humaine avant archivage en notes/
```

---

## Profils d'agents

### `opportunity_radar_orchestrator`
**Rôle :** Chef d'orchestre. Lance les agents Tier 1 en parallèle, agrège leurs outputs,
déclenche Tier 2 séquentiellement, puis Tier 3. Gère les quality gates entre tiers.

**Workflow modes :**
- `weekly_scan` — cycle complet, lancé automatiquement chaque semaine
- `deep_dive` — analyse approfondie sur une verticale ciblée manuellement
- `on_signal` — déclenché par un clip _inbox/ tagué `a-approfondir`

**Quality gate :** Ne déclenche Tier 2 que si Tier 1 produit ≥ 5 signaux scorés > seuil minimum.

---

### `market_scanner`
**Rôle :** Surveille les levées de fonds, lancements et acquisitions dans le SaaS vertical US/EU.
Cherche les secteurs où de l'argent commence à se déplacer mais où les acteurs sont encore peu nombreux.

**Méthodologie :**
1. Scrute les annonces de seed/Série A dans le SaaS vertical (Dealroom, Crunchbase, TechCrunch)
2. Filtre par secteurs cibles (industrie, BTP, agro, logistique, santé, services B2B)
3. Identifie les patterns récurrents : même problème résolu dans plusieurs pays = signal fort

**Sources (P0→P3) :**
- P0 : Crunchbase / Dealroom (levées < 3M€, vertical B2B)
- P1 : YC batches (W/S chaque année), newsletters SaaStr, Lenny's Newsletter
- P2 : ProductHunt (filtre "B2B tools", "productivity for [sector]")
- P3 : LinkedIn news, presse sectorielle FR (L'Usine Nouvelle, Le Moniteur, etc.)

**Output :** Liste de signaux avec : secteur, géographie, montant, description du problème résolu.

---

### `review_miner`
**Rôle :** Extrait les douleurs non résolues depuis les avis utilisateurs sur les outils existants.
Là où les gens se plaignent qu'il n'y a "pas de solution", c'est un marché.

**Méthodologie :**
1. Cible les catégories G2/Capterra avec des outils vieux (< 3.5 étoiles, dernière MAJ > 2 ans)
2. Mine les avis négatifs pour les patterns : "spreadsheet", "manuel", "pas d'API", "trop cher pour une PME"
3. Cherche les fils Reddit/HN du type "Ask HN: why isn't there a tool for X" ou "we use Excel because..."

**Sources (P0→P3) :**
- P0 : G2, Capterra (filtres : secteur industriel, rating < 3.8, reviews récentes)
- P1 : Trustpilot (B2B software), GetApp
- P2 : Reddit (r/smallbusiness, r/entrepreneur, r/SaaS, subreddits sectoriels)
- P3 : Hacker News ("Ask HN", fils "what tools do you use for X")

**Output :** Liste de douleurs non résolues avec verbatims, fréquence, secteur, taille des plaignants.

---

### `trend_detector`
**Rôle :** Détecte les verticales en émergence avant qu'elles deviennent des marchés saturés.
Cherche les signaux faibles : mots-clés en croissance, communautés qui se forment, réglementations qui créent de nouveaux besoins.

**Méthodologie :**
1. Suit les tendances de recherche sur des termes sectoriels + "logiciel", "outil", "automatiser"
2. Identifie les nouvelles réglementations FR/EU qui vont forcer des secteurs à se digitaliser
3. Repère les conférences/salons pro où des besoins émergent sans solution claire

**Sources (P0→P3) :**
- P0 : Exploding Topics, Google Trends (mots-clés sectoriels)
- P1 : Journal Officiel / EUR-Lex (nouvelles obligations de traçabilité, reporting, conformité)
- P2 : Agenda des salons professionnels FR (Industrie, BTP, Agri), LinkedIn Events
- P3 : Rapports France Num, BpiFrance sur la digitalisation des PME

**Output :** Liste de tendances avec : signal, secteur concerné, horizon temporel estimé, niveau de maturité.

---

### `competitive_analyst`
**Rôle :** Pour chaque opportunité identifiée par Tier 1, analyse l'état de la concurrence.
L'objectif est de confirmer que le marché est réel mais la concurrence encore faible ou vieillissante.

**Méthodologie :**
1. Identifie les 3-5 acteurs existants sur la verticale
2. Évalue leur santé : âge du produit, dernière mise à jour, trafic, avis, funding
3. Cherche les signaux de faiblesse : UX dépassée, absence d'API, pas de mobile, pricing rigide

**Sources (P0→P3) :**
- P0 : G2 / Capterra (profils produits, historique des reviews)
- P1 : Similarweb (trafic, tendances), BuiltWith (stack technique)
- P2 : LinkedIn (taille équipe, recrutements récents = signe de croissance ou non)
- P3 : Wayback Machine (évolution UI produit), changelogs publics

**Output :** Fiche concurrentielle par opportunité : acteurs, forces/faiblesses, fenêtre d'entrée estimée.

---

### `fit_scorer`
**Rôle :** Score chaque opportunité par rapport au profil spécifique : réseau de distribution existant
(clients infra/DevOps/Cloud), stack technique maîtrisée, contraintes de temps et de ressources du pivot.

**Méthodologie — grille de scoring (0-10 chaque axe) :**
- **Distribution** : est-ce que le réseau clients actuel donne accès à ce secteur directement ?
- **Tech** : est-ce que Python/Kubernetes/AWS/APIs couvre 80%+ de ce qu'il faut construire ?
- **Taille de marché** : proxy TAM — combien d'acteurs potentiels en France/EU ?
- **Complexité build** : MVP réalisable en < 3 mois solo ou petite équipe ?
- **Défendabilité** : effets de réseau, données propriétaires, coût de switch élevé ?

**Output :** Score composite + radar chart textuel + verdict : À creuser / Passer / Watch list.

---

### `opportunity_analyst`
**Rôle :** Synthétise les outputs de `competitive_analyst` et `fit_scorer` pour produire une fiche
d'opportunité consolidée. Identifie les hypothèses critiques à valider avant d'aller plus loin.

**Méthodologie :**
1. Croise signal marché + analyse concurrentielle + fit score
2. Formule les 3 hypothèses clés à tester (problème réel ? willingness to pay ? distribution accessible ?)
3. Propose une action concrète de validation à faible coût (5 entretiens, landing page, post LinkedIn)

**Output :** Fiche opportunité complète avec : score global, résumé, hypothèses, action de validation recommandée.

---

### `brief_writer`
**Rôle :** Produit le brief hebdomadaire final, formaté pour être archivé dans `notes/` du vault.
Classe les opportunités par score, met en avant les 2-3 priorités de la semaine, signale les tendances persistantes.

**Format de sortie :** Note Markdown conforme aux conventions du vault, avec frontmatter complet,
résumé en 3 phrases, tableau classé des opportunités, et section "À faire avant la prochaine run".

**Output :** Fichier `notes/opportunity-brief-YYYY-WXX.md` prêt à relire et valider.

---

## Flux d'artefacts

```
market_scanner ──┐
review_miner   ──┼──→ [signals.json] ──→ competitive_analyst ──→ fit_scorer ──→ opportunity_analyst ──→ brief_writer
trend_detector ──┘                                                                                              │
                                                                                                                ↓
                                                                                              notes/opportunity-brief-YYYY-WXX.md
                                                                                                    [HITL: validation manuelle]
```

---

## HITL Checkpoints

| Point | Déclencheur | Action humaine requise |
|-------|-------------|------------------------|
| Post Tier 1 | < 5 signaux collectés | Ajuster sources ou élargir critères |
| Post scoring | Toutes opportunités < 5/10 | Revoir grille de fit ou hypothèses sectorielles |
| Post brief | Toujours | Valider avant de committer dans notes/ |

---

## Fichiers à créer (prochaine étape)

```
teams/opportunity-radar/
├── team.yaml         ← définition complète des 7 agents
├── TEAM.md           ← documentation + diagramme
└── scoring-grid.yaml ← grille de fit scorer paramétrée
```

---

## Questions ouvertes

- Quels secteurs "ennuyeux" prioriser en premier pour calibrer les agents ? (BTP, agro, logistique ?)
- La grille fit_scorer doit-elle intégrer un critère "lien avec TechOS" pour détecter des synergies ?
- Fréquence de run : hebdomadaire suffit, ou bi-hebdomadaire au démarrage pour calibrer ?
