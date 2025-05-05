---
title: '''MDVA-39153 : le montant de la remise est mal calculé lors d''une réorganisation dans l''administrateur'''
description: Le correctif MDVA-39153 corrige le problème en raison duquel le montant de la remise est mal calculé lors d’une réorganisation dans l’Admin. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 est installé. L’ID de correctif est MDVA-39153. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
feature: Admin Workspace, Orders, Personalization, Payments
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39153 : Le montant de la remise est mal calculé lors d&#39;un réorganisation dans l&#39;Admin

Le correctif MDVA-39153 corrige le problème en raison duquel le montant de la remise est mal calculé lors d’une réorganisation dans l’Admin. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 est installé. L’ID de correctif est MDVA-39153. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le montant de la remise est mal calculé lors d&#39;un nouvel ordre dans l&#39;Admin.

<u>Étapes à reproduire</u> :

1. Accédez à **Admin** > **Magasins** > **Configuration** > **Ventes** > **Taxes**.
1. Activez la taxe pour l’expédition affichant la taxe dans le panier.
1. Activez et configurez la méthode d’expédition Taux de tableau (15 $).
1. Créez une règle de taxe pour le taux de taxe intégré (pour CA).
1. Créez une règle de prix de panier avec une remise fixe de 5 $ appliquée à l’ensemble du panier et du montant d’expédition.
1. Ajoutez un produit au prix de 12 € au panier et accédez à la page Panier.
1. Appliquez la remise au panier.
1. Définissez le mode de livraison dans la section &quot;Estimations&quot; sur &quot;Taux plat&quot;.
1. Passez en caisse jusqu’aux étapes de révision (ne pas passer la commande).
1. Accédez à la page d’accueil, puis revenez au panier.
1. Remplacez le mode de livraison dans la section &quot;Estimations&quot; par &quot;Taux de la table&quot;.

<u>Résultats attendus</u> :

La remise reste la même : 5 $.

<u>Résultats réels</u> :

La remise est de 6,31 $.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
