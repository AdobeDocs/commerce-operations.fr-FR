---
title: '"ACSD-57074: *Oui/Non* attribut personnalisé avec le préfixe "price_*" dans l’attribut "attribute_code" ne fonctionne pas avec l’indexation"'
description: Appliquez le correctif ACSD-57074 pour résoudre le problème Adobe Commerce en raison duquel l’attribut personnalisé *Oui/Non* avec le préfixe `price_*` dans l’attribut `attribute_code` ne fonctionne pas avec l’indexation.
feature: Products, Categories, Catalog Management
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-57074 : l’attribut personnalisé *Oui/Non* avec le préfixe `price_*` dans l’attribut `attribute_code` ne fonctionne pas avec l’indexation.

Le correctif ACSD-57074 corrige le problème où l’attribut personnalisé *Oui/Non* avec le préfixe `price_*` dans l’attribut `attribute_code` ne fonctionne pas avec l’indexation. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.47 est installé. L’ID de correctif est ACSD-57074. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’attribut personnalisé *Oui/Non* avec le préfixe `price_*` dans l’attribut `attribute_code` ne fonctionne pas avec l’indexation.

<u>Étapes à reproduire</u> :

1. Créez un attribut de produit personnalisé avec les options suivantes :
   * *[!UICONTROL Catalog Input Type]* : *Oui/Non*
   * *[!UICONTROL Scope]* : *StoreView*
   * *[!UICONTROL Use in Search]* : *Oui*
1. Attribuez l’attribut au jeu d’attributs par défaut.
1. Créez un produit avec l’attribut que nous avons créé.
1. Attribuez le produit que nous venons de créer à une catégorie.
1. Exécutez la réindexation complète.

<u>Résultats attendus</u> :

Le produit s’affiche dans la catégorie qui lui est assignée.

<u>Résultats réels</u> :

Le produit n’apparaît pas sur la page de catégorie de premier plan.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
