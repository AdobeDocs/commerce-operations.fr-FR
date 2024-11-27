---
title: "ACSD-61667 : améliore les performances d’inventaire pour la création d’expédition"
description: Appliquez le correctif ACSD-60584 afin d’améliorer les performances d’inventaire pour la création d’expédition en cas de nombreuses sources avec une récupération en magasin.
feature: Customers, Shipping/Delivery
role: Admin, Developer
source-git-commit: 29748a439992c0e3efbbc84c5ab9c8239f460b73
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-61667 : améliore les performances d’inventaire pour la création d’expédition

Le correctif ACSD-61667 corrige le problème où le commerçant ne peut pas envoyer la commande lorsque le magasin de récupération [[!DNL Inventory Management for Commerce]](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) (anciennement MSI) est activé avec plusieurs sources. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 est installé. L’ID de correctif est ACSD-61667. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Vous ne pouvez pas envoyer la commande lorsque le magasin de récupération MSI est activé, avec plusieurs sources. Ce correctif améliore les performances de l’inventaire pour créer l’expédition en cas de nombreuses sources avec la récupération en magasin.

<u>Conditions préalables :</u> :

Les modules d’inventaire Adobe Commerce sont installés et activés.

<u>Étapes à reproduire</u> :

1. Créez plus de *10* sources et activez leurs emplacements de récupération.
1. Le magasin de sélections est activé sous **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**.
1. Créez un grand volume de commandes de saut.
1. Accédez à **[!UICONTROL Admin login]** et sélectionnez **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL View]**.
1. Filtrez et recherchez les commandes en attente.
1. Cliquez sur **[!UICONTROL Ship]**.

<u>Résultats attendus</u> :

La page d’expédition se charge comme prévu.

<u>Résultats réels</u> :

Vous obtenez une erreur *503 Maximum execution time out*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.

