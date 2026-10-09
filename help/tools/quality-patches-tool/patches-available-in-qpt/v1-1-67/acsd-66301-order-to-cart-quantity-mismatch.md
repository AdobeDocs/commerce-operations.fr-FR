---
title: 'ACSD-66301 : le déplacement de produits d’une commande vers le panier dans Commerce Admin entraîne une incohérence de la quantité'
description: Appliquez le correctif ACSD-66301 pour résoudre le problème d’Adobe Commerce en raison duquel, lors de la création d’une commande à partir du panneau d’administration, les produits du panier du client ne sont pas supprimés après avoir été ajoutés à la commande.
feature: Orders, Products
role: Admin, Developer
type: Troubleshooting
exl-id: 61e0e491-b2dc-4ae0-807e-2ae80d17f9c2
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
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
source-wordcount: '423'
ht-degree: 0%
---
# ACSD-66301 : le retour des produits d’une commande au panier dans l’administration Commerce entraîne une incohérence de la quantité

Le correctif ACSD-66301 corrige le problème en raison duquel le déplacement de produits d’une commande vers le panier dans l’administration entraîne une incohérence de la quantité. Ce correctif est disponible lorsque la version 1.1.67 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66301. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p10, 2.4.7-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p9 - 2.4.6-p11, 2.4.7-p4 - 2.4.7-p6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le déplacement de produits d’une commande vers le panier dans l’administration Commerce entraîne une incohérence de la quantité.

<u>Procédure à suivre </u> :

1. Créez un utilisateur via le storefront.
2. Ajoutez un produit au panier avec une quantité = *5*.
3. Accédez au panneau d’administration et ouvrez le compte utilisateur auquel le produit a été ajouté.
4. Cliquez sur **[!UICONTROL Create Order]**.
5. Dans le panneau de gauche, vous pouvez afficher les activités du client, y compris le produit et la quantité ajoutée.
6. Ajoutez le produit à la commande.
7. Mettez à jour la quantité = *4* dans la section de commande principale.
8. Cliquez sur **[!UICONTROL Update Items and Quantities]** bouton.
9. Transférer les articles sélectionnés de la commande vers le panier du client.

<u>Résultats attendus</u> :

Produit ajouté au panier avec la nouvelle quantité = *4*.

<u>Résultats réels</u> :

Produit ajouté au panier avec l’ancienne quantité = *5*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
