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

Les exemples de données fournissent une vitrine basée sur le thème Luma doté de produits, de catégories, de l’enregistrement des clients, etc. Il fonctionne comme une vitrine Commerce et vous pouvez manipuler les prix, les stocks et les règles de tarification promotionnelle à l’aide de l’administrateur.

>[!NOTE]
>
>Pour examiner et analyser la base de données et diverses fonctionnalités, pensez à utiliser des données réelles plutôt que des données d’exemple. Les exemples de données sont conçus comme une simulation de magasin prégénérée, pour démontrer la conception du thème et le comportement de base du storefront. Toutes les entités de données d’exemple sont écrites directement dans les tables de la base de données, tandis que les données d’exemple sont installées.

Vous pouvez installer des données d’exemple avant ou après l’installation du logiciel Commerce. Lorsque vous avez terminé d’utiliser les exemples de données, vous pouvez soit les supprimer, soit les installer à nouveau, comme indiqué dans la section [Supprimer des exemples de modules de données ou mettre à jour des exemples de données](remove-or-update.md).

>[!WARNING]
>
>Vous ne pouvez pas désinstaller les données d’exemple. Utilisez des données d’exemple uniquement pour en savoir plus sur le fonctionnement d’Adobe Commerce. Évitez d’effectuer tout développement dans un système dans lequel vous avez installé des données d’exemple.

Vous pouvez installer les données d’exemple facultatives de l’une des manières suivantes :

| Méthode d’installation | Description | Niveau de compétence requis |
|--- |--- |--- |
| Utilisation du compositeur | [Exécutez `magento sampledata:deploy` pour modifier le `composer.json`](composer-packages.md) racine de l’application afin d’activer les exemples de modules de données. | Nécessite des connaissances en compositeur et un accès au système de fichiers Commerce. |
| Clonage de référentiels | [Clonez le référentiel GitHub](git-repositories.md) ainsi que le référentiel de données d’exemple, puis liez-les. | Pour les développeurs contributeurs uniquement. Toute autre personne doit utiliser l’une des méthodes précédentes. |
