---
title: 'ACSD-61553 : [!UICONTROL Cart Price Rule] est incorrectement calculé lorsque plusieurs remises avec des priorités différentes sont appliquées.'
description: Appliquez le correctif ACSD-61553 pour résoudre le problème Adobe Commerce où le [!UICONTROL Cart Price Rule] est mal calculé lorsque plusieurs remises avec des priorités différentes sont appliquées.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 0fb7a988-d391-49e5-a59d-62315a16132c
source-git-commit: b182fc0cd2f00f36138675277ac1de8a7179135a
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-61553 : [!UICONTROL Cart Price Rule] est incorrectement calculé lorsque plusieurs remises avec des priorités différentes sont appliquées.

Le correctif ACSD-61553 corrige le problème où le [!UICONTROL Cart Price Rule] est mal calculé lorsque plusieurs remises avec des priorités différentes sont appliquées. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.53 est installé. L’ID de correctif est ACSD-61553. Veuillez noter que ce problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p8

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!UICONTROL Cart Price Rule] est mal calculé lorsque plusieurs remises avec des priorités différentes sont appliquées.

<u>Étapes à reproduire</u> :

1. Créez un produit simple au prix de 9 000 $.
1. Créez un [!UICONTROL Cart Price Rule] : règle A avec une remise fixe de 700 $ sans conditions et sans ignorer les règles suivantes.
1. Créez un autre [!UICONTROL Cart Price Rule] : règle B avec une remise fixe de 1 000 $ sans conditions et sans ignorer les règles suivantes.
1. Ajoutez le produit avec la quantité 13 au panier.
1. Mettez à jour les règles avec l’un des scénarios suivants :

   Scénario 01

       Règle A
       Priorité : 1
       Remise De Qualité Maximale Appliquée À : 1
       
       Règle B
       Priorité : 0
       Remise De Qualité Maximale Appliquée À : 0
   
   Scénario 02

       Règle A
       Priorité : 0
       Remise De Qualité Maximale Appliquée À : 0
       
       Règle B
       Priorité : 1
       Remise De Qualité Maximale Appliquée À : 1
   
   Scénario 03

       Règle A
       Priorité : 0
       Remise De Qualité Maximale Appliquée À : 0
       
       Règle B
       Priorité : 0
       Remise De Qualité Maximale Appliquée À : 1
   
1. Cliquez sur le bouton **[!UICONTROL Update Shopping Cart]** pour recalculer les remises.

<u>Résultats attendus</u> :

Vous voyez la remise totale suivante pour différents scénarios :

    Scénario 01 : 13 700 $
    Scénario 02 : 10 100 $
    Scénario 03 : 10 100 $

<u>Résultats réels</u> :

Dans les trois scénarios, la remise totale est de 9 000 $.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
