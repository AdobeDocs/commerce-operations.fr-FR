---
title: 'ACSD-62146 : l’adresse de facturation sélectionnée disparaît de la page de paiement de la commande'
description: Appliquez le correctif ACSD-62146 pour résoudre le problème d’Adobe Commerce où l’adresse de facturation sélectionnée disparaît sur la page de paiement de la commande lorsque la recherche d’adresses est activée et que la limite du nombre d’adresses client est définie sur 1.
feature: Customers, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: 3de3de80383372d0e3bec5485fd65b9d70fe8860
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# ACSD-62146 : l’adresse de facturation sélectionnée disparaît de la page de paiement de la commande

Le correctif ACSD-62146 corrige le problème où l’adresse de facturation sélectionnée disparaît sur la page de paiement de la commande lorsque la recherche d’adresse est activée et que la [!UICONTROL Number of Customer Addresses Limit] est définie sur 1. Ce correctif est disponible lorsque la version 1.1.68 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62146. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’adresse de facturation sélectionnée disparaît sur la page de paiement de la commande lorsque la recherche d’adresse est activée et que la **[!UICONTROL Number of Customer Addresses Limit]** est définie sur 1.

<u>Procédure à suivre </u> :

1. Pour activer la recherche d’adresses, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**.
1. Définissez **[!UICONTROL Number of Customer Addresses Limit]** sur 1.
1. Créez un client et ajoutez deux adresses différentes.
1. Ajoutez un produit au panier et passez en caisse.
1. Cliquez sur **[!UICONTROL Change Address]** et utilisez la fenêtre contextuelle pour modifier l’adresse.
1. Sélectionnez Adresse 2 comme adresse de livraison.
1. Cliquez sur **[!UICONTROL Next]** pour passer à l’étape de paiement.
1. Vérifiez que l’adresse de facturation et l’adresse d’expédition sont identiques.
1. Actualisez la page sans effectuer le paiement.

<u>Résultats attendus</u> :

L’adresse d’expédition est visible lorsque les adresses de facturation et d’expédition sont identiques.

<u>Résultats réels</u> :

L’adresse de facturation par défaut et l’adresse de livraison sélectionnée ne sont pas visibles.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
