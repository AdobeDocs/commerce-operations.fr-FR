---
title: Bonnes pratiques de configuration pour les indexeurs
description: Maintenez et optimisez les performances du site en suivant les bonnes pratiques pour la configuration de l’indexeur.
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 29168544e3a33b874b104f308bd53cb475ac2638
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Bonnes pratiques relatives à la configuration de l’indexeur

Pour optimiser et maintenir les performances du site, passez en revue et mettez à jour la configuration de l’indexeur à l’aide des bonnes pratiques de performances décrites dans cet article.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

## Définir les indexeurs pour qu’ils se mettent à jour selon un planning

Adobe Commerce dispose de deux types de modes d’indexeur : [!UICONTROL Update on Save] et [!DNL Update on Schedule].

- Le mode **[!UICONTROL Update on Save]** met immédiatement à jour les index chaque fois que votre catalogue ou d’autres données sont modifiés. Par exemple, si un utilisateur administrateur ajoute de nouveaux produits à une catégorie, l’index des produits de la catégorie est réindexé immédiatement lorsque la mise à jour est enregistrée.

- **[!UICONTROL Update on Schedule]** mode stocke des informations sur les mises à jour de données. Les opérations de réindexation et les mises à jour d’index sont gérées par une tâche cron qui s’exécute en arrière-plan à des intervalles planifiés. La tâche cron n’effectue pas toujours une réindexation à chaque exécution. Il réindexe uniquement lorsqu’il existe de nouvelles entrées dans les journaux des modifications de l’indexeur (par exemple, une liste d’attente se trouve sur les indexeurs).

Un magasin volumineux avec plusieurs administrateurs travaillant en arrière-plan ou ayant de nombreux imports et exports déclenche de fréquentes mises à jour d’index. Si la configuration de l’index de votre site est définie sur le mode [!UICONTROL Update on Save], une réindexation fréquente dégrade les performances de la base de données, ce qui ralentit les performances du site et entraîne de longs retards dans le processus de réindexation, en particulier pour les grands magasins.

Pour optimiser les performances du site, suivez ces bonnes pratiques d’indexation :

- Vérifiez la configuration de l’index.
- Définissez les indexeurs sur _[!UICONTROL Update on Schedule]_&#x200B;pour les sites volumineux et les sites comportant des mises à jour fréquentes et un trafic important. Voir [Gestion des index](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management#change-the-index-mode).
- Appliquez les [bonnes pratiques en matière de performances](../../../performance/configuration.md) pour gérer les index.

>[!IMPORTANT]
>
>Le comportement de l’indexeur [!DNL Customer Grid] a changé dans la version 2.4.8 :
>
>- **Antérieur à la version 2.4.8** : l’indexeur de [!DNL Customer Grid] ne peut être réindexé qu’à l’aide de l’option [!UICONTROL Update on Save] et ne prend pas en charge l’option [!UICONTROL Update by Schedule].
>- **2.4.8 et versions ultérieures** : l’indexeur de [!DNL Customer Grid] prend en charge les modes [!UICONTROL Update on Save] et [!UICONTROL Update by Schedule], et la valeur par défaut est [!UICONTROL Update by Schedule].

## Informations supplémentaires

- [Gestion des index pour les utilisateurs administrateurs](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Gestion des index à l’aide de l’interface de ligne de commande Magento](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [Présentation de l’indexation pour les développeurs](https://developer.adobe.com/commerce/php/development/components/indexing/)
