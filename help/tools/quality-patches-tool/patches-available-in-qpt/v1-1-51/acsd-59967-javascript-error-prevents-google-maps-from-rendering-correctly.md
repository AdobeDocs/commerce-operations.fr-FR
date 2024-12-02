---
title: 'ACSD-59967 : l’erreur JavaScript empêche [!DNL Google Maps] d’effectuer correctement le rendu.'
description: Appliquez le correctif ACSD-59967 pour résoudre le problème Adobe Commerce où l’erreur JavaScript empêche [!DNL Google Maps] d’effectuer correctement le rendu.
feature: Admin Workspace, Page Builder, CMS
role: Admin, Developer
exl-id: 2982857a-7adb-4163-be18-4d2caf0d645c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-59967 : l’erreur JavaScript empêche [!DNL Google Maps] d’effectuer correctement le rendu.

Le correctif ACSD-59967 corrige le problème où l’erreur JavaScript empêche [!DNL Google Maps] d’effectuer correctement le rendu. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51 est installé. L’ID de correctif est ACSD-59967. Veuillez noter que ce problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p3

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’erreur JavaScript empêche [!DNL Google Maps] d’effectuer correctement le rendu.

<u>Étapes à reproduire</u> :

1. Générez une clé [!DNL Google Maps] valide.
1. Configurez la clé d’API [!DNL Google Maps] sous **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Content Management]**.
1. Ajoutez le champ [!DNL Google API Key] à **[!UICONTROL Google Maps API Key]** et enregistrez la configuration.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** > **[!UICONTROL Create New Page]**.
1. Ajoutez un élément **[!UICONTROL Row]** et un élément **[!UICONTROL Maps]**.

<u>Résultats attendus</u> :

Aucune erreur JavaScript n’est présente dans la console et la carte s’affiche correctement sur *Storefront* et *Admin*.

<u>Résultats réels</u> :

Les erreurs JavaScript s’affichent dans la console et le mappage n’est pas correctement rendu.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
