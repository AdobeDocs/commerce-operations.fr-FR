---
title: 'ACSD-47137 : amélioration de la vitesse de chargement de la galerie d’images &grave;pub/media&grave; grand dossier'
description: Appliquez le correctif ACSD-47137 pour améliorer la vitesse de chargement de la galerie d’images lorsque le dossier "pub/media" est très volumineux.
feature: Cache, Catalog Management, Categories, Media
role: Admin
exl-id: 8a5dd930-1940-486e-96db-ee1b166cf312
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-47137 : amélioration de la vitesse de chargement de la galerie d’images lorsque le dossier `pub/media` est volumineux

Le correctif ACSD-47137 améliore la vitesse de chargement de la galerie d’images lorsque le dossier `pub/media` est très volumineux. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24 est installé. L’ID de correctif est ACSD-47137. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La vitesse de chargement de la galerie d’images est lente lorsque le dossier `pub/media` est très volumineux.

<u>Étapes à reproduire</u> :

1. Accédez à l’administrateur Adobe Commerce > **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]** à _Non_.
1. Nettoyez le cache de configuration.
1. Déconnectez-vous et reconnectez-vous en tant qu’utilisateur administrateur.
1. Dans la barre latérale Admin, accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** et sélectionnez la catégorie racine.
1. Développez la section **[!UICONTROL Content]** et cliquez sur **[!UICONTROL Select from Gallery]**.

Lors du chargement de la page, Adobe Commerce envoie une requête `media_gallery/directories/gettree` pour charger l’arborescence du dossier multimédia.

<u>Résultats attendus</u> :

La requête `media_gallery/directories/gettree` ne doit charger le contenu que depuis les répertoires nécessaires, à l’exception de la boucle de la liste complète des chemins d’accès à partir du dossier `pub/media/`.

<u>Résultats réels</u> :

Le chargement de la requête `media_gallery/directories/gettree` prend beaucoup de temps lorsque le dossier `pub/media/` comporte beaucoup de contenu.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
