---
title: 'ACSD-55334 : libellés non traduits par le biais des dictionnaires de traduction dans la réponse GraphQL'
description: Appliquez le correctif ACSD-55334 pour résoudre le problème d’Adobe Commerce en raison duquel les libellés ne sont pas traduits par le biais de dictionnaires de traduction dans la réponse de GraphQL.
feature: Categories, GraphQL
role: Admin, Developer
exl-id: c22e5007-c661-49d4-90b7-dcee9b97c823
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# ACSD-55334 : libellés non traduits par le biais des dictionnaires de traduction dans la réponse GraphQL

Le correctif ASCD-55334 corrige le problème où les libellés ne sont pas traduits par le biais de dictionnaires de traduction dans la réponse de GraphQL. Ce correctif est disponible lorsque la version 1.1.43 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ASCD-55334. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les libellés ne sont pas traduits dans les dictionnaires de traduction dans la réponse de GraphQL.

<u>Procédure à suivre </u> :

1. Installez un module linguistique.
1. Envoyer une requête GraphQL telle que :

   ```GrapQL
   query {
       products(filter: {}, pageSize: 25, sort: {}) {
           aggregations {
               label
           }
           total_count
       }
   }
   ```

1. Vérifiez la réponse.

<u>Résultats attendus</u> :

Le libellé *[!UICONTROL Category]* est traduit.

<u>Résultats réels</u> :

Le libellé *[!UICONTROL Category]* n&#39;est pas traduit.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
