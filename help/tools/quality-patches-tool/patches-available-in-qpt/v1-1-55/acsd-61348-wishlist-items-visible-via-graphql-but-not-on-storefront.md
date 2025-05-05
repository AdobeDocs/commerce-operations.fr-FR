---
title: 'ACSD-61348 : Mise en liste blanche des éléments visibles via GraphQL mais pas sur le storefront'
description: Appliquez le correctif ACSD-61348 pour résoudre le problème Adobe Commerce en raison duquel les éléments de liste bloquée sont visibles via GraphQL, mais pas sur le storefront dans un environnement multi-site.
feature: Customers
role: Admin, Developer
source-git-commit: b3dcce33b5710cd3c4b835f5fc7fd8f16cdc6a7f
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-61348 : Mise en liste blanche des éléments visibles via GraphQL mais pas sur le storefront

Le correctif ACSD-61348 corrige le problème en raison duquel les éléments de liste bloquée sont visibles via GraphQL, mais pas sur le storefront dans un environnement multi-site web. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 est installé. L’ID de correctif est ACSD-61348. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p5

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les éléments de liste blanche sont visibles via GraphQL, mais pas sur le storefront dans un environnement multisite.

<u>Étapes à reproduire</u> :

1. Configurez deux sites web.
1. Accédez à **[!UICONTROL Config Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** et définissez **[!UICONTROL Share Customer Accounts]** sur *[!UICONTROL Global]*.
1. Accédez à **[!UICONTROL Config Customers]** > **[!UICONTROL Wishlist]** > **[!UICONTROL General Options]** et définissez **[!UICONTROL Enable Multiple Wish Lists]** sur *Oui*.
1. Accédez à **[!UICONTROL Config General]** > **[!UICONTROL Web]** et définissez **[!UICONTROL Add Store Code to URLs]** sur *Oui*.
1. Créez un produit simple et affectez-le au deuxième site web.
1. Créer un client et se connecter.
1. Ajoutez un produit à la liste des souhaits.
1. Affectez le produit au site web par défaut.
1. Accédez à la page *[!UICONTROL Wishlist]* du site web par défaut.

<u>Résultats attendus</u> :

Le produit figure sur la liste des souhaits.

<u>Résultats réels</u> :

Il n’y a aucun produit sur la liste des souhaits.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
