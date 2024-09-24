---
title: Correctif du problème Adobe Commerce avec l’outil Correctifs de qualité
description: Cet article présente un aperçu de l’outil de correctifs de qualité (QPT) et des liens vers des ressources expliquant comment l’utiliser.
feature: Tools and External Services
role: Admin
source-git-commit: 6f311fc4c20caca8b98d4c3c06642e5f61dc614f
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Correctif du problème Adobe Commerce avec l’outil Correctifs de qualité

Cet article présente un aperçu de l’outil de correctifs de qualité (QPT) et des liens vers des ressources expliquant comment l’utiliser.

## Produits et versions concernés

* Adobe Commerce sur site, toutes les [versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce sur l’infrastructure cloud, toutes les [ versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Que sont les outils de correctifs de qualité ?

L’ [outil de correctifs de qualité](https://github.com/magento/quality-patches) (QPT) sont des correctifs individuels développés par Adobe et la communauté des Magento Open Sources.

Il vous permet d’effectuer les opérations suivantes :

* appliquer des correctifs de qualité inclus dans le package ;
* rétablir les correctifs précédemment appliqués
* consultez les informations générales sur les correctifs de qualité disponibles pour la version installée d’Adobe Commerce.

Voici un exemple du tableau d’état pour afficher les correctifs disponibles :

![}Magento_Correctifs_list](/help/assets/tools/status_table.png)

L’outil a pour but de vous permettre d’utiliser en libre-service des correctifs pour les problèmes que vous pouvez rencontrer avec Adobe Commerce ou d’appliquer facilement des correctifs suggérés par le support d’Adobe Commerce.

>[!NOTE]
>
>QPT est réservé aux correctifs de qualité. Les correctifs de sécurité sont disponibles dans le [Centre de sécurité Magento](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview).

## Correctifs disponibles dans l’outil Correctifs de qualité

Pour obtenir la liste des correctifs disponibles, reportez-vous à la section [Outil de correctifs de qualité](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans la documentation destinée aux développeurs.

## Comment installer et utiliser l’outil Correctifs de qualité

Les commandes d’installation et d’utilisation sont différentes pour Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud, car pour le cloud, le package QPT est inclus dans le package ece-tools.

### Comment installer et utiliser QPT pour Adobe Commerce sur site

Pour plus d’informations sur l’installation et l’utilisation de QPT pour appliquer et rétablir des correctifs, reportez-vous au [Guide de mise à jour de logiciel > Patching](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans la documentation destinée aux développeurs.

### Comment installer et utiliser QPT pour Adobe Commerce sur l’infrastructure cloud

Pour plus d’informations sur l’installation et l’utilisation du protocole QPT pour l’application et la restauration de correctifs sur Adobe Commerce sur l’infrastructure cloud, reportez-vous à la section [Cloud for Adobe Commerce > Apply patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans la documentation destinée aux développeurs.

## Lecture connexe

* [Notes de mise à jour de l’outil de correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/release-notes) dans la documentation destinée aux développeurs.
* [Comment appliquer les correctifs de compositeur fournis par Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento) dans la base de connaissances de support.
