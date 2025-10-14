---
title: Guide des bonnes pratiques [!DNL Cloud Automation Patching Service (CAPS)]
description: Découvrez les bonnes pratiques pour une utilisation efficace et  [!DNL Cloud Automation Patching Service (CAPS)]  sécurité.
hide: true
hidefromtoc: true
source-git-commit: 9d377babd1059d7ec0af687755965ca4d0b541fb
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 0%

---

# Guide [!DNL Cloud Automation Patching Service (CAPS)] bonnes pratiques

Le respect des bonnes pratiques est essentiel pour la réussite et la sécurité des opérations d’application de correctifs avec [!DNL Cloud Automation Patching Service] ([!DNL CAPS]). Ce guide fournit les bonnes pratiques complètes pour des opérations de correctifs efficaces, la gestion de l’environnement et l’excellence opérationnelle.

## Bonnes Pratiques Relatives Aux Correctifs Préalables

### Préparation à l’environnement

**Bonne pratique :** préparez toujours soigneusement votre environnement avant d’appliquer les correctifs afin de garantir le succès des opérations et de réduire les risques.

Avant d’appliquer les correctifs, assurez-vous que votre environnement est correctement préparé :

* **Compte Adobe Commerce Cloud**
   * Abonnement Adobe Commerce Cloud actif
   * Licence Adobe Commerce valide
   * Identifiants d’accès au référentiel configurés
   * Autorisations de projet et d’environnement

* **Ressources d’environnement**
   * Emplacements d’environnement disponibles pour les tests temporaires
   * Stockage, CPU et mémoire suffisants
   * Accès réseau aux référentiels Adobe
   * Environnement parent stable pour la synchronisation

* **Préparation de l’environnement de production** (pour l’application de correctifs en production)
   * Le mode de maintenance peut être activé.
   * Les tâches cron peuvent être désactivées
   * Procédures relatives aux fenêtres de maintenance établies
   * Procédures de restauration documentées
   * Plan de communication des parties prenantes prêt

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

### Bonnes pratiques essentielles pour le succès [!DNL CAPS]

* Effectuez toujours des tests de pré-production avant d’appliquer des correctifs aux environnements de production
* Activez le mode de maintenance et désactivez les tâches cron pour les opérations de correctifs d’exploitation.
* Surveiller étroitement les opérations et disposer de procédures de restauration prêtes
* Documentez toutes les opérations de correctifs et conservez des enregistrements complets.
* Suivez les procédures de gestion des modifications appropriées et obtenez les approbations appropriées
* Maintien de la synchronisation des environnements et de l’allocation appropriée des ressources
* Établir des procédures de soutien claires et maintenir la formation de l&#39;équipe
* Examinez et améliorez régulièrement vos processus de gestion des correctifs

## Rubriques connexes

* [Présentation de CAPS](intro.md)
* [Accès](access.md)
* [Workflow](workflow.md)
* [Dépannage](troubleshooting.md)
