---
title: 'ACSD-57394 : tri incorrect des produits en fonction de plusieurs attributs de tri dans  [!DNL GraphQL]'
description: Appliquez le correctif ACSD-57394 pour résoudre le problème d’Adobe Commerce en raison duquel les produits sont incorrectement triés lors de l’utilisation de plusieurs attributs de tri dans  [!DNL GraphQL].
feature: GraphQL, Products
role: Admin, Developer
exl-id: 3e4ca535-37ed-4363-ba6c-968eb53b98b3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-57394 : tri incorrect des produits en fonction de plusieurs attributs de tri dans [!DNL GraphQL]

Le correctif ACSD-57394 corrige le problème de tri incorrect des produits lors de l’utilisation de plusieurs attributs de tri dans les [!DNL GraphQL]. Ce correctif est disponible lorsque la version 1.1.48 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-57394. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits ne sont pas triés correctement lors de l’utilisation de plusieurs attributs de tri dans [!DNL GraphQL].

<u>Procédure à suivre </u> :

1. Créez quelques produits avec des prix et des noms différents.
1. Créez une catégorie et attribuez-lui les produits créés.
1. Envoyez une requête de produits [!DNL GraphQL] pour la catégorie créée avec quelques attributs *sort*. Par exemple :

   ```
   {
   products(
     currentPage: 1
     pageSize: 10
     filter: {
       category_id: {
         eq :"3"
       }
     }
     sort: {  price: DESC, name: ASC, position: ASC
     }
   ){
   items{
     name
     sku
   
       price_range {
           minimum_price {
   
         regular_price {
           value
           currency
         }
         final_price {
           value
           currency
         }
         discount {
           amount_off
           percent_off
         }
               }
           }
      }
     }
    }
   ```

1. Vérifiez la réponse après la création des attributs *sort*.

<u>Résultats attendus</u> :

Les produits doivent être retournés dans le bon ordre. Le tri des produits en fonction de plusieurs attributs doit fonctionner.

<u>Résultats réels</u> :

Les produits ne sont pas retournés dans le bon ordre. Le tri des produits en fonction de plusieurs attributs ne fonctionne pas.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
