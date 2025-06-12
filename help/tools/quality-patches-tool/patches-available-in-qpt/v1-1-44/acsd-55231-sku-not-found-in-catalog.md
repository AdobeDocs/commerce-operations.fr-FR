---
title: 'ACSD-55231 : erreur de SKU introuvable lors de l’utilisation de la fonctionnalité de commande rapide'
description: Appliquez le correctif ACSD-55231 pour résoudre le problème Adobe Commerce où vous obtenez l’erreur « Le SKU n’a pas été trouvé dans le catalogue » lors de la tentative d’ajout d’un produit au panier à l’aide de la fonctionnalité de commande rapide.
feature: Products, Checkout, B2B
role: Admin, Developer
exl-id: f0a04773-7395-4945-a72b-5a6a018bc94e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# ACSD-55231 : erreur de SKU introuvable lors de l’utilisation de la fonctionnalité de commande rapide

Le correctif ACSD-55231 corrige le problème en raison duquel le SKU n’a pas été trouvé dans l’erreur *catalogue* lors de l’ajout d’un produit au panier à l’aide de la fonctionnalité de commande rapide. Ce correctif est disponible lorsque la version 1.1.44 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-55231. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L *obtention du SKU est introuvable dans l’erreur* catalogue lors de la recherche de produits à ajouter au panier à l’aide de la fonctionnalité de commande rapide.

<u>Procédure à suivre </u> :

1. Installez Adobe Commerce avec les modules B2B.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** et définissez les éléments suivants :
   * **[!UICONTROL Enable company]** : *Oui*
   * **[!UICONTROL Enable Shared Catalog]** : *Oui*
   * **[!UICONTROL Enable Quick Order]** : *Oui*
1. Enregistrez la configuration ci-dessus.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** et créez un catalogue partagé.
1. Accédez à **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** et créez un nouveau client :
   * Dans le champ de groupe, sélectionnez le catalogue partagé récemment créé et définissez *[!UICONTROL Allow remote shopping assistance]* sur *Oui*.
1. Générez un produit simple avec le SKU *p12*, associez-le à la catégorie *c1*, puis optez pour le catalogue partagé nouvellement créé dans la section [!UICONTROL Product in Shared Catalog].
1. Exécuter :

   ```
   bin/magento ind:rei 
   bin/magento c:f 
   bin/magento cron:run (multiple times)
   ```

1. Actualisez la page d’administration.
1. Accédez à **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** et modifiez le client créé précédemment.
1. Cliquez sur **[!UICONTROL Login as customer]**.
1. Accédez à **[!UICONTROL Quick order]**.
1. Recherchez le SKU *p12* et cliquez sur le **[!UICONTROL Product Suggestion]**.
1. Ajoutez ce produit au panier et passez la commande.
1. Revenez à **[!UICONTROL Quick Order]**, recherchez à nouveau SKU *p12*, puis cliquez sur **[!UICONTROL Product Suggestion]**.

<u>Résultats attendus</u> :

Vous pouvez ajouter le produit au panier à l’aide de la fonctionnalité de commande rapide.

<u>Résultats réels</u> :

Vous ne pouvez pas ajouter le produit au panier à l’aide de la fonctionnalité de commande rapide et obtenir *’Le SKU est introuvable dans l’erreur* catalogue lors de la recherche du SKU du produit.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
