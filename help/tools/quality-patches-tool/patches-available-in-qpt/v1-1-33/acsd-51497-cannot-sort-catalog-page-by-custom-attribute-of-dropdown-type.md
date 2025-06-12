---
title: 'ACSD-51497 : impossible de trier la page du catalogue par attribut personnalisé de type Liste déroulante'
description: Appliquez le correctif ACSD-51497 pour résoudre le problème d’Adobe Commerce en raison duquel un client ne peut pas trier une page de catalogue par attribut personnalisé de type Liste déroulante.
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
exl-id: c66a7e04-fd2a-47be-8f7a-7982780a5414
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-51497 : impossible de trier la page du catalogue par attribut personnalisé de type *Liste déroulante*

Le correctif ACSD-51497 corrige le problème en raison duquel un client ne peut pas trier une page de catalogue en fonction d’un attribut personnalisé du type *Liste déroulante*. Ce correctif est disponible lorsque la version 1.1.33 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-51497. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un client ne peut pas trier une page de catalogue en fonction d’un attribut personnalisé du type *Liste déroulante*.

<u>Procédure à suivre</u>

1. Créez environ six produits simples et affectez-les à une seule catégorie.
1. Créez un attribut de produit afin de l’ajouter en tant qu’option de tri dans les pages de liste.

   * Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Add New Attribute]**.
   * Dans l’onglet **[!UICONTROL Properties]** , définissez les éléments suivants :

      * *[!UICONTROL Default Label]* = *test*
      * *[!UICONTROL Catalog Input Type]* pour Propriétaire de la boutique = *Liste déroulante*
      * *[!UICONTROL Options]* :

         * *premier*
         * *seconde*
         * *troisième*
         * *quatrième*

   * Dans l’onglet **[!UICONTROL Storefront Properties]** , définissez les éléments suivants :

      * *[!UICONTROL Used for sorting in product listing]* = *Oui*
      * Laissez toutes les autres options sur *Par défaut*.

1. Attribuez l’attribut *test* à l’attribut *Default* défini dans **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Configurez les produits pour qu’ils aient des valeurs d’attribut *test*.

   * SKU : s00001, test : quatrième
   * SKU : s00002, test : troisième
   * SKU : s00003, test : second
   * SKU : s00004, test : first
   * SKU : s00005, test : quatrième
   * SKU : s00006, test : troisième

1. Réindexez et effacez le cache.
1. Accédez à la catégorie sur le storefront.
1. Triez par attribut *test*.

<u>Résultats attendus</u> :

Les produits sont triés en fonction de l’attribut *test*.

<u>Résultats réels</u> :

Les produits ne sont pas triés par l’attribut *test*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
