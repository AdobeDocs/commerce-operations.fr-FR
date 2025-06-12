---
title: 'ACSD-47292 : les produits groupés en rupture de stock ne sont pas disponibles dans la réponse GraphQL'
description: Appliquez le correctif ACSD-47292 pour résoudre le problème d’Adobe Commerce en raison duquel les produits en rupture de stock ne sont pas disponibles dans la réponse de GraphQL, même si l’option « Afficher les produits en rupture de stock » est définie sur Oui.
feature: Admin Workspace, Categories, GraphQL, Orders, Products
role: Admin
exl-id: 3b8114a3-cc45-4d65-af74-cb3e905d7f75
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-47292 : les produits groupés en rupture de stock ne sont pas disponibles dans la réponse GraphQL

Le correctif ACSD-47292 corrige le problème où les produits en rupture de stock groupés ne sont pas disponibles dans la réponse GraphQL même si le [!UICONTROL Display Out-of-Stock Products] est défini sur *[!UICONTROL Yes]*. Ce correctif est disponible lorsque la version 1.1.25 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-47292. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits en rupture de stock groupés ne sont pas disponibles dans la réponse de GraphQL, même si la [!UICONTROL Display Out-of-Stock Products] est définie sur *[!UICONTROL Yes]*.

<u>Procédure à suivre </u> :

1. Accédez à Adobe Commerce Admin > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** et définissez la [!UICONTROL Display Out-of-Stock Products] sur *[!UICONTROL Yes]*.
1. Créez deux produits simples, s1 et s2.
1. Rendre s1 en rupture de stock et non visibles individuellement et s2 en stock et non visibles individuellement, et les affecter à une catégorie.
1. Créez un produit groupé avec au moins une option de produit et affectez s1 et s2 à cette option (type d’entrée « RadioButton »).
1. Enregistrez le produit groupé et affectez-le à une catégorie.
1. Accédez à la vitrine et ouvrez ce produit groupé. L’option en rupture de stock s1 est grisée mais visible.
1. Envoyer une requête GraphQL :

```GraphQL
{
  categoryList(filters: { ids: { in: ["3"] } }) {
    id
    name
    products(pageSize: 8, sort: { position: ASC }) {
      total_count
      items {
        id
        sku
        name
        ... on BundleProduct {
          url_key
          items {
            title
            sku
            options {
              quantity
              position
              is_default
              product {
                id
                name
                sku
              }
            }
          }
        }
      }
    }
  }
}
```

<u>Résultats attendus</u> :

l’option de lot s1 est répertoriée dans la réponse GraphQL, car [!UICONTROL Display Out-of-Stock Products] est défini sur *[!UICONTROL Yes]* et est visible sur le storefront.

<u>Résultats réels</u> :

l’option de lot s1 n’est pas répertoriée dans la réponse GraphQL.

```GraphQL
"items": [
                                {
                                    "title": "oo1",
                                    "sku": "bundle2",
                                    "options": [
                                        {
                                            "quantity": 1,
                                            "position": 2,
                                            "is_default": false,
                                            "product": {
                                                "id": 2,
                                                "name": "s2",
                                                "sku": "s2"
                                            }
                                        }
                                    ]
                                }
                            ]
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
