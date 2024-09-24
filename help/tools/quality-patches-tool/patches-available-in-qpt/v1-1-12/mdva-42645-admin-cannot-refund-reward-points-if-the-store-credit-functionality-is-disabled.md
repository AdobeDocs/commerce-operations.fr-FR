---
title: "MDVA-42645 : L'administrateur ne peut pas rembourser les points de récompense pour le crédit de magasin désactivé"
description: Le correctif MDVA-42645 résout le problème où l’administrateur ne peut pas rembourser les points de récompense si la fonctionnalité de crédit de magasin est désactivée. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID de correctif est MDVA-42645. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-42645 : L’administrateur ne peut pas rembourser les points de récompense pour le crédit de magasin désactivé

Le correctif MDVA-42645 résout le problème où l’administrateur ne peut pas rembourser les points de récompense si la fonctionnalité de crédit de magasin est désactivée. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID de correctif est MDVA-42645. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’administrateur ne peut pas rembourser les points de récompense si la fonctionnalité de crédit de magasin est désactivée.

<u>Étapes à reproduire</u> :

1. Créez un produit simple.
1. Créez un compte client et ajoutez des points de récompense.
1. Désactivez la fonctionnalité Stocker le crédit en accédant à **Magasin** > Paramètres > **Configuration** > **Client** > **Configuration client** > **Options de stockage du crédit**.
1. Connectez-vous en tant que client auquel les points de récompense sont attribués.
1. Ajoutez un produit au panier et accédez au passage en caisse.
1. Utilisez les points de récompense de la section paiement et passez votre commande.
1. Ouvrez la commande dans l&#39;administrateur et facturez-la.
1. Cliquez sur le lien **Avoir de crédit** pour créer un nouvel avoir.
1. Cochez l’option Rembourser les points de récompense en bas de l’écran et cliquez sur le bouton **Rembourser hors ligne**.

<u>Résultats attendus</u> :

* La note de crédit a été créée.
* Les points de récompense sont remboursés avec succès.

<u>Résultats réels</u> :

Le message d&#39;erreur suivant s&#39;affiche : *Vous ne pouvez pas utiliser plus de crédit de magasin que le montant de la commande.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
