---
title: Correctifs disponibles dans la présentation de l’outil QPT
description: Cet article présente  [!DNL Quality Patches Tool] (QPT) et fournit des liens vers des ressources expliquant comment l’utiliser.
feature: Support, Tools and External Services
role: Admin
exl-id: e67e5823-d878-4efc-90af-c7bb8c59d654
type: Troubleshooting
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# Correctifs disponibles dans la présentation de l’outil QPT

Cet article présente un aperçu de [!DNL Quality Patches Tool] (QPT) et des liens vers des ressources expliquant comment l’utiliser.

## Produits et versions concernés

* Adobe Commerce On-premise, toutes les [versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce sur les infrastructures cloud, toutes les [versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Qu’est-ce que l’outil de correctifs de qualité ?

Le [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) (QPT) est un outil permettant d’appliquer des correctifs de qualité individuels développés par Adobe et la communauté Magento Open Source.

Il permet d’effectuer les opérations suivantes :

* appliquez les correctifs de qualité inclus dans le package
* rétablir les correctifs précédemment appliqués
* affichez les informations générales sur les correctifs de qualité disponibles pour la version installée d’Adobe Commerce.

Voici un exemple du tableau d’état auquel vous pouvez accéder pour afficher les correctifs disponibles :

![Tableau de statut de l’outil de correctifs de qualité présentant les correctifs disponibles et leur statut d’installation](/help/assets/tools/status_table.png)

L’outil a pour but de vous permettre d’utiliser des correctifs en libre-service pour résoudre les problèmes que vous pourriez rencontrer avec Adobe Commerce, ou d’appliquer facilement des correctifs recommandés par la prise en charge d’Adobe Commerce.

>[!NOTE]
>
>QPT est réservé aux correctifs de qualité uniquement. Les correctifs de sécurité sont disponibles dans les [ Notes de mise à jour d’Adobe Commerce et de Magento Open Source ](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/overview.html).

## Correctifs disponibles dans le [!DNL Quality Patches Tool]

Dans cette section de la base de connaissances de l’assistance Adobe Commerce, vous trouverez des descriptions détaillées des problèmes, résolus par des correctifs QPT, regroupés par version de QPT.
Vous pouvez également afficher la liste des correctifs QPT disponibles et filtrer le composant par, à l’aide du tableau généré dynamiquement sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans notre base de connaissances d’assistance.

## Installation et utilisation du [!DNL Quality Patches Tool]

Les commandes d’installation et d’utilisation sont différentes pour Adobe Commerce On-Premise et Adobe Commerce sur l’infrastructure cloud, car pour le cloud, le package QPT est inclus dans le package ece-tools.

### Installation et utilisation de QPT pour Adobe Commerce On-Premise

Consultez [Commerce > Outils > Utilisation](../usage.md) dans la documentation destinée aux développeurs pour plus d’informations sur l’installation et l’utilisation de QPT pour appliquer et rétablir des correctifs.

### Installation et utilisation de QPT pour Adobe Commerce sur une infrastructure cloud

Consultez le [Guide de Commerce sur les infrastructures cloud > Application de correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans notre documentation destinée aux développeurs, pour plus d’informations sur l’installation et l’utilisation de QPT pour appliquer et rétablir des correctifs sur Adobe Commerce sur les infrastructures cloud.

## Lecture connexe

* [[!DNL Quality Patches Tool] notes de mise à jour](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) dans notre documentation destinée aux développeurs et développeuses.
