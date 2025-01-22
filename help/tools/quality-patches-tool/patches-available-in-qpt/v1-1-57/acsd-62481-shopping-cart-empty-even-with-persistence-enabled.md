---
title: 'ACSD-62481 : le panier reste vide même si le [!UICONTROL Persistence] est activé'
description: Appliquez le correctif ACSD-62481 pour résoudre le problème d’Adobe Commerce en raison duquel la fonction de panier persistante échoue lors de l’utilisation du pop-up de connexion lors du passage en caisse.
feature: Shopping Cart, Checkout
role: Admin, Developer
source-git-commit: 27a98c42f2c514b3dd1a2f59c140b60b7ac26592
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---


# ACSD-62481 : le panier reste vide même si le *[!UICONTROL Persistence]* est activé

Le correctif ACSD-62481 corrige le problème d’échec de la fonctionnalité de panier persistante lors de l’utilisation du pop-up de connexion lors du passage en caisse, car il ne comporte pas la case à cocher *[!UICONTROL Remember Me]*, ce qui entraîne la disparition des produits du panier après la déconnexion. Ce correctif est disponible lorsque la version 1.1.57 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62481. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La fonctionnalité de panier persistant échoue lors de l’utilisation du pop-up de connexion lors du passage en caisse, car il lui manque la case à cocher *[!UICONTROL Remember Me]*. Cela entraîne la disparition des produits du panier après la déconnexion.

<u>Procédure à suivre </u> :

1. Dans l’administration, configurez le compte invité et les paramètres persistants du panier comme suit :

   * Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** et définissez *[!UICONTROL Allow Guest Checkout]* sur *Non*.

      * Cliquez sur **[!UICONTROL Save Config]**.

   * Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** > **[!UICONTROL General Options]** et définissez *[!UICONTROL Enable Persistence]* sur *Oui*.
   * Laissez tous les autres paramètres par défaut, mais remplacez *[!UICONTROL Clear Persistence on Sign Out]* par *Non*.

      * Cliquez sur **[!UICONTROL Save Config]**.

1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add product]** pour ajouter un produit simple au catalogue.

   * Renseignez les informations minimales requises et assurez-vous qu’elles sont en stock.

1. Sur le front-end, créez un compte client à l’aide du formulaire principal `(../customer/account/create/)` et déconnectez-vous.
1. Ajoutez le produit au panier en tant qu’invité.
1. Ouvrez le mini-panier avec l’icône en haut à droite, puis cliquez sur **[!UICONTROL View and Edit Cart]**.
1. Passer en caisse.
1. Connectez-vous au nouveau compte client à l’aide de la boîte de dialogue pop-up qui s’affiche et déconnectez-vous.

<u>Résultats attendus</u> :

Le panier conserve les produits de l’utilisateur précédemment connecté.

<u>Résultats réels</u> :

* Le panier est vide.
* La boîte de dialogue de connexion pop-up n’affiche pas l’option *[!UICONTROL Remember Me]*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-Premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : mises à niveau et correctifs > Appliquer des correctifs dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
