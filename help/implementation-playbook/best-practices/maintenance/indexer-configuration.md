---
title: Bonnes pratiques de configuration pour les indexeurs
description: Maintenez et optimisez les performances du site en suivant les bonnes pratiques de configuration de l’indexeur.
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: af66d47279245f8ee105030bbb33d77b1b35c3e5
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Bonnes pratiques relatives à la configuration de l’indexeur

Pour optimiser et maintenir les performances du site, passez en revue et mettez à jour la configuration de l’indexeur à l’aide des bonnes pratiques de performances décrites dans cet article.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Définir les indexeurs à mettre à jour selon un planning

Adobe Commerce possède deux types de modes d’indexation : [!UICONTROL Update on Save] (paramètre par défaut) et [!DNL Update on Schedule].

- **[!UICONTROL Update on Save]** Le mode met immédiatement à jour les index chaque fois que votre catalogue ou d’autres données changent. Par exemple, si un utilisateur administrateur ajoute de nouveaux produits à une catégorie, l’index des produits de catégorie est réindexé immédiatement lors de l’enregistrement de la mise à jour.

- **[!UICONTROL Update on Schedule]** Le mode stocke des informations sur les mises à jour des données. Les opérations de réindexation et les mises à jour d’index sont gérées par une tâche cron qui s’exécute en arrière-plan à des intervalles planifiés. La tâche cron n’effectue pas toujours une réindexation à chaque exécution. Il effectue une nouvelle indexation uniquement lorsqu’il existe de nouvelles entrées dans les journaux des modifications de l’indexeur (par exemple, qu’il y a un journal sur les indexeurs).

Le fait qu’un grand magasin avec plusieurs administrateurs fonctionne en arrière-plan ou qu’il y ait de nombreux imports et exports déclenche de fréquentes mises à jour de l’index. Si la configuration de l’index de site est définie sur [!UICONTROL Update on Save] , la réindexation fréquente dégrade les performances de la base de données, ce qui ralentit les performances du site et entraîne de longs délais dans le processus de réindexation, en particulier pour les grands magasins.

Pour optimiser les performances du site, suivez les bonnes pratiques d’indexation suivantes :

- Examinez la configuration de l’index.
- Définissez les indexeurs sur _[!UICONTROL Update on Schedule]_pour les sites volumineux, les sites avec des mises à jour fréquentes et un trafic important. Voir [Gestion des index](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- Suivez [bonnes pratiques en matière de performances](../../../performance/configuration.md) pour la gestion des index.

>[!IMPORTANT]
>
>La variable [!DNL Customer Grid] ne peut être réindexé qu’à l’aide de la fonction [!UICONTROL Update on Save] . Cet index ne prend pas en charge la variable `Update by Schedule` .

## Informations supplémentaires

- [Gestion des index pour les utilisateurs administrateurs](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Gestion des index à l’aide de l’interface de ligne de commande du Magento](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [Présentation de l’indexation pour les développeurs](https://developer.adobe.com/commerce/php/development/components/indexing/)
