---
title: 'MDVA-41350 : exception lorsque l’administrateur ajoute des produits en dehors de son accès'
description: Le correctif MDVA-41350 corrige le problème où une erreur d’exception est déclenchée au lieu d’une notification d’accès limité lorsqu’un utilisateur administrateur ajoute un produit dans la commande par SKU qui n’est pas accessible. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11 est installé. L’ID du correctif est MDVA-41350. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Admin Workspace, Products
role: Admin
exl-id: 4dc5ee5c-bd93-42e1-9c63-93ffb8e5f21c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-41350 : exception lorsque l’administrateur ajoute des produits en dehors de son accès

Le correctif MDVA-41350 corrige le problème où une erreur d’exception est déclenchée au lieu d’une notification d’accès limité lorsqu’un utilisateur administrateur ajoute un produit dans la commande par SKU qui n’est pas accessible. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11 est installé. L’ID du correctif est MDVA-41350. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsqu’un utilisateur administrateur à accès restreint ajoute un produit par SKU en dehors de son accès dans la commande, une exception se produit au lieu d’un message informant l’utilisateur de son accès limité.

<u>Procédure à suivre </u> :

1. Connectez-vous à l’administrateur en tant qu’utilisateur ayant accès à un site web spécifique uniquement.
1. Accédez à **Ventes** > **Commandes** et cliquez sur **Créer une commande**.
1. Sélectionnez un client et une vue de magasin.
1. Cliquez sur **Ajouter des produits par SKU**.
1. Recherchez un SKU qui n’est affecté à aucun site web ou qui n’est pas affecté au site web auquel vous avez accès.
1. Cliquez sur **Ajouter à la commande**.

<u>Résultats attendus</u> :

Un message d’erreur approprié s’affiche.

<u>Résultats réels</u> :

Une exception se produit.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
