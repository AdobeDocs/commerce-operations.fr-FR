---
title: 'ACSD-45754 : points de récompense non ajoutés après l’application du coupon au panier'
description: Le correctif ACSD-45754 résout le problème où les points de récompense ne sont pas ajoutés après l’application d’un coupon au panier. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18 est installé. L’ID du correctif est ACSD-45754. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.
feature: Orders, Rewards, Shopping Cart
role: Admin
exl-id: 02f3bfc4-440b-4d77-adf5-0824d1b21073
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-45754 : points de récompense non ajoutés après l’application du coupon au panier

Le correctif ACSD-45754 résout le problème où les points de récompense ne sont pas ajoutés après l’application d’un coupon au panier. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) version 1.1.18 est installé. L’ID du correctif est ACSD-45754. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.1 - 2.4.5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les points de récompense ne sont pas ajoutés après l’application d’un coupon au panier.

<u>Conditions préalables</u> :

Le mode de paiement PayPal est configuré.

<u>Procédure à suivre </u> :

1. Créez des taux de change de points de récompense en accédant à **Boutique** > **Autres paramètres** > **Taux de change de récompense**.
1. Créez une règle de prix de panier avec un code de coupon pour appliquer 100 points de récompense aux clients connectés.
1. Découvrez un produit en tant que client connecté avec PayPal et le code de coupon.
1. Vérifiez l’historique des points de récompense sous le compte client dans l’administrateur.

<u>Résultats attendus</u> :

Les points de récompense sont ajoutés au client selon la règle de prix.

<u>Résultats réels</u> :

Aucun point de récompense n’est ajouté au client.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
