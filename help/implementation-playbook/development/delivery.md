---
title: Méthodologie de mise en oeuvre du projet
description: Familiarisez-vous avec le fonctionnement de la diffusion logicielle Adobe Commerce.
exl-id: 579cd083-8b12-49ff-bc8a-8db1ca588d74
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Méthodologie de mise en oeuvre du projet

Maintenant que vous avez une meilleure idée des outils impliqués, nous allons ventiler nos processus de diffusion et de test.

## Intégration continue (CI)

Les tâches d’intégration continue effectuent automatiquement les actions suivantes :

- Créez le code source pour vérifier les erreurs de compilation.
- Exécutez des tests lorsqu’une requête de tirage est créée/mise à jour. Actuellement, les tests unitaires PHP sont exécutés.

La tâche publie son état d’exécution dans la requête de tirage. Les développeurs peuvent afficher les détails de l’exécution de la tâche afin qu’ils puissent corriger ou améliorer le code existant.

## Diffusion continue (CD)

La diffusion continue (CD) déploie immédiatement le code source sur le serveur une fois tous les tests réussis. Les développeurs peuvent vérifier rapidement leurs fonctions, puis affecter la tâche à l’équipe d’assurance qualité en vue de la révision.

Lorsque la version s’exécute sur le système de génération, elle réduit non seulement le temps d’arrêt du déploiement, mais également la charge sur le serveur. Par conséquent, les activités d’assurance qualité, qui se produisent sur le serveur, sont moins affectées.

![Infographie de diffusion continue](../../assets/playbooks/cicd.svg)

Le processus CI/CD du schéma précédent peut être brièvement décrit comme suit :

- Bitbucket héberge le référentiel Git.
- Les images Docker sont répliquées à partir des configurations de pile de la technologie de production.
- Les conteneurs Docker sont utilisés pour tous les environnements de développement et de test. D’autres environnements peuvent tirer parti de ces configurations si nécessaire.
- Les développeurs effectuent un passage en caisse de la branche de code appropriée pour chaque nouvelle tâche/ticket.
- Pour toutes les branches de validation, automatiquement :
   - Exécution d’une analyse de code standard.
   - Exécutez un test de compilation de code.
   - Exécutez une analyse de code statique (par exemple, SonarQube).
- Toutes les validations d’analyse qui passent sont fusionnées avec la branche cible.
- Une nouvelle balise publiée est envoyée à AWS S3 pour le package de préparation au déploiement.
- Le nouveau déploiement est déclenché par l’équipe d’ingénierie de déploiement.
   - Une tâche de déploiement déploie le nouveau package dans l’environnement cible.
   - Les mises à jour de la structure de la base de données nécessitent une pause pour répondre aux nouvelles demandes du client.
- Le processus de déploiement se termine par une notification par email/Slack/équipes, envoyée automatiquement par le serveur à l’équipe d’ingénierie de déploiement.
