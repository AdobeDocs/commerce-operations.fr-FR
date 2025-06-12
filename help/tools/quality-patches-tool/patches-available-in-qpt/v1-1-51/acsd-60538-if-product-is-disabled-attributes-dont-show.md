---
title: 'ACSD-60538 : les attributs ne s’affichent pas correctement si le produit est désactivé dans [!UICONTROL All Store Views]'
description: 'Appliquez le correctif ACSD-60538 pour résoudre le problème d’Adobe Commerce : si un produit est désactivé dans *Toutes les vues de magasin* et activé uniquement dans des portées d’affichage de magasin spécifiques, les attributs de produit ne s’affichent pas correctement dans la réponse de GraphQL, ce qui entraîne l’affichage incorrect du produit.'
feature: Attributes, GraphQL
role: Admin, Developer
exl-id: 2ea9de11-b750-4ab6-9cc7-e940e1791f22
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-60538 : les attributs ne s’affichent pas correctement si le produit est désactivé dans *[!UICONTROL All Store Views]*

Le correctif ACSD-60538 corrige le problème suivant : si un produit est désactivé dans *[!UICONTROL All Store Views]* et activé uniquement dans des portées d’affichage de magasin spécifiques, les attributs de produit ne s’affichent pas correctement dans la réponse GraphQL, ce qui entraîne un affichage incorrect du produit. Ce correctif est disponible lorsque la version 1.1.51 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-60538. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Si un produit est désactivé dans *[!UICONTROL All Store Views]* et activé uniquement dans des portées d’affichage de magasin spécifiques, les attributs de produit ne s’affichent pas correctement dans la réponse GraphQL, ce qui entraîne un affichage incorrect du produit.

<u>Conditions préalables</u> :

Le module Inventaire est installé.

<u>Procédure à suivre </u> :

1. Créez un produit configurable avec l’attribut *color* et trois produits enfants (*blue*, *black* et *brown*).
1. Désactivez deux produits enfants associés (*bleu* et *noir*) sur la portée du *[!UICONTROL All Store Views]*.
1. Accédez à la portée **[!UICONTROL Store View]**.
1. Activez les produits enfants (*bleu* et *noir*) sur *[!UICONTROL Store View]* portée.
1. Exécutez la requête GraphQL ci-dessous :

   ```GraphQL
   {
     products(filter: { sku: { eq: "SKU" } }) {
       items {
           ... on ConfigurableProduct {
             configurable_options {
               attribute_id,
               attribute_code,
            values {
             value_index
             label
           }
       }
       variants {
         product {
           sku
         }
         attributes {
           label
           code
           value_index
          }
         }
        }
       }
      }
     }  
   ```

<u>Résultats attendus</u> :

La réponse de GraphQL inclut les valeurs d’attribut pour le produit associé enfant désactivé sur *[!UICONTROL All Store Views]* et activé sur la portée de *[!UICONTROL Store View]*.

<u>Résultats réels</u> :

La réponse de GraphQL contient des valeurs d’attribut vides pour le produit associé enfant lorsque le produit est désactivé sur *[!UICONTROL All Store Views]* et activé sur la portée de *[!UICONTROL Store View]*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
