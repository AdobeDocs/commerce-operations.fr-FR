---
title: 'MDVA-41061 : le statut du stock est réinitialisé sur vendable lorsque le produit est enregistré depuis l’administrateur'
description: Le correctif MDVA-41061 corrige le problème en raison duquel l’état du stock est réinitialisable lorsque le produit est enregistré auprès de l’administrateur. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 est installé. L’ID du correctif est MDVA-41061. La dernière version du correctif est disponible dans QPT 1.1.15 avec l’ID de correctif MDVA-41061-V3. Notez que le problème a été résolu dans Adobe Commerce 2.4.4.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: ddbc30ef-bc88-4878-8bd8-6880823819a2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# MDVA-41061 : le statut du stock est réinitialisé sur vendable lorsque le produit est enregistré depuis l’administrateur

Le correctif MDVA-41061 corrige le problème en raison duquel l’état du stock est réinitialisable lorsque le produit est enregistré auprès de l’administrateur. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 est installé. L’ID du correctif est MDVA-41061. La dernière version du correctif est disponible dans QPT 1.1.15 avec l’ID de correctif MDVA-41061-V3. Notez que le problème a été résolu dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.2-p2, 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le statut du stock est réinitialisé à la vente lorsque le produit est enregistré auprès de l’administrateur.

<u>Conditions préalables</u> :

Les modules d&#39;inventaire sont installés.

<u>Procédure à suivre </u> :

1. Créez un produit simple avec Qté = 1.
1. Commandez en utilisant le produit créé à l&#39;étape 1.
1. Exécuter cron : assurez-vous que `inventory.reservations.updateSalabilityStatus` file d’attente est exécutée et que le statut du stock de produits a été défini sur zéro dans la table `cataloginventory_stock_status`.
1. Vérifiez le produit sur le serveur frontal. Il doit être marqué comme **En rupture de stock**.
1. Enregistrez le produit dans l’Admin sans aucune modification.

<u>Résultats attendus</u> :

* L’état des stocks ne doit pas être mis à jour.
* Le produit doit être **en rupture de stock** sur le serveur frontal.

<u>Résultats réels</u> :

* Le produit simple est marqué comme **En stock** sur le front-end.
* Les utilisateurs reçoivent le message *La quantité demandée n’est pas disponible* lorsqu’ils tentent de l’ajouter au panier.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
