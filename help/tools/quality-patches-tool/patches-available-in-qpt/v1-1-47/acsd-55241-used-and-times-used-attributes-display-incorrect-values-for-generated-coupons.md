---
title: 'ACSD-55241 : les attributs **Used** et **Times Used** affichent des valeurs incorrectes pour les coupons générés'
description: Appliquez le correctif ACSD-55241 pour résoudre le problème d’Adobe Commerce où les attributs **Used** et **Times Used** affichent des valeurs incorrectes pour les coupons générés
feature: Price Rules
role: Admin, Developer
exl-id: a156f03c-c939-4ea7-bd34-03c2234edbff
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# ACSD-55241 : les attributs **Used** et **Times Used** affichent des valeurs incorrectes pour les coupons générés

Le correctif ACSD-55241 corrige le problème où les attributs **Used** et **Times Used** affichent des valeurs incorrectes pour les coupons générés. Ce correctif est disponible lorsque la version 1.1.47 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-55241. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les attributs **Used** et **Times Used** affichent des valeurs incorrectes pour les coupons générés.

<u>Procédure à suivre </u> :

1. Créez des **[!UICONTROL Cart Price Rules]** à partir de **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]** et ajoutez toute condition correspondant lors d’une commande (exemple : sous-total supérieur à *5$*)

   * Appliquez une remise.
   * Sélectionnez **[!UICONTROL Auto Coupon]**.
   * Il générera quelques codes de coupon à partir de **Gérer les codes de coupon**.
   * Réindexez et nettoyez le cache.

1. Créez un **[!UICONTROL customer account]** et connectez-vous au serveur frontal.
1. Ajoutez un produit avec plus de 2 ** de quantités dans le panier et appliquez un coupon.
1. Cliquez sur **[!UICONTROL Check Out with Multiple Addresses]**.
1. Sélectionnez une adresse distincte pour chaque quantité, passez la commande et terminez le processus de passage en caisse.
1. Observez le total des commandes de l’administrateur et la remise appliquée.
1. Passer une autre commande avec un autre coupon.
1. Exécutez la commande `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` pour mettre à jour l’utilisation du code de coupon.

<u>Résultats attendus</u> :

Le nombre correct doit être affiché dans les colonnes **Durée d’utilisation** et **Utilisé** avec la valeur **Oui** pour **[!UICONTROL manage coupon]** dans le **[!UICONTROL cart price rule]** de l’administrateur.

<u>Résultats réels</u> :

Le nombre de codes coupon utilisés n’est pas mis à jour dans la colonne **Temps utilisé** de la grille des coupons, et la colonne **Utilisé** affiche la valeur *Non* si vous passez une commande avec plusieurs adresses de livraison.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
