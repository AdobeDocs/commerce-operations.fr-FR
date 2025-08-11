---
title: 'ACSD-66118 : la mise à jour de [!UICONTROL Store View Code] efface [!UICONTROL Design Configuration] paramètres si [!UICONTROL Configuration Cache] n’est pas actualisé'
description: Appliquez le correctif ACSD-66118 pour résoudre le problème d’Adobe Commerce où la mise à jour du [!UICONTROL Store View Code] efface le [!UICONTROL Design Configuration] (thème et paramètres personnalisés) si le [!UICONTROL Configuration Cache] n’est pas correctement actualisé.
feature: Cache, Configuration, Themes
role: Admin, Developer
type: Troubleshooting
source-git-commit: ef4d6e420f304b0229c54c8ec7bd5500039bcb6b
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# ACSD-66118 : la mise à jour de **[!UICONTROL Store View Code]** efface **[!UICONTROL Design Configuration]** paramètres si **[!UICONTROL Configuration Cache]** n’est pas actualisé

Le correctif ACSD-66118 corrige le problème en raison duquel la mise à jour du **[!UICONTROL Store View Code]** efface **[!UICONTROL Design Configuration]** paramètres si le **[!UICONTROL Configuration Cache]** n’est pas actualisé. Ce correctif est disponible lorsque la version 1.1.67 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66118. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

**[!UICONTROL Design Configuration]** paramètres (tels que le thème et les paramètres personnalisés) sont effacés lors de la mise à jour du champ **[!UICONTROL Store View Code]**, si le **[!UICONTROL Configuration Cache]** n’est pas actualisé.

<u>Procédure à suivre </u> :

1. Connectez-vous au panneau **[!UICONTROL Admin]**.
2. Accédez à **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL All Stores]**.
3. Modifiez une vue de magasin dont le thème personnalisé est configuré dans **[!UICONTROL Content]** > *[!UICONTROL Design]* > **[!UICONTROL Configuration]**.
4. Modifiez le champ **[!UICONTROL Code]** (par exemple, de `storeview_1` en `storeview_main`).
5. Cliquez sur **[!UICONTROL Save Store View]** pour enregistrer les modifications.
6. Actualisez ou rouvrez la page **[!UICONTROL Content]** > *[!UICONTROL Design]* > **[!UICONTROL Configuration]** pour le **[!UICONTROL Store View]** mis à jour et aucun thème ne sera sélectionné.

<u>Résultats attendus</u> :

Après la mise à jour du **[!UICONTROL Store View Code]**, le **[!UICONTROL Design Configuration]** (y compris le thème et les paramètres personnalisés) doit rester intact.

<u>Résultats réels</u> :

Le **[!UICONTROL Design Configuration]** est effacé. Le thème revient aux valeurs par défaut et les paramètres personnalisés sont perdus.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
