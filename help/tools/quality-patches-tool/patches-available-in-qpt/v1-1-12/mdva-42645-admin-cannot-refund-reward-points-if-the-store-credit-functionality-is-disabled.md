---
title: 'MDVA-42645 : l''administrateur ne peut pas rembourser les points de récompense pour le crédit de magasin désactivé'
description: Le correctif MDVA-42645 résout le problème où l’administrateur ne peut pas rembourser les points de récompense si la fonctionnalité de crédit de magasin est désactivée. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-42645. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
exl-id: 8053fcc7-d30c-424a-9494-df6e8630b095
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-42645 : l&#39;administrateur ne peut pas rembourser les points de récompense pour le crédit de magasin désactivé

Le correctif MDVA-42645 résout le problème où l’administrateur ne peut pas rembourser les points de récompense si la fonctionnalité de crédit de magasin est désactivée. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-42645. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’administrateur ne peut pas rembourser les points de récompense si la fonctionnalité de crédit de magasin est désactivée.

<u>Procédure à suivre </u> :

1. Créez un produit simple.
1. Créez un compte client et ajoutez des points de récompense.
1. Désactivez la fonctionnalité de crédit de la boutique en accédant à **Boutique** > Paramètres > **Configuration** > **Client** > **Configuration client** > **Options de crédit de la boutique**.
1. Connectez-vous en tant que client auquel les points de récompense sont attribués.
1. Ajoutez un produit au panier et accédez à la commande.
1. Utilisez les points de récompense dans la section de paiement et passez la commande.
1. Ouvrez la commande dans l’administrateur et facturez-la.
1. Cliquez sur le lien **Avoir** pour créer un avoir.
1. Cochez l’option Rembourser les points de récompense en bas de l’écran et cliquez sur **Rembourser hors ligne**.

<u>Résultats attendus</u> :

* L&#39;avoir a été créé.
* Les points de récompense sont remboursés avec succès.

<u>Résultats réels</u> :

Le message d’erreur suivant s’affiche : *Vous ne pouvez pas utiliser un crédit de magasin supérieur au montant de la commande.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
