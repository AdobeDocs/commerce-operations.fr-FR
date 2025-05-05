---
title: "ACSD-58735 : l’administrateur avec restriction ne peut pas afficher les paniers abandonnés sur le compte client du site web associé"
description: Appliquez le correctif ACSD-58735 pour résoudre le problème Adobe Commerce en raison duquel un administrateur restreint ne peut pas afficher les paniers abandonnés sur la page du compte client de l’administrateur Commerce d’un site web associé.
feature: Shopping Cart, Admin Workspace, Customers
role: Admin, Developer
source-git-commit: 35bae8cff40235957f8fea418a43ccead13536da
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---



# ACSD-58735 : L’administrateur restreint ne peut pas afficher les paniers abandonnés sur le compte client pour le site Web associé.

Le correctif ACSD-58735 corrige le problème lorsqu’un utilisateur administrateur avec un rôle limité ne peut pas afficher les paniers des clients abandonnés à partir de l’onglet Commerce **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** > **[!UICONTROL Select Cart]** > **[!UICONTROL Shopping Cart]** .

Le problème se produit car lors de l’affichage de la grille pour plusieurs sites web, si un panier abandonné est chargé par défaut dans le panneau Admin, l’identifiant de magasin associé n’est pas affiché.

Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 est installé. L’ID de correctif est ACSD-58735. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les administrateurs avec restriction ne peuvent pas afficher les paniers abandonnés sur la page du compte client dans le panneau d’administration.

<u>Étapes à reproduire</u> :

1. Créez un rôle d’administrateur n’ayant accès qu’à l’un des sites web.
1. Créez un panier abandonné.
1. Connectez-vous en tant qu’utilisateur administrateur avec des privilèges complets. Cochez **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** et vérifiez que le panier s’affiche.
1. Cochez **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** comme utilisateur administrateur restreint.

<u>Résultats attendus</u> :

L’administrateur restreint peut voir les paniers abandonnés pour le site web associé.

<u>Résultats réels</u> :

L’administrateur restreint ne voit pas les paniers abandonnés pour le site Web associé.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
