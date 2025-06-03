---
title: 'ACSD-65223 : les termes et accords sélectionnés manuellement pour les commandes fournisseur B2B génèrent une erreur'
description: Appliquez le correctif ACSD-65223 pour résoudre le problème d'Adobe Commerce où les commandes créées à l'aide de [!UICONTROL Purchase Orders] ne peuvent pas être exécutées avec des méthodes de paiement en ligne telles que les cartes de crédit lorsque les conditions générales sont requises pour le paiement.
feature: B2B, Purchase Orders
role: Admin, Developer
source-git-commit: 57c0cb63f1e2c7b12d11b759eddf0d21b5db78b2
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---


# ACSD-65223 : les termes et accords sélectionnés manuellement pour les commandes fournisseur B2B génèrent une erreur

Le correctif ACSD-65223 corrige le problème où les commandes créées à l&#39;aide de **[!UICONTROL Purchase Orders]** ne peuvent pas être effectuées avec des méthodes de paiement en ligne comme les cartes de crédit lorsque les conditions générales sont requises pour le paiement. Ce correctif est disponible lorsque la version 1.1.64 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-65223.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) B2B 1.5.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) B2B 1.5.1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Si les conditions générales sont requises pour passer une commande et que vous essayez de finaliser une commande créée à l&#39;aide de [!UICONTROL Purchase Orders], la commande ne peut pas être passée à l&#39;aide de méthodes de paiement en ligne telles que les cartes de crédit.

<u>Procédure à suivre </u> :

1. Créez un produit simple.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** et choisissez **[!UICONTROL B2B Features]**.
1. Définissez **[!UICONTROL Enable Company]** et **[!UICONTROL Enable Purchase Orders]** sur *Oui*.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Terms and Conditions]** et créez une condition. Définissez **[!UICONTROL Applied]** sur *[!UICONTROL Manually]*.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** et définissez **[!UICONTROL Enable Terms and Conditions]** sur *Oui*.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment Methods]** et configurez [!DNL Braintree].
1. Sur le storefront, créez une entreprise.
1. Dans l’administration, accédez à **[!UICONTROL Customers]** > **[!UICONTROL Companies]**.
1. Valider la société et autoriser le **[!UICONTROL Purchase Orders]**.
1. Sur le front-end, connectez-vous au compte .
1. Ajoutez un article au panier.
1. Passer une commande à l’aide de **[!UICONTROL Purchase Order]**.
1. Dans le tableau de bord du client, cliquez sur l&#39;onglet **[!UICONTROL Purchase Orders]** .
1. Créez une commande à partir de la nouvelle commande fournisseur. Sélectionnez ensuite carte de crédit comme mode de paiement.
1. Acceptez les conditions générales.
1. Passez la commande.

<u>Résultats attendus</u> :

Vous pouvez passer une commande à l&#39;aide d&#39;un mode de paiement en ligne sur les commandes fournisseur approuvées lorsque les conditions générales sont requises pour le passage en caisse.

<u>Résultats réels</u> :

Vous ne pouvez pas passer de commande à l&#39;aide d&#39;un mode de paiement en ligne sur des commandes fournisseur approuvées lorsque les conditions générales sont requises pour le passage en caisse.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
