---
title: 'ACSD-50887 : *[!UICONTROL Use in Search Results Layered Navigation]* défini sur Oui sans l’option *[!UICONTROL Use in Search]*'
description: Appliquez le correctif ACSD-50887 pour résoudre le problème d’Adobe Commerce où la propriété d’attribut de produit *[!UICONTROL Use in Search Results Layered Navigation]* peut être définie sur *Oui* sans que l’option *[!UICONTROL Use in Search]* ne soit également définie sur *Oui*.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: 5e797121-c386-4aca-9139-0a02a60be38a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-50887 : *[!UICONTROL Use in Search Results Layered Navigation]* défini sur *Oui* sans l’option *[!UICONTROL Use in Search]*

Le correctif ACSD-50887 corrige le problème en raison duquel la propriété d’attribut de produit *[!UICONTROL Use in Search Results Layered Navigation]* peut être définie sur *Oui* sans que l’option *[!UICONTROL Use in Search]* ne soit également définie sur *Oui*. Ce correctif est disponible lorsque la version 1.1.36 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-50887. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La *[!UICONTROL Use in Search Results Layered Navigation]* de propriété d’attribut de produit peut être définie sur *Oui* sans que l’option *[!UICONTROL Use in Search]* soit également définie sur *Oui*.

Ces paramètres ont été conçus pour être utilisés conjointement. Une fois le correctif appliqué, lorsque l’option *[!UICONTROL Use in Search]* est définie sur *Non*, l’option *[!UICONTROL Use in Search Results Layered Navigation]* est masquée pour fonctionner comme si elle était également définie sur *Non*.

<u>Procédure à suivre </u> :

1. Dans Admin, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]** , créez un attribut avec le type à sélection multiple et définissez les éléments suivants :

   * *[!UICONTROL Use in Search]= Non*
   * *[!UICONTROL Use in Layered Navigation]= (toute option)*
   * *[!UICONTROL Use in Search Results Layered Navigation]= Oui*
   * *Name = Test_attribute*
   * *Options* :
      * *Autocollant*
      * *Sélecteur*

1. Ajoutez le nouvel attribut au jeu d’attributs par défaut.
1. Créez deux produits :

   1. Premier produit :
      * Nom = autocollant
      * Régler le prix, la quantité, le poids sur 1
      * Test_attribute = select option *Sticker*

   1. Deuxième produit :
      * Nom = Sélecteur
      * Régler le prix, la quantité, le poids sur 1
      * Test_attribute = sélectionner les deux options

1. Exécutez `catalogsearch_fulltext` réindexation :

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. Recherchez par le mot *sticker* sur le storefront.

<u>Résultats attendus</u> :

Seul le produit *Sticker* est renvoyé, car [!DNL Elasticsearch] n&#39;indexe pas Test_attribute lorsque *[!UICONTROL Use in Search]* a été défini sur *No*.

<u>Résultats réels</u> :

Les deux produits sont retournés.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
