---
title: Guide des bonnes pratiques [!DNL Adobe Commerce Patching Automation]
description: Découvrez comment utiliser pour planifier [!DNL Adobe Commerce Patching Automation]  valider et appliquer des correctifs en toute sécurité, ce qui réduit les risques de déploiement et les interruptions de service.
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---

# Guide [!DNL Adobe Commerce Patching Automation] bonnes pratiques

Le respect des bonnes pratiques est essentiel à la réussite et à la sécurité des opérations de correctifs avec [!DNL Adobe Commerce Patching Automation]. Ce guide fournit les bonnes pratiques complètes pour des opérations de correctifs efficaces, la gestion de l’environnement et l’excellence opérationnelle.

## Bonnes pratiques en matière de pré-patch

### Préparation à l’environnement

**Bonne pratique :** préparez toujours soigneusement votre environnement avant d’appliquer les correctifs afin de garantir le succès des opérations et de réduire les risques.

Avant d’appliquer les correctifs, assurez-vous que votre environnement est correctement préparé :

* **Compte Adobe Commerce Cloud**
  * Abonnement Adobe Commerce Cloud actif
  * Licence Adobe Commerce valide
  * [Clés d’authentification du compositeur](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/authentication-keys) configurées pour accéder au référentiel Adobe Commerce
  * Autorisations de projet et d’environnement

* **Ressources d’environnement**
  * Le projet a la capacité de créer un environnement d’intégration actif supplémentaire pour l’opération de correctif — voir [Gérer les branches avec la console cloud](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/console-branches) pour plus d’informations sur les limites de l’environnement actif
  * Stockage, CPU et mémoire suffisants
  * Accès réseau aux référentiels Adobe
  * Environnement parent stable pour la synchronisation

* **Préparation de l’environnement de production** (pour l’application de correctifs en production)
  * Activer le mode de maintenance
  * Désactiver les tâches cron
  * Définir des procédures relatives aux fenêtres de maintenance
  * Procédures de restauration de documents
  * Préparer le plan de communication des parties prenantes

## Bonnes pratiques relatives aux applications de correctifs

### Planning et planification

**Bonne pratique :** planifiez les opérations d’application de correctifs pendant les périodes de faible trafic et assurez la coordination avec les parties prenantes pour minimiser l’impact sur l’entreprise.

**Choisir l’heure appropriée pour l’application de correctif :**

* **Période de faible trafic**
  * Planification des correctifs pendant les heures creuses
  * Évitez d’appliquer des correctifs lors d’événements à trafic élevé
  * Planifier les temps d’arrêt potentiels pendant la validation

* **Considérations relatives à l’environnement de production**
  * **Fenêtres de maintenance** - Planification des correctifs de production pendant les fenêtres de maintenance planifiées
  * **Communication client** - Informer les clients du mode de maintenance et du temps d’arrêt prévu
  * **Coordination de l’équipe** - Assurez-vous que tous les membres de l’équipe connaissent le calendrier de maintenance
  * **Préparation de la restauration** - Mettez des membres de l’équipe à disposition pour une restauration immédiate si nécessaire.

### Surveillance et validation

**Pendant les opérations de correctif :**

* **Suivre la progression**
  * Observer le statut des opérations en temps réel
  * Prêtez attention aux avertissements ou aux erreurs
  * N’interrompez pas le processus une fois qu’il a été lancé

* **Validation des résultats**
  * Tester les fonctionnalités critiques après une application réussie
  * Vérifiez les mesures de performances pour détecter toute dégradation.
  * Vérifier que les mesures de sécurité restent intactes

## Bonnes pratiques après l’application du correctif

### Vérification et test

**Bonne pratique :** toujours vérifier le succès des applications de correctifs par des tests et une surveillance complets pour assurer la stabilité et la fonctionnalité du système.

**Après une application de correctif réussie :**

* **Tests fonctionnels**
  * Tester tous les processus d’entreprise critiques
  * Vérifier le passage en caisse et les flux de paiement
  * Vérifier les fonctionnalités du panneau d’administration

* **Surveillance des performances**
  * Surveiller les temps de chargement des pages
  * Vérifier les performances de la base de données
  * Surveillez tous les pics d’utilisation des ressources

* **Validation de la sécurité**
  * Vérifier que les fonctionnalités de sécurité fonctionnent
  * Recherchez d&#39;éventuelles nouvelles vulnérabilités de sécurité
  * Authentification et autorisation des tests

## Bonnes pratiques relatives à l’environnement de production

### Tests de pré-production

**Bonne pratique :** n’appliquez jamais de correctifs directement en production sans effectuer de tests approfondis dans les environnements de préproduction qui reflètent la configuration de production.

**Testez toujours les correctifs avant le déploiement en production :**

* **Configuration de l’environnement de test**
  * Utiliser des environnements d’évaluation ou d’intégration pour les tests
  * Assurez-vous que l’environnement de test reflète la configuration de production.
  * Testez si possible avec des données de type production.

* **Tests complets**
  * Tester tous les processus d’entreprise critiques
  * Vérifier le passage en caisse et les flux de paiement
  * Vérifier les fonctionnalités du panneau d’administration
  * Tester toutes les intégrations personnalisées

* **Test de performance**
  * Surveillance de l’impact des correctifs sur les performances
  * Recherchez toute dégradation des performances
  * Vérifier que l’utilisation des ressources reste acceptable

### Atténuation des risques

**Réduire les risques lors de l’application des correctifs en production :**

* **Plan de communication**
  * Informer les clients des fenêtres de maintenance
  * Tenir les parties prenantes informées des progrès
  * Préparer les procédures d’escalade

* **Stratégie de restauration**
  * Savoir comment rétablir rapidement les correctifs si nécessaire
  * Disposer de membres de l’équipe pour une réponse immédiate
  * Procédures de restauration de documents

* **Surveillance et alertes**
  * Configurer la surveillance des problèmes postérieurs à l’application du correctif
  * disposer d’alertes pour les échecs critiques ;
  * Surveiller de près les mesures de performances

## Résumé des bonnes pratiques clés

### Bonnes pratiques essentielles pour le succès [!DNL Patching Automation]

* Effectuez toujours des tests de pré-production avant d’appliquer des correctifs aux environnements de production
* Activez le mode de maintenance et désactivez les tâches cron pour les opérations de correctifs d’exploitation.
* Surveiller étroitement les opérations et disposer de procédures de restauration prêtes
* Documentez toutes les opérations de correctifs et conservez des enregistrements complets.
* Suivez les procédures de gestion des modifications appropriées et obtenez les approbations appropriées
* Maintien de la synchronisation des environnements et de l’allocation appropriée des ressources
* Établir des procédures de soutien claires et maintenir la formation de l&#39;équipe
* Examinez et améliorez régulièrement vos processus de gestion des correctifs

## Rubriques connexes

* [Présentation de l&#39;automatisation des correctifs](intro.md)
* [Accès](access.md)
* [Présentation des workflows](workflow.md)
* [Intégration de GitHub](github-integration.md)
* [Dépannage](troubleshooting.md)
