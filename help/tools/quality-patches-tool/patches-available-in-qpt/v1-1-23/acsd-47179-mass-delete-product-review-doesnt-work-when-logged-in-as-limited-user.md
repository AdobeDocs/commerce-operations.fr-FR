---
title: "ACSD-47179 : la suppression en masse des révisions de produits ne fonctionne pas lorsque vous êtes connecté en tant que rôle d’utilisateur limité"
description: Appliquez le correctif ACSD-47179 pour résoudre le problème Adobe Commerce en raison duquel la suppression en masse des révisions de produits ne fonctionne pas lorsque vous êtes connecté en tant que rôle d’utilisateur limité.
feature: Marketing Tools, Products, Roles/Permissions
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-47179 : la suppression en masse des révisions de produits ne fonctionne pas lorsque vous êtes connecté en tant que rôle d’utilisateur limité

Le correctif ACSD-47179 corrige le problème en raison duquel la suppression en masse des révisions de produits ne fonctionne pas lorsqu’elle est connectée en tant que rôle d’utilisateur limité. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23 est installé. L’ID de correctif est ACSD-47179. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La suppression en masse des révisions de produits ne fonctionne pas lorsqu’elle est connectée en tant que rôle d’utilisateur limité.

<u>Étapes à reproduire</u> :

1. Créez un site web secondaire.
1. Créez un rôle d’utilisateur limité au site web secondaire avec une autorisation complète pour les sections suivantes :
   * Catalogue
   * Client
   * Marketing
1. Créez un produit et affectez-le au site web secondaire.
1. Ajoutez deux révisions au produit à partir du front-end.
1. Connectez-vous à l’administrateur [!DNL Commerce] à l’aide de l’utilisateur administrateur restreint qui vient d’être créé.
1. Essayez de supprimer en masse les révisions en attente.

<u>Résultats attendus</u> :

Un administrateur disposant d’autorisations suffisantes peut supprimer en masse les révisions en attente.

<u>Résultats réels</u> :

Vous obtenez l’erreur suivante : _Quelque chose s’est mal passé. Exception générée dans support_report.log_

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
