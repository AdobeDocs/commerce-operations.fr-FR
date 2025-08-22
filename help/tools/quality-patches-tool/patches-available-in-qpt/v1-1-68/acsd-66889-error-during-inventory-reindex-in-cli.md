---
title: 'ACSD-66889 : erreur lors de la réindexation de l’inventaire dans l’interface de ligne de commande'
description: Appliquez le correctif ACSD-66889 pour résoudre le problème d’Adobe Commerce qui déclenche une erreur lors de l’exécution de l’indexeur d’inventaire.
feature: Inventory
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9631e0864b2ad8fc09734aedd476e96852cd70fb
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---


# ACSD-66889 : erreur lors de la réindexation de l’inventaire dans l’interface de ligne de commande

Le correctif ACSD-66889 corrige l’erreur qui se produit lors de l’exécution de l’indexeur d’inventaire. Ce correctif est disponible lorsque la version 1.1.68 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66889.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p13

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de l’exécution de l’indexeur d’inventaire, le processus génère un avertissement d’obsolescence et ne se termine pas en raison d’une syntaxe de chaîne obsolète.

<u>Procédure à suivre </u> :

1. Exécutez la réindexation de l’inventaire à l’aide de la commande de l’interface de ligne de commande :

   ```
   php bin/magento indexer:reindex inventory
   ```

<u>Résultats attendus</u> :

L’interface en ligne de commande reconstruit l’indexeur d’inventaire avec succès.

<u>Résultats réels</u> :

L’interface de ligne de commande renvoie une erreur de fonctionnalité obsolète et les index d’inventaire conservent l’état *Réindexation requise* :

```
Deprecated Functionality: Using ${var} in strings is deprecated, use {$var} instead in /home/vendor/magento/module-elasticsearch-catalog-permissions/Model/Adapter/FieldMapper/Product/FieldProvider/FieldName/Resolver/CategoryPermission.php on line 24
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
