---
title: 'ACSD-48694 : l''erreur de demande de changement d''état non valide empêche le client de passer commande'
description: Appliquez le correctif ACSD-48694 pour résoudre le problème d'Adobe Commerce où l'erreur *Invalid state change requested* empêche un client de passer une commande.
feature: Admin Workspace, Orders
role: Admin
exl-id: 6b9fa474-1d9d-411d-bbca-ce7463cfeb0d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# ACSD-48694 : *modification d’état non valide demandée* l’erreur empêche le client de passer une commande

Le correctif ACSD-48694 corrige le problème où l’erreur *modification d’état non valide demandée* empêche un client de passer une commande. Ce correctif est disponible lorsque la version 1.1.27 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48694. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.37-p4, 2.4.1 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’erreur *Changement d’état non valide demandé* empêche un client de passer une commande.

<u>Procédure à suivre </u> :

1. Ajoutez un léger retard pendant la demande de `/estimate-shipping-methods` en incluant une fonction `sleep()` à `app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()` , de sorte que la demande de `/estimate-shipping-methods` soit terminée après la `/shipping-information` lors du passage de l’étape d’expédition à l’étape de paiement lors du passage en caisse.
1. Configurez la session à utiliser [!DNL Redis] avec le paramètre *disable_lock: 1*.
1. Ouvrez **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** et activez *[!UICONTROL Persistent Shopping Cart]*.
1. Connectez-vous en tant que client et ajoutez un produit au panier.
1. Laissez la session du client expirer. Le cookie persistant et le panier persistent.
1. Accédez maintenant à Passer en caisse, ajoutez l’adresse de livraison et accédez à la section de paiement.
1. Revenez à la page d’accueil ou à toute autre page et connectez-vous avec le compte client.
1. Laissez la session expirer à nouveau.
1. Accédez maintenant directement à la page de passage en caisse et accédez à l’étape de paiement.
1. Essayez de passer la commande.

<u>Résultats attendus</u> :

* Il n’y a aucune erreur.
* La commande a été passée avec succès et une page *Merci* s’affiche.

<u>Résultats réels</u> :

L’erreur *Modification d’état non valide demandée* s’affiche, mais la commande est passée.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
