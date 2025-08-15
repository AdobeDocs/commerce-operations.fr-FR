---
title: 'ACSD-65822 : les quantités de produits groupés et configurables ne sont pas correctement reflétées dans le panier'
description: Appliquez le correctif ACSD-65822 pour résoudre le problème d’Adobe Commerce où la quantité apparaissait comme 0 dans la section du panier du client dans le panneau d’administration lors de l’ajout de produits groupés.
feature: Admin Workspace, Checkout, Orders
role: Admin, Developer
exl-id: 6740b5a6-8710-458c-abe4-03d2a8a694c5
source-git-commit: 7e9598e3ac0558706ef98ca81c19d27c37f7e860
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-65822 : les quantités de produits groupés et configurables ne sont pas correctement reflétées dans le [!UICONTROL Shopping Cart]

Le correctif ACSD-65822 corrige le problème où le lot et les quantités de produits configurables ne s’affichent pas correctement dans la section **[!UICONTROL Shopping Cart]** sous *[!UICONTROL Customer's Activities]*. Ce correctif est disponible lorsque la version 1.1.65 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-65822. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le lot et les quantités de produits configurables ne s&#39;affichent pas correctement dans la section **[!UICONTROL Shopping Cart]** sous *[!UICONTROL Customer's Activities]*.

<u>Procédure à suivre </u> :

1. Créez un utilisateur sur le storefront.
2. Créez un **[!UICONTROL Bundle product]** dans le panneau d’administration.
3. Sur le storefront, en tant qu’utilisateur connecté, ajoutez le produit groupé au panier avec une quantité spécifiée.
4. Dans le panneau *Admin*, accédez à **[!UICONTROL Customers]** et cliquez sur **[!UICONTROL Edit]** pour le client créé à l’étape 1.
5. Cliquez sur **[!UICONTROL Create Order]**.
6. Sur le côté gauche, sous *[!UICONTROL Customer's Activities]*, vérifiez la section **[!UICONTROL Shopping Cart]** . Vous devriez voir le produit groupé avec la quantité sélectionnée.

<u>Résultats attendus</u> :

La quantité de l&#39;article groupé doit correspondre à la quantité affichée sur le storefront.

<u>Résultats réels</u> :

La quantité d&#39;article groupé s&#39;affiche sous la forme 0.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
