---
title: 'ACSD-49433 : Montant par défaut affiché comme sous-total dans le panier pour la carte cadeau.'
description: Appliquez le correctif ACSD-49433 pour résoudre le problème d’Adobe Commerce où le montant par défaut est affiché comme sous-total dans le panier pour la carte cadeau avec un montant ouvert.
feature: Admin Workspace, Gift, Orders, Shopping Cart
role: Admin
exl-id: 22691e35-0491-4935-8e7c-148900706491
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-49433 : montant par défaut affiché comme sous-total dans le panier pour la carte cadeau

Le correctif ACSD-49433 corrige le problème où le montant par défaut est affiché comme sous-total dans le panier pour la carte cadeau avec un montant ouvert. Ce correctif est disponible lorsque la version 1.1.28 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-49433. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le montant par défaut est affiché comme sous-total dans le panier pour la carte cadeau avec un montant ouvert.

<u>Procédure à suivre </u> :

1. Créez une carte cadeau.
1. Assurez-vous que le montant ouvert est défini sur *[!UICONTROL Yes]* (entre 50 $ et 500 $).
1. Accédez au produit [!UICONTROL Gift Card] sur le storefront et choisissez un autre montant dans la liste déroulante.
1. Indiquez 100 $ dans le montant en USD.
1. Renseignez d’autres champs et ajoutez-les au panier.
1. Accédez à la page du mini-panier ou du panier.

<u>Résultats attendus</u> :

Le sous-total affiche le montant saisi par l’utilisateur.

<u>Résultats réels</u> :

Le sous-total affiche le montant par défaut de la carte cadeau.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
