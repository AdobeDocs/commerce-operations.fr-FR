---
title: 'ACSD-57337 : l’utilisateur administrateur avec des restrictions d’accès peut afficher toutes les sociétés dans la grille *Sociétés*'
description: Appliquez le correctif ACSD-57337 pour résoudre le problème d’Adobe Commerce en raison duquel un utilisateur administrateur disposant de restrictions d’accès à des sites web spécifiques pouvait afficher les sociétés de tous les sites web dans la grille *Sociétés*.
feature: Companies, B2B, Configuration
role: Admin, Developer
exl-id: 7a05d335-5ed8-460e-80c4-dbc51d06c5bd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-57337 : l’utilisateur administrateur avec des restrictions d’accès peut afficher toutes les sociétés dans la grille *Sociétés*.

Le correctif ACSD-57337 corrige le problème en raison duquel un utilisateur administrateur disposant de restrictions d’accès à des sites web spécifiques pouvait afficher les sociétés de tous les sites web dans la grille *Sociétés*. Ce correctif est disponible lorsque la version 1.1.48 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-57337. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un utilisateur administrateur disposant de restrictions d’accès à des sites web spécifiques peut afficher les sociétés de tous les sites web dans la grille *Sociétés*.

<u>Procédure à suivre </u> :

1. Créez un site web, un magasin et une révision supplémentaires.
1. Créez quelques sociétés affectées à différents sites web.
1. Créez un rôle d’utilisateur administrateur et définissez l’étendue du rôle sur le site web créé.
1. Créez un administrateur et affectez-le au rôle créé.
1. Connectez-vous avec un nouvel administrateur.
1. Ouvrez **[!UICONTROL Customers]** > **[!UICONTROL Companies]** et observez la liste des entreprises.

<u>Résultats attendus</u> :

Les sociétés qui ont été affectées au site web supplémentaire sont visibles dans la grille *Sociétés*.

<u>Résultats réels</u> :

Toutes les sociétés sont visibles dans la grille *Sociétés*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
