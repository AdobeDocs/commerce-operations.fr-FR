---
title: '"ACSD-59786 : GraphQL renvoie une erreur lors de la récupération d’un "guillemet_id" pour un guillemet expiré"'
description: Appliquez le correctif ACSD-59786 pour résoudre le problème Adobe Commerce en raison duquel une requête GraphQL renvoie une erreur lors de la récupération d’un guillemet_apostrophe pour un guillemet expiré.
feature: GraphQL, Quotes, Companies
role: Admin, Developer
source-git-commit: fec2ee4a047d8b33fa1cb3b2c4d9364f925fa028
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-59786 : GraphQL renvoie une erreur lors de la récupération d’un `quote_id` pour un guillemet expiré

Le correctif ACSD-59786 corrige le problème en raison duquel une requête GraphQL renvoie une erreur lors de la récupération d’un `quote_id` pour un guillemet expiré. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51 est installé. L’ID de correctif est ACSD-59786. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une requête GraphQL renvoie une erreur lors de la récupération d’un `quote_id` pour un guillemet expiré.

<u>Étapes à reproduire</u> :

1. Activez **[!UICONTROL Companies]** et **[!UICONTROL Purchase Orders]**.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** et définissez **[!UICONTROL Enable Company]** sur *Oui*.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** > **[!UICONTROL Order Approval Configuration]** et définissez **[!UICONTROL Enable Purchase Orders]** sur *Yes*.
1. Créez une nouvelle société et définissez **[!UICONTROL Enable Purchase Orders]** sur *Yes* pour la même.
1. Créez un produit simple et affectez-le à une catégorie.
1. Connectez-vous à Storefront à l’aide du compte administrateur de la société et créez une commande en utilisant **[!UICONTROL Purchase Order]** comme méthode de paiement.
1. Modifiez le **[!UICONTROL Quote Lifetime (days)]**.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Shopping Cart]** > **[!UICONTROL Quote Lifetime (days)]** = *0*.
1. Exécutez la commande `bin/magento c:f`.
1. Accédez à la base de données `quote_table` et modifiez les valeurs `created_at` et `updated_at` avec un jour dans le passé.
1. Exécutez la commande `bin/magento cron:run --group="sales_clean_quotes`.
1. Exécutez la requête GraphQL donnée ci-dessous à l’aide d’un jeton autorisé pour l’administrateur qui crée le **[!UICONTROL Purchase Order]** :

   ```GraphQL
   {
       customer {
           purchase_order(uid: "MQ==") {
               quote {
                   id
               }
           }
       }
   } 
   ```

<u>Résultats attendus</u> :

La requête GraphQL renvoie le `quote_id`.

<u>Résultats réels</u> :

La requête GraphQL renvoie une erreur de serveur interne.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
