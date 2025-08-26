---
title: 'ACP2E-4050 : [!UICONTROL Free Shipping] non appliqué avec la commande avec expédition multiple'
description: Appliquez le correctif ACP2E-4050 pour résoudre le problème d’Adobe Commerce où [!UICONTROL Free Shipping] n’est pas appliqué lors de la passage en caisse multi-adresses lorsque [!UICONTROL Cart Price Rules] incluez des conditions et des produits sous-sélectionnés à des prix spécifiques.
feature: Shopping Cart, Shipping/Delivery
role: Admin, Developer
type: Troubleshooting
source-git-commit: d36ce39fcd897261b784d57f8806b3eceb66fc01
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# ACP2E-4050 : **[!UICONTROL Free Shipping]** non appliqué avec la commande avec expédition multiple

Le correctif ACP2E-4050 corrige le problème où **[!UICONTROL Free Shipping]** n’est pas appliqué lors d’une commande avec expédition multiple lorsque **[!UICONTROL Cart Price Rules]** incluez des conditions de sous-sélection et des produits à des prix spécifiques. Ce correctif est disponible lorsque la version 1.1.69 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACP2E-4050. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p10

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

**[!UICONTROL Free Shipping]** n’est pas appliqué lors d’un passage en caisse avec expédition multiple lorsque **[!UICONTROL Cart Price Rules]** incluez des conditions de sous-sélection et des produits à des prix spécifiques.

<u>Procédure à suivre </u> :

1. Créez un compte client avec deux adresses.
1. Activez **[!UICONTROL Free Shipping]** et définissez **[!UICONTROL Minimum Order Amount]** sur *999999*.
1. Accédez à [!UICONTROL Admin] > [!UICONTROL Marketing] > [!UICONTROL Cart Price Rules], puis créez une règle de prix de panier avec les conditions suivantes :

```
If ALL of these conditions are TRUE:
 * Subtotal is at least 50
 * The subtotal is at most 500
 * Apply this condition if the total amount is 50 or more for a subset of cart items that meet all specified criteria:
 * Category is 23
```

1. Installer les exemples de données.
1. Ajoutez les produits suivants au panier dans l’ordre spécifié :
   * Wayfarer Messenger Bag
   * Olivia 1/4 Zip Light Jacket
   * Sprite Yoga Companion Kit.
1. Ouvrez le panier et vérifiez que l’option **[!UICONTROL Free Shipping]** est disponible.
1. Cliquez sur **[!UICONTROL Check Out with Multiple Addresses]**.
1. Sélectionnez une autre adresse de livraison pour le produit simple.
1. Cliquez sur **[!UICONTROL Go to Shipping Information]**.

<u>Résultats attendus</u> :

**[!UICONTROL Free Shipping]** s’applique aux expéditions de produits configurables et groupées.

<u>Résultats réels</u> :

**[!UICONTROL Free Shipping]** n’est pas disponible.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
