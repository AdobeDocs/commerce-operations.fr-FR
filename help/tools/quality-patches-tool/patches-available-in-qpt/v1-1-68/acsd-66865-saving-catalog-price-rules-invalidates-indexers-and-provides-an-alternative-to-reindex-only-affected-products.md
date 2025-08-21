---
title: 'ACSD-66865 : l’enregistrement d’un [!UICONTROL Catalog Price Rule] invalide les indexeurs et offre une alternative à la réindexation des produits affectés uniquement'
description: Appliquez le correctif ACSD-66865 pour résoudre le problème Adobe Commerce où  l’enregistrement d’un [!UICONTROL Catalog Price Rules] invalide les indexeurs et fournit une alternative à la réindexation uniquement des produits affectés.
feature: Price Rules, Price Indexer
role: Admin, Developer
type: Troubleshooting
source-git-commit: fe36522b99ec3fe7189d164cfca6127c9119e06e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# ACSD-66865 : l’enregistrement d’un **[!UICONTROL Catalog Price Rule]** invalide les indexeurs et offre une alternative à la réindexation des produits affectés uniquement

Le correctif ACSD-66865 corrige le problème où l’enregistrement d’un **[!UICONTROL Catalog Price Rule]** invalide les indexeurs et fournit une alternative à la réindexation des produits affectés uniquement. Ce correctif est disponible lorsque la version 1.1.68 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66865. Ce problème a été résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’enregistrement d’un **[!UICONTROL Catalog Price Rule]** entraîne l’invalidation de tous les indexeurs, ce qui déclenche des réindexations complètes au lieu de réindexer uniquement les produits affectés.

<u>Procédure à suivre </u> :

1. Assurez-vous que cron n’est pas en cours d’exécution et que tous les indexeurs sont définis pour se mettre à jour selon le calendrier (à l’exception de `customer_grid` qui peut se mettre à jour lors de l’enregistrement).
2. Exécutez une réindexation manuelle complète à l’aide de la commande : `php bin/magento indexer:reindex`.
3. Vérifiez que tous les index affichent le statut *[!UICONTROL Ready]* avec des éléments *0* dans la liste d’attente.
4. Dans la barre latérale d’administration, accédez à **[!UICONTROL Marketing]** > *[!UICONTROL Promotions]* > **[!UICONTROL Catalog Price Rule]**. Créez une règle de prix de catalogue active pour un seul produit (par exemple, à l’aide d’une condition *SKU*).
5. Exécutez la commande : `php bin/magento indexer:status` pour vérifier le statut de l’indexeur.
6. Notez que plusieurs index sont marqués comme **[!UICONTROL Reindex Required]**, même si un seul produit est affecté.

<u>Résultats attendus</u> :

Seules les données de produit affectées sont identifiées et une réindexation partielle est déclenchée au lieu d’une réindexation complète sur tous les indexeurs.

<u>Résultats réels</u> :

Une réindexation complète est déclenchée pour tous les indexeurs, même lorsqu’un seul produit est affecté par le **[!UICONTROL Catalog Price Rule]**.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
