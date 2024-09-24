---
title: '''ACSD-49502 : le lien téléchargeable n''a pas été correctement mis à jour après [!DNL staging] update'''
description: Appliquez le correctif ACSD-49502 pour résoudre le problème Adobe Commerce en raison duquel le lien téléchargeable n’est pas correctement mis à jour après l’application d’une  [!DNL staging] mise à jour au produit téléchargeable.
feature: Staging
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-49502 : mise à jour incorrecte du lien téléchargeable après [!DNL staging]

Le correctif ACSD-49502 corrige le problème en raison duquel le lien téléchargeable n’est pas correctement mis à jour après l’application d’une mise à jour de [!DNL staging] au produit téléchargeable. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 est installé. L’ID de correctif est ACSD-49502. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le lien téléchargeable n’est pas mis à jour correctement après l’application d’une mise à jour de [!DNL staging] au produit téléchargeable.

<u>Étapes à reproduire</u> :

1. Créez un produit téléchargeable avec un ou plusieurs liens.
1. Créez un compte client et connectez-vous.
1. Ajoutez le produit téléchargeable au panier à partir du storefront.
1. Dans **[!UICONTROL Admin]**, planifiez une nouvelle mise à jour pour le produit téléchargeable et laissez la mise à jour planifiée s’achever.
1. Exécutez la commande sur le storefront.

<u>Résultats attendus</u> :

Les liens téléchargeables sont conservés lors de l’utilisation de mises à jour planifiées alors que les produits précédemment ajoutés sont dans le panier.

<u>Résultats réels</u> :

Il manque des liens téléchargeables sous les *[!UICONTROL My Account]* ([!UICONTROL My Downloadable Products]) du client et les pages d’affichage des commandes dans **[!UICONTROL Admin]**.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
