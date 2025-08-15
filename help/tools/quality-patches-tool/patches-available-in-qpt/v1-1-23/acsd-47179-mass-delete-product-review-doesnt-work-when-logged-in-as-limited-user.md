---
title: 'ACSD-47179 : la suppression en masse de révisions de produits ne fonctionne pas lorsque vous êtes connecté en tant que rôle d’utilisateur limité'
description: Appliquez le correctif ACSD-47179 pour résoudre le problème d’Adobe Commerce en raison duquel la suppression en masse des révisions de produits ne fonctionne pas lorsque vous êtes connecté en tant que rôle d’utilisateur limité.
feature: Marketing Tools, Products, Roles/Permissions
role: Admin
exl-id: 7131ee47-fadc-4e93-b8b2-5b2e0521ad97
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-47179 : la suppression en masse de révisions de produits ne fonctionne pas lorsque vous êtes connecté en tant que rôle d’utilisateur limité

Le correctif ACSD-47179 corrige le problème en raison duquel la suppression en masse des révisions de produits ne fonctionne pas lorsque vous êtes connecté en tant que rôle d’utilisateur limité. Ce correctif est disponible lorsque la version 1.1.23 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-47179. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La suppression en masse de révisions de produits ne fonctionne pas lorsque vous êtes connecté en tant que rôle d’utilisateur limité.

<u>Procédure à suivre </u> :

1. Créez un site web secondaire.
1. Créez un rôle d’utilisateur limité au site web secondaire avec une autorisation complète pour les sections suivantes :
   * Catalogue
   * Client
   * Marketing
1. Créez un produit et affectez-le au site web secondaire.
1. Ajoutez deux commentaires au produit à partir du front-end.
1. Connectez-vous à l’administrateur [!DNL Commerce] en utilisant l’utilisateur administrateur restreint qui vient d’être créé.
1. Essayez de supprimer en masse les révisions en attente.

<u>Résultats attendus</u> :

Un administrateur disposant des autorisations suffisantes peut effectuer une suppression en masse des révisions en attente.

<u>Résultats réels</u> :

Vous obtenez l’erreur suivante : _Un problème est survenu. Exception générée dans support_report.log_

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
