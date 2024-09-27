---
title: "ACSD-54972 : Mise à jour de l’URL de catégorie canonique impossible"
description: Appliquez le correctif ACSD-54972 pour résoudre le problème Adobe Commerce en raison duquel l’URL de catégorie canonique n’est pas mise à jour après modification de l’URL de catégorie.
feature: Catalog Management, Products, Categories
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-54972 : l’URL de catégorie canonique n’est pas mise à jour après la modification de l’URL de catégorie

Le correctif ACSD-54972 corrige le problème en raison duquel l’URL de catégorie canonique n’est pas mise à jour après modification de l’URL de catégorie. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43 est installé. L’ID de correctif est ACSD-54972. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’URL de catégorie canonique n’est pas mise à jour après avoir modifié l’URL de catégorie.

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**.

   * Set *[!UICONTROL Use Canonical Link Meta Tag for Categories]*: *YES*

2. Créez une catégorie (par exemple, *Nom* : *Catégorie 01*, *Clé URL* : *catégorie-01*).
3. Mettez à jour la *clé URL* vers une valeur différente de la valeur d’origine tout en maintenant la case à cocher **[!UICONTROL Create Permanent Redirect for old URL]** cochée.
4. Nettoyez le cache.
5. Accédez au *[!UICONTROL Category Page]* sur le front-end.
6. Vérifiez la source de la page et recherchez la balise *canonical* .

<u>Résultats attendus</u> :

`<link rel="canonical" href="http://127.0.0.1/pub/category-01-new.html" />`

<u>Résultats réels</u> :

`<link rel="canonical" href="http://127.0.0.1/pub/category-01.html" />`

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
