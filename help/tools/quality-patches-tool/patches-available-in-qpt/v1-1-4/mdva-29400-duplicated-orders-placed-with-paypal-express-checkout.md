---
title: 'MDVA-29400 : commandes dupliquées passées avec PayPal Express Checkout'
description: Le correctif MDVA-29400 résout le problème de création de commandes dupliquées lorsque les clients passent des commandes avec PayPal Express Checkout. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 est installé. L’ID du correctif est MDVA-29400. Notez que le problème a été résolu dans Adobe Commerce 2.4.1.
feature: Checkout, Orders, Payments
role: Admin
exl-id: 6f7291d3-d554-4e4e-a55d-89ea2b9dea33
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# MDVA-29400 : commandes dupliquées passées avec PayPal Express Checkout

Le correctif MDVA-29400 résout le problème de création de commandes dupliquées lorsque les clients passent des commandes avec PayPal Express Checkout. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 est installé. L’ID du correctif est MDVA-29400. Notez que le problème a été résolu dans Adobe Commerce 2.4.1.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les commandes en double sont créées lorsque les utilisateurs passent des commandes avec PayPal Express Checkout.

<u>Conditions préalables</u> :

Activation et configuration du paiement PayPal Express.

<u>Procédure à suivre </u> :

1. Ajoutez un produit au panier.
1. Accédez à la page de passage en caisse et utilisez PayPal Express comme mode de paiement.
1. Il sera redirigé vers la page paypal/express/review/ .
1. Passer une commande. Vous serez redirigé vers la page de succès.
1. Retournez sur la page PayPal/express/review/.
1. Cliquez sur le bouton **Passer une commande**.

<u>Résultats attendus</u> :

Une seule commande est créée.

<u>Résultats réels</u> :

Vous obtenez l&#39;erreur suivante : *le jeton de paiement PayPal Express n&#39;existe pas*, mais la deuxième commande a été passée avec succès.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
