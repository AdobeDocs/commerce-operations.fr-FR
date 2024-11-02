---
title: '« MDVA-44147 : la demande GraphQL ne renvoie pas les listes de réquisitions »'
description: Le correctif MDVA-44147 résout le problème où la requête GraphQL ne renvoie pas les listes de demande. Ce correctif est disponible lorsque [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 est installé. L’ID de correctif est MDVA-44147. Notez que ce problème devrait être résolu dans Adobe Commerce 2.4.5.
feature: B2B, GraphQL
role: Admin
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-44147 : la requête GraphQL ne renvoie pas les listes de demande

Le correctif MDVA-44147 résout le problème où la requête GraphQL ne renvoie pas les listes de demande. Ce correctif est disponible lorsque QPT [(Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 est installé. L’ID de correctif est MDVA-44147. Notez que ce problème devrait être résolu dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour Adobe version de Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions Adobe Commerce :**

* Adobe Commerce (toutes méthodes de déploiement) 2.4.2 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil Correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le `magento/quality-patches` package vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool]page](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) : Search des correctifs. Utilisez l’identifiant du correctif comme mot-clé de recherche pour localiser le correctif.

## Émettre

La requête GraphQL ne renvoie pas les listes de demandes.

<u>Étapes à reproduire</u> :

1. Accédez à **Store** > **Settings** > **Configuration** > **General** > **B2B Features** et activez la liste des demandes.
1. Connectez-vous en tant que client et ajoutez un produit à la [liste](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/requisition-lists/requisition-lists) des demandes.
1. Créez un [jeton](https://developer.adobe.com/commerce/webapi/graphql/mutations/generate-customer-token.html) client.

   <pre>
    <code class="language-graphql">
    mutation {
      generateCustomerToken(
        email: "test@gmail.com"
        password: "xxxxxxxx"
        ) {
          token
        }
      }
      </code>
      </pre>

1. Utilisez la requête suivante pour récupérer toutes les listes de demandes du client. Utilisez l’en-tête **Authorization** avec la valeur `Bearer <customer_token>`. Pour plus d’informations, reportez-vous à l’article [Requête](https://developer.adobe.com/commerce/webapi/graphql/queries/customer.html) client de notre documentation destinée aux développeurs.

   Demander:

   <pre>
    <code class="language-graphql">
    query {
      customer {
        requisition_lists(
          pageSize: 20
          ) {
            items {
              uid
              name
              description
              items(pageSize: 20) {
                items {
                  uid
                  product {
                    uid
                    name
                    sku
                    __typename
                  }
                  quantity
                }
                total_pages
              }
            }
            total_count
          }
        }
      }
      </code>
      </pre>

   Réponse:

   <pre>
    <code class="language-graphql">
    {
      "data": {
        "customer": {
          "requisition_lists": {
            "items": [
            {
              "uid": "MQ==",
              "name": "Name",
              "description": "Description",
              "items": {
                "items": [
                {
                  "uid": "MQ==",
                  "product": {
                    "uid": "MQ==",
                    "name": "Simple 01",
                    "sku": "s00001",
                    "__typename": "SimpleProduct"
                    },
                    "quantity": 1
                  }
                  ],
                  "total_pages": 1
                }
              }
              ],
              "total_count": 1
            }
          }
        }
      }
      </code>
      </pre>

1. Copiez l’UID de n’importe quel élément de la liste renvoyée (MQ==) et utilisez la requête suivante pour obtenir la liste filtrée par l’UID.

   <pre>
    <code class="language-graphql">
    query {
      customer {
        requisition_lists(
          pageSize: 20,
          filter: {
            uids: {
              eq: "MQ=="
            }
          }
          ) {
            items {
              uid
              name
              description
              items(pageSize: 20) {
                items {
                  uid
                  product {
                    uid
                    name
                    sku
                    __typename
                  }
                  quantity
                }
                total_pages
              }
            }
            total_count
          }
        }
      }
      </code>
      </pre>

<u>Résultats</u> attendus :

Un résultat est renvoyé.

<u>Résultats</u> réels :

Aucun résultat n’est renvoyé.

## Appliquez le patch

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source local : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > appliquez des](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) correctifs dans le guide Commerce on Cloud Infrastructure.

## Lectures connexes

Pour en savoir plus sur l’outil Correctifs de qualité, reportez-vous à :

* [Publication de l’outil de correctifs de qualité : un nouvel outil pour le libre-service des](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) correctifs de qualité dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Correctifs de qualité dans le [!DNL Quality Patches Tool] guide.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool]: Search pour les](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) correctifs dans le [!DNL Quality Patches Tool] guide.
