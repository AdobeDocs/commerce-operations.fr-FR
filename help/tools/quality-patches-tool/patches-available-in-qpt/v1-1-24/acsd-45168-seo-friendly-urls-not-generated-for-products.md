---
title: 'ACSD-45168 : URL compatibles avec l’optimisation du moteur de recherche non générées pour les produits pour lesquels les attributs url_key sont remplacés'
description: Appliquez le correctif ACSD-45168 pour résoudre le problème d’Adobe Commerce en raison duquel les URL compatibles avec l’optimisation du moteur de recherche ne sont pas générées pour les produits dont les attributs url_key sont remplacés au niveau de la vue du magasin.
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
exl-id: 7d908307-f60c-4758-ad0f-f108ebb94558
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-45168 : URL compatibles avec l’optimisation du moteur de recherche non générées pour les produits pour lesquels les attributs url_key sont remplacés

Le correctif ACSD-45168 corrige le problème où les URL compatibles avec l’optimisation du moteur de recherche ne sont pas générées pour les produits pour lesquels les attributs url_key sont remplacés au niveau de la vue du magasin. Ce correctif est disponible lorsque la version 1.1.24 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-45168. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les URL compatibles avec l’optimisation du moteur de recherche ne sont pas générées pour les produits pour lesquels les attributs url_key sont remplacés au niveau de la vue du magasin.

<u>Procédure à suivre </u> :

1. Définissez la configuration comme suit en accédant à **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** :
   * [!UICONTROL Use Categories Path for Product URLs] = *Oui*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *Oui*
1. Nettoyez le cache de configuration.
1. Créez deux catégories : [!UICONTROL Category 1] et [!UICONTROL Category 2].
1. Créez deux produits : [!UICONTROL Product 1] dans [!UICONTROL Category 1], [!UICONTROL Product 2] dans [!UICONTROL Category 1].
1. Remplacez la portée par [!UICONTROL Default Store View] pour [!UICONTROL Product 1].
1. Décochez la [!UICONTROL Key] d’URL facultative dans [!UICONTROL Search Engine Optimization].
1. Enregistrez le produit.
1. Revenez à [!UICONTROL All Store Views].
1. Ajoutez des [!UICONTROL Product 1] aux [!UICONTROL Category 2] et des [!UICONTROL Product 2] aux [!UICONTROL Category 2].
1. Vérifiez le tableau `url_rewrite` ou [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites].

<u>Résultats attendus</u> :

L’URL d’optimisation pour les moteurs de recherche pour [!UICONTROL Category 2] est créée pour [!UICONTROL Product 1].

<u>Résultats réels</u> :

L’URL compatible avec l’optimisation du moteur de recherche pour [!UICONTROL Category 2] est manquante pour [!UICONTROL Product 1], car l’attribut de clé URL a été remplacé pour la portée d’affichage du magasin.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool]
* Adobe Commerce sur les infrastructures cloud : [ Mises à niveau et correctifs > Appliquer des correctifs ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool]
* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
