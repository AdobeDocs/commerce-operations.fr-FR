---
title: 'ACSD-54264 : erreur lorsque le client tente de passer en caisse avec un devis négociable'
description: 'Appliquez le correctif ACSD-54264 pour résoudre le problème Adobe Commerce où un message d’erreur « Vous ne pouvez pas mettre à jour l’attribut demandé. « ID de ligne : id_magasin » s’affiche lorsqu’un client tente de passer en caisse avec un devis négociable provenant d’une autre vue de magasin.'
feature: B2B, Checkout
role: Admin, Developer
exl-id: b1696228-b2ed-44eb-9e75-bf25ccf2f1cd
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '467'
ht-degree: 0%
---
# ACSD-54264 : une erreur s&#39;affiche lorsque le client tente de payer avec un devis négociable

Le correctif ACSD-54264 corrige le problème où un message d’erreur *Vous ne pouvez pas mettre à jour l’attribut demandé. ID de ligne : store_id* s’affiche lorsqu’un client tente de passer en caisse avec un devis négociable provenant d’une autre vue de magasin. Ce correctif est disponible lorsque la version 1.1.42 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-54264. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Message d’erreur *Vous ne pouvez pas mettre à jour l’attribut demandé. ID de ligne : store_id* s’affiche lorsqu’un client tente de passer en caisse avec un devis négociable provenant d’une autre vue de magasin.

<u>Conditions préalables</u> :

Les modules B2B d’Adobe Commerce sont installés et activés.

<u>Procédure à suivre </u> :

1. Créez une vue de magasin supplémentaire pour le site web par défaut.
1. Activez la *[!UICONTROL B2B Quote]* dans la configuration.
1. Connectez-vous en tant que client d’entreprise dans l’une des vues de la boutique.
1. Ajoutez un produit au *[!UICONTROL Shopping Cart]*.
1. Soumettre le devis pour révision.
1. En tant qu’utilisateur administrateur, accédez à **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** et soumettez le devis approuvé.
1. En tant que client de la société, modifiez l’affichage du magasin en un affichage différent.
1. Essayez de quitter la chambre.

<u>Résultats attendus</u> :

Le client passe une commande avec ce devis.

<u>Résultats réels</u> :

* L’erreur se produit lors de l’enregistrement des informations d’expédition :

  `You cannot update the request attribute. Row ID: store_id =#`

* L’erreur suivante est consignée :

  `report.CRITICAL: Magento\Framework\Exception\InputException: You cannot update the requested attribute. Row ID: store_id = 2. in /app/code/Magento/NegotiableQuote/Plugin/Quote/Model/QuoteUpdateValidator.php:100`

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
