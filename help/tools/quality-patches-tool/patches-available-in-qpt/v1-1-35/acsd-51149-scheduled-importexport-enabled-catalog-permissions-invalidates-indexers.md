---
title: 'ACSD-51149 : Le [!UICONTROL ImportExport] planifié avec activé [!UICONTROL Catalog Permissions] invalide les indexeurs.'
description: Appliquez le correctif ACSD-51149 pour résoudre le problème de performances Adobe Commerce où le [!UICONTROL ImportExport] planifié avec activé [!UICONTROL Catalog Permissions] invalide les indexeurs.
feature: Cache, Data Import/Export
role: Admin
exl-id: eafc69ab-ec81-4192-85f8-a235f0a131a9
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-51149 : Le [!UICONTROL ImportExport] planifié avec activé [!UICONTROL Catalog Permissions] invalide les indexeurs.

Le correctif ACSD-51149 corrige le problème où le [!UICONTROL ImportExport] planifié avec activé [!UICONTROL Catalog Permissions] invalide les indexeurs. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.35 est installé. L’ID de correctif est ACSD-51149. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!UICONTROL ImportExport] planifié avec activé [!UICONTROL Catalog Permissions] invalide les indexeurs.

<u>Étapes à reproduire</u> :

1. Activez *[!UICONTROL Catalog Permissions]*.
1. Définissez tous les indexeurs sur *[!UICONTROL Update by Schedule]*.
1. Créez un produit simple.
1. Exportez ce produit via **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**.
1. Téléchargez le fichier CSV exporté et placez-le dans `<AC root folder>/var/import`.
1. Créez une importation de produit planifiée avec le fichier CSV téléchargé.
1. Exécutez la réindexation complète.
1. Vérifiez l’état des indexeurs. Tous les indexeurs doivent être à l’état *[!UICONTROL Ready]*.
1. Exécutez l’importation planifiée créée à partir de la grille.
1. Vérifiez l’état des indexeurs.

<u>Résultats attendus</u> :

Tous les indexeurs sont à l’état *[!UICONTROL Ready]*.

<u>Résultats réels</u> :

Certains des indexeurs sont à l’état *[!UICONTROL Reindex Required]*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
