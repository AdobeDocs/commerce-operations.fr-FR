---
title: Le magasin présélectionné dans « Ramassage en magasin » n’est pas mis à jour lors du changement d’adresse de livraison.
description: Appliquez le correctif ACSD-64753 pour résoudre le problème d’Adobe Commerce en raison duquel le magasin présélectionné ne s’est pas mis à jour lorsqu’une nouvelle adresse de livraison a été saisie en dehors du rayon de service du magasin sélectionné.
feature: Inventory
role: Admin, Developer
source-git-commit: 9d76014fb86fd92b2fffbf2de35b25a7f6d1cbae
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---


# ACSD-64753 : le magasin présélectionné dans « Pickup in Store » ne se met pas à jour lors du changement d’adresse d’expédition.

Le correctif ACSD-64753 corrige le problème en raison duquel le magasin présélectionné n’était pas mis à jour lorsqu’une nouvelle adresse d’expédition était saisie en dehors du rayon de service du magasin sélectionné. Ce correctif est disponible lorsque la version 1.1.63 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-64753. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le magasin présélectionné n&#39;a pas été mis à jour lorsqu&#39;une nouvelle adresse d&#39;expédition a été saisie en dehors du rayon de service du magasin sélectionné.

<u>Procédure à suivre </u> :

1. Activez **[!UICONTROL In-Store Delivery]** en accédant à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**.
1. Fournissez une clé API [!DNL Google] valide pour [!DNL Google Distance Provider]. Pour ce faire, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Google Distance Provider]**.
1. Ajoutez une nouvelle source (**[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]**) et définissez les valeurs suivantes :
   * **[!UICONTROL Latitude]** : *-41.917344*
   * **[!UICONTROL Longitude]** : *-88.102569*
   * **[!UICONTROL Use as Pickup Location]** : *Oui*
   * **[!UICONTROL Country United]** : *États*
   * **[!UICONTROL State]** : *Illinois*
   * **[!UICONTROL City]** : *Carol Stream*
   * **[!UICONTROL Postcode]** : *60188*
1. Ajoutez un nouveau stock (**[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** > **[!UICONTROL Add New Stock]**), attribuez-lui la nouvelle source et le site web principal.
1. Modifiez un produit, attribuez-le au nouveau Source, En stock et qté > *0*.
1. Patientez jusqu’à ce que la réindexation soit terminée.
1. Sur le storefront, créez un nouveau client, puis ajoutez une adresse Californie comme adresse de facturation et d’expédition par défaut.
1. Ajoutez une autre adresse Illinois autre que celle par défaut pour ce client.
1. Ajoutez le produit au panier et passez en caisse.
1. Laissez l&#39;adresse de livraison californienne sélectionnée et choisissez **[!UICONTROL Pick in Store]** mode de livraison. Cliquez sur **[!UICONTROL Next]**.

<u>Résultats attendus</u> :

Comme l&#39;adresse de la Californie se trouve en dehors du rayon de recherche maximal (200 km), l&#39;Illinois Source ne devrait pas être disponible pour le client.

<u>Résultats réels</u> :

La source Illinois peut être sélectionnée et le client peut passer en caisse.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
