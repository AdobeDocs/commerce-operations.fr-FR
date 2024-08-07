---
title: Présentation des exemples de données
description: Découvrez comment utiliser des exemples de données pour les projets Adobe Commerce.
exl-id: 828b009d-a6ff-4db2-aa1a-838f6f55a194
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Présentation des exemples de données

Les exemples de données fournissent une vitrine basée sur le thème Luma équipé de produits, de catégories, d’enregistrement de clients, etc. Il fonctionne comme un storefront Commerce et vous pouvez manipuler les prix, les stocks et les règles de prix promotionnels à l’aide de l’administrateur.

>[!NOTE]
>
>Pour passer en revue et analyser la base de données et différentes fonctionnalités, pensez à utiliser des données réelles plutôt que des exemples de données. Les exemples de données sont conçus comme une simulation de magasin prégénérée, afin de démontrer la conception de thème et le comportement de base du storefront. Toutes les entités de données d’exemple sont écrites directement dans les tables de base de données, tandis que les données d’exemple sont installées.

Vous pouvez installer des exemples de données avant ou après l’installation du logiciel Commerce. Lorsque vous avez terminé avec les exemples de données, vous pouvez soit le supprimer, soit l’installer à jour, comme décrit dans la section [Suppression des exemples de modules de données ou mise à jour des exemples de données](remove-or-update.md).

>[!WARNING]
>
>Vous ne pouvez pas désinstaller les exemples de données. Utilisez des exemples de données uniquement pour en savoir plus sur le fonctionnement d’Adobe Commerce. Évitez d’effectuer un développement dans un système dans lequel vous avez installé des exemples de données.

Vous pouvez installer des exemples de données facultatifs de l’une des manières suivantes :

| Méthode d&#39;installation | Description | Niveau de compétence requis |
|--- |--- |--- |
| Utilisation du compositeur | [ Exécutez `magento sampledata:deploy` pour modifier la racine de l’application `composer.json`](composer-packages.md) afin d’activer les exemples de modules de données. | Nécessite des connaissances du compositeur et un accès au système de fichiers Commerce. |
| Clonage des référentiels | [Cloner le référentiel GitHub](git-repositories.md) et le référentiel de données d’exemple, puis les lier. | Pour les développeurs qui contribuent uniquement. Tous les autres devraient utiliser l&#39;une des méthodes précédentes. |
