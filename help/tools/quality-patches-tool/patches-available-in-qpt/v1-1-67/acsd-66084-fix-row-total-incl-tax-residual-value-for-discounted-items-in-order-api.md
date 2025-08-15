---
title: 'ACSD-66084 : « row_total_incl_tax » renvoie un résultat proche de zéro au lieu de 0,00 pour les articles bénéficiant d’une remise totale dans l’API de commande'
description: Appliquez le correctif ACSD-66084 pour résoudre le problème d’Adobe Commerce où « row_total_incl_tax » renvoyait une valeur résiduelle proche de zéro au lieu de 0,00 pour les éléments entièrement actualisés dans la réponse de l’API de commande.
feature: Orders, REST, Taxes, Payments, Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 421c6fe6-b6b1-4f33-acb6-fbd4306bcc4c
source-git-commit: 951738a4c671ed6fcc47b2a928d2110c78763d26
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# ACSD-66084 : `row_total_incl_tax` renvoie un résultat proche de zéro au lieu de 0,00 pour les articles bénéficiant d’une remise totale dans l’API de commande

Le correctif ACSD-66084 corrige le problème où `row_total_incl_tax` est renvoyée comme une valeur résiduelle proche de zéro dans la réponse de l’API de commande au lieu de 0,00 pour les articles bénéficiant d’une remise totale. Ce correctif est disponible lorsque la version 1.1.67 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66084. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le `row_total_incl_tax` est renvoyé sous la forme d’une valeur résiduelle proche de zéro dans la réponse de l’API de commande au lieu de 0,00 pour les articles entièrement actualisés.

<u>Procédure à suivre </u> :

1. Créez un produit avec un prix et un prix spécial. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > Cliquez sur **[!UICONTROL Add Product]** > définissez **[!UICONTROL Price]** sur 25 $ et **[!UICONTROL Special Price]** sur 16,99 $ sous **[!UICONTROL Advanced Pricing]**.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Taxes]** > **[!UICONTROL Tax Zones and Rates]** et ajoutez un taux de 20 %. Accédez ensuite à **[!UICONTROL Tax Rules]** , créez une règle et affectez .
   **[!UICONTROL Taxable Goods]** comme classe de taxe du produit.
1. Créez une règle de vente avec une remise de 100 % et un coupon. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** et ajoutez une règle avec une réduction de 100 %, puis utilisez **[!UICONTROL Specific Coupon]** et saisissez votre code.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** > et configurez les paramètres de taxe.
1. Activez la livraison gratuite. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL Free Shipping]**. Définissez **[!UICONTROL Enabled]** paramètres sur **[!UICONTROL Yes]** et ajustez-les.
1. Accédez à la page produit et sélectionnez **[!UICONTROL Add to Cart]**. Accédez au panier et appliquez le code de coupon.
1. Passez la commande avec la zone fiscale applicable.
1. Générez un jeton d’administration (API) via l’API REST.
1. Récupérez les détails de la commande via l’API REST.
1. Vérifiez `row_total_incl_tax` dans la réponse.

<u>Résultats attendus</u> :

`row_total_incl_tax` doit renvoyer une valeur adaptée à la devise, telle que `0.00` lorsque l&#39;article est entièrement actualisé.

<u>Résultats réels</u> :

`row_total_incl_tax` renvoie une valeur en virgule flottante proche de zéro telle que `3.5527136788005e-15`, qui n’est pas appropriée pour l’affichage de la devise.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
