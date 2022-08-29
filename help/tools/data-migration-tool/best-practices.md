---
title: Bonnes pratiques relatives à la migration des données
description: Suivez ces bonnes pratiques de migration de données pour assurer une mise à niveau réussie de Magento 1 vers Magento 2.
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# Bonnes pratiques relatives à la migration des données

Cette section fournit les meilleures recommandations pour accélérer et simplifier votre migration, ainsi que des conseils sur le temps nécessaire.

* **Utiliser une copie de la base de données à partir d’une instance Magento 1** lors des tests de migration. N’utilisez pas l’instance de production de votre base de données de magasin Magento 1.

* **Supprimer les données obsolètes et redondantes** de la base de données Magento 1 avant la migration.

Ces données peuvent inclure des logs, des devis de commande, des produits récemment consultés ou comparés, des visiteurs, des catégories spécifiques à un événement et des règles promotionnelles.

* **Suivez la [règles générales pour une migration réussie](migrate-data/overview.md#migration-overview)**.

* Pour améliorer les performances, **activez la variable `direct_document_copy` option** dans votre `config.xml` fichier :

   ```xml
   <direct_document_copy>1</direct_document_copy>
   ```

>[!NOTE]
>
>Les bases de données de Magento 1 et de Magento 2 doivent se trouver sur le même serveur MySQL et le compte de base de données doit avoir accès aux deux bases de données.

## Évaluations comparatives

Adobe a testé la migration des données sur le système suivant :

* Virtual Box VM, CentOS 6, 2,5 Go de mémoire vive, CPU 1 core 2,6 GHz
* Base de données de 177 000 produits, 355 000 commandes et 214 000 clients

## Résultats des performances

* Temps de migration des paramètres : ~10 minutes
* Temps de migration des données : ~9 heures (toutes les données sauf les réécritures d’URL, ~85 % du total des données)
* Estimation du temps d’arrêt du site : quelques minutes pour réindexer et modifier les paramètres DNS. Temps supplémentaire nécessaire pour réchauffer le cache de la page.
