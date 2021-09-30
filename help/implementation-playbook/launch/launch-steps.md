---
title: Étapes de lancement
description: Utilisez notre liste de contrôle de lancement pour garantir une mise en oeuvre fluide du site Commerce Adobe.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Étapes de lancement

Après avoir testé et terminé la liste de contrôle de prélancement, nous pouvons commencer les dernières étapes à lancer au moment de la coupure. Ces étapes comprennent l’entrée sur le site de lancement (activation), la suppression de l’accès et enfin le test de votre ou de vos magasins lorsqu’ils sont actifs.

Adobe Commerce Support staff work with you through the process, checking the status and helping to address any questions or issues that occur. Tous les problèmes doivent être suivis avec les tickets pour capturer au mieux ce qui s’est passé et comment il a été résolu. Lorsque vous commencez à déployer des itérations continues de mises à jour dans votre boutique lancée, des problèmes similaires peuvent se produire à nouveau. Ces tickets peuvent vous aider à identifier les problèmes et à ajuster vos tâches de déploiement.

- Configuration de l’application sur l’URL de base
   - Basculer le DNS vers le nouveau site
   - Accès à votre service DNS
   - Mettre à jour vos enregistrements A et CNAME pour vos domaines et noms d’hôtes
   - Wait for the TTL time to pass and access your store

- Completely test in Production
   - Vérification de toutes les fonctions du site web
   - Vérification du cache CDN
   - Vérification de tous les services tiers intégrés
   - Vérification de tous les systèmes tiers

- Contact Adobe Commerce hotline in case any issues are blocking the go-live

![Diagram showing phase 3 of the launch process](../../assets/playbooks/launch-steps-3.svg)
