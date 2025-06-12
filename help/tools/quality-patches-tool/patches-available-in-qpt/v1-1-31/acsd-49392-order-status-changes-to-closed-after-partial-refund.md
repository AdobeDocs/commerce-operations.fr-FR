---
title: 'ACSD-49392 : le statut de la commande passe à Clôturé après remboursement partiel'
description: Appliquez le correctif ACSD-49392 pour résoudre le problème Adobe Commerce où le statut de la commande passe à fermé après un remboursement partiel pour un produit groupé.
feature: Orders
role: Admin
exl-id: e12cbf2d-219e-4cb5-a226-6c7ae4929549
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-49392 : le statut de la commande passe à Clôturé après remboursement partiel

>[!NOTE]
>
>Le patch ACSD-49392 a été remplacé par le patch [ACSD-57003](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-57003-order-status-changed-to-complete-instead-of-processing) pour les versions 2.4.6-p7 à 2.4.6-p10.

Le correctif ACSD-49392 corrige le problème en raison duquel le statut de la commande passe à Fermé après un remboursement partiel pour un produit groupé. Ce correctif est disponible lorsque la version 1.1.31 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-49392. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.3.7-p4 et 2.4.1 - 2.4.6-p6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le statut de la commande passe à Fermé après un remboursement partiel pour un produit groupé.

<u>Procédure à suivre </u> :

1. Connectez-vous à Adobe Commerce et créez un produit groupé, ou utilisez le produit groupé existant.
1. Passez une commande avec ce produit groupé avec une quantité supérieure à 1.
1. Accédez à Admin , ouvrez la commande créée à l’étape 2 dans **[!UICONTROL Sales]** > **[!UICONTROL Order]** et créez une facture. Observez le statut de la commande. Il sera en cours de traitement.
1. Créer un avoir partiel (ne pas rembourser tous les produits du lot).
1. Vérifiez le statut de la commande.

<u>Résultats attendus</u>

Après avoir créé un avoir partiel pour le produit groupé, le statut de la commande est en cours de traitement.

<u>Résultats réels</u>

Après la création d&#39;un avoir partiel pour le produit groupé, le statut de la commande est terminé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
