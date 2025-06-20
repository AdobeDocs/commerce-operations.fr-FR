---
title: 'ACSD-50116 : un utilisateur administrateur ne peut pas créer de réécriture d’URL pour les sous-catégories de niveau 3 ou inférieur'
description: Appliquez le correctif ACSD-50116 pour résoudre le problème d’Adobe Commerce où un utilisateur administrateur ne peut pas créer de réécriture d’URL pour les sous-catégories de niveau 3 ou inférieur.
feature: Admin Workspace, Categories
role: Admin
exl-id: b2a248eb-a6c4-4596-acac-04a52c5c2a61
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-50116 : un utilisateur administrateur ne peut pas créer de réécriture d’URL pour les sous-catégories de niveau 3 ou inférieur

Le correctif ACSD-50116 corrige le problème en raison duquel un utilisateur administrateur ne peut pas créer de réécriture d’URL pour les sous-catégories de niveau 3 ou inférieur. Ce correctif est disponible lorsque la version 1.1.30 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-50116. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un utilisateur administrateur ne peut pas créer de réécriture d’URL pour les sous-catégories de niveau 3 ou inférieur.

<u>Procédure à suivre </u> :

1. Créez une arborescence de catégories qui comporte plus de trois niveaux de sous-catégories.
1. Essayez de créer un *[!UICONTROL URL Rewrite]* pour la catégorie de niveau 4 à l’aide des options *[!UICONTROL For Product]* et *[!UICONTROL For Category]*.

<u>Résultats attendus</u> :

L’arborescence des catégories affiche les sous-catégories jusqu’au niveau quatre ou inférieur.

<u>Résultats réels</u> :

L’arborescence des catégories affiche uniquement les sous-catégories de niveau 3 au maximum.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
