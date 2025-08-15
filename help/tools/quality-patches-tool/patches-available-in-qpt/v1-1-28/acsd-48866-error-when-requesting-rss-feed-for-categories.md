---
title: 'ACSD-48866 : erreur lors de la demande d’un flux RSS pour les catégories'
description: Appliquez le correctif ACSD-48866 pour résoudre le problème d'Adobe Commerce où une erreur se produit lors de la demande d'un flux RSS pour des catégories.
feature: Admin Workspace, Categories
role: Admin
exl-id: f278a90f-f30c-401f-a544-713c89eb208a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# ACSD-48866 : erreur lors de la demande d’un flux RSS pour les catégories

Le correctif ACSD-48866 corrige le problème où une erreur se produit lors de la demande d&#39;un flux RSS pour les catégories. Ce correctif est disponible lorsque la version 1.1.28 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48866. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur se produit lors de la demande d’un flux RSS pour les catégories.

<u>Procédure à suivre </u> :

1. Activez le flux RSS dans **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Catalog]** > **[!UICONTROL RSS Feeds]** > **[!UICONTROL RSS Config]** > **[!UICONTROL Enable RSS]**.
1. Activez [!UICONTROL Top Level Category] dans **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Catalog]** > **[!UICONTROL RSS Feeds]** > **[!UICONTROL Catalog]** > **[!UICONTROL Top Level Category]**.
1. Parcourez la page de catégorie Flux RSS de storefront.
1. Vérifiez les fichiers journaux dans `var/log`.

<u>Résultats attendus</u> :

Aucune erreur dans le fichier journal.

<u>Résultats réels</u> :

L’erreur suivante s’affiche dans le fichier journal :

```
Text fields are not optimised for operations that require per-document field data like aggregations and sorting, so these operations are disabled by default. Please use a keyword field instead. Alternatively, set fielddata=true on [updated_at] in order to load field data by uninverting the inverted index.
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
