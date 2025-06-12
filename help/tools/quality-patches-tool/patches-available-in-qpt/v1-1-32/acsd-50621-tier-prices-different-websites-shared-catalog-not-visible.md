---
title: 'ACSD-50621 : les prix de niveau pour différents sites web dans le catalogue partagé ne sont pas visibles'
description: Appliquez le correctif ACSD-50621 pour résoudre le problème d’Adobe Commerce en raison duquel les prix de niveau pour différents sites web du catalogue partagé ne sont pas visibles lors de leur modification dans un environnement multi-sites web.
feature: Catalog Management, Orders
role: Admin
exl-id: 2256dee7-e544-4723-9753-ba9cf7247880
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-50621 : les prix de niveau pour différents sites web dans le catalogue partagé ne sont pas visibles

Le correctif ACSD-50621 corrige le problème en raison duquel les prix de niveau pour différents sites web dans le catalogue partagé ne sont pas visibles lors de leur modification dans un environnement multi-sites web. Ce correctif est disponible lorsque la version 1.1.32 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-50621. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les prix de niveau pour différents sites web dans le catalogue partagé ne sont pas visibles lors de leur modification dans un environnement multi-site.

<u>Procédure à suivre </u> :

1. Définissez la **[!UICONTROL Catalog Price Scope]** sur **[!UICONTROL Website]**.
1. Créez un site web, un magasin et une révision supplémentaires.
1. Créez un produit simple et affectez-le à tous les sites web.
1. Créez un catalogue partagé personnalisé.
1. Accédez à **[!UICONTROL Set Pricing and Structure]** pour le catalogue partagé personnalisé que vous avez créé.
1. À l’étape 1 : sélectionnez les produits à cataloguer. Ajoutez le produit simple que vous avez créé.
1. À l’étape 2 : définissez des prix personnalisés et cliquez sur **[!UICONTROL Configure]**.
1. Définissez des prix de niveau différents pour différents sites web.
1. Sélectionnez **[!UICONTROL Done]**, cliquez sur **[!UICONTROL Generate Catalog]**, puis sur **[!UICONTROL Save]**.
1. Exécutez cron.
1. Accédez à **[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]** et vérifiez le prix de niveau.

<u>Résultats attendus</u> :

Tous les prix de niveau configurés précédemment pour différents sites web sont présents.

<u>Résultats réels</u> :

Les prix de niveau précédemment configurés ne sont pas présents.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
