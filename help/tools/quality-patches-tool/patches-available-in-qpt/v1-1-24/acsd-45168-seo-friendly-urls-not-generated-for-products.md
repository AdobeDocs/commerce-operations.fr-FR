---
title: "ACSD-45168 : URL compatibles avec le SEO non générées pour les produits dont les attributs url_key sont remplacés"
description: Appliquez le correctif ACSD-45168 pour résoudre le problème Adobe Commerce en raison duquel les URL compatibles avec l’optimisation pour les moteurs de recherche n’étaient pas générées pour les produits dont les attributs url_key sont remplacés au niveau de l’affichage en magasin.
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
source-git-commit: 809defe75d7b218d8085f85ff815472a531040cf
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-45168 : URL compatibles SEO non générées pour les produits dont les attributs url_key sont remplacés

Le correctif ACSD-45168 corrige le problème en raison duquel les URL compatibles avec l’optimisation pour les moteurs de recherche ne sont pas générées pour les produits dont les attributs url_key sont remplacés au niveau de l’affichage de magasin. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24 est installé. L’ID de correctif est ACSD-45168. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les URL compatibles avec l’optimisation pour les moteurs de recherche ne sont pas générées pour les produits dont les attributs url_key sont remplacés au niveau de l’affichage de magasin.

<u>Étapes à reproduire</u> :

1. Définissez la configuration comme suit en accédant à **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** :
   * [!UICONTROL Use Categories Path for Product URLs] = *Oui*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *Oui*
1. Nettoyez le cache de configuration.
1. Créez deux catégories : [!UICONTROL Category 1] et [!UICONTROL Category 2].
1. Créez deux produits : [!UICONTROL Product 1] dans [!UICONTROL Category 1], [!UICONTROL Product 2] dans [!UICONTROL Category 1].
1. Remplacez la portée par [!UICONTROL Default Store View] pour [!UICONTROL Product 1].
1. Décochez l’URL facultative [!UICONTROL Key] dans [!UICONTROL Search Engine Optimization].
1. Enregistrez le produit.
1. Revenez à [!UICONTROL All Store Views].
1. Ajoutez [!UICONTROL Product 1] à [!UICONTROL Category 2] et [!UICONTROL Product 2] à [!UICONTROL Category 2].
1. Vérifiez la table `url_rewrite` ou [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites].

<u>Résultats attendus</u> :

L’URL conviviale pour SEO pour [!UICONTROL Category 2] est créée pour [!UICONTROL Product 1].

<u>Résultats réels</u> :

L’URL conviviale pour SEO pour [!UICONTROL Category 2] est manquante pour [!UICONTROL Product 1] car l’attribut de clé d’URL a été remplacé pour la portée de la vue de magasin.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool]
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide d’infrastructure Commerce on Cloud

## Lecture connexe

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].
* [ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
