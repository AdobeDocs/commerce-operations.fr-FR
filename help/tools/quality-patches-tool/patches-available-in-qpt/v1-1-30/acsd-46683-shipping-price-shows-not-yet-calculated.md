---
title: 'ACSD-46683 : Affichage des prix d''expédition *Pas encore calculé*'
description: Appliquez le correctif ACSD-46683 pour résoudre le problème d’Adobe Commerce où le prix d’expédition indique *Pas encore calculé*.
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
exl-id: ebd79187-2835-403b-945d-80ac34d6fb9c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# ACSD-46683 : Le prix d&#39;expédition indique *Pas encore calculé*

Le correctif ACSD-46683 corrige le problème où le prix d’expédition indique *Pas encore calculé*. Ce correctif est disponible lorsque la version 1.1.30 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-46683. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le prix d’expédition indique *Pas encore calculé*.

<u>Conditions préalables</u> :

Les modules Adobe Commerce Inventory management (MSI) sont installés.

<u>Procédure à suivre </u> :

1. Créez un produit simple et fixez son prix à 34 *de*.
1. Configurez la méthode de livraison gratuite.
1. Configurez au moins une autre méthode de diffusion.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** et créez une règle :
   * Nom = *75more*
   * Coupon = Aucun
   * Priorité = 1
   * Conditions : le sous-total est égal ou supérieur à *$75*
   * Actions :
      * Appliquer au montant d&#39;expédition = Oui
      * Ignorer les règles suivantes = Non
      * Livraison gratuite = pour les envois avec articles correspondants
1. Créez une autre règle de prix de panier :
   * Nom = *35off*
   * Priorité = 0
   * Coupon = Coupon Spécifique
   * Code de coupon = 35off
   * Actions :
      * Appliquer = pourcentage de la remise sur le prix du produit
      * Montant de remise = 35
      * Appliquer au montant d&#39;expédition = Non
      * Ignorer les règles suivantes = Oui
      * Livraison gratuite = Non
1. Ouvrez le storefront et ajoutez trois produits au panier afin que le sous-total dépasse 75 $.
1. Passez en caisse en tant qu’invité.
1. À l’étape d’expédition, sélectionnez **0 $ - expédition gratuite** puis passez à l’étape de paiement.
1. Vérifiez les [!UICONTROL Order Summary] de l’étape de paiement. Ça montre *[!UICONTROL $0 - Free Shipping - Free]*.
1. Appliquez le code de coupon *35off*, il mettra à jour le sous-total et le rendra inférieur à 75 $.
1. Vérifiez les [!UICONTROL Order Summary] de l’étape de paiement.

<u>Résultats attendus</u> :

Le message suivant s’affiche : *Le mode d’expédition sélectionné n’est pas disponible. Veuillez sélectionner un autre mode d&#39;expédition pour cette commande.*

<u>Résultats réels</u> :

Le prix d’expédition s’affiche *Pas encore calculé*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
