---
title: 'MDVA-44147: [!DNL GraphQL] request ne renvoie pas [!UICONTROL Requisition Lists]'
description: Le correctif MDVA-44147 corrige le problème où  [!DNL GraphQL]  requête ne renvoie pas de [!UICONTROL Requisition Lists]. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 est installé. L’ID du correctif est MDVA-44147. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: B2B, GraphQL
role: Admin
exl-id: 534c4e45-6521-45c0-ae4e-c60b754f432f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# MDVA-44147 : [!DNL GraphQL] demande ne renvoie pas [!UICONTROL Requisition Lists]

Le correctif MDVA-44147 corrige le problème en raison duquel [!DNL GraphQL] requête ne renvoie pas de [!UICONTROL Requisition Lists]. Ce correctif est disponible lorsque la version 1.1.14 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est MDVA-44147. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!DNL GraphQL] requête ne renvoie pas de [!UICONTROL Requisition Lists].

<u>Procédure à suivre </u> :

1. Accédez à **Store** > **Settings** > **Configuration** > **General** > **B2B Features** et activez **[!UICONTROL Requisition List]**.
1. Connectez-vous en tant que client et ajoutez un produit au [[!UICONTROL Requisition List]](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/requisition-lists/requisition-lists).
1. Créez un [[!UICONTROL Customer Token]](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/generate-token/).

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      generateCustomerToken(
        email: "test@gmail.com"
        password: "xxxxxxxx"
        ) &lbrace;
          token
        &rbrace;
      &rbrace;
      </code>
      </pre>

1. Utilisez la requête suivante pour récupérer toutes les [!UICONTROL Requisition Lists] du client. Utilisez l’en-tête **Authorization** avec la valeur `Bearer <customer_token>`. Pour plus d’informations, reportez-vous à l’article [Requête client](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/customer/) dans la documentation destinée aux développeurs.

   Requête :

   <pre>
    <code class="language-graphql">
    query &lbrace;
      customer &lbrace;
        requisition_lists(
          pageSize: 20
          ) &lbrace;
            items &lbrace;
              uid
              name
              description
              items(pageSize: 20) &lbrace;
                items &lbrace;
                  uid
                  product &lbrace;
                    uid
                    name
                    sku
                    __typename
                  &rbrace;
                  quantity
                &rbrace;
                total_pages
              &rbrace;
            &rbrace;
            total_count
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

   Réponse :

   <pre>
    <code class="language-graphql">
    &lbrace;
      "data": &lbrace;
        "customer": &lbrace;
          "requisition_lists": &lbrace;
            "items": &lbrack;
            &lbrace;
              "uid": "MQ==",
              "name": "Name",
              "description": "Description",
              "items": &lbrace;
                "items": &lbrack;
                &lbrace;
                  "uid": "MQ==",
                  "product": &lbrace;
                    "uid": "MQ==",
                    "name": "Simple 01",
                    "sku": "s00001",
                    "__typename": "SimpleProduct"
                    &rbrace;,
                    "quantity": 1
                  &rbrace;
                  &rbrack;,
                  "total_pages": 1
                &rbrace;
              &rbrace;
              &rbrack;,
              "total_count": 1
            &rbrace;
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

1. Copiez l’UID de n’importe quel élément de la liste renvoyée (MQ==) et utilisez la requête suivante pour obtenir la liste filtrée par UID.

   <pre>
    <code class="language-graphql">
    query &lbrace;
      customer &lbrace;
        requisition_lists(
          pageSize: 20,
          filter: &lbrace;
            uids: &lbrace;
              eq: "MQ=="
            &rbrace;
          &rbrace;
          ) &lbrace;
            items &lbrace;
              uid
              name
              description
              items(pageSize: 20) &lbrace;
                items &lbrace;
                  uid
                  product &lbrace;
                    uid
                    name
                    sku
                    __typename
                  &rbrace;
                  quantity
                &rbrace;
                total_pages
              &rbrace;
            &rbrace;
            total_count
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

<u>Résultats attendus</u> :

Un résultat est renvoyé.

<u>Résultats réels</u> :

Aucun résultat n’est renvoyé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur le [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide du  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans la [!DNL QPT], reportez-vous à la section [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
