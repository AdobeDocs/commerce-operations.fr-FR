---
title: 'ACSD-47875 : impossible d''ajouter un produit au panier pour la portée d''affichage du magasin avec la gestion des stocks'
description: Appliquez le correctif ACSD-47875 pour résoudre le problème d’Adobe Commerce en raison duquel un produit ne peut pas être ajouté à un panier client par l’administrateur pour une portée d’affichage de magasin spécifique avec la gestion des stocks.
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
exl-id: 10862e09-d561-4ed5-ab6f-cf002fae6850
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
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
source-wordcount: '501'
ht-degree: 0%
---
# ACSD-47875 : impossible d&#39;ajouter un produit au panier pour la portée d&#39;affichage du magasin avec la gestion des stocks

Le correctif ACSD-47875 corrige le problème en raison duquel un produit ne peut pas être ajouté à un panier client à partir de l’administration pour une portée d’affichage de magasin particulière avec la gestion des stocks. Ce correctif est disponible lorsque la version 1.1.36 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-47875. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs administrateurs ne peuvent pas ajouter un produit à un panier client à l’aide de la fonctionnalité **[!UICONTROL Manage Shopping Cart]** dans l’administration pour une portée d’affichage de magasin particulière avec MSI installé.

<u>Conditions préalables</u> :

Les modules [!DNL Adobe Commerce Inventory Management (MSI)] sont installés et activés.

<u>Procédure à suivre </u> :

1. Créez un site web, un magasin et une vue de magasin.
1. Créez une source supplémentaire autre que *Par défaut*.
1. Créez un nouveau stock et affectez-le au nouveau site web et à la nouvelle source.
1. Créez un nouveau client pour le nouveau site web.
1. Affectez un produit au nouveau site web uniquement. Annulez l’affectation du site web par défaut.

   * Attribuez la nouvelle source et définissez Qté *supérieure à 0* pour la nouvelle source et *0* pour la source par défaut.

1. Accédez à la page **[!UICONTROL Customer Edit]** de l’Administration. Cliquez sur **[!UICONTROL Manage Shopping Cart]**.
1. Modifiez la portée de l’affichage du magasin en le remplaçant par le nouvel affichage du magasin.
1. Accédez à la section **[!UICONTROL Products]** et recherchez le produit.
1. Sélectionnez le produit et cliquez sur **[!UICONTROL Add selections to my cart]**.

<u>Résultats attendus</u> :

Le produit est ajouté au panier.

<u>Résultats réels</u> :

* L’erreur suivante est générée : *Le produit que vous essayez d’ajouter n’est pas disponible.*
* Le produit n’est pas ajouté au panier.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
