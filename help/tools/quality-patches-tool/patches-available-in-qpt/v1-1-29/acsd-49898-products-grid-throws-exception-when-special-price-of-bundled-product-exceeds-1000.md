---
title: "ACSD-49898 : la grille Produits renvoie une exception"
description: Appliquez le correctif ACSD-49898 pour résoudre le problème Adobe Commerce où la grille de produits renvoie une exception lorsqu’un produit groupé a un prix spécial supérieur à 1 000.
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-49898 : La grille Produits renvoie une exception

Le correctif ACSD-49898 corrige le problème où la grille de produits renvoie une exception lorsqu’un produit groupé a un prix spécial supérieur à 1 000. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 est installé. L’ID de correctif est ACSD-49898. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La grille de produits renvoie une exception lorsqu’un produit regroupé a un prix spécial supérieur à 1 000. Le problème concerne l&#39;utilisation de virgules au lieu de points pour les nombres décimaux dans certains paramètres régionaux.

<u>Étapes à reproduire</u> :

1. Créez un produit regroupé.
1. Définissez le prix spécial sur 999 ; enregistrez et fermez.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]**

>[!NOTE]
>
>Recherchez le SKU du produit fourni s’il n’est pas visible.

<u>Résultats attendus</u> :

* L’utilisateur peut filtrer/voir le produit fourni avec le prix spécial.
* Le prix spécial est présenté sous la forme d’un pourcentage pour les produits regroupés et d’un prix pour d’autres types de produits.

<u>Résultats réels</u> :

L’erreur suivante est générée : *Valeur non numérique rencontrée*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
