---
title: 'ACSD-57074 : l’attribut personnalisé *Oui/Non* avec le préfixe « price _* » dans l’attribut « attribute_code » ne fonctionne pas avec l’indexation'
description: Appliquez le correctif ACSD-57074 pour résoudre le problème d’Adobe Commerce en raison duquel l’attribut personnalisé *Oui/Non* avec le préfixe « price _* » de l’attribut « attribute_code » ne fonctionne pas avec l’indexation.
feature: Products, Categories, Catalog Management
role: Admin, Developer
exl-id: 718b8f2d-4d3d-4755-8a91-5c2f97114813
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-57074 : *Oui/Non* l’attribut personnalisé avec préfixe `price_*` dans `attribute_code` attribut ne fonctionne pas avec l’indexation

Le correctif ACSD-57074 corrige le problème en raison duquel l’attribut personnalisé *Oui/Non* avec `price_*` préfixe dans l’attribut `attribute_code` ne fonctionne pas avec l’indexation. Ce correctif est disponible lorsque la version 1.1.47 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-57074. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’attribut personnalisé *Oui/Non* avec `price_*` préfixe dans l’attribut `attribute_code` ne fonctionne pas avec l’indexation.

<u>Procédure à suivre </u> :

1. Créez un attribut de produit personnalisé avec les options suivantes :
   * *[!UICONTROL Catalog Input Type]* : *Oui/Non*
   * *[!UICONTROL Scope]* : *StoreView*
   * *[!UICONTROL Use in Search]* : *Oui*
1. Attribuez l’attribut au jeu d’attributs par défaut.
1. Créez un produit avec l’attribut que nous avons créé.
1. Affectez le produit que nous venons de créer à une catégorie.
1. Exécutez la réindexation complète.

<u>Résultats attendus</u> :

Le produit s’affiche dans la catégorie affectée.

<u>Résultats réels</u> :

Le produit n’apparaît pas sur la page de catégorie principale.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
