---
title: 'MDVA-40601 : impossible de récupérer les données sur la catégorie modifiée par une mise à jour planifiée via GraphQL'
description: Le correctif de qualité MDVA-40601 Adobe Commerce corrige le problème d’erreur des utilisateurs lorsqu’ils obtiennent des informations sur la catégorie modifiée par une mise à jour planifiée via GraphQL. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.3 est installé. L’ID de correctif est MDVA-40601. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
feature: Categories, GraphQL
role: Admin
exl-id: c50e9f77-66eb-4c4c-b0b5-b77db84a4a0b
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-40601 : impossible de récupérer les données sur la catégorie modifiée par une mise à jour planifiée via GraphQL

Le correctif de qualité MDVA-40601 Adobe Commerce corrige le problème d’erreur des utilisateurs lorsqu’ils obtiennent des informations sur la catégorie modifiée par une mise à jour planifiée via GraphQL. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.3 est installé. L’ID de correctif est MDVA-40601. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.3 et 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.1 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs reçoivent une erreur lorsqu’ils tentent de récupérer des informations sur la catégorie modifiée par une mise à jour planifiée via GraphQL.

<u>Étapes à reproduire</u> :

1. Configurez une structure de catégorie avec une sous-catégorie comme indiqué ci-dessous :

   <pre>
   <code class="language-graphql">
   - Root
    - Some category
         - Some child category

   </code>
   </pre>

1. Exécutez la requête GraphQL avec l’ID de catégorie 49.

   <pre>
    <code class="language-graphql">
    query &lbrace;
     category(id: 49) &lbrace;
      name
      children &lbrace;
        name
       &rbrace;
     &rbrace;
   &rbrace;
   </code>
   </pre>

   Résultat :

   <pre>
    <code class="language-graphql">
    &lbrace;
      "data": &lbrace;
        "category": &lbrace;
          "name": "Some category",
          "children": &lbrack;
            &lbrace;
              "name": "Some child category"
            &rbrace;
          &rbrack;
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>

1. Créez une mise à jour de planning pour &quot;Une catégorie&quot; avec un nom de catégorie différent.
1. Attendez que la mise à jour du planning soit activée.
1. Exécutez la même requête que celle ci-dessus.

<u>Résultats attendus</u> :

Vous recevez le même résultat, mais avec le nom de catégorie mis à jour.

<u>Résultats réels</u> :

Vous obtenez l’erreur suivante :

<pre>
<code class="language-graphql">
&lbrace;
  "errors": &lbrack;
    &lbrace;
      "debugMessage": "uasort() expects parameter 1 to be array, string given",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 2,
          "column": 3
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "category"
      &rbrack;
    &rbrace;
  &rbrack;,
  "data": &lbrace;
    "category": null
  &rbrace;
&rbrace;
</code>
</pre>

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

&#x200B;* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
&#x200B;* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur les correctifs de qualité pour Adobe Commerce, consultez :

&#x200B;* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
&#x200B;* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) .
