---
title: 'ACSD-61667 : améliore les performances de l''inventaire pour créer l''expédition'
description: Appliquez le correctif ACSD-60584 pour améliorer les performances de l'inventaire pour créer l'expédition dans le cas de nombreuses sources avec ramassage en magasin.
feature: Customers, Shipping/Delivery
role: Admin, Developer
exl-id: 47682daf-9117-45f1-ab09-a66c13132ff3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-61667 : améliore les performances de l&#39;inventaire pour créer l&#39;expédition

Le correctif ACSD-61667 corrige le problème en raison duquel le commerçant ne peut pas expédier la commande lorsque la boutique de retrait [[!DNL Inventory Management for Commerce]](https://experienceleague.adobe.com/fr/docs/commerce-admin/inventory/introduction) (anciennement MSI) est activée avec plusieurs sources. Ce correctif est disponible lorsque la version 1.1.53 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-61667. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Vous ne pouvez pas expédier la commande lorsque la boutique de retrait MSI est activée, avec plusieurs sources. Ce correctif améliore les performances de l’inventaire afin de créer une expédition dans le cas de nombreuses sources avec ramassage en magasin.

<u>Conditions préalables requises:</u> :

Les modules Adobe Commerce Inventory sont installés et activés.

<u>Procédure à suivre </u> :

1. Créez plus de 10 sources *10* et activez leurs emplacements de collecte.
1. Le Pickup Store est activé sous **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**.
1. Créez un grand volume d&#39;ordres de prélèvement.
1. Accédez à **[!UICONTROL Admin login]** et sélectionnez **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL View]**.
1. Filtrer et vérifier les commandes en attente.
1. Cliquez sur **[!UICONTROL Ship]**.

<u>Résultats attendus</u> :

La page d’expédition se charge comme prévu.

<u>Résultats réels</u> :

Vous obtenez une erreur de délai d’exécution maximal *503*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
