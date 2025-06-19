---
title: 'ACSD-53658 : **[!UICONTROL Recently Viewed Product]** les données ne sont pas correctement mises à jour dans la vue du magasin'
description: Appliquez le correctif ACSD-53658 pour résoudre le problème d’Adobe Commerce où les données **[!UICONTROL Recently Viewed Product]** ne sont pas correctement mises à jour dans la vue du magasin.
feature: CMS, Personalization
role: Admin, Developer
exl-id: a91fac3d-cb6f-4f65-aec2-d28cee4fd39f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-53658 : les données **[!UICONTROL Recently Viewed Product]** ne sont pas correctement mises à jour dans la vue du magasin

Le correctif ACSD-53658 corrige le problème où les données **[!UICONTROL Recently Viewed Product]** ne sont pas correctement mises à jour dans la vue du magasin. Ce correctif est disponible lorsque la version 1.1.42 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-53658. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les données **[!UICONTROL Recently Viewed Product]** ne sont pas correctement mises à jour dans la vue du magasin.

<u>Procédure à suivre </u> :

1. Connectez-vous au panneau d’administration.
1. Créez une deuxième vue de magasin pour le site web par défaut.
1. Créez un produit simple.
1. Définissez un nom de produit différent pour la nouvelle vue de magasin.
1. Créez un widget **[!UICONTROL Recently Viewed Product]**.
1. Configurez ce widget à afficher sur la page d’accueil.
1. Ouvrez la page produit sur le storefront à partir de la vue de magasin par défaut.
1. Ouvrez la page d’accueil .
1. En utilisant le sélecteur de magasin, passez à la deuxième vue du magasin.

<u>Résultats attendus</u> :

Le nom du produit est mis à jour dans le widget.

<u>Résultats réels</u> :

Le nom du produit n’est pas mis à jour dans le widget.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
