---
title: 'ACSD-46541 : un utilisateur administrateur ne peut pas créer d''avoir si un article de commande est supprimé'
description: Appliquez le correctif ACSD-46541 pour résoudre le problème d’Adobe Commerce en raison duquel, une fois qu’un produit est supprimé, vous ne pouvez pas créer d’avoir dans l’administrateur Adobe Commerce.
feature: Admin Workspace, Orders, Returns
role: Admin
exl-id: c46ee888-92b1-4798-bd2b-1a082fd1406a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-46541 : un utilisateur administrateur ne peut pas créer d&#39;avoir si un article de commande est supprimé

Le correctif ACSD-46541 corrige le problème en raison duquel un utilisateur administrateur ne peut pas créer d’avoir en cas de suppression d’un élément de commande. Ce correctif est disponible lorsque la version 1.1.21 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-46541. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une fois qu’un produit est supprimé, vous ne pouvez pas créer d’avoir dans l’administrateur Commerce.

<u>Procédure à suivre </u> :

1. Connectez-vous à l’administration Commerce.
1. Créer une commande.
1. Facture la commande.
1. Supprimez le produit de la commande.
1. Cliquez sur le lien **[!UICONTROL Credit Memo]** de la page de modification de la commande.
1. Cliquez sur **[!UICONTROL Refund Offline]** pour créer un avoir.

<u>Résultats attendus</u> :

Un avoir a été créé.

<u>Résultats réels</u> :

Les produits _suivants avec les SKU demandés) sont introuvables : SKU001_ s’affiche en cas d’erreur.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
