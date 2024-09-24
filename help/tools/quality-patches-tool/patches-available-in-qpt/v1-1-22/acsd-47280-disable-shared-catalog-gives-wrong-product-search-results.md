---
title: '''[!DNL ACSD-47280] : désactiver le catalogue partagé donne des résultats de recherche de produits incorrects.'
description: Appliquez le correctif  [!DNL ACSD-47280] pour corriger l’affichage des résultats de recherche corrects lorsque la fonctionnalité de catalogue partagé est désactivée.
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280] : la désactivation du catalogue partagé donne de mauvais résultats de recherche de produits

Le correctif [!DNL ACSD-47280] corrige l’affichage des résultats de recherche corrects lorsque la fonction [!DNL shared catalog] est désactivée. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.22 est installé. [!DNL patch ID] est [!DNL ACSD-47280]. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez [!DNL patch ID] comme mot-clé de recherche pour localiser le correctif.

## Problème

La désactivation de [!DNL shared catalog] donne des résultats de recherche de produits incorrects.

<u>Conditions préalables</u> :

* [!DNL B2B] modules installés

<u>Étapes à reproduire</u> :

1. Créez un second site web.
1. Affectez un produit au deuxième site web.
1. Vérifiez les produits sur le **second site web** en utilisant [!DNL GraphQL] :

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

1. Activez **[!UICONTROL Shared Catalog]** sur la valeur par défaut [!DNL scope].
1. La requête [!DNL GraphQL] n’affiche plus aucun produit pour le deuxième site web, ce qui est le résultat correct.
1. Accédez au [!DNL scope] du deuxième site web et désactivez **[!UICONTROL Company]**.

<u>Résultats attendus</u> :

La requête [!DNL GraphQL] doit toujours afficher les produits pour le deuxième site web.

<u>Résultats réels</u> :

La requête [!DNL GraphQL] n’affiche aucun produit pour le deuxième site web.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
