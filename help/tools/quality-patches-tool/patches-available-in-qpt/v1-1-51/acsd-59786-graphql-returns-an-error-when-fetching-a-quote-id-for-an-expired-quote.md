---
title: 'ACSD-59786 : GraphQL renvoie une erreur lors de la récupération d’un « quote_id » pour un devis expiré'
description: Appliquez le correctif ACSD-59786 pour résoudre le problème d’Adobe Commerce où une requête GraphQL renvoie une erreur lors de la récupération d’un « quote_id » pour un devis expiré.
feature: GraphQL, Quotes, Companies
role: Admin, Developer
exl-id: 3c7aaa99-a2e0-44fe-9426-b24095615915
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-59786 : GraphQL renvoie une erreur lors de la récupération d’un `quote_id` pour un devis expiré

Le correctif ACSD-59786 corrige le problème où une requête GraphQL renvoie une erreur lors de la récupération d’un `quote_id` pour un devis expiré. Ce correctif est disponible lorsque la version 1.1.51 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-59786. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une requête GraphQL renvoie une erreur lors de la récupération d’un `quote_id` pour un devis expiré.

<u>Procédure à suivre </u> :

1. Activez **[!UICONTROL Companies]** et **[!UICONTROL Purchase Orders]**.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** et définissez **[!UICONTROL Enable Company]** sur *Oui*.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** > **[!UICONTROL Order Approval Configuration]** et définissez **[!UICONTROL Enable Purchase Orders]** sur *Oui*.
1. Créez une nouvelle société et définissez **[!UICONTROL Enable Purchase Orders]** sur *Oui* pour la même raison.
1. Créez un produit simple et affectez-le à une catégorie.
1. Connectez-vous à Storefront à l&#39;aide du compte administrateur de la société et créez une commande en utilisant **[!UICONTROL Purchase Order]** comme mode de paiement.
1. Modifiez la **[!UICONTROL Quote Lifetime (days)]**.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Shopping Cart]** > **[!UICONTROL Quote Lifetime (days)]** = *0*.
1. Exécutez la `bin/magento c:f` de commande.
1. Accédez à la `quote_table` de la base de données et modifiez les valeurs `created_at` et `updated_at` avec un jour dans le passé.
1. Exécutez la `bin/magento cron:run --group="sales_clean_quotes` de commande.
1. Exécutez la requête GraphQL donnée ci-dessous à l’aide d’un jeton autorisé pour l’administrateur qui crée la **[!UICONTROL Purchase Order]** :

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

La requête GraphQL renvoie la `quote_id`.

<u>Résultats réels</u> :

La requête GraphQL renvoie une erreur de serveur interne.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
