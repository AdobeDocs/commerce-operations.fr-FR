---
title: "ACSD-49822 : mises à jour sur la page de liste des demandes d’acquisition non répercutées sur la liste des demandes d’impression"
description: Appliquez le correctif ACSD-49822 pour résoudre le problème Adobe Commerce en raison duquel les mises à jour de la page de liste des demandes d’achat ne sont pas répercutées sur la liste des demandes d’impression.
feature: Admin Workspace, B2B
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-49822 : les mises à jour de la liste des demandes d’acquisition ne sont pas répercutées sur la liste des demandes d’impression.

Le correctif ACSD-49822 corrige le problème en raison duquel les mises à jour de la page de liste des demandes d’achat ne sont pas répercutées sur la liste des demandes d’impression. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 est installé. L’ID de correctif est ACSD-49822. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les mises à jour de la page de liste des demandes d’achat ne sont pas répercutées dans la liste des demandes d’impression.

<u>Étapes à reproduire</u> :

1. Activez la liste des demandes en accédant à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[Fonctionnalités B2B]**.
1. Créez un produit.
1. Connectez-vous en tant que client et ajoutez deux produits à la liste des demandes.
1. Accédez à **[!UICONTROL My Account]** > **[!UICONTROL My Requisition Lists]**.
1. Affichez une liste de demandes d’approvisionnement.
1. Cliquez sur **[!UICONTROL Print]** dans le coin supérieur droit.
1. Fermez la fenêtre d’impression et la page de liste des demandes d’impression.
1. Supprimez un élément de la liste ou mettez à jour une quantité d’un élément, puis essayez de l’imprimer à nouveau.
1. Vous remarquerez que les éléments ne sont pas mis à jour dans la fenêtre d&#39;impression.
1. Fermez la fenêtre d’impression.
1. Vous remarquerez que les éléments ne sont pas mis à jour sur la page d’impression de la liste des demandes.

<u>Résultats attendus</u> :

La liste à imprimer est mise à jour après toute modification.

<u>Résultats réels</u> :

Les mises à jour ne sont pas répercutées sur la page d’impression de la liste des demandes d’achat.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
