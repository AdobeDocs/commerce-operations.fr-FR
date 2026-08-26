---
title: '[!DNL Adobe Commerce Patching Automation]'
description: Découvrez  [!DNL Adobe Commerce Patching Automation], ses utilisations, comment y accéder et les bonnes pratiques pour appliquer des correctifs automatisés
hide: true
source-git-commit: f70924d6f0d1777104c59f3f9e776360308abceb
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# [!DNL Adobe Commerce Patching Automation]

[!DNL Adobe Commerce Patching Automation] est un outil qui automatise le processus d’application et de rétablissement des correctifs pour Adobe Commerce dans les environnements cloud. Il offre aux administrateurs de projet Commerce un workflow rationalisé pour appliquer et rétablir les correctifs. La validation et les contrôles d’intégrité intégrés permettent de garantir la stabilité et la sécurité des environnements cloud.

Ce guide est destiné aux commerçants et partenaires Adobe Commerce Cloud qui souhaitent rationaliser leur processus d’application de correctifs, réduire le risque de problèmes liés aux correctifs, améliorer la sécurité et la stabilité de leur environnement et automatiser les opérations d’application de correctifs de routine.

## [!DNL Patching Automation] les rubriques

* **[Accès](access.md)**
* **[Présentation des workflows](workflow.md)**
* **[Intégration de GitHub](github-integration.md)**
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
  * **Validation** - Effectue un contrôle d’intégrité pour confirmer le démarrage de l’application et l’accessibilité de ses connexions de base de données et de cache

* **Caractéristiques de sécurité**
  * Valide la compatibilité des correctifs avant application
  * Applique d’abord le correctif dans un environnement d’intégration temporaire (en confirmant qu’il se déploie correctement et qu’il réussit le contrôle de l’intégrité) avant de le fusionner dans votre environnement cible, puis effectue un contrôle de l’intégrité final immédiatement après le déploiement
  * Applique des correctifs au dossier `m2-hotfixes` avec suppression automatique lors de la réversion

## Intégrations avec Adobe Commerce Cloud

[!DNL Patching Automation] est entièrement intégré à l’infrastructure cloud d’Adobe Commerce et fonctionne en toute transparence avec vos environnements cloud existants. Il tire parti des fonctionnalités natives du cloud d’pour des performances optimales, fournit une journalisation et une surveillance détaillées et s’intègre aux outils de support cloud d’Adobe Commerce.

## Tutoriel vidéo

Découvrez [!DNL Adobe Commerce Patching Automation] et comment cet outil permet aux utilisateurs et utilisatrices de trouver et d’appliquer rapidement des correctifs de sécurité. La vidéo suivante explique comment y accéder via le tableau de bord de l’outil d’analyse à l’échelle du site (SWAT), choisir votre projet et votre environnement, et appliquer des correctifs en un seul clic.

>[!VIDEO](https://video.tv.adobe.com/v/3476247/?learn=on&enablevpops)

## Cas d’utilisation courants

* **Correctifs de sécurité** - Appliquez rapidement des mises à jour de sécurité critiques
* **Restauration des correctifs** - Annulez en toute sécurité les correctifs problématiques appliqués par le service
* **Conformité en matière de sécurité** - Maintenir les normes de sécurité grâce à l&#39;application automatique de correctifs
* **Stabilité opérationnelle** - Confirme que l’application démarre et passe un contrôle d’intégrité après chaque opération de correctif
