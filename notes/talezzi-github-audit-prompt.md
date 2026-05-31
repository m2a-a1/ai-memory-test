---
title: "Prompt — Audit GitHub Talezzi"
date: 2026-05-31
tags: [projet-perso, acquisition]
status: active
source: "deal-2026-05-15-talezzi"
---

# Prompt d'audit GitHub — Talezzi.com

> À envoyer à un agent (Claude Code, Gemini CLI, ou agent custom) avec accès au repo GitHub.

---

## Contexte

Je suis en due diligence pour l'acquisition de Talezzi.com, une plateforme d'ebooks pour enfants
en 10 langues. Stack : React + Vite + TypeScript (frontend), Node.js + Express + TypeScript
(backend), SQLite, Docker Compose. Le vendeur a confirmé que le repo contient des fichiers de
prompts Claude Code (prompt7 à prompt11) et une Universe Bible en markdown.

Je t'accorde un accès en lecture seule au repo. Produis un rapport d'audit structuré couvrant
les sections suivantes, dans cet ordre de priorité.

---

## 1. Les prompt files Claude Code (PRIORITÉ MAXIMALE)

Lis tous les fichiers dont le nom contient "prompt" à la racine du repo (prompt7 à prompt11,
et tout autre fichier similaire).

Pour chacun, indique :
- Son contenu exact ou un résumé fidèle s'il est long
- Ce qu'il documente (feature, workflow de production de contenu, autre)
- Dans quelle mesure il est réutilisable tel quel pour produire de nouvelles histoires ou
  développer de nouvelles fonctionnalités

Conclus par une évaluation globale : ces fichiers constituent-ils un système de production
documenté et réplicable, ou sont-ils des artefacts de développement sans valeur opérationnelle ?

---

## 2. Universe Bible et histoires en markdown

Lis le fichier Universe Bible (probablement à la racine ou dans un dossier /content ou /docs).

Rapporte :
- Sa structure exacte (sections, longueur approximative)
- La qualité et la complétude des éléments clés : description du monde, archétypes des
  personnages, formule narrative, guide de style visuel, principes éditoriaux
- Dans quelle mesure elle pourrait guider un rédacteur ou un outil IA pour créer une nouvelle
  histoire sans intervention du fondateur
- Si la structure est suffisamment générique pour être réutilisée comme template pour un
  univers entièrement différent (personnages, monde, ton différents)

Lis également un des fichiers d'histoires en markdown. Rapporte sa structure, sa longueur,
et si le format semble directement utilisable comme template de prompt pour générer de nouvelles
histoires.

---

## 3. Architecture et qualité du code

Lis ARCHITECTURE.md en entier et résume-le.

Ensuite, explore la structure des dossiers et rapporte :
- Organisation générale (monorepo ? séparation frontend/backend ?)
- Rigueur TypeScript (strict mode activé ? types explicites ou `any` partout ?)
- Présence de tests (dossiers `__tests__`, fichiers `.test.ts`, configuration Jest/Vitest)
- Qualité des dépendances : versions récentes ? dépendances abandonnées ? vulnérabilités
  évidentes dans package.json ?
- Présence d'un `.env.example` documentant les variables d'environnement requises
- Configuration Docker Compose : nombre de services, volumes, ports exposés

Donne une note globale de qualité du code sur 5 avec justification.

---

## 4. Base de données et schéma

Trouve le schéma SQLite (fichier de migration, `schema.sql`, ou équivalent ORM).

Rapporte :
- Tables existantes et leurs colonnes principales
- Structure de la table users (champ is_admin, OAuth fields)
- Structure de la table books/stories (comment le contenu multilingue est organisé)
- Structure de la table payments (si elle existe — champs Stripe)
- Toute relation entre tables
- Présence de migrations ou de gestion de version du schéma

---

## 5. Admin dashboard

Trouve les fichiers du dashboard admin (route `/{lang}/admin` mentionnée par le vendeur).

Rapporte :
- Fonctionnalités implémentées (upload PDF, gestion du contenu, analytics avec Recharts ?)
- Mécanisme de protection (vérification is_admin côté serveur ou uniquement côté client ?)
- Quelles opérations sont possibles via l'interface sans modifier le code

---

## 6. Intégration Stripe

Trouve les fichiers liés à Stripe (webhook handler, création de checkout session, etc.).

Rapporte :
- Localisation des fichiers (route `/api/payments/webhook` et autres)
- Ce qui est implémenté : création de session, gestion des événements webhook, enregistrement
  des paiements en base
- Ce qui reste à configurer (variables d'env, product/price IDs dans la DB)
- Estimation honnête : est-ce réellement plug-and-play ou y a-t-il du dev résiduel ?

---

## 7. Authentification et sécurité de base

Rapporte :
- Implémentation Google OAuth (librairie utilisée, flow)
- Gestion des sessions (JWT ? cookies ? durée ?)
- Faisabilité d'ajouter une authentification email/password sans refactoring majeur
- Présence de protections de base : CORS configuré, rate limiting, validation des inputs,
  sanitisation des données

---

## 8. Routing multilingue et serving des PDFs

Rapporte :
- Comment le routing `/{lang}/` est implémenté (côté client ? côté serveur ? les deux ?)
- Liste des 10 langues supportées et comment elles sont configurées
- Comment les 30 PDFs sont stockés dans le repo (dossier dédié ?) et servis (endpoint API,
  fichiers statiques ?)
- Présence d'un mécanisme de contrôle d'accès sur les PDFs (gratuit vs payant)

---

## 9. Points de vigilance techniques

Signale tout ce qui mérite attention pour un repreneur :
- Secrets ou credentials committés par erreur (même anciens)
- Valeurs hard-codées qui devraient être dans des variables d'environnement
- TODOs ou FIXMEs significatifs dans le code
- Dette technique évidente (code mort, dépendances dupliquées, patterns problématiques)
- Contraintes de la SQLite pour la croissance (taille max pratique, concurrence en écriture)
  et complexité estimée d'une migration vers PostgreSQL

---

## Format de sortie attendu

Rapport structuré suivant exactement les 9 sections ci-dessus.
Pour chaque section : findings factuels d'abord, évaluation ensuite.
Termine par un **résumé exécutif en 10 lignes maximum** : les 3 points les plus positifs,
les 3 points les plus préoccupants, et une recommandation go/no-go technique.

Sois direct et honnête — je prends une décision d'acquisition sur la base de ce rapport.
