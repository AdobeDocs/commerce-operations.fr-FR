---
title: 'ACSD-51036 : les conditions de concurrence lors d’appels simultanés de l’API REST entraînent un remplacement du statut d’expédition'
description: Appliquez le correctif ACSD-51036 pour résoudre le problème d’Adobe Commerce où des conditions de concurrence existent lors d’appels simultanés de l’API REST, ce qui entraîne un remplacement du statut d’expédition dans la table des articles commandés.
feature: REST, Orders, Shipping/Delivery
role: Admin
exl-id: 6150d072-05fe-4010-b31b-8ccde9cab656
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '394'
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
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

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
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
