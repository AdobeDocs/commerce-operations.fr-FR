---
title: 'ACSD-59378 : les réécritures au niveau  [!DNL URL]  magasin ne sont pas correctement mises à jour lors de l’importation'
description: Appliquez le correctif ACSD-59378 pour résoudre le problème d’Adobe Commerce en raison duquel les réécritures au niveau  [!DNL URL]  magasin sont incorrectement mises à jour lors de l’importation.
feature: Data Import/Export
role: Admin, Developer
exl-id: dc54d810-dcc6-42c6-a877-d00d3cf4f9a5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-59378 : le [!DNL URL] au niveau du magasin n’est pas correctement mis à jour lors de l’importation

Le correctif ACSD-59378 corrige le problème en raison duquel les réécritures de [!DNL URL] au niveau du magasin sont incorrectement mises à jour lors de l’importation. Ce correctif est disponible lorsque la version 1.1.50 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-59378. Ce problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p5

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.5x (toutes les versions de la version 2.4.5)

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les réécritures [!DNL URL] au niveau du magasin ne sont pas correctement mises à jour lors de l’importation.

<u>Procédure à suivre </u> :

1. Créez un produit avec des `url_key = key_default` sur la portée **Toutes les vues de la boutique**.
1. Définissez `url_key = key_store` dans la portée **Affichage de la boutique par défaut**.
1. Exportez le produit.
1. Importez un fichier [!DNL CSV] pour ce produit contenant les données suivantes :
   * `store_view_code` colonne est définie sur *vide* afin qu’elle s’applique à la portée **Toutes les vues de la boutique**.
   * `url_key` est défini sur le *`key_default`* de clé par défaut.

<u>Résultats attendus</u> :

Les réécritures [!DNL URL] ne sont régénérées que pour les vues de magasin pour lesquelles il n’existe aucune `url_key` remplacée (lorsque la `url_key` par défaut s’applique).

<u>Résultats réels</u> :

`key_store` réécritures [!DNL URL] sont supprimées, mais la réécriture [!DNL URL] au niveau **Affichage de la boutique par défaut** pour le produit est toujours définie sur *`key_store`*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
