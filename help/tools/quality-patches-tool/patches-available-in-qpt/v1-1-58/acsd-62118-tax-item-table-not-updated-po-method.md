---
title: 'ACSD-62118 : table « sales_order_tax_item » non entièrement mise à jour pour les commandes B2B passées à l’aide de la méthode [!UICONTROL Purchase Order]'
description: Appliquez le correctif ACSD-62118 pour résoudre le problème d’Adobe Commerce en raison duquel la table « sales_order_tax_item » n’est pas entièrement mise à jour lorsque des commandes B2B sont passées à l’aide de la méthode [!UICONTROL Purchase Order].
feature: Purchase Orders, B2B
role: Admin, Developer
source-git-commit: 5812b90fe07a084a1d3487784d0f36a2b7958286
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---


# ACSD-62118 : `sales_order_tax_item` table n&#39;est pas entièrement mise à jour pour les commandes B2B passées à l&#39;aide de la méthode [!UICONTROL Purchase Order]

Le correctif ACSD-62118 corrige le problème où la table `sales_order_tax_item` n’est pas entièrement mise à jour lorsqu’une commande B2B est passée à l’aide de la méthode *[!UICONTROL Purchase Order]*. Ce correctif est disponible lorsque la version 1.1.58 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62118. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque des commandes B2B sont passées à l’aide de la méthode *[!UICONTROL Purchase Order]*, la table `sales_order_tax_item` n’est pas entièrement mise à jour. Ce problème affecte les calculs de taxe et le traitement des commandes. Plus précisément, le tableau `applied_taxes` est vide lors de l’interrogation de la commande via l’API et les `tax_item_amount` et `tax_item_percent` sont NULL.

<u>Procédure à suivre </u> :

1. Ajoutez des règles fiscales pour **[!UICONTROL Product]** et **[!UICONTROL Shipping]**.
1. Activez la méthode **[!UICONTROL Purchase Order]** dans les paramètres d’entreprise.
1. Connectez-vous en tant qu’utilisateur administrateur d’entreprise.
1. Placez un **[!UICONTROL Purchase Order]** à l’aide d’un mode de paiement hors ligne.
1. Une fois la [!UICONTROL Purchase Order] approuvée automatiquement et convertie en commande, vérifiez les données de taxe dans la table `sales_order_tax_item` et via l’API REST.

<u>Résultats attendus</u> :

* La table `sales_order_tax_item` doit contenir des données `tax_item`.
* Le tableau `applied_taxes` doit afficher les informations fiscales correctes dans la réponse API pour les commandes fournisseur, comme pour d’autres méthodes de paiement (par exemple, chèque/mandat).

<u>Résultats réels</u> :

* Le tableau `sales_order_tax_item` ne contient aucune donnée `tax_item`.
* Les tableaux `applied_taxes` et `item_applied_taxes` sont vides dans la réponse API pour le *[!UICONTROL Purchase Order]*.
* Aucune donnée de taxe n&#39;est affichée lors de l&#39;utilisation du mode de paiement *[!UICONTROL Purchase Order]*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-Premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
