---
title: 'ACSD-54887 : le panier client est effacé une fois la session du client expirée.'
description: Appliquez le correctif ACSD-54887 pour résoudre le problème Adobe Commerce en raison duquel le panier du client est effacé une fois la session du client expirée avec [!UICONTROL Persistent Shopping Cart] activé.
feature: Shopping Cart
role: Admin, Developer
exl-id: de2a96b2-48ce-4b9b-93bc-f7b64c37463a
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-54887 : le panier client est effacé une fois la session du client expirée.

Le correctif ACSD-54887 corrige le problème en raison duquel le panier du client est effacé une fois la session du client expirée avec [!UICONTROL Persistent Shopping Cart] activé. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 est installé. L’ID de correctif est ACSD-54887. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p8, 2.4.5-p3 - 2.4.5-p7 et 2.4.6-p1 - 2.4.6-p5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le panier client est effacé une fois la session client expirée avec [!UICONTROL Persistent Shopping Cart] activé.

<u>Étapes à reproduire</u> :

1. Activez [!UICONTROL Persistent Shopping Cart]. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** = *Oui*.

   Connectez-vous avec la persistance activée (Remarque : elle n’est pas disponible sur l’autorisation contextuelle, mais uniquement sur la page [!UICONTROL Sign in] directe).

1. Ajoutez un produit au panier.
1. Passez à la caisse et sélectionnez un mode de paiement.
1. Expire la session (supprimer `PHPSESSID`).
1. Actualisez la page. Notez que le guillemet est immédiatement converti en guillemet invité, car un mode de paiement est déjà sélectionné et le cookie [!UICONTROL Persistent Cart] est supprimé.
1. Expire la session (supprimer `PHPSESSID`).
1. Actualisez la page. Vérifiez que le panier est vide.
1. Connectez-vous à nouveau.

<u>Résultats attendus</u> :

Le panier contient le produit lorsque vous vous reconnectez.

<u>Résultats réels</u> :

Le panier est vide lors de la reconnexion.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
