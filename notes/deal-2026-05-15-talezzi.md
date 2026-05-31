---
title: "Deal — Talezzi.com (Plateforme ebooks enfants multilingue)"
date: 2026-05-15
tags: [projet-perso, a-approfondir]
status: active
source: https://flippa.com/12767079-turnkey-multilingual-children-s-ebook-platform-in-10-languages-live-seo-indexed-85-pages-with-original-brand-ip-ready-for-a-content-driven-owner
verdict: À APPROFONDIR — Audit GitHub en cours
workflow: due_diligence
last_updated: 2026-05-31
---

# Deal — Talezzi.com

## Résumé exécutif (mis à jour post-questionnaire)

Talezzi.com est une plateforme d'ebooks pour enfants en 10 langues, construite en sprint solo
par un dev néerlandais. Entièrement pré-revenue, mais les réponses du vendeur ont **confirmé
deux hypothèses critiques** : les fondations GenAI sont réelles (Claude Code prompt files dans
le repo), et le cadre narratif (Universe Bible) est conçu pour être réutilisé sur d'autres univers.

L'actif est plus solide que le quick screen ne le laissait penser. La stratégie post-acquisition
envisagée (IP factory, multi-univers, multi-canaux) est directement validée par les réponses.
Prix demandé : $5,600. Fourchette de négociation recommandée : **$3,000–$3,500**.

**Verdict : 🟡 À APPROFONDIR — audit GitHub requis avant décision finale.**

---

## Ce qui a changé depuis le quick screen

### ✅ Hypothèses confirmées

**Fondations GenAI réelles.** Le repo contient des fichiers de prompts Claude Code (prompt7
à prompt11) qui documentent exactement comment chaque fonctionnalité a été construite et comment
le contenu est produit. Ces fichiers transfèrent avec la vente et servent de templates
réutilisables pour les développements futurs et la production de contenu.

**Universe Bible = framework réutilisable.** Le vendeur confirme explicitement que la structure
(monde, archétypes de personnages, guide visuel, formule narrative, principes éditoriaux) est
conçue pour être répliquée sur d'autres univers indépendants. La thèse multi-univers est validée.

**3 histoires en markdown = templates de production.** Les histoires complètes transfèrent en
format markdown et servent de référence pour le ton, la longueur, le rythme et la structure.
Avec la Bible et les prompt files, le workflow de production est documenté de bout en bout.

**Stripe plug-and-play.** Le flow complet est implémenté et testé en mode test. Activation :
swap des clés API + config webhook + product/price IDs dans le dashboard Stripe. 30–60 min.
Pas de développement supplémentaire.

**Stack minimale et propre.** Aucun service caché. Hetzner + Google Workspace ($16/mois total).
Déploiement Docker en 30 minutes selon le vendeur.

### 🟡 Points à surveiller (non résolus)

**Illustrations : placeholders uniquement.** Générées par un script Python/ReportLab one-shot,
non intégré dans le codebase principal. Les 30 PDFs sont committés dans le repo. Aucune
illustration professionnelle n'est incluse ni attendue. Pour la stratégie YouTube/KDP, des
visuels de qualité seront indispensables — c'est un coût à anticiper (AI image generation
ou illustrateur).

**SQLite en production.** Valide pour le stade actuel mais limitant pour la croissance.
Migration vers PostgreSQL nécessaire si le trafic monte sérieusement.

**Aucun compte social media.** Pas de présence social existante — à construire from scratch.

**Marque non déposée.** "Talezzi" disponible au moment de la vérification du vendeur (EU, UK, US).
À déposer en priorité post-acquisition.

**Hetzner VPS non transféré.** Le buyer redéploie sur sa propre infrastructure. Guide de
déploiement fourni + appel de passation. Budget infra à prévoir (~$10–20/mois selon le provider).

---

## Audit financier (inchangé)

| Métrique | Valeur |
|---|---|
| Revenus | $0 (pre-revenue) |
| Dépenses mensuelles | ~$16/mois (Hetzner $10 + Google Workspace $6) |
| Prix demandé | $5,600 (réduit de $9,500, -41%) |
| Fourchette négociation recommandée | $3,000–$3,500 |

**Justification de la fourchette révisée :** La confirmation des prompt files et du framework
réutilisable rehausse la valeur de l'actif par rapport au quick screen. $3,000–$3,500 reste
défendable sur un actif pré-revenue de 2 mois, mais intègre la valeur du système de production
documenté. Ouvrir à $2,800, viser $3,200.

---

## Assets inclus dans la vente (confirmés)

- Domaine talezzi.com (Squarespace → transfert registrar)
- Codebase complet (GitHub privé) — frontend React/Vite/TS + backend Node/Express/TS + SQLite
- Admin dashboard (intégré au même repo, même déploiement)
- Google Workspace email info@talezzi.com
- Google Search Console property
- 30 fichiers PDF (3 histoires × 10 langues)
- Universe Bible (markdown)
- 3 histoires originales en markdown complet
- Prompt files Claude Code (prompt7–prompt11)
- Documentation déploiement (ARCHITECTURE.md)
- 1–2h de support passation live

**Non inclus :** VPS Hetzner, compte Stripe, comptes social media (inexistants)

---

## Raison de la vente

Le vendeur a construit Talezzi en sprint parallèle à un poste d'ingénieur full-time. La
plateforme technique est complète, mais opérer une marque de contenu jeunesse (production
d'histoires, commissioning d'illustrations, marketing communautaire) requiert un type
d'engagement différent qu'il ne peut pas maintenir. Réponse crédible et cohérente avec le
profil et la transparence affichée tout au long du processus.

---

## Stratégie post-acquisition envisagée

**Phase 1 — Activation rapide (0–3 mois)**
- Déploiement sur infrastructure propre (Kubernetes ou VPS)
- Activation Stripe + premiers prix
- Dépôt de marque Talezzi (EU en priorité)
- Lecture approfondie des prompt files + Bible pour maîtriser le workflow de production

**Phase 2 — Extension de l'univers Talezzi (3–12 mois)**
- Production de nouvelles histoires via le workflow AI documenté
- Lancement chaîne YouTube (histoires animées / read-aloud)
- Livres audio (gratuits et payants)
- Amazon KDP (livres illustrés + livres de coloriage)
- Newsletter

**Phase 3 — Réplication multi-univers**
- Créer 1–2 nouveaux univers en utilisant le framework Bible comme template
- Sites dédiés sur la même stack technique
- Tester d'autres niches (autre tranche d'âge, autre positionnement culturel)

**Dépendance critique :** toute la stratégie repose sur la qualité réelle des prompt files
et de la Bible. L'audit GitHub est l'étape de validation avant engagement financier.

---

## Red flags mis à jour

### 🔴 CRITIQUES
Aucun.

### 🟡 ATTENTION
- **Illustrations placeholders** — coût de production à anticiper pour KDP/YouTube
- **SQLite** — migration nécessaire à terme
- **Aucune validation commerciale** — aucun client, aucun revenu
- **Marque non déposée** — action prioritaire post-acquisition

### ℹ️ INFO
- Prompt files Claude Code dans le repo → workflow production documenté et réplicable
- Universe Bible framework réutilisable → multi-univers validé
- Stripe implémenté et testé → activation rapide
- Admin dashboard intégré → upload PDF natif, pas de dev nécessaire

---

## Prochaines étapes

1. **Audit GitHub** — valider la qualité du code, lire les prompt files, évaluer la Bible
2. **Décision go/no-go** sur la base de l'audit
3. Si go : négocier à $3,000–$3,500, formaliser l'IP transfer agreement (clause AI content)
4. Post-acquisition : déposer la marque Talezzi (EU) en priorité

---

## Sources et historique

- Listing Flippa : `_inbox/Talezzi.com - Website listed on Flippa.md`
- Quick screen initial : 2026-05-15
- Message de contact envoyé : 2026-05-16
- Questionnaire vendeur reçu et analysé : 2026-05-31
- Audit GitHub : en cours
