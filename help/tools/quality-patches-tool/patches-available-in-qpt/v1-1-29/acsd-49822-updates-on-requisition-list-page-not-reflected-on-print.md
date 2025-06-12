---
title: 'ACSD-49822 : les mises à jour de la page de la liste des demandes d''approvisionnement ne sont pas répercutées sur la liste des demandes d''impression'
description: Appliquez le correctif ACSD-49822 pour résoudre le problème Adobe Commerce en raison duquel les mises à jour de la page de la liste des demandes d'approvisionnement ne sont pas reflétées dans la liste des demandes d'impression.
feature: Admin Workspace, B2B
role: Admin
exl-id: 053b8900-0900-4b7e-ba1b-ad4b88ca3f35
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-49822 : les mises à jour de la liste des demandes d&#39;approvisionnement ne sont pas reflétées dans la liste des demandes d&#39;impression

Le correctif ACSD-49822 corrige le problème où les mises à jour de la page de la liste des demandes d&#39;approvisionnement ne sont pas reflétées sur la liste des demandes d&#39;impression. Ce correctif est disponible lorsque la version 1.1.29 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-49822. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les mises à jour de la page de la liste des demandes d&#39;approvisionnement ne sont pas répercutées sur la liste d&#39;impression des demandes d&#39;approvisionnement.

<u>Procédure à suivre </u> :

1. Activez la liste de demandes d&#39;approvisionnement en accédant à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[Fonctionnalités B2B]**.
1. Créez un produit.
1. Connectez-vous en tant que client et ajoutez deux produits à la liste des demandes d&#39;approvisionnement.
1. Accédez à **[!UICONTROL My Account]** > **[!UICONTROL My Requisition Lists]**.
1. Afficher une liste de demandes d&#39;approvisionnement.
1. Cliquez sur **[!UICONTROL Print]** dans le coin supérieur droit.
1. Fermez la fenêtre Imprimer et imprimez la page de liste des demandes d&#39;approvisionnement.
1. Supprimez un élément de la liste ou modifiez la quantité d&#39;un élément, puis réessayez de l&#39;imprimer.
1. Vous remarquerez que les éléments ne sont pas mis à jour dans la fenêtre d’impression.
1. Fermez la fenêtre d&#39;impression.
1. Vous remarquerez que les articles ne sont pas mis à jour sur la page d&#39;impression de la liste de demandes d&#39;approvisionnement.

<u>Résultats attendus</u> :

La liste à imprimer est mise à jour après l’application de toute modification.

<u>Résultats réels</u> :

Les mises à jour ne sont pas reflétées sur la page d&#39;impression de la liste de demandes.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
