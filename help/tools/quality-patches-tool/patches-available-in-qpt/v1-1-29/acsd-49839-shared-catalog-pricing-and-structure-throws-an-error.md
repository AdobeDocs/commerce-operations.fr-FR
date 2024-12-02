---
title: 'ACSD-49839 : La tarification et la structure du catalogue partagées renvoie une erreur.'
description: Appliquez le correctif ACSD-49839 pour résoudre le problème Adobe Commerce en raison duquel la tarification et la structure du catalogue partagé renvoient une erreur dans l’administrateur lorsque les produits ont des guillemets simples ou doubles dans la SKU.
feature: Admin Workspace, Catalog Management, Categories
role: Admin
exl-id: b74e3926-16c8-4222-b642-ed1b7095dea4
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-49839 : La tarification et la structure du catalogue partagées renvoie une erreur.

Le correctif ACSD-49839 corrige le problème en raison duquel la tarification et la structure du catalogue partagé renvoyaient une erreur dans l’administrateur lorsque les produits avaient des guillemets simples ou doubles dans le SKU. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 est installé. L’ID de correctif est ACSD-49839. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La tarification et la structure du catalogue partagées renvoie une erreur à l’administrateur lorsque les produits comportent des guillemets simples ou doubles dans le SKU.

<u>Étapes à reproduire</u> :

1. Définissez certains SKU du produit avec un caractère spécial, c’est-à-dire des guillemets doubles tels que :
   *[Product&quot;12, Product&quot;14, Product&quot;15]*.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Add Shared Catalog]** (par exemple,*[Test du catalogue partagé]*).
1. Affectez tous les **[!UICONTROL Products and Categories]** > **[!UICONTROL Generate Catalog]** > **[!UICONTROL Save]**.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Test Shared Catalog]** > **[!UICONTROL Action]** > **[!UICONTROL Set Pricing and Structure]**.
1. Marquez *[!UICONTROL Root Catalog]* pour sélectionner toutes les catégories et tous les produits.
1. Observez les requêtes d’AJAX dans le panneau réseau.

<u>Résultats attendus</u> :

La structure et le prix du catalogue partagé ne génèrent pas d’erreur dans l’administrateur lorsque les produits comportent des guillemets simples ou doubles dans le SKU.

<u>Résultats réels</u> :

La structure et le prix du catalogue partagé affichent une erreur dans l’administrateur lorsque les produits ont des guillemets simples ou doubles dans le SKU.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
