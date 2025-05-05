---
title: 'ACSD-50887 : *[!UICONTROL Use in Search Results Layered Navigation]* défini sur Oui sans l’option *[!UICONTROL Use in Search]*'
description: Appliquez le correctif ACSD-50887 pour résoudre le problème Adobe Commerce en raison duquel la propriété d’attribut de produit *[!UICONTROL Use in Search Results Layered Navigation]* peut être définie sur *Oui* sans que l’option *[!UICONTROL Use in Search]* soit également définie sur *Oui*.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: 5e797121-c386-4aca-9139-0a02a60be38a
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-50887 : *[!UICONTROL Use in Search Results Layered Navigation]* défini sur *Yes* sans l’option *[!UICONTROL Use in Search]*

Le correctif ACSD-50887 corrige le problème où la propriété d’attribut de produit *[!UICONTROL Use in Search Results Layered Navigation]* peut être définie sur *Oui* sans que l’option *[!UICONTROL Use in Search]* soit également définie sur *Oui*. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.36 est installé. L’ID de correctif est ACSD-50887. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La propriété d’attribut de produit *[!UICONTROL Use in Search Results Layered Navigation]* peut être définie sur *Yes* sans l’option *[!UICONTROL Use in Search]* également définie sur *Yes*.

Ces paramètres ont été conçus pour être utilisés ensemble. Une fois le correctif appliqué, lorsque l’option *[!UICONTROL Use in Search]* est définie sur *Non*, l’option *[!UICONTROL Use in Search Results Layered Navigation]* est masquée pour fonctionner comme si elle était également définie sur *Non*.

<u>Étapes à reproduire</u> :

1. Dans l’Admin, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]** et créez un attribut avec le type multiselect et définissez les éléments suivants :

   * *[!UICONTROL Use in Search]= Non*
   * *[!UICONTROL Use in Layered Navigation]= (N’importe quelle option)*
   * *[!UICONTROL Use in Search Results Layered Navigation]= Oui*
   * *Nom = Test_attribute*
   * *Options* :
      * *Sticker*
      * *Sélecteur*

1. Ajoutez le nouvel attribut au jeu d’attributs par défaut.
1. Créez deux produits :

   1. Premier produit :
      * Nom = Sticker
      * Définir le prix, la qualité, le poids sur 1
      * Test_attribute = sélectionner l’option *Sticker*

   1. Deuxième produit :
      * Nom = Sélecteur
      * Définir le prix, la qualité, le poids sur 1
      * Test_attribute = sélectionner les deux options

1. Exécutez la réindexation `catalogsearch_fulltext` :

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. Recherchez le mot *sticker* sur le storefront.

<u>Résultats attendus</u> :

Seul le produit *Sticker* est renvoyé, car [!DNL Elasticsearch] n’indexe pas Test_attribute lorsque *[!UICONTROL Use in Search]* a été défini sur *No*.

<u>Résultats réels</u> :

Les deux produits sont renvoyés.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
