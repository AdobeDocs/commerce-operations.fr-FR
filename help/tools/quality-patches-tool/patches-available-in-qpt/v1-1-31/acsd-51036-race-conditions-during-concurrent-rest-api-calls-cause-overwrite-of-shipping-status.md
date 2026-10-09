---
title: 'ACSD-51036 : les conditions de concurrence lors d’appels simultanés de l’API REST entraînent un remplacement du statut d’expédition'
description: Appliquez le correctif ACSD-51036 pour résoudre le problème d’Adobe Commerce où des conditions de concurrence existent lors d’appels simultanés de l’API REST, ce qui entraîne un remplacement du statut d’expédition dans la table des articles commandés.
feature: REST, Orders, Shipping/Delivery
role: Admin
exl-id: 6150d072-05fe-4010-b31b-8ccde9cab656
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%
---
# ACSD-51036 : les conditions de concurrence lors d’appels simultanés de l’API REST entraînent un remplacement du statut d’expédition dans la table des articles commandés

Le correctif ACSD-51036 corrige le problème où les conditions de concurrence lors d’appels simultanés de l’API REST entraînent un remplacement du statut d’expédition dans la table des articles commandés. Ce correctif est disponible lorsque la version 1.1.31 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-51036. Notez que le problème a été résolu dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les conditions de concurrence lors d’appels simultanés de l’API REST entraînent un remplacement du statut d’expédition dans la table des articles commandés.

<u>Procédure à suivre </u> :

1. Créez une commande comportant deux articles.
1. Élément de facture A.
1. Envoyez simultanément une demande de remboursement pour l’article A via l’API REST et une demande d’expédition pour l’article B.
1. Accédez à l’ordre dans **[!UICONTROL Admin Panel]**.

<u>Résultats attendus</u>

*[!UICONTROL Shipped 1]* statut doit être présent pour l’élément B dans le tableau ordonné *[!UICONTROL Items]*.

<u>Résultats réels</u>

*[!UICONTROL Shipped 1]* statut n’est pas présent pour l’élément B dans le tableau ordonné *[!UICONTROL Items]*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
