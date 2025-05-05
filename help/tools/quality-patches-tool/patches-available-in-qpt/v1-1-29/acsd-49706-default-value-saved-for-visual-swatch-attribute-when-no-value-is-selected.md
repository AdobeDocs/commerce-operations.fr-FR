---
title: 'ACSD-49706 : valeur par défaut enregistrée pour l’attribut d’échantillon visuel lorsqu’aucune valeur n’est sélectionnée'
description: Appliquez le correctif ACSD-49706 pour résoudre le problème Adobe Commerce en raison duquel une valeur par défaut est enregistrée pour un attribut d’échantillon visuel lorsqu’aucune valeur n’est sélectionnée.
feature: Admin Workspace, Attributes
role: Admin
exl-id: fa3cb0a1-f898-4826-aa64-efeba1af58a8
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-49706 : valeur par défaut enregistrée pour l’attribut d’échantillon visuel lorsqu’aucune valeur n’est sélectionnée

Le correctif ACSD-49706 corrige le problème d’enregistrement d’une valeur par défaut pour un attribut d’échantillon visuel lorsqu’aucune valeur n’est sélectionnée. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 est installé. L’ID de correctif est ACSD-49706. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une valeur par défaut est enregistrée pour un attribut d’échantillon visuel lorsqu’aucune valeur n’est sélectionnée.

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Cliquez sur **[!UICONTROL Add New Attribute]**.
1. Renseignez les champs.

   * Par exemple, choisissez le type d’entrée *[!UICONTROL Visual Swatch]* et ajoutez plusieurs options (telles que *Rouge*, *Vert*). Veillez à choisir l’une de ces options par défaut.
   * Cliquez sur **[!UICONTROL Save Attribute]**.

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Modifiez le jeu d’attributs *[!UICONTROL Default]*.
1. Déplacez *[!UICONTROL New Attribute]* de la colonne *[!UICONTROL Unassigned Attributes]* vers le dossier *[!UICONTROL Product Details]* de la colonne du milieu.

   * Cliquez sur **[!UICONTROL Save]**.

1. Créez un produit à l’aide de l’ensemble d’attributs *[!UICONTROL Default]*.

   * Laissez le *[!UICONTROL New Attribute]* vide et enregistrez-le.

1. Une fois enregistrée, une valeur apparaît dans *[!UICONTROL New Attribute]*.

<u>Résultats attendus</u> :

Aucune valeur n’est affectée à *[!UICONTROL New Attribute]* par défaut.

<u>Résultats réels</u> :

Une valeur par défaut est appliquée à l’attribut lors de l’enregistrement d’un produit.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
