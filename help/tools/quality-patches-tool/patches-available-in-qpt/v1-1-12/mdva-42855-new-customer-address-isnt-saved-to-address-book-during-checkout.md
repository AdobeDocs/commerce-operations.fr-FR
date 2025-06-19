---
title: 'MDVA-42855 : la nouvelle adresse du client n’est pas enregistrée dans le carnet d’adresses lors du passage en caisse '
description: Le correctif MDVA-42855 corrige le problème en raison duquel la nouvelle adresse du client n’est pas enregistrée dans le carnet d’adresses lors du passage en caisse. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-42855. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Checkout, Orders, Shipping/Delivery
role: Admin
exl-id: 924b8f57-1fec-4e62-bf0e-1f9cafa75cab
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# MDVA-42855 : la nouvelle adresse du client n’est pas enregistrée dans le carnet d’adresses lors du passage en caisse

Le correctif MDVA-42855 corrige le problème en raison duquel la nouvelle adresse du client n’est pas enregistrée dans le carnet d’adresses lors du passage en caisse. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-42855. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La nouvelle adresse du client n’est pas enregistrée dans le carnet d’adresses lors du passage en caisse.

<u>Procédure à suivre </u> :

1. Créez un compte client et mettez à jour l’adresse d’expédition et de facturation par défaut.
1. Ajoutez un produit au panier et accédez à la page de passage en caisse.
1. Lors de l&#39;expédition, cliquez sur **+ Nouvelle adresse**.
1. Saisissez votre nouvelle adresse et gardez la case **Enregistrer dans le carnet d’adresses** cochée.
1. Lors du paiement, cochez la case **Mes adresses de facturation et d’expédition sont les mêmes**.
1. Passez la commande.
1. Vérifie le carnet d&#39;adresses.

<u>Résultats attendus</u> :

La nouvelle adresse de livraison est enregistrée dans le carnet d&#39;adresses.

<u>Résultats réels</u> :

La nouvelle adresse de livraison n&#39;est pas enregistrée dans le carnet d&#39;adresses.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
