---
title: 'ACSD-63062 : calculs de remise de panier incorrects avec plusieurs règles se chevauchant'
description: Appliquez le correctif ACSD-63062 pour résoudre le problème Adobe Commerce en raison duquel des calculs d’escompte de panier incorrects se produisent lorsque plusieurs règles se chevauchent.
feature: Price Rules
role: Admin, Developer
source-git-commit: 06fbdf730c670065e3105c62ae9604307b296a45
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-63062 : calculs de remise de panier incorrects avec plusieurs règles se chevauchant

Le correctif ACSD-63062 corrige le problème en raison duquel des calculs d’escompte de panier incorrects surviennent lorsque plusieurs règles se chevauchent. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 est installé. L’ID de correctif est ACSD-63062. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Des calculs d’escompte de panier incorrects se produisent lorsque plusieurs règles se chevauchent.

<u>Étapes à reproduire</u> :

1. Installez une nouvelle instance avec des exemples de données.
1. Créez trois produits simples :

   * simple1 : 1 080 $
   * simple2 : 260 $
   * simple3 : 280 $

1. Créez quatre *[!UICONTROL Cart Price Rules]* comme suit :

   * Règle 1 :

      * *[!UICONTROL Priority]* : 100
      * Onglet *[!UICONTROL Conditions]* : utilisez un produit simple2 (280 $) si la quantité totale est égale ou supérieure à 3
      * Onglet *[!UICONTROL Actions]* : le SKU est simple2
      * *[!UICONTROL Fixed Amount Discount]* : 80 $

   * Règle 2 :

      * *[!UICONTROL Priority]* : 200
      * Onglet *[!UICONTROL Actions]* : le SKU est simple2
      * *[!UICONTROL Percentage of Product Price Discount]* : 20 %

   * Règle 3 :

      * *[!UICONTROL Priority]* : 300
      * Onglet *[!UICONTROL Conditions]* : le sous-total est égal ou supérieur à 1 000 $
      * *[!UICONTROL Fixed Amount Discount]* pour l’ensemble du panier : 100 $

   * Règle 4 :

      * *[!UICONTROL Priority]* : 400
      * Onglet *[!UICONTROL Conditions]* : utilisez un produit simple 1 (1 080 $) si la quantité totale est égale ou supérieure à 2
      * Onglet *[!UICONTROL Actions]* : le SKU est simple1
      * *[!UICONTROL Fixed Amount Discount]* pour l’ensemble du panier : 960 $

1. Positionnez-vous sur le storefront et ajoutez les produits suivants avec une quantité donnée au panier :

   * simple1 = 2
   * simple2 = 1
   * simple3 = 3

1. Vérifiez le panier.

<u>Résultats attendus</u> :

La remise appliquée est de 1 352 $.

<u>Résultats réels</u> :

La remise appliquée est de 1525,33 $.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
