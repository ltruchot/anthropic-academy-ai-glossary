---
tags: [ia, anthropic, claude, mindmap]
created: 2026-11-03
updated: 2026-11-05
---
# Schémas du cours « Claude Platform 101 »

Les schémas du [glossaire](index.md), un par partie du cours. Chacun est un fichier PlantUML (`.puml`, la source) rendu en `.png` et `.svg`, dans `mindmap/`.

## Sommaire

1. [Schéma des trois couches](#schéma-des-trois-couches)
2. [Schéma du premier appel API](#schéma-du-premier-appel-api)

## Schéma des trois couches

![Schéma des trois couches](mindmap/three-layers.png)

*La Claude Platform, l'infrastructure d'Anthropic pour développer avec Claude par programmation, et ses trois couches : les primitives (on construit avec : l'API Messages et les autres briques de base de l'API), l'infrastructure (on passe à l'échelle : les agents gérés, les nouvelles tentatives, les files d'attente) et le pilotage (on pilote en production : les tableaux de bord, les évaluations) ; l'appel à messages.create et ses paramètres ; la Claude Console, où se trouvent l'infrastructure et le pilotage.* Source : [three-layers.puml](mindmap/three-layers.puml)

## Schéma du premier appel API

![Schéma du premier appel API](mindmap/first-api-call.png)

*Votre premier appel API : la mise en place (la clé API, obtenue sur platform.claude.com et rangée dans un fichier .env.local, hors du contrôle de version ; le SDK), l'appel à messages.create et ce que vous y indiquez (model, max_tokens, messages aux rôles user ou assistant, system pour le prompt système), le contenu de la réponse (un tableau de blocs : texte, appels d'outils, réflexion), puis le même appel dans un gestionnaire de route, au cœur d'un produit.* Source : [first-api-call.puml](mindmap/first-api-call.puml)
