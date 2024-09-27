---
title: "ACSD-56280 : les achats du registre des cadeaux ne sont pas terminés"
description: Appliquez le correctif ACSD-56280 pour résoudre le problème Adobe Commerce où les achats du registre des cadeaux ne sont pas terminés.
feature: Checkout
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-56280 : les achats du registre des cadeaux ne sont pas terminés

Le correctif ACSD-56280 corrige le problème lorsque les achats du registre des cadeaux ne sont pas terminés. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44 est installé. L’ID de correctif est ACSD-56280. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les achats effectués dans le registre des cadeaux ne sont pas terminés.

<u>Étapes à reproduire</u> :

1. Connectez-vous en tant que client et ajoutez un **[!UICONTROL product]** au registre des cadeaux.
1. Partagez le lien du registre des cadeaux.
1. Ouvrez le lien du registre des cadeaux dans une autre fenêtre de navigateur/incognito.
1. Ajoutez la quantité et ajoutez les éléments au panier.
1. Accédez à **[!UICONTROL Checkout Page]**, sélectionnez **[!UICONTROL shipping method]** (L’adresse de livraison étant déjà sélectionnée, fournie par l’inscrit).
1. Sélectionnez le mode de paiement.
1. Cliquez sur le bouton Passer commande .

<u>Résultats attendus</u> :

La commande doit être passée.

<u>Résultats réels</u> :

La commande n’est pas placée et l’erreur affichée est `Call to a member function getUpdatedQty() on null`.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
