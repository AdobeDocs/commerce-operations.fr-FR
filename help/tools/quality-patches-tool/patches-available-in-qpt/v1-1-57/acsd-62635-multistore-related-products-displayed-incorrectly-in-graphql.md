---
title: 'ACSD-62635 : les produits associés à plusieurs magasins ne s’affichent pas correctement dans  [!DNL GraphQL]'
description: Appliquez le correctif ACSD-62635 pour résoudre le problème d’Adobe Commerce en raison duquel les produits associés à plusieurs magasins ne s’affichent pas correctement dans la requête  [!DNL GraphQL]  produit.
feature: B2B
role: Admin, Developer
source-git-commit: 8e6f6590dbed43eb8ce75b694a05ee951b538814
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-62635 : produits associés à plusieurs boutiques affichés incorrectement dans [!DNL GraphQL]

Le correctif ACSD-62635 corrige le problème d’affichage incorrect des produits associés à plusieurs magasins dans la requête de produit [!DNL GraphQL]. Ce correctif est disponible lorsque la version 1.1.57 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) est installée. L’ID du correctif est ACSD-62635. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque B2B est activé, [!DNL GraphQL] requête renvoie tous les produits associés de tous les sites web, même si une portée d’affichage de magasin est utilisée dans la requête.

<u>Procédure à suivre </u> :

1. Créez deux sites web, magasins et vues de magasin.
1. Créez les produits simples suivants :
   * Une principale avec SKU *product1* affectée à tous les sites web
   * Un affecté uniquement au *site web 1*
   * Un affecté uniquement à *Site web 2*
   * Une affectée à la fois au *site web 1* et au *site web 2*
1. Ajoutez tous les produits associés à *product1*.
1. Activez [!UICONTROL B2B] et [!UICONTROL Shared Catalog].
1. Ajoutez tous les produits au catalogue partagé par défaut.
1. Envoyez [!DNL GraphQL] requête pour récupérer *product1* et ses produits associés avec le code de magasin *Website 1* dans l’en-tête.

<u>Résultats attendus</u> :

La réponse contient uniquement les produits associés des sites web qui correspondent au code de magasin envoyé dans l’en-tête de la requête.

<u>Résultats réels</u> :

La réponse contient tous les produits associés de tous les sites Web, quel que soit le code de magasin spécifié dans la requête.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-Premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
