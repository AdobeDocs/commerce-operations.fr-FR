---
title: 'ACSD-51291 : l’administration restreinte peut ajouter des images/vidéos au produit affecté à plusieurs sites web'
description: Appliquez le correctif ACSD-51291 pour résoudre le problème d’Adobe Commerce où un administrateur restreint ayant accès à un site web peut ajouter des images/vidéos à un produit attribué à plusieurs sites web.
feature: Admin Workspace, Products, Page Content
role: Admin
exl-id: a4edd034-f718-4559-9993-11609f0d0efa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-51291 : l’administration restreinte peut ajouter des images/vidéos au produit affecté à plusieurs sites web

Le correctif ACSD-51291 corrige le problème où un administrateur restreint ayant accès à un site web peut ajouter des images/vidéos à un produit affecté à plusieurs sites web. Ce correctif est disponible lorsque la version 1.1.32 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-51291. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p3, 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un administrateur restreint ayant accès à un site web peut ajouter des images/vidéos à un produit affecté à plusieurs sites web.

<u>Procédure à suivre</u>

1. Connectez-vous en tant qu’administrateur
1. Créez une deuxième vue de site web, de magasin et de magasin.
1. Créez un second rôle d’administrateur avec des ressources uniquement pour la seconde vue de site web, de magasin et de magasin.
1. Créez un second administrateur et affectez-le au nouveau rôle d’administrateur restreint.
1. Créez un produit et affectez-le à la fois au site web par défaut et au nouveau site web.
1. Déconnectez-vous du profil d’administration principal.
1. Connectez-vous en tant que nouvel administrateur restreint.
1. Modifiez le produit créé, qui a été affecté aux deux sites web.
1. Ouvrez l’onglet **[!UICONTROL Images and Videos]** .

<u>Résultats attendus</u> :

* Le message suivant s’affiche :

  *L’administration restreinte est autorisée à effectuer des actions avec des images ou des vidéos, uniquement lorsque l’administrateur dispose de droits sur tous les sites web auxquels le produit est affecté.*

* Le bouton **[!UICONTROL Add Video]** n’est pas actif.

<u>Résultats réels</u> :

L’administrateur restreint peut ajouter des images et des vidéos même lorsque le produit est affecté à un site web auquel il n’a pas accès.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
