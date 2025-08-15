---
title: 'ACSD-56193: [!DNL Fastly] cache n’est pas effacé pour la mise à jour de l’évaluation du contenu'
description: Appliquez le correctif ACSD-56193 pour résoudre le problème d’Adobe Commerce où le cache n [!DNL Fastly] est pas effacé pour la mise à jour de l’évaluation du contenu.
feature: Cache, GraphQL, Staging
role: Admin, Developer
exl-id: a702ce22-cc85-4f58-8766-637a1b93d405
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-56193 : [!DNL Fastly] cache n’est pas effacé pour la mise à jour de l’évaluation du contenu

Le correctif ACSD-56193 corrige le problème où le cache [!DNL Fastly] n’est pas effacé pour la mise à jour de l’évaluation du contenu. Ce correctif est disponible lorsque la version 1.1.44 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-56193. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le cache [!DNL Fastly/Varnish] n’est pas effacé pour la mise à jour de l’évaluation du contenu

<u>Procédure à suivre </u> :

1. Installez et configurez le cache [!DNL Varnish].
1. Créez un bloc statique avec une mise à jour planifiée.
1. Créez une catégorie incorporant le bloc statique .
1. Récupérez le contenu de la catégorie à l’aide de la requête GraphQL ci-dessous :

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
1. Exécutez la commande cron pour appliquer la modification planifiée.
1. Exécutez à nouveau la requête GraphQL ci-dessus.
1. Créez un planning pour le même bloc statique.
1. Répétez les étapes numérotées 5 à 9.

<u>Résultats attendus</u> :

Le contenu mis à jour est renvoyé après l’exécution des mises à jour planifiées.

<u>Résultats réels</u> :

Le contenu obsolète est renvoyé après l’exécution des mises à jour planifiées.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
