---
title: '[!DNL Cloud Automation Patching Service (CAPS)]'
description: Découvrez  [!DNL Cloud Automation Patching Service (CAPS)], ses utilisations, comment y accéder et les bonnes pratiques pour appliquer des correctifs automatisés
hide: true
hidefromtoc: true
source-git-commit: 6db46ef802edaeeec8a6986d4621ea647b171b0c
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# [!DNL Cloud Automation Patching Service (CAPS)]

Le [!DNL Cloud Automation Patching Service] ([!DNL CAPS]) est un outil qui automatise le processus d’application et de restauration des correctifs pour Adobe Commerce dans les environnements cloud. Il offre aux administrateurs de projet Commerce un workflow rationalisé permettant d’appliquer et d’annuler les correctifs. Ce workflow inclut une validation intégrée et des contrôles d’intégrité pour garantir la stabilité et la sécurité des environnements cloud.

Ce guide est destiné aux commerçants et partenaires Adobe Commerce Cloud qui souhaitent rationaliser leur processus d’application de correctifs, réduire le risque de problèmes liés aux correctifs, améliorer la sécurité et la stabilité de leur environnement et automatiser les opérations d’application de correctifs de routine.

## [!DNL CAPS] les rubriques

* **[Accès](access.md)**
* **[Workflow](workflow.md)**
* **[Bonnes pratiques](best-practices.md)**
* **[Dépannage](troubleshooting.md)**

## Présentation de l’outil

* **Interface utilisateur**
   * Affichage de la disponibilité et du statut des correctifs en temps réel pour des combinaisons de projet et d’environnement spécifiques
   * Informations complètes sur le statut de l&#39;application de correctifs indiquant la progression, les erreurs et tout autre message pertinent
   * [!UICONTROL Patch Management Dashboard] pour :
      * Affichage des correctifs disponibles
      * Application de correctifs en un clic
      * Rétablissement des correctifs précédemment appliqués
      * Surveillance du statut et des résultats de l’opération de correctif

* **Service de correctifs automatisés avec workflow structuré**
   * **Vérification préliminaire** - Valide la compatibilité des correctifs et la préparation de l’environnement.
   * **Application de correctifs** - Applique ou rétablit automatiquement les correctifs dans les environnements d’intégration
   * **Validation** - Effectue des contrôles d’intégrité et s’assure que les fonctionnalités critiques ne sont pas affectées

* **Caractéristiques de sécurité**
   * Crée des environnements d’intégration temporaires pour les tests.
   * Valide la compatibilité des correctifs avant application
   * Restauration automatique en cas d’échec de la validation
   * Applique des correctifs au dossier `m2-hotfixes` avec suppression automatique lors de la réversion

## Intégrations avec Adobe Commerce Cloud

[!DNL CAPS] est entièrement intégré à l’infrastructure cloud d’Adobe Commerce et fonctionne en toute transparence avec vos environnements cloud existants. Il tire parti des fonctionnalités natives du cloud d’pour des performances optimales, fournit une journalisation et une surveillance détaillées et s’intègre aux outils de support cloud d’Adobe Commerce.

## Cas d’utilisation courants

* **Correctifs de sécurité** - Appliquez rapidement des mises à jour de sécurité critiques
* **Restauration des correctifs** - Annulez en toute sécurité les correctifs problématiques appliqués via [!DNL CAPS]
* **Conformité en matière de sécurité** - Maintenir les normes de sécurité grâce à l&#39;application automatique de correctifs
* **Stabilité opérationnelle** - Assurer la stabilité de l’environnement par une validation automatisée
