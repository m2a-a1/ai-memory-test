# Skill : acquisition-contact

> **Déclencheur :** L'utilisateur mentionne "prise de contact vendeur", "contacter le vendeur",
> "préparer le contact", ou référence un deal avec un quick_screen disponible.

---

## Objectif

Produire deux livrables pour initier le contact avec un vendeur dans le cadre d'une acquisition :

1. **Un message de prise de contact** — prêt à envoyer (Flippa, email, etc.)
2. **Un document questionnaire vendeur (.docx)** — à importer dans Google Drive et partager avec le vendeur

---

## Étape 1 — Lire le quick_screen

Demander ou identifier le chemin vers le quick_screen du deal.
Le lire entièrement. En extraire :

- **Type de contact** : vendeur direct (particulier / fondateur) ou intermédiaire (agent, mandataire, broker)
- **Nature de l'actif** : SaaS, contenu/média, e-commerce, code + IP, autre
- **Stade** : pre-revenue, early-revenue, profitable
- **Flags identifiés** : rouges, jaunes, informatifs
- **Points restants à éclaircir** (section "Éléments à vérifier en full evaluation" du quick_screen)
- **Plateforme de listing** : Flippa, Acquire.com, cold outreach, autre

---

## Étape 2 — Questions de contexte à poser à l'utilisateur

Poser ces questions via `AskUserQuestion` (une seule invocation, max 3 questions simultanées) :

**Question 1 — Angle d'approche**
Options : Acheteur sérieux mais prudent / Investisseur curieux / Prêt à avancer vite

**Question 2 — Stratégie prix au premier contact**
Options : Ne pas mentionner le prix / Signaler une fourchette basse / Mentionner la capacité de deal rapide

**Question 3 — Points prioritaires** (multi-select, basé sur les flags du quick_screen + éléments à vérifier)
Générer 3-4 options à partir du quick_screen + toujours proposer "Autre" implicitement via la réponse libre.

---

## Étape 3 — Générer le message de prise de contact

### Règles de rédaction

- **Langue** : anglais si plateforme internationale (Flippa, Acquire.com), français si cold outreach FR
- **Longueur** : 180–280 mots. Pas plus. Le vendeur est sollicité par d'autres acheteurs.
- **Ton** : adapter selon l'angle choisi :
  - *Sérieux mais prudent* → professionnel, factuel, montrer qu'on a lu le listing
  - *Investisseur curieux* → ouvert, questions larges, pas de pression
  - *Prêt à avancer vite* → signaler la capacité opérationnelle, délai court
- **Structure** :
  1. Accroche : montrer qu'on a vraiment lu le listing (référencer 1 élément spécifique)
  2. Positionnement : qui on est, pourquoi ce deal est pertinent pour nous
  3. Ce qu'on veut : accès au questionnaire + éventuellement accès repo / données
  4. Call-to-action clair et sans pression
- **Ne jamais** : mentionner le prix si stratégie "ne pas mentionner", promettre une clôture rapide si angle "sérieux mais prudent", utiliser des formules génériques ("I came across your listing")

### Format de sortie

Fournir le message dans un bloc Markdown avec :
- Le texte prêt à copier-coller
- Une note courte sur le canal d'envoi recommandé

Sauvegarder dans `notes/[deal-id]-contact-message.md` avec frontmatter YAML complet.

---

## Étape 4 — Générer le document questionnaire vendeur

### Structure du document

**Section A — Socle fixe** (toujours présente, 5 questions) :
1. Présentation du vendeur et de son parcours avec le projet
2. Raison principale de la vente
3. Inventaire complet des actifs inclus / exclus
4. Dettes, obligations contractuelles, litiges en cours
5. Disponibilité pour la passation post-vente

**Section B — Questions variables** (générées à partir du quick_screen et des priorités identifiées) :
- Minimum 5, maximum 10 questions
- Regroupées en sous-sections thématiques (ex: B1 — Technique, B2 — Droits IP, B3 — Financier)
- Chaque question calibrée sur les flags et les "éléments à vérifier" du quick_screen
- Zone de réponse après chaque question (espace vide clairement délimité)

### Génération technique

Utiliser `python-docx` (disponible sans installation) avec le script de référence :
`_templates/skills/acquisition-contact/gen_questionnaire_template.py`

Adapter les questions Section B au deal en cours. Ne pas modifier les questions Section A.

Sauvegarder dans `notes/[deal-id]-questionnaire-vendeur.docx`.

### Formatage

- En-tête avec fiche deal (nom, source, date, statut quick_screen)
- Note introductive : contexte du document, ton collaboratif
- Section A et B clairement séparées
- Zones de réponse : fond légèrement coloré, bordure discrète
- Pied de page : "Document confidentiel — Acquisition Desk · [Société] · [Année]"

---

## Étape 5 — Récapitulatif final

Après génération des deux livrables, fournir :

```
✅ Message de contact : notes/[deal-id]-contact-message.md
✅ Questionnaire vendeur : notes/[deal-id]-questionnaire-vendeur.docx

Actions suivantes :
1. Importer le .docx dans Google Drive → Partager avec le vendeur (accès "Peut modifier")
2. Envoyer le message via [plateforme] en joignant le lien Drive
3. Délai de relance si pas de réponse : [X] jours ouvrés
```

---

## Contraintes et règles

- Ne jamais inventer d'informations non présentes dans le quick_screen
- Si le quick_screen est incomplet ou absent : demander à l'utilisateur les éléments manquants avant de continuer
- Le document questionnaire est destiné au vendeur : ton neutre, collaboratif, sans jugement
- Le message de contact est destiné au vendeur : ne jamais révéler la stratégie de négociation interne
- Toujours sauvegarder les deux fichiers dans `notes/` avec les conventions de nommage du vault

---

## Référence — Deal Talezzi (cas d'usage initial)

Quick screen : `notes/deal-2026-05-15-talezzi.md`
Message généré : `notes/talezzi-contact-message.md`
Questionnaire : `notes/talezzi-questionnaire-vendeur.docx`
