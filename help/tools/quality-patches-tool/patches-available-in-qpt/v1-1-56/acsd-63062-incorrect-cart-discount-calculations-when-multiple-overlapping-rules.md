---
title: 'ACSD-63062 : calculs de remise de panier incorrects avec plusieurs règles qui se chevauchent'
description: Appliquez le correctif ACSD-63062 pour résoudre le problème d’Adobe Commerce en raison duquel des calculs de remise de panier incorrects se produisent lorsque plusieurs règles se chevauchent.
feature: Price Rules
role: Admin, Developer
exl-id: c4a93063-b640-444e-ba0e-552dd8d1895b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-63062 : calculs de remise de panier incorrects avec plusieurs règles qui se chevauchent

Le correctif ACSD-63062 corrige le problème où des calculs de remise de panier incorrects se produisent lorsque plusieurs règles qui se chevauchent sont appliquées. Ce correctif est disponible lorsque la version 1.1.56 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63062. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Des calculs de remise de panier incorrects se produisent lorsque plusieurs règles qui se chevauchent sont appliquées.

<u>Procédure à suivre </u> :

1. Installez une nouvelle instance avec des exemples de données.
1. Créez trois produits simples :

   * simple1: 1 080 $
   * simple2: 260 $
   * simple3: $280

1. Créez quatre *[!UICONTROL Cart Price Rules]* comme suit :

   * Règle 1 :

      * *[!UICONTROL Priority]* : 100
      * *[!UICONTROL Conditions]* : utilisez le produit simple2 (280 $) si la quantité totale est égale ou supérieure à 3
      * Onglet *[!UICONTROL Actions]* : SKU simple2
      * *[!UICONTROL Fixed Amount Discount]*: 80 $

   * Règle 2 :

      * *[!UICONTROL Priority]* : 200
      * Onglet *[!UICONTROL Actions]* : SKU simple2
      * *[!UICONTROL Percentage of Product Price Discount]* : 20 %

   * Règle 3 :

      * *[!UICONTROL Priority]* : 300
      * *[!UICONTROL Conditions]* onglet : le sous-total est égal ou supérieur à 1 000 $
      * *[!UICONTROL Fixed Amount Discount]* pour l&#39;ensemble du panier : 100 $

   * Règle 4 :

      * *[!UICONTROL Priority]* : 400
      * *[!UICONTROL Conditions]* : utilisez le produit simple1 (1 080 $) si la quantité totale est égale ou supérieure à 2
      * Onglet *[!UICONTROL Actions]* : SKU simple1
      * *[!UICONTROL Fixed Amount Discount]* pour l&#39;ensemble du panier : 960 $

1. Accédez à la vitrine et ajoutez au panier les produits suivants avec une quantité donnée :

   * simple1 = 2
   * simple2 = 1
   * simple3 = 3

1. Vérifiez le panier.

<u>Résultats attendus</u> :

La remise appliquée est de 1 352 $.

<u>Résultats réels</u> :

La remise appliquée est de 1 525,33 $.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
