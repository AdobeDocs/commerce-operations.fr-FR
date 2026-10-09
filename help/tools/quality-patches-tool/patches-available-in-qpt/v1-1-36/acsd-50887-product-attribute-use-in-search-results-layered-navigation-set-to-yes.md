---
title: 'ACSD-50887 : *[!UICONTROL Use in Search Results Layered Navigation]* défini sur Oui sans l’option *[!UICONTROL Use in Search]*'
description: Appliquez le correctif ACSD-50887 pour résoudre le problème d’Adobe Commerce où la propriété d’attribut de produit *[!UICONTROL Use in Search Results Layered Navigation]* peut être définie sur *Oui* sans que l’option *[!UICONTROL Use in Search]* ne soit également définie sur *Oui*.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: 5e797121-c386-4aca-9139-0a02a60be38a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '461'
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
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
