---
title: 'ACSD-47137 : amélioration de la vitesse de chargement de la galerie d’images du dossier « pub/media »'
description: Appliquez le correctif ACSD-47137 pour améliorer la vitesse de chargement de la galerie d’images lorsque le dossier « pub/media » est très volumineux.
feature: Cache, Catalog Management, Categories, Media
role: Admin
exl-id: 8a5dd930-1940-486e-96db-ee1b166cf312
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-47137 : amélioration de la vitesse de chargement de la galerie d’images lorsque `pub/media` dossier est volumineux

Le correctif ACSD-47137 améliore la vitesse de chargement de la galerie d’images lorsque le dossier `pub/media` est très volumineux. Ce correctif est disponible lorsque la version 1.1.24 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-47137. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La vitesse de chargement de la galerie d’images est lente lorsque le dossier `pub/media` est très volumineux.

<u>Procédure à suivre </u> :

1. Accédez à Adobe Commerce Admin > **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]** en _Non_.
1. Nettoyez le cache de configuration.
1. Déconnectez-vous et reconnectez-vous en tant qu’utilisateur administrateur.
1. Dans la barre latérale d’administration, accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** et sélectionnez la catégorie racine.
1. Développez la section **[!UICONTROL Content]** et cliquez sur **[!UICONTROL Select from Gallery]**.

Lors du chargement de la page, Adobe Commerce envoie `media_gallery/directories/gettree` requête pour charger l’arborescence de dossiers médias.

<u>Résultats attendus</u> :

La requête `media_gallery/directories/gettree` ne doit charger le contenu que depuis les répertoires nécessaires, à l’exception de la boucle de la liste complète des chemins d’accès depuis le dossier `pub/media/` .

<u>Résultats réels</u> :

Le chargement de la requête `media_gallery/directories/gettree` prend beaucoup de temps lorsque le dossier `pub/media/` contient beaucoup de contenu.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
