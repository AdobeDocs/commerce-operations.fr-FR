---
title: 'ACSD-61553 : [!UICONTROL Cart Price Rule] n’est pas correctement calculé lorsque plusieurs remises avec des priorités différentes sont appliquées'
description: Appliquez le correctif ACSD-61553 pour résoudre le problème d’Adobe Commerce où le [!UICONTROL Cart Price Rule] est incorrectement calculé lorsque plusieurs remises avec des priorités différentes sont appliquées.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 0fb7a988-d391-49e5-a59d-62315a16132c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%
---
# ACSD-61553 : [!UICONTROL Cart Price Rule] n’est pas correctement calculé lorsque plusieurs remises avec des priorités différentes sont appliquées

Le correctif ACSD-61553 corrige le problème où le [!UICONTROL Cart Price Rule] est incorrectement calculé lorsque plusieurs remises avec des priorités différentes sont appliquées. Ce correctif est disponible lorsque la version 1.1.53 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-61553. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p8

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!UICONTROL Cart Price Rule] n’est pas correctement calculé lorsque plusieurs remises avec des priorités différentes sont appliquées.

<u>Procédure à suivre </u> :

1. Créez un produit simple au prix de 9 000 $.
1. Créez une [!UICONTROL Cart Price Rule] : règle A avec une remise fixe de 700 $ sans aucune condition et sans ignorer les règles suivantes.
1. Créez une autre [!UICONTROL Cart Price Rule] : Règle B avec une remise fixe de 1 000 $ sans aucune condition et sans ignorer les règles suivantes.
1. Ajoutez le produit avec la quantité 13 au panier.
1. Mettez à jour les règles avec l’un des scénarios suivants :

   Scénario 01

       Règle A
     Priorité : 1
     Escompte Qté maximum appliqué à : 1
     
     Règle B
     Priorité : 0
     Escompte Qté maximum appliqué à : 0
   
   Scénario 02

       Règle A
     Priorité : 0
     Escompte Qté maximum appliqué à : 0
     
     Règle B
     Priorité : 1
     Escompte Qté maximum appliqué à : 1
   
   Scénario 03

       Règle A
     Priorité : 0
     Escompte Qté maximum appliqué à : 0
     
     Règle B
     Priorité : 0
     Escompte Qté maximum appliqué à : 1
   
1. Cliquez sur le bouton **[!UICONTROL Update Shopping Cart]** pour recalculer les remises.

<u>Résultats attendus</u> :

La remise totale suivante s’affiche pour différents scénarios :

    Scénario 01: 13 700
    Scénario 02: 10 100
    Scénario 03: 10 100 $

<u>Résultats réels</u> :

Dans les trois scénarios, la remise totale est de 9 000 $.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
