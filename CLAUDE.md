# CLAUDE.md — Vault Personnel de Marc-Antoine

> Ce fichier est lu automatiquement par les agents IA (Claude, Gemini, Copilot).
> Il définit le contexte, les conventions et les règles de ce vault.
> **Ne pas supprimer. Mettre à jour régulièrement.**

---

## Qui je suis

Je suis Marc-Antoine, dirigeant d'une société spécialisée en infrastructures informatiques
(Cloud, DevOps, Kubernetes) en pivot vers l'édition de logiciels. Je suis aussi développeur
indépendant. Ces deux sphères sont complémentaires mais distinctes — certaines notes appartiennent
à l'une, à l'autre, ou aux deux.

**Stack principal :** Python, Kubernetes, AWS/Bedrock, Terraform, GitHub Actions, Docker  
**Outils IA utilisés :** Claude (Cowork & Code), GitHub Copilot, Gemini CLI, agents custom sur Bedrock  
**Éditeur principal :** VS Code

---

## À quoi sert ce vault

Vault personnel de test — objectif : valider la synchronisation Git multi-postes avec Obsidian,
explorer le workflow de capture + organisation de notes, et expérimenter les intégrations IA
avant de mettre en place un vault collectif d'équipe.

**Usages principaux :**
- Veille technologique (articles, talks, repos GitHub)
- Notes de travail et réflexions personnelles
- Journal de travail quotidien (optionnel)
- Brouillons d'idées et de décisions

---

## Structure des dossiers

```
vault-test/
├── CLAUDE.md          ← ce fichier
├── _inbox/            ← zone d'atterrissage : Web Clipper, idées brutes, notes non traitées
├── notes/             ← notes travaillées, références durables, synthèses
├── journal/           ← entrées quotidiennes (format YYYY-MM-DD.md)
├── _templates/        ← templates de notes (ne pas modifier le contenu directement)
└── _archive/          ← notes finies ou obsolètes (ne plus modifier)
```

**Règle d'or :** tout ce qui arrive atterrit dans `_inbox/`. On trie ensuite, pas avant.

---

## Conventions

### Nommage des fichiers
- Notes : `titre-en-kebab-case.md` (ex: `graphify-knowledge-graph.md`)
- Journal : `YYYY-MM-DD.md` (ex: `2026-05-12.md`)
- Pas d'espaces, pas de caractères spéciaux, pas de majuscules

### Frontmatter YAML (obligatoire sur toutes les notes de `notes/`)
```yaml
---
title: "Titre lisible de la note"
date: YYYY-MM-DD
tags: [tag-1, tag-2]
status: draft | active | archived
source: url ou "personnel"
---
```

### Tags
- Format : `lowercase-kebab-case` uniquement (ex: `kubernetes`, `agent-ia`, `veille-tech`)
- Réutiliser un tag existant avant d'en créer un nouveau
- Maximum 5 tags par note
- Tags principaux de ce vault : `veille-tech`, `devops`, `cloud`, `agent-ia`, `python`,
  `architecture`, `projet-perso`, `projet-societe`, `a-approfondir`

### Liens internes
- Lier systématiquement vers les notes existantes quand c'est pertinent
- Format : `[[nom-du-fichier]]` ou `[[nom-du-fichier|texte affiché]]`

---

## Ce que tu peux faire (agents)

- **Résumer** les notes de `_inbox/` en ~100 mots et proposer des tags
- **Créer des notes** dans `notes/` à partir d'une demande explicite, en respectant le template
- **Lier** les nouvelles notes aux notes existantes pertinentes
- **Mettre à jour** le frontmatter (tags, status) d'une note existante
- **Lire et synthétiser** n'importe quelle note ou ensemble de notes
- **Suggérer** un déplacement de `_inbox/` vers `notes/` ou `_archive/`
- **Créer des entrées de journal** dans `journal/` si demandé

## Ce que tu NE dois PAS faire (agents)

- **Ne jamais modifier** les notes dans `_archive/`
- **Ne jamais créer** de dossiers hors de la structure définie ci-dessus
- **Ne jamais supprimer** de fichiers — déplacer vers `_archive/` si obsolète
- **Ne jamais créer** de nouveaux tags sans les proposer d'abord
- **Ne pas modifier** les fichiers dans `_templates/`
- **Ne jamais committer** ou pusher vers Git — c'est le rôle du plugin Obsidian Git

---

## Projets actifs (à maintenir à jour)

- **KM Agentique** : mise en place d'un système de knowledge management d'équipe
  augmenté par IA — vault individuel (cette phase) → vault collectif → automatisation
- **Vault collectif d'équipe** : à démarrer en Phase 2 après validation de ce vault

---

## Notes pour les agents

- Ce vault est en phase de test. La priorité est la validation du workflow Git, pas la perfection
  des notes.
- Si une convention n'est pas claire, demander avant d'agir.
- Le fichier `_templates/note.md` est la référence pour créer toute nouvelle note.
- En cas de doute sur le dossier de destination : mettre dans `_inbox/`.
