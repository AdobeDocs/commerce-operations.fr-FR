---
title: "ACSD-48807 : révisions de produits non filtrées par storeview"
description: Appliquez le correctif ACSD-48807 pour résoudre le problème Adobe Commerce en raison duquel les révisions de produits ne sont pas filtrées par l’aperçu de magasin via GraphQL.
feature: Admin Workspace, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-48807 : Les révisions de produits ne sont pas filtrées par storeview

Le correctif ACSD-48807 corrige le problème en raison duquel les révisions de produits ne sont pas filtrées par l’aperçu de magasin via GraphQL. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28 est installé. L’ID de correctif est ACSD-48807. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les révisions de produit ne sont pas filtrées par storeview via GraphQL.

<u>Étapes à reproduire</u> :

1. Créez un autre storeview.
1. Créez un compte client et connectez-vous.
1. Dans l’affichage de magasin par défaut, créez une révision pour un produit.
1. Passez à une autre vue d’ensemble et créez une autre révision pour un produit.
1. Approuvez les deux révisions dans l’administrateur Adobe Commerce.
1. Envoyez une requête GraphQL client pour récupérer les révisions de produit lors de la spécification de l’aperçu de magasin créé à l’étape 1 dans l’en-tête .
1. Observez la réponse.

<u>Résultats attendus</u> :

Seule la révision de produit pour l’aperçu de magasin spécifié est renvoyée dans la réponse.

<u>Résultats réels</u> :

Les deux révisions sont renvoyées dans la réponse.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
