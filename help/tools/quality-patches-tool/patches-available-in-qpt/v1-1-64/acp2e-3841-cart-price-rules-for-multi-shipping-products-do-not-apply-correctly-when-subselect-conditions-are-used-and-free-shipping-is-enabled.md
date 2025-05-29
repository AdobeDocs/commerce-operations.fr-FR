---
title: 'ACP2E-3841 : les règles de prix de panier pour les produits à expédition multiple ne s’appliquent pas correctement lorsque des conditions de sous-sélection sont utilisées et que l’expédition gratuite est activée'
description: Appliquez le correctif ACP2E-3841 pour résoudre le problème d’Adobe Commerce en raison duquel les règles de prix de panier pour les produits à expédition multiple ne s’appliquent pas correctement lorsque des conditions de sous-sélection sont utilisées et que l’expédition gratuite est activée.
feature: Shopping Cart, Price Rules
role: Admin, Developer
source-git-commit: 1abb32109d5ca4a90cdd1d210d1fae6a728699fd
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---


# ACP2E-3841 : les règles de prix de panier pour les produits à expédition multiple ne s’appliquent pas correctement lorsque des conditions de sous-sélection sont utilisées et que l’expédition gratuite est activée

Le correctif ACP2E-3841 corrige le problème où les règles de prix de panier pour les produits à expédition multiple ne s’appliquent pas correctement lorsque des conditions de sous-sélection sont utilisées et que l’expédition gratuite est activée. Ce correctif est disponible lorsque la version 1.1.64 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACP2E-3841. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p9

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.7-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les règles de prix de panier pour les produits multi-expédition ne s’appliquent pas correctement lorsque des conditions de sous-sélection sont utilisées et que l’expédition gratuite est activée.

<u>Conditions préalables</u> :

**Paramètres:**
1. **[!UICONTROL Free Shipping]** = *Activé*
1. **[!UICONTROL Minimum Order Amount]** = *99999999*

**Catégories nécessaires :**
1. Test de catégorie 1
1. Test de catégorie 2

**Produits nécessaires :**
1. Test de produit 1 :
   1. Catégories : Test de catégorie 1
   1. Prix : 45 $
1. Test de produit 2 :
   1. Catégories : Test de catégorie 2
   1. Prix : 56,25 $ 

      **(Les prix doivent être identiques à ceux affichés ici pour garantir le bon fonctionnement du test.)**

**Règle de prix du panier :**

Connectez-vous en tant qu’administrateur et accédez à **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add new rule]**. Utilisez les valeurs suivantes :

**[!UICONTROL Rule Information]:**
1. **[!UICONTROL Rule Name]** : Tester l&#39;expédition gratuite
1. **[!UICONTROL Active]** : *Oui*
1. **[!UICONTROL Websites]** : *Site web principal*
1. **[!UICONTROL Customer Groups]** : *NON CONNECTÉ, Général, Vente en gros, Retailer*
1. **[!UICONTROL Coupon]** : *Aucun Coupon*
1. **[!UICONTROL Uses per Customer]** : *0*
1. **[!UICONTROL Priority]** : *1*

**[!UICONTROL Conditions]:**

**[!UICONTROL If ALL of these conditions are TRUE:]**


**[!UICONTROL If total amount (incl. tax) equals or greater than 100 for a subselection of items in cart matching ALL of these conditions:]**


**[!UICONTROL Category is]** 5 12 13 **

Actions :

**[!UICONTROL Percent of product price discount]** = *10*

<u>Procédure à suivre </u> :

1. Connectez-vous à la vitrine.
2. Ajouter un test de produit 1.
3. Ajouter deux quantités de Produit Test 2.
4. Consultez le panier.
5. Sélectionnez **[!UICONTROL Check Out with Multiple Addresses]**.

<u>Résultats attendus</u> :

Aucune erreur.

<u>Résultats réels</u> :

Erreur *500*

*Message : fonctionnalité obsolète : la conversion implicite de la virgule flottante 112.5 en int perd en précision dans /app/code/Magento/SalesRule/Model/Rule/Condition/Product/Subselect.php sur la ligne 214*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
