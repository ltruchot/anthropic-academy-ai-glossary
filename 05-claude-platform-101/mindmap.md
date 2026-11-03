---
tags: [ia, anthropic, claude, mindmap]
created: 2026-11-03
updated: 2026-11-03
---
# Schémas du cours « Claude Platform 101 »

Les schémas du [glossaire](index.md), un par partie du cours. Chacun est un fichier PlantUML (`.puml`, la source) rendu en `.png` et `.svg`, dans `mindmap/`.

## Sommaire

1. [Schéma des trois couches](#schéma-des-trois-couches)

## Schéma des trois couches

![Schéma des trois couches](mindmap/three-layers.png)

*La Claude Platform, l'infrastructure d'Anthropic pour développer avec Claude par programmation, et ses trois couches : les primitives (on construit avec : l'API Messages et les autres briques de base de l'API), l'infrastructure (on passe à l'échelle : les agents gérés, les nouvelles tentatives, les files d'attente) et le pilotage (on pilote en production : les tableaux de bord, les évaluations) ; l'appel à messages.create et ses paramètres ; la Claude Console, où se trouvent l'infrastructure et le pilotage.* Source : [three-layers.puml](mindmap/three-layers.puml)
