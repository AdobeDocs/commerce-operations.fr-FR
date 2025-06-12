---
title: 'ACSD-48044 : l''application de plusieurs cartes-cadeaux empêche de passer des commandes'
description: Appliquez le correctif ACSD-48044 pour résoudre le problème d'Adobe Commerce où l'application de plusieurs cartes-cadeaux à une seule commande avec expédition multiple empêche les commandes d'être passées.
feature: Admin Workspace, Gift, Orders
role: Admin
exl-id: c7b72b1f-2f1b-4445-b842-5847d05d5ae9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-48044 : l&#39;application de plusieurs cartes-cadeaux empêche de passer des commandes

Le correctif ACSD-48044 corrige le problème où l&#39;application de plusieurs cartes-cadeaux à une seule commande avec expédition multiple empêche de passer des commandes. Ce correctif est disponible lorsque la version 1.1.25 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48044. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’application de plusieurs cartes-cadeaux à une seule commande avec expédition multiple empêche le passage de commandes.

<u>Procédure à suivre </u> :

1. Installez une version propre d’Adobe Commerce.
1. Créez un produit simple au prix de 100 $ et un autre produit simple au prix de 10 $.
1. Connectez-vous au [!UICONTROL Admin panel] et créez deux cartes-cadeaux.

   * 02KB8M0H0GRD = 50 $
   * 00GXM6SUGBLW = 25 $

1. Créez un client avec deux adresses.
1. Ajoutez deux produits au panier.

   * Ajoutez d’abord le produit à 10 $, puis ajoutez le produit à 100 $. Le problème ne peut pas être reproduit si le produit de 100 $ est ajouté en premier.

1. Accédez au panier et ajoutez les deux cartes-cadeaux que vous avez créées.
1. Cliquez sur **[!UICONTROL Ship to Multiple Addresses]** dans la page du panier.
1. Attribuez chaque produit à une adresse différente.
1. Accédez à la page **[!UICONTROL Shipping information]** .
1. Accédez à la page **[!UICONTROL Billing information]** .
1. Accédez à la page **[!UICONTROL Review Your Order]**, où vous pouvez voir le problème.
1. Essayez de passer la commande.

<u>Résultats attendus</u> :

* Les cartes-cadeaux sont correctement appliquées au montant total.
* Les commandes sont passées.

<u>Résultats réels</u> :

Les montants des cartes-cadeaux sont mélangés avec une erreur *« Veuillez corriger le code de la carte-cadeau. »* lors de la commande.

* Premier produit :

   * Supprimer Carte Cadeau (00GXM6SUGBLW) - 15,00 $
   * Supprimer Carte Cadeau (02KB8M0H0GRD) - 0,00 $

* Deuxième produit :

   * Supprimer Carte Cadeau (00GXM6SUGBLW) - 25,00 $
   * Supprimer la carte-cadeau (02KB8M0H0GRD) - 35,00 $

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
