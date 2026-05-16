# Skill : acquisition-contact

> **Déclencheur :** L'utilisateur mentionne "prise de contact vendeur", "contacter le vendeur",
> "préparer le contact", ou référence un deal avec un quick_screen disponible.

---

## Objectif

Produire deux livrables pour initier le contact avec un vendeur dans le cadre d'une acquisition :

1. **Un message de prise de contact** — prêt à envoyer (Flippa, email, etc.)
2. **Un document questionnaire vendeur (.docx)** — à importer dans Google Drive et partager avec le vendeur

Ces livrables ne sont générés qu'après validation explicite de l'approche retenue par l'utilisateur.

---

## Étape 1 — Lire le quick_screen

Demander ou identifier le chemin vers le quick_screen du deal.
Le lire entièrement. En extraire et mémoriser :

- **Type de contact** : vendeur direct (particulier / fondateur) ou intermédiaire (agent, mandataire, broker)
- **Nature de l'actif** : SaaS, contenu/média, e-commerce, code + IP, autre
- **Stade** : pre-revenue, early-revenue, profitable
- **Flags identifiés** : rouges, jaunes, informatifs
- **Points restants à éclaircir** (section "Éléments à vérifier en full evaluation" du quick_screen)
- **Plateforme de listing** : Flippa, Acquire.com, cold outreach, autre
- **Verdict** : À approfondir / À rejeter / À accélérer

---

## Étape 2 — Recueillir la stratégie post-acquisition

**C'est une étape de dialogue, pas un formulaire.** L'objectif est de comprendre ce que l'utilisateur
veut faire de l'actif s'il l'acquiert : cette vision doit informer à la fois le message (pourquoi
ce deal est pertinent pour lui) et les questions posées au vendeur (ce qu'il est critique de savoir
pour valider la stratégie).

### 2a — Inviter l'utilisateur à exposer sa stratégie

Demander directement, en prose, avant tout choix ou option :

> "Avant d'aller plus loin, j'aimerais comprendre votre vision post-acquisition pour ce deal.
> Qu'est-ce que vous comptez faire de [nom de l'actif] si vous l'achetez ?
> Pas besoin d'un plan détaillé — une direction suffit pour calibrer le message et les questions."

Laisser l'utilisateur répondre librement.

### 2b — Évaluer la réponse

Analyser la réponse sur trois axes :

**Clarté de la direction** : l'utilisateur sait-il ce qu'il veut faire de l'actif ?
- *Oui, claire* → passer à 2c
- *Vague ou exploratoire* → poser des questions ciblées (voir ci-dessous)
- *Absente ou "je ne sais pas encore"* → poser des questions ciblées

**Alignement avec le quick_screen** : la stratégie est-elle cohérente avec la nature de l'actif ?
Si incohérence détectée (ex : stratégie B2B sur un actif grand public), la signaler honnêtement
avant de continuer.

**Éléments manquants critiques** : identifier ce qui manque pour calibrer le message et les questions.
Les éléments critiques à connaître sont :
- Horizon d'investissement (flip rapide, développement long terme, intégration dans un projet existant)
- Qui va opérer l'actif (l'utilisateur seul, une équipe, externalisation)
- Marché cible visé (même niche, extension, pivot)
- Modèle économique envisagé (si différent de l'actuel)

### 2c — Poser les questions de clarification si nécessaire

Si des éléments critiques manquent, poser au maximum **3 questions ciblées** via `AskUserQuestion`,
formulées à partir des lacunes identifiées. Ne pas poser de questions dont la réponse peut être
inférée du quick_screen ou de ce qui a déjà été dit.

Exemples de questions selon le contexte :
- "Envisagez-vous de faire évoluer le modèle économique ou de repartir sur la même base ?"
- "Comptez-vous opérer cet actif vous-même ou le déléguer ?"
- "Est-ce un investissement autonome ou une brique d'un projet plus large ?"
- "Quel est votre horizon : revendre dans 12–18 mois, ou développer sur la durée ?"

**Règle** : ne jamais bloquer le workflow sur une stratégie imparfaite. Si l'utilisateur reste
vague après une relance, noter l'incertitude et continuer avec ce qui est disponible.

---

## Étape 3 — Questions de contexte tactique

Une fois la stratégie suffisamment claire, poser les questions tactiques via `AskUserQuestion`
(une seule invocation, max 3 questions) :

**Question 1 — Angle d'approche**
Options : Acheteur sérieux mais prudent / Investisseur curieux / Prêt à avancer vite

**Question 2 — Stratégie prix au premier contact**
Options : Ne pas mentionner le prix / Signaler une fourchette basse / Mentionner la capacité de deal rapide

**Question 3 — Points prioritaires à éclaircir** (multi-select)
Générer 3-4 options à partir des flags du quick_screen + des lacunes identifiées pour valider la
stratégie post-acquisition. Toujours proposer "Autre" via la réponse libre.

---

## Étape 4 — Présenter l'approche retenue pour validation

**Avant de générer quoi que ce soit**, exposer à l'utilisateur la logique de ce qui va être produit.
Cette étape est obligatoire. Elle prend la forme d'un mémo structuré en prose, pas d'une liste à puces.

Le mémo doit couvrir :

### 4a — Lecture du contexte vendeur
En 3-5 phrases : qui est le vendeur, ce qu'il vend réellement, ce qui motive vraisemblablement
la vente (inféré du quick_screen), et ce qui rend ce deal atypique ou standard.

### 4b — Votre position et votre stratégie
En 3-5 phrases : résumer la stratégie post-acquisition telle que comprise, identifier en quoi
elle est pertinente (ou risquée) au regard de l'actif, et ce que cela implique pour le premier contact.

### 4c — Approche retenue pour le message
Expliquer :
- Le ton choisi et pourquoi (angle + stratégie + profil vendeur)
- Ce qui sera mis en avant dans le message (et ce qui sera volontairement absent)
- Ce qui ne sera pas dit et pourquoi (ex : prix, stratégie de pivot, doutes sur la valeur)

### 4d — Logique des questions du questionnaire
Expliquer :
- Quels thèmes couvrent les questions Section B et pourquoi (lien explicite avec les flags et la stratégie)
- Ce qui a été priorisé et ce qui a été écarté
- Les questions "à double fond" : celles qui semblent neutres mais révèlent des informations critiques
  pour évaluer la faisabilité de la stratégie post-acquisition

### 4e — Demander la validation

Terminer par :
> "Est-ce que cette approche vous convient, ou souhaitez-vous ajuster quelque chose avant que je génère les documents ?"

**Ne pas continuer avant d'avoir reçu une réponse de validation.** Si l'utilisateur demande des ajustements,
les intégrer et re-présenter l'approche modifiée (ou juste confirmer les modifications si elles sont mineures).

---

## Étape 5 — Générer le message de prise de contact

### Règles de rédaction

- **Langue** : anglais si plateforme internationale (Flippa, Acquire.com), français si cold outreach FR
- **Longueur** : 180–280 mots. Pas plus. Le vendeur est sollicité par d'autres acheteurs.
- **Ton** : adapter selon l'angle choisi :
  - *Sérieux mais prudent* → professionnel, factuel, montrer qu'on a lu le listing
  - *Investisseur curieux* → ouvert, questions larges, pas de pression
  - *Prêt à avancer vite* → signaler la capacité opérationnelle, délai court
- **Structure** :
  1. Accroche : montrer qu'on a vraiment lu le listing (référencer 1 élément spécifique et non générique)
  2. Positionnement : qui on est, pourquoi ce deal est pertinent — ancré dans la stratégie post-acquisition
     sans la révéler en détail
  3. Ce qu'on veut : accès au questionnaire + éventuellement accès repo / données
  4. Call-to-action clair et sans pression
- **Ne jamais** :
  - Mentionner le prix si stratégie "ne pas mentionner"
  - Promettre une clôture rapide si angle "sérieux mais prudent"
  - Utiliser des formules génériques ("I came across your listing", "I'm interested in your business")
  - Révéler la stratégie post-acquisition si elle implique un pivot ou une valorisation différente de celle du vendeur

### Format de sortie

Fournir le message dans un bloc Markdown avec :
- Le texte prêt à copier-coller
- Une note courte sur le canal d'envoi recommandé

Sauvegarder dans `notes/[deal-id]-contact-message.md` avec frontmatter YAML complet.

---

## Étape 6 — Générer le document questionnaire vendeur

### Structure du document

**Section A — Socle fixe** (toujours présente, 5 questions) :
1. Présentation du vendeur et de son parcours avec le projet
2. Raison principale de la vente
3. Inventaire complet des actifs inclus / exclus
4. Dettes, obligations contractuelles, litiges en cours
5. Disponibilité pour la passation post-vente

**Section B — Questions variables** (générées à partir du quick_screen, des priorités identifiées
et de la stratégie post-acquisition) :
- Minimum 5, maximum 10 questions
- Regroupées en sous-sections thématiques (ex: B1 — Technique, B2 — Droits IP, B3 — Financier)
- Chaque question calibrée sur les flags, les "éléments à vérifier" du quick_screen,
  ET les informations nécessaires pour valider la stratégie post-acquisition
- Zone de réponse après chaque question (espace vide clairement délimité)
- **Ton neutre** : le vendeur ne doit pas percevoir la stratégie de l'acheteur dans les questions

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

## Étape 7 — Récapitulatif final

Après génération des deux livrables, fournir :

```
✅ Message de contact : notes/[deal-id]-contact-message.md
✅ Questionnaire vendeur : notes/[deal-id]-questionnaire-vendeur.docx

Actions suivantes :
1. Importer le .docx dans Google Drive → Partager avec le vendeur (accès "Peut commenter")
2. Envoyer le message via [plateforme] en joignant le lien Drive
3. Délai de relance si pas de réponse : [X] jours ouvrés
```

---

## Contraintes et règles

- Ne jamais générer les documents sans validation de l'étape 4
- Ne jamais inventer d'informations non présentes dans le quick_screen ou la conversation
- Si le quick_screen est incomplet ou absent : demander les éléments manquants avant de continuer
- Le document questionnaire est destiné au vendeur : ton neutre, collaboratif, sans jugement
- Le message de contact est destiné au vendeur : ne jamais révéler la stratégie de négociation
  interne ni la stratégie post-acquisition si elle implique un repositionnement de l'actif
- Toujours sauvegarder les deux fichiers dans `notes/` avec les conventions de nommage du vault

---

## Référence — Deal Talezzi (cas d'usage initial)

Quick screen : `notes/deal-2026-05-15-talezzi.md`
Message généré : `notes/talezzi-contact-message.md`
Questionnaire : `notes/talezzi-questionnaire-vendeur.docx`
