---
title: Bonnes pratiques de configuration pour les indexeurs
description: Maintenez et optimisez les performances du site en suivant les bonnes pratiques de configuration de l’indexeur.
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 153cf3bae74a78d7a41176e0216203d354d2513b
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Bonnes pratiques relatives à la configuration de l’indexeur

Pour optimiser et maintenir les performances du site, passez en revue et mettez à jour la configuration de l’indexeur à l’aide des bonnes pratiques de performances décrites dans cet article.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Définir les indexeurs à mettre à jour selon un planning

Adobe Commerce a deux types de modes d&#39;indexation : [!UICONTROL Update on Save] et [!DNL Update on Schedule].

- Le mode **[!UICONTROL Update on Save]** met immédiatement à jour les index chaque fois que votre catalogue ou d’autres données changent. Par exemple, si un utilisateur administrateur ajoute de nouveaux produits à une catégorie, l’index des produits de catégorie est réindexé immédiatement lors de l’enregistrement de la mise à jour.

- Le mode **[!UICONTROL Update on Schedule]** stocke des informations sur les mises à jour de données, et les opérations de réindexation et les mises à jour d’index sont gérées par une tâche cron qui s’exécute en arrière-plan à des intervalles planifiés. La tâche cron n’effectue pas toujours une réindexation à chaque exécution. Il effectue une nouvelle indexation uniquement lorsqu’il existe de nouvelles entrées dans les journaux des modifications de l’indexeur (par exemple, qu’il y a un journal sur les indexeurs).

Le fait qu’un grand magasin avec plusieurs administrateurs fonctionne en arrière-plan ou qu’il y ait de nombreux imports et exports déclenche de fréquentes mises à jour de l’index. Si la configuration de l’index de votre site est définie sur le mode [!UICONTROL Update on Save], la réindexation fréquente dégrade les performances de la base de données, ce qui ralentit les performances du site et entraîne de longs délais dans le processus de réindexation, en particulier pour les grands magasins.

Pour optimiser les performances du site, suivez les bonnes pratiques d’indexation suivantes :

- Examinez la configuration de l’index.
- Définissez les indexeurs sur _[!UICONTROL Update on Schedule]_pour les sites volumineux et les sites avec des mises à jour fréquentes et un trafic élevé. Voir [Gestion des index](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- Suivez les [bonnes pratiques de performances](../../../performance/configuration.md) pour gérer les index.

>[!IMPORTANT]
>
>[!DNL Customer Grid] ne peut être réindexé qu&#39;à l&#39;aide de l&#39;option [!UICONTROL Update on Save]. Cet index ne prend pas en charge l’option `Update by Schedule`.

## Informations supplémentaires

- [Gestion des index pour les utilisateurs administrateurs](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Gestion des index à l’aide de l’interface de ligne de commande du Magento](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [Présentation de l’indexation pour les développeurs](https://developer.adobe.com/commerce/php/development/components/indexing/)
