---
title: 'ACSD-56193: [!DNL Fastly] Le cache n’est pas effacé pour la mise à jour de l’évaluation du contenu'
description: Appliquez le correctif ACSD-56193 pour résoudre le problème Adobe Commerce où le cache  [!DNL Fastly] n’est pas effacé pour la mise à jour de l’évaluation du contenu.
feature: Cache, GraphQL, Staging
role: Admin, Developer
exl-id: a702ce22-cc85-4f58-8766-637a1b93d405
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-56193 : le cache [!DNL Fastly] n’est pas effacé pour la mise à jour de l’évaluation du contenu.

Le correctif ACSD-56193 corrige le problème en raison duquel le cache [!DNL Fastly] n’est pas effacé pour la mise à jour de l’évaluation du contenu. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44 est installé. L’ID de correctif est ACSD-56193. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le cache [!DNL Fastly/Varnish] n’est pas effacé pour la mise à jour de l’évaluation du contenu.

<u>Étapes à reproduire</u> :

1. Installez et configurez le cache [!DNL Varnish].
1. Créez un bloc statique avec une mise à jour planifiée.
1. Créez une catégorie incorporant le bloc statique.
1. Récupérez le contenu de la catégorie à l’aide de la requête GraphQL suivante :

   ```GraphQL
      query GetCategories($id: String!) {
         categoryList(filters: { category_uid: { eq: $id } }) 
       {
           meta_title
           meta_keywords
           meta_description
           description
           path
           cms_block {
             content
             identifier
             title
             __typename
           }
           __typename
       }
     }
     {"id":"Mwo="}
   ```

1. Exécutez cette requête plusieurs fois et assurez-vous que la réponse est mise en cache dans le [!DNL Varnish].
1. Exécutez le cron pour appliquer la modification planifiée.
1. Réexécutez la requête GraphQL ci-dessus.
1. Créez un nouveau planning pour le même bloc statique.
1. Répétez les étapes numérotées 5-9.

<u>Résultats attendus</u> :

Le contenu mis à jour est renvoyé après l’exécution des mises à jour planifiées.

<u>Résultats réels</u> :

Le contenu obsolète est renvoyé après l’exécution des mises à jour planifiées.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
