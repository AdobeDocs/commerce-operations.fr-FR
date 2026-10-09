---
title: 'ACSD-65202 : la page Mon compte n’affiche pas les commandes récentes provenant d’autres vues de la boutique'
description: Appliquez le correctif ACSD-65202 pour résoudre le problème d’Adobe Commerce en raison duquel la page Mon compte n’affiche pas les commandes récentes provenant d’autres vues du même magasin.
feature: Orders, User Account
role: Admin, Developer
type: Troubleshooting
exl-id: 031f12f2-1b70-4cbc-92a0-8eb561e34067
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4560f5f5-d00c-5b5d-b61b-369d85ef7a26
    internal-label: User Account
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%
---
# ACSD-65202 : [!UICONTROL My Account] page n’affiche pas les commandes récentes provenant d’autres vues de la boutique

Le correctif ACSD-65202 corrige le problème où la page **[!UICONTROL My Account]** n’affiche pas les commandes récentes provenant d’autres vues du même magasin. Ce correctif est disponible lorsque la version 1.1.65 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-65202. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p12

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque vous accédez à la page Compte client (section **[!UICONTROL My Account]**), vous ne voyez pas les commandes récentes passées dans une autre vue de magasin. Cependant, lorsque vous accédez à l&#39;historique des commandes (section *[!UICONTROL My Orders]*), vous pouvez voir toutes les commandes dans les deux vues de la boutique.

<u>Procédure à suivre </u> :

1. Installez Adobe Commerce.
1. Dans le panneau *Admin*, créez une vue de boutique et saisissez son code, *seconde*, pour identifier la vue.
1. Créer un produit simple et le réindexer.
1. Créez un compte client et passez une commande dans la vue de magasin par défaut dont le code est *par défaut*.
1. Accédez à la page **[!UICONTROL My Orders]** et vérifiez que la commande est visible dans les deux affichages de la boutique, par exemple :
1. Valeur par défaut : https://localhost/pub/default/sales/order/history/
1. Deuxième point : https://localhost/pub/second/sales/order/history/

1. Accédez à la page **[!UICONTROL My Account]** dans les deux affichages de la boutique :
1. Valeur par défaut : https://localhost/pub/default/customer/account/
1. Deuxième point : https://localhost/pub/second/customer/account/

<u>Résultats attendus</u> :

Vous pouvez afficher les commandes à partir des deux vues de magasin sur la page Commandes . C’est le même magasin, juste une vue différente.

<u>Résultats réels</u> :

Le comportement est incohérent. Les commandes n’apparaissent pas dans la deuxième vue du magasin.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
