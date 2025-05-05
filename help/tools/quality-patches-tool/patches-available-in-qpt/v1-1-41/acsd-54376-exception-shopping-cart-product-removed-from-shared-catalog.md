---
title: 'ACSD-54376 : exception dans le panier lorsque le produit est supprimé de [!UICONTROL shared catalog]'
description: Appliquez le correctif ACSD-54376 pour résoudre le problème Adobe Commerce en raison duquel une exception se produit dans le panier lorsqu’un produit est supprimé de l’ [!UICONTROL shared catalog] après avoir été ajouté au panier.
feature: Shopping Cart, B2B
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-54376 : exception dans le panier lorsque le produit est supprimé de [!UICONTROL shared catalog]

Le correctif ACSD-54376 corrige le problème lorsqu’une exception se produit dans le panier lorsqu’un produit est supprimé du [!UICONTROL shared catalog] après avoir été ajouté au panier. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41 est installé. L’ID de correctif est ACSD-54376. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une exception se produit dans le panier lorsqu’un produit est supprimé de [!UICONTROL shared catalog] après avoir été ajouté au panier.

<u>Étapes à reproduire</u> :

1. Installez Adobe Commerce avec B2B.
1. Activez [!UICONTROL shared catalog].
1. Créez un produit et affectez-le à la valeur par défaut [!UICONTROL shared catalog].
1. Ajoutez un produit au panier à partir du storefront.
1. Supprimez le produit du [!UICONTROL shared catalog].
1. Accédez à la page de passage en caisse à l’aide de la liste déroulante des mini-paniers.

<u>Résultats attendus</u> :

Les exceptions sont gérées et ne s’affichent pas.

<u>Résultats réels</u> :

Une exception non gérée s’affiche sur la page de passage en caisse.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
