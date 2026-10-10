---
title: 'ACSD-47336 : erreur [!UICONTROL Something went wrong] lors de l’ignorance des notifications dans Adobe Commerce Admin'
description: Appliquez le correctif ACSD-47336 pour résoudre le problème d’Adobe Commerce où l’utilisateur voit [!UICONTROL Something went wrong] erreur lors de l’abandon des notifications dans l’administrateur [!DNL Commerce].
feature: Admin Workspace
role: Admin
exl-id: da0c0119-6720-493f-a278-d573ed898a63
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%
---
# ACSD-47336 : erreur _[!UICONTROL Something went wrong]_&#x200B;lors de l’ignorance des notifications dans Adobe Commerce Admin

Le correctif ACSD-47336 corrige le problème en raison duquel l’utilisateur voit l’erreur _[!UICONTROL Something went wrong]_&#x200B;lors de l’ignorance des notifications dans l’administrateur [!DNL Commerce]. Ce correctif est disponible lorsque la version 1.1.24 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-47336. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) : 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) : 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur voit _[!UICONTROL Something went wrong]_&#x200B;erreur lors de l’ignorance des notifications dans l’administration [!DNL Commerce].

<u>Procédure à suivre </u> :

1. Effectuer une opération en bloc (par exemple, mettre à jour en bloc les attributs de produit à partir de la grille de produits).
1. Terminez l’opération (par exemple, exécutez `bin/magento queue:consumer:start product_action_attribute.update`).
1. Actualisez la page [!DNL Commerce] Admin, développez la section Notification de l’administrateur et cliquez sur le lien **[!UICONTROL Dismiss All Completed Tasks]**.

<u>Résultats attendus</u> :

L’erreur _[!UICONTROL Something went wrong]_&#x200B;ne doit pas s’afficher lors de l’effacement des tâches terminées.

<u>Résultats réels</u> :

L’erreur _[!UICONTROL Something went wrong]_&#x200B;s’affiche.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
