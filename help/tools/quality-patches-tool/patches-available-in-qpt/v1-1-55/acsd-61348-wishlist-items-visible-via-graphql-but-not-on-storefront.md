---
title: 'ACSD-61348 : éléments de liste de souhaits visibles via GraphQL mais pas sur storefront'
description: Appliquez le correctif ACSD-61348 pour résoudre le problème d’Adobe Commerce où les éléments de liste de souhaits sont visibles via GraphQL, mais pas sur le storefront dans un environnement multi-sites web.
feature: Customers
role: Admin, Developer
exl-id: fcba2c28-077d-4663-b129-7da436e2791d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-61348 : éléments de liste de souhaits visibles via GraphQL mais pas sur storefront

Le correctif ACSD-61348 corrige le problème où les éléments de liste de souhaits sont visibles via GraphQL, mais pas sur le storefront dans un environnement multi-sites web. Ce correctif est disponible lorsque la version 1.1.55 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-61348. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p5

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les éléments de liste de souhaits sont visibles via GraphQL, mais pas sur le storefront dans un environnement multi-site web.

<u>Procédure à suivre </u> :

1. Configurez deux sites web.
1. Accédez à **[!UICONTROL Config Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** et définissez **[!UICONTROL Share Customer Accounts]** sur *[!UICONTROL Global]*.
1. Accédez à **[!UICONTROL Config Customers]** > **[!UICONTROL Wishlist]** > **[!UICONTROL General Options]** et définissez **[!UICONTROL Enable Multiple Wish Lists]** sur *Oui*.
1. Accédez à **[!UICONTROL Config General]** > **[!UICONTROL Web]** et définissez **[!UICONTROL Add Store Code to URLs]** sur *Oui*.
1. Créez un produit simple et affectez-le au deuxième site web.
1. Créer un client et se connecter.
1. Ajouter un produit à la liste de souhaits.
1. Attribuez le produit au site web par défaut.
1. Accédez à la page *[!UICONTROL Wishlist]* du site web par défaut.

<u>Résultats attendus</u> :

Le produit est sur la liste de souhaits.

<u>Résultats réels</u> :

Aucun produit n&#39;est sur la liste de souhaits.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
