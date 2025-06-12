---
title: 'ACSD-54264 : erreur lorsque le client tente de passer en caisse avec un devis négociable'
description: 'Appliquez le correctif ACSD-54264 pour résoudre le problème Adobe Commerce où un message d’erreur « Vous ne pouvez pas mettre à jour l’attribut demandé. « ID de ligne : id_magasin » s’affiche lorsqu’un client tente de passer en caisse avec un devis négociable provenant d’une autre vue de magasin.'
feature: B2B, Checkout
role: Admin, Developer
exl-id: b1696228-b2ed-44eb-9e75-bf25ccf2f1cd
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-54264 : une erreur s&#39;affiche lorsque le client tente de payer avec un devis négociable

Le correctif ACSD-54264 corrige le problème où un message d’erreur *Vous ne pouvez pas mettre à jour l’attribut demandé. ID de ligne : store_id* s’affiche lorsqu’un client tente de passer en caisse avec un devis négociable provenant d’une autre vue de magasin. Ce correctif est disponible lorsque la version 1.1.42 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-54264. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

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
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
