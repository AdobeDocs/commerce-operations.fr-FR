---
title: 'ACSD-46213 : requête d’arborescence de catégorie limitée à 20 catégories'
description: 'Le correctif ACSD-46213 corrige le problème en raison duquel la requête d’arborescence de catégories est limitée à 20 catégories. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.19 est installé. L’ID du correctif est ACSD-46213. '
feature: Categories
role: Admin
exl-id: 2cd4b102-db52-424f-9a7f-d775cb2b2c49
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-46213 : requête d’arborescence de catégorie limitée à 20 catégories

Le correctif ACSD-46213 corrige le problème en raison duquel la requête d’arborescence de catégories est limitée à 20 catégories. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.19 est installé. L’ID du correctif est ACSD-46213.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.


## Problème

La requête d’arborescence de catégories est limitée à 20 catégories.

<u>Procédure à suivre </u> :

1. Créez une catégorie sous la catégorie racine .
1. Créez 24 sous-catégories sous la catégorie racine créée à l’étape 1.
1. Exécutez la requête GraphQL suivante :

   <pre>
    <code class="language-graphql">
    &lbrace;
      categoryList(filters: { parent_id: { in: ["3"] } }) &lbrace;
        name
        level
        path
        url_path
        children &lbrace;
          id
          level
          name
          path
          url_path
          url_key
          children &lbrace;
            uid
            level
            name
            path
            url_path
            url_key
          &rbrace;
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>

1. Vérifiez les résultats.

<u>Résultats attendus</u> :

Il affiche 24 catégories.

<u>Résultats réels</u> :

Il n&#39;affiche que 20 catégories.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
