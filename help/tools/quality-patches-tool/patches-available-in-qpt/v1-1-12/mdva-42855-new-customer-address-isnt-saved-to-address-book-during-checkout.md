---
title: 'MDVA-42855 : la nouvelle adresse du client n’est pas enregistrée dans le carnet d’adresses lors du passage en caisse '
description: Le correctif MDVA-42855 corrige le problème en raison duquel la nouvelle adresse du client n’est pas enregistrée dans le carnet d’adresses lors du passage en caisse. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID de correctif est MDVA-42855. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# MDVA-42855 : La nouvelle adresse du client n’est pas enregistrée dans le carnet d’adresses lors du passage en caisse

Le correctif MDVA-42855 corrige le problème en raison duquel la nouvelle adresse du client n’est pas enregistrée dans le carnet d’adresses lors du passage en caisse. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID de correctif est MDVA-42855. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La nouvelle adresse du client n’est pas enregistrée dans le carnet d’adresses lors du passage en caisse.

<u>Étapes à reproduire</u> :

1. Créez un compte client et mettez à jour l’adresse de livraison et de facturation par défaut.
1. Ajoutez un produit au panier et accédez à la page de passage en caisse.
1. Sur l’expédition, cliquez sur **+ Nouvelle adresse**.
1. Saisissez votre nouvelle adresse et cochez la case **Enregistrer dans le carnet d’adresses** .
1. Sur paiement, cochez la case **Mon adresse de facturation et de livraison sont les mêmes** .
1. Placez la commande.
1. Vérifiez le carnet d&#39;adresses.

<u>Résultats attendus</u> :

La nouvelle adresse de livraison est enregistrée dans le carnet d’adresses.

<u>Résultats réels</u> :

La nouvelle adresse de livraison n’est pas enregistrée dans le carnet d’adresses.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
