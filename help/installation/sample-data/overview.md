---
title: Présentation des exemples de données
description: Découvrez comment utiliser des exemples de données pour les projets Adobe Commerce et Magento Open Source.
exl-id: 828b009d-a6ff-4db2-aa1a-838f6f55a194
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Présentation des exemples de données

Les exemples de données fournissent une vitrine basée sur le thème Luma équipé de produits, de catégories, d’enregistrement de clients, etc. Il fonctionne comme un storefront Commerce et vous pouvez manipuler les prix, les stocks et les règles de prix promotionnels à l’aide de l’administrateur.

Vous pouvez installer des exemples de données avant ou après l’installation du logiciel Commerce. Lorsque vous avez terminé avec les exemples de données, vous pouvez soit le supprimer, soit l’installer à nouveau, comme décrit dans la section [Supprimer des exemples de modules de données ou mettre à jour des exemples de données](remove-or-update.md).

>[!WARNING]
>
>Vous ne pouvez pas désinstaller les exemples de données. Nous vous recommandons d’utiliser des exemples de données uniquement pour en savoir plus sur le fonctionnement d’Adobe Commerce et de Magento Open Source. Évitez d’effectuer un développement dans un système dans lequel vous avez installé des exemples de données.

Vous pouvez installer des exemples de données facultatifs de l’une des manières suivantes :

| Méthode d&#39;installation | Description | Niveau de compétence requis |
|--- |--- |--- |
| Utilisation du compositeur | [Exécuter `magento sampledata:deploy` modification de la racine de l’application `composer.json`](composer-packages.md) pour activer les exemples de modules de données. | Nécessite des connaissances du compositeur et un accès au système de fichiers Commerce. |
| Clonage des référentiels | [Clonage du référentiel GitHub](git-repositories.md) et l’exemple de référentiel de données, puis reliez-les. | Pour les développeurs qui contribuent uniquement. Tous les autres devraient utiliser l&#39;une des méthodes précédentes. |
