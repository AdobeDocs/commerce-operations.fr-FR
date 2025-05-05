---
title: 'ACSD-50621 : Les prix de niveau pour les différents sites web du catalogue partagé ne sont pas visibles.'
description: Appliquez le correctif ACSD-50621 pour résoudre le problème Adobe Commerce en raison duquel les prix de niveau des différents sites web du catalogue partagé ne sont pas visibles lors de leur modification dans un environnement multi-site.
feature: Catalog Management, Orders
role: Admin
exl-id: 2256dee7-e544-4723-9753-ba9cf7247880
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-50621 : Les prix de niveau pour les différents sites web du catalogue partagé ne sont pas visibles.

Le correctif ACSD-50621 corrige le problème en raison duquel les prix de niveau des différents sites web du catalogue partagé ne sont pas visibles lors de leur modification dans un environnement multi-site web. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.32 est installé. L’ID de correctif est ACSD-50621. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les prix de niveau pour différents sites web du catalogue partagé ne sont pas visibles lors de leur modification dans un environnement multisite.

<u>Étapes à reproduire</u> :

1. Définissez le **[!UICONTROL Catalog Price Scope]** sur **[!UICONTROL Website]**.
1. Créez un site web, un magasin et un storeview supplémentaires.
1. Créez un produit simple et affectez-le à tous les sites web.
1. Créez un catalogue partagé personnalisé.
1. Accédez à **[!UICONTROL Set Pricing and Structure]** pour le catalogue partagé personnalisé que vous avez créé.
1. À l’étape 1 : sélectionnez les produits pour le catalogue. Ajoutez le produit simple que vous avez créé.
1. À l’étape 2 : définissez des prix personnalisés et cliquez sur **[!UICONTROL Configure]**.
1. Définissez des prix différents pour différents sites web.
1. Sélectionnez **[!UICONTROL Done]** et cliquez sur **[!UICONTROL Generate Catalog]**, puis sur **[!UICONTROL Save]**.
1. Exécutez cron.
1. Accédez à **[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]** et vérifiez le prix du niveau.

<u>Résultats attendus</u> :

Tous les prix de niveau configurés précédemment pour différents sites web sont présents.

<u>Résultats réels</u> :

Les prix de niveau qui ont été configurés précédemment ne sont pas présents.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
