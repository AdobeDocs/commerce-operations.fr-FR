---
title: "ACSD-49433 : Montant par défaut affiché comme sous-total du panier pour la carte-cadeau"
description: Appliquez le correctif ACSD-49433 pour résoudre le problème Adobe Commerce en raison duquel le montant par défaut s’affiche comme sous-total dans le panier pour la carte cadeau avec un montant ouvert.
feature: Admin Workspace, Gift, Orders, Shopping Cart
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-49433 : Montant par défaut affiché comme sous-total dans le panier pour la carte-cadeau

Le correctif ACSD-49433 corrige le problème en raison duquel le montant par défaut s’affiche sous la forme d’un sous-total dans le panier pour la carte cadeau avec un montant ouvert. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28 est installé. L’ID de correctif est ACSD-49433. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le montant par défaut est présenté comme sous-total dans le panier pour la carte cadeau avec un montant ouvert.

<u>Étapes à reproduire</u> :

1. Créez une carte-cadeau.
1. Assurez-vous que le montant ouvert est défini sur *[!UICONTROL Yes]* (entre 50 et 500 $).
1. Accédez au produit [!UICONTROL Gift Card] sur le storefront et choisissez une autre quantité dans la liste déroulante.
1. Indiquez 100 $ en USD.
1. Renseignez les autres champs et ajoutez-les au panier.
1. Accédez à la page du mini-panier ou du panier.

<u>Résultats attendus</u> :

Le sous-total indique le montant saisi par l’utilisateur.

<u>Résultats réels</u> :

Le sous-total affiche le montant de la carte cadeau par défaut.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
