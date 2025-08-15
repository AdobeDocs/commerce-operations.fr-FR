---
title: Vérifiez que le correctif ne présente aucun problème avec l’outil de correctifs de qualité d’Adobe Commerce.
description: Cet article présente l’outil de correctifs de la qualité (QPT) et contient des liens vers des ressources expliquant comment l’utiliser.
feature: Tools and External Services
role: Admin
exl-id: 4d651c3c-95ad-4b53-bf77-92758acb795d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Vérifiez que le correctif ne présente aucun problème avec l’outil de correctifs de qualité d’Adobe Commerce.

Cet article présente l’outil de correctifs de la qualité (QPT) et contient des liens vers des ressources expliquant comment l’utiliser.

## Produits et versions concernés

* Adobe Commerce On-premise, toutes les [versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce sur les infrastructures cloud, toutes les [versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## En quoi consiste l’outil de correctifs de qualité ?

L’[outil de correctifs de qualité](https://github.com/magento/quality-patches) (QPT) est un correctif individuel développé par Adobe et la communauté Magento Open Source.

Il permet d’effectuer les opérations suivantes :

* appliquez les correctifs de qualité inclus dans le package
* rétablir les correctifs précédemment appliqués
* affichez les informations générales sur les correctifs de qualité disponibles pour la version installée d’Adobe Commerce.

Voici un exemple du tableau d’état auquel vous pouvez accéder pour afficher les correctifs disponibles :

![Magento_patches_list](/help/assets/tools/status_table.png)

L’outil a pour but de vous permettre d’utiliser des correctifs en libre-service pour résoudre les problèmes que vous pourriez rencontrer avec Adobe Commerce, ou d’appliquer facilement des correctifs recommandés par la prise en charge d’Adobe Commerce.

>[!NOTE]
>
>QPT est réservé aux correctifs de qualité uniquement. Les correctifs de sécurité sont disponibles dans le Centre de sécurité [Magento](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview).

## Correctifs disponibles dans l’outil de correctifs de la qualité

Reportez-vous à [Outil de correctifs de qualité](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans notre documentation destinée aux développeurs pour obtenir la liste des correctifs disponibles.

## Installation et utilisation de l’outil de correctifs de qualité

Les commandes d’installation et d’utilisation sont différentes pour Adobe Commerce On-Premise et Adobe Commerce sur l’infrastructure cloud, car pour le cloud, le package QPT est inclus dans le package ece-tools.

### Installation et utilisation de QPT pour Adobe Commerce On-Premise

Consultez le [Guide de mise à jour logicielle > Correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs pour plus d’informations sur l’installation et l’utilisation de QPT pour l’application et le rétablissement des correctifs.

### Installation et utilisation de QPT pour Adobe Commerce sur une infrastructure cloud

Consultez [Cloud for Adobe Commerce > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs pour plus d’informations sur l’installation et l’utilisation de QPT pour appliquer et rétablir des correctifs sur Adobe Commerce sur les infrastructures cloud.

## Lecture connexe

* [Notes de mise à jour de l’outil de correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/release-notes) dans notre documentation destinée aux développeurs.
* [Application des correctifs de compositeur fournis par Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento) dans la base de connaissances d’assistance.
