---
title: '[!DNL ACSD-47280] : la désactivation du catalogue partagé donne des résultats de recherche de produit incorrects'
description: Appliquez le correctif  [!DNL ACSD-47280]  corriger l’affichage des résultats de recherche corrects lorsque la fonctionnalité de catalogue partagé est désactivée.
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# [!DNL ACSD-47280] : la désactivation du catalogue partagé donne des résultats de recherche de produit incorrects

Le correctif [!DNL ACSD-47280] corrige l’affichage des résultats de recherche corrects lorsque la fonction [!DNL shared catalog] est désactivée. Ce correctif est disponible lorsque la version 1.1.22 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. La [!DNL patch ID] est [!DNL ACSD-47280]. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez le [!DNL patch ID] comme mot-clé de recherche pour localiser le correctif.

## Problème

La désactivation de [!DNL shared catalog] donne des résultats de recherche de produit incorrects.

<u>Conditions préalables</u> :

* Modules [!DNL B2B] installés

<u>Procédure à suivre </u> :

1. Créez un second site web.
1. Attribuez un produit au deuxième site web.
1. Vérifiez les produits sur le **deuxième site web** à l’aide de [!DNL GraphQL] :

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
       total_count
       items {
         name
         sku
       }
       page_info {
         page_size
         current_page
       }
     }
   }
   ```

1. Activez **[!UICONTROL Shared Catalog]** sur les [!DNL scope] par défaut.
1. La demande de [!DNL GraphQL] n’affiche plus aucun produit pour le deuxième site web, ce qui est le résultat correct.
1. Accédez à la [!DNL scope] du deuxième site web et désactivez-**[!UICONTROL Company]**.

<u>Résultats attendus</u> :

La requête [!DNL GraphQL] doit toujours afficher les produits du deuxième site web.

<u>Résultats réels</u> :

La requête [!DNL GraphQL] n’affiche aucun produit pour le deuxième site web.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
