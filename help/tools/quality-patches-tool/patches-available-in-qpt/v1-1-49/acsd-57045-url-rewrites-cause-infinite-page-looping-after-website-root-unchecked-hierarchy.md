---
title: 'ACSD-57045 : les réécritures d’URL entraînent un bouclage de page infini après [!UICONTROL Website Root] décoché de [!UICONTROL Hierarchy]'
description: Appliquez le correctif ACSD-57045 pour résoudre le problème d’Adobe Commerce où les réécritures d’URL provoquent un bouclage de page infini après la désactivation de la [!UICONTROL Website Root] de [!UICONTROL Hierarchy].
feature: CMS
role: Admin, Developer
exl-id: 7beaee40-a392-4644-917e-c507e79bddcc
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# ACSD-57045 : les réécritures d’URL entraînent un bouclage de page infini après [!UICONTROL Website Root] décoché de [!UICONTROL Hierarchy]

Le correctif ACSD-57045 corrige le problème où les réécritures d’URL provoquent un bouclage de page infini après que **[!UICONTROL Website Root]** n’est plus coché dans **[!UICONTROL Hierarchy]**. Ce correctif est disponible lorsque la version 1.1.49 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-57045. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les réécritures d’URL entraînent un bouclage de page infini après la désélection de **[!UICONTROL Website Root]** dans **[!UICONTROL Hierarchy]**.

<u>Procédure à suivre </u> :

1. Créez une page CMS nommée *Test-Parent*.
1. Créez une page nommée *Test-Child*, puis, dans la section **[!UICONTROL Hierarchy]**, sélectionnez **[!UICONTROL Website Root]** > **[!UICONTROL Parent]** et enregistrez.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**.
1. Notez qu’il existe deux nouvelles réécritures :
   * Chemin d’accès de la requête vers *Test-Parent* qui pointe vers *cms/page/view/page_id/ID_NUMBER_FOR_PAGE*
   * Chemin d’accès de la requête à *Test-Child* qui pointe vers *cms/page/view/page_id/ID_NUMBER_FOR_PAGE*
1. Rendez-vous sur le storefront et ajoutez *test-child* à l’URL. Vous devriez voir la page enfant.
1. Faites de même, mais ajoutez *test-parent/test-child/* à l’URL et affichez la même page.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]** et sélectionnez **[!UICONTROL Add URL Rewrite]**. Choisissez les paramètres suivants :
   * Type : *Personnalisé*
   * Chemin d’accès de la requête : *test-parent/test-child*
   * Chemin cible : *test-child*
   * Type de redirection : *Permanent (301)*
1. Rendez-vous sur le chemin *test-parent/test-child* et vous devriez être redirigé vers *test-child*.
1. Modifiez la page Enfant (**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** > Choisir un enfant et sélectionner **[!UICONTROL Edit]**).
1. Dans la section **[!UICONTROL Hierarchy]** , gardez *Test-Parent* sélectionné, mais désélectionnez **[!UICONTROL Website Root]** et enregistrez.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]** et notez que la redirection d’origine *test-child* vers *cms/page/view/page_id* est manquante et à ce stade, elle est remplacée par un chemin qui pointe *test-child* vers *test-parent/test-child*.
1. Rendez-vous sur le storefront et essayez de consulter la page *Test-Child*.

<u>Résultats attendus</u> :

La page *Test-Child* s’ouvre.

<u>Résultats réels</u> :

La page *Test-Child* n’est pas ouverte. Le navigateur tente d’ouvrir la page *test-parent/test-child* en boucle infinie.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
