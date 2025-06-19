---
title: 'ACSD-54885 : exception lors de l’extraction de plusieurs adresses lorsque l’administrateur se connecte en tant que client'
description: Appliquez le correctif ACSD-54885 pour résoudre le problème d’Adobe Commerce en raison duquel une erreur se produit lors de l’extraction de plusieurs adresses lorsque l’administrateur utilise la fonctionnalité *[!UICONTROL Login as Customer]*.
feature: Checkout
role: Admin, Developer
exl-id: c146bc2a-2df1-4825-9cfc-69e04095b3c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-54885 : exception lors de l’extraction de plusieurs adresses lorsque l’administrateur se connecte en tant que client

Le correctif ACSD-54885 corrige le problème où une erreur se produit lors de l’extraction de plusieurs adresses lorsque l’administrateur utilise la fonctionnalité *[!UICONTROL Login as Customer]*. Ce correctif est disponible lorsque la version 1.1.43 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-54885. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur se produit lors de l’extraction de plusieurs adresses lorsque l’administrateur utilise la fonctionnalité *[!UICONTROL Login as Customer]*.

<u>Procédure à suivre </u> :

1. Assurez-vous que *[!UICONTROL Login as Customer]* est activé. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Advanced]** > **[!UICONTROL Admin]** > **[!UICONTROL Admin Actions]** > **[!UICONTROL Logging]** > **[!UICONTROL Login as Customer]**.
1. Créez un produit simple.
1. Créez un compte client avec une adresse.
1. Accédez au compte client sur le serveur principal :

   * Accédez à l’onglet **[!UICONTROL Account Information]** et définissez *[!UICONTROL Allow remote shopping assistance]* = *Oui*.
   * Cliquez sur **[!UICONTROL Login as Customer]**.

1. Ajoutez le produit au panier et passez à la *[!UICONTROL Checkout with multiple addresses]*.
1. Mettez à jour la quantité de produit.
1. Essayez de retourner au panier.

<u>Résultats attendus</u> :

Vous pouvez mettre à jour le panier et utiliser le passage en caisse à adresses multiples.

<u>Résultats réels</u> :

Vous obtenez l’erreur suivante lorsque vous revenez au panier.

```PHP
report.CRITICAL: Error: Call to a member function getCustomer() on null in magento2ee/app/code/Magento/LoginAsCustomerLogging/Observer/LogUpdateQtyObserver.php:88
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
