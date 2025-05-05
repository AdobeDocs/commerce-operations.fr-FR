---
title: 'MDVA-42326 : les clients reçoivent une erreur lors de l’extraction après le délai d’expiration de la session'
description: Le correctif MDVA-42326 résout le problème où les clients reçoivent une erreur lors de l’extraction après le délai d’expiration de la session, même si le panier persistant est activé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 est installé. L’ID de correctif est MDVA-42326. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
feature: Checkout, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# MDVA-42326 : les clients reçoivent une erreur lors de leur passage en caisse après expiration de la session.

Le correctif MDVA-42326 résout le problème où les clients reçoivent une erreur lors de l’extraction après le délai d’expiration de la session, même si le panier persistant est activé. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 est installé. L’ID de correctif est MDVA-42326. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les clients reçoivent une erreur lors de l’extraction après le délai d’expiration de la session, même si le panier persistant est activé.

<u>Conditions préalables</u> :

1. Accédez à **Config** > **Général** > **Web** > **Paramètres de cookie par défaut** > **Durée de vie du cookie** et définissez cette variable sur **120**.
1. Accédez à **Config** > **Customers** > **Configuration client** > **Options clients en ligne** et définissez les deux valeurs sur **2**.
1. Accédez à **Config** > **Customers** > **Panier persistant** et définissez-le sur **Activer**.
1. Accédez à **Config** > **Sales** > **payment Methods** et désactivez tous les modes de paiement sauf **Check/Money Order** (il doit être activé).

<u>Étapes à reproduire</u> :

1. Connectez-vous en tant que client et ajoutez des produits au panier.
1. Vérifiez le panier.
1. Patientez deux minutes (défini dans la condition préalable) ; la session doit expirer.
1. Cliquez sur **Atteindre l’extraction** et n’actualisez pas la page.
1. Passage en caisse en tant qu’invité, renseignez l’adresse de livraison et choisissez un mode de livraison.
1. Cliquez sur **Suivant**.
1. Sur la page **Révision et paiements**, cliquez sur **Passer commande**. Comme un seul mode de paiement est autorisé, le client doit pouvoir passer la commande sans sélectionner le mode de paiement.

<u>Résultats attendus</u> :

Le client doit pouvoir passer la commande.

<u>Résultats réels</u> :

Le client reçoit l’erreur suivante : *Échec de la validation de l’adresse : le format de l’email est incorrect*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
