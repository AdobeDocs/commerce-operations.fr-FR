---
title: 'ACSD-65331 : le magasin sélectionné dans [!UICONTROL Pick in Store] effacé après être revenu en caisse'
description: Appliquez le correctif ACSD-65331 pour résoudre le problème d’Adobe Commerce où le magasin sélectionné sous l’option [!UICONTROL Pick In Store] est effacé lorsque les utilisateurs reviennent à plusieurs reprises sur la page de passage en caisse.
feature: Inventory
role: Admin, Developer
type: Troubleshooting
source-git-commit: a322e822ccf0b584d2385d3f38a3b92ebe3a23d3
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---


# ACSD-65331 : le magasin sélectionné dans **[!UICONTROL Pick in Store]** effacé après être revenu en caisse

Le correctif ACSD-65331 corrige le problème où le magasin sélectionné sous l’option **[!UICONTROL Pick In Store]** est effacé lorsque les utilisateurs reviennent à plusieurs reprises sur la page de passage en caisse. Ce correctif est disponible lorsque la version 1.1.65 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-65331. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le magasin sélectionné sous l’option **[!UICONTROL Pick In Store]** est effacé lorsque les utilisateurs reviennent à plusieurs reprises sur la page de passage en caisse.

<u>Procédure à suivre </u> :

1. Activez **[!UICONTROL In-Store Delivery]** en accédant à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**.
1. Configurez une clé API [!DNL Google] valide à [!UICONTROL Google Distance Provider] en accédant à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Google Distance Provider]**.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]** pour ajouter une nouvelle source avec les détails suivants :

   * **[!UICONTROL Latitude]** : 41,917344 **
   * **[!UICONTROL Longitude]** : *-88.102569*
   * **[!UICONTROL Use as Pickup Location]** : *Oui*
   * **[!UICONTROL Country]** : *États-Unis*
   * **[!UICONTROL State]** : *Illinois*
   * **[!UICONTROL City]** : *Carol Stream*
   * **[!UICONTROL Street]** : *565 E. Fullerton Ave.*
   * **[!UICONTROL Postcode]** : *60188*

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Stocks]** > **[!UICONTROL Add New Stock]** pour créer un nouveau stock.

   Affectez la source nouvellement créée et le site web principal à ce stock.
1. Modifiez un produit et :

   1. Attribuez-le à la source nouvellement créée.
   1. Définissez son statut sur *[!UICONTROL In Stock]* et sa quantité sur une valeur supérieure à 0.

1. Exécutez vos réindexeurs.
1. Sur le storefront, créez un nouveau client et définissez une adresse Californie comme adresse de facturation et d’expédition par défaut.
1. Ajoutez une adresse Illinois supplémentaire au même client (non par défaut).
1. Ajoutez le produit configuré au panier et passez à la **[!UICONTROL Checkout]**.
1. Sélectionnez l’adresse Illinois, choisissez **[!UICONTROL Pick In Store]** comme mode d’expédition, puis cliquez sur **[!UICONTROL Next]**.
1. Attendez que la source se charge et cliquez sur **[!UICONTROL Next]**.
1. Revenez à la page d’accueil.
1. Revoyez la page **[!UICONTROL Checkout]**.

<u>Résultats attendus</u> :

Le magasin sélectionné doit rester disponible sous **[!UICONTROL Pick In Store]**.

<u>Résultats réels</u> :

L’étape d’expédition commence à charger et à rediriger vers **[!UICONTROL Pick In Store]**, mais aucun magasin n’est visible.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] **&#x200B; > Utilisation]**(/help/tools/quality-patches-tool/usage.md) dans le guide de[!DNL Quality Patches Tool]**.
* ** Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs]&#x200B;(https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool]**, consultez :

* [[!DNL Quality Patches Tool]&#x200B;**: outil en libre-service pour les correctifs de qualité]**(/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
