---
title: 'ACSD-47520 : les clients perdent des points de récompense lors de la création d''un avoir'
description: Appliquez le correctif ACSD-47520 pour résoudre le problème d’Adobe Commerce en raison duquel les clients perdent des points de récompense lors de la création d’un avoir.
feature: Admin Workspace, Cache, Orders, Rewards, Returns
role: Admin
exl-id: 09104451-e9f0-4ddb-b019-8aa34630edb9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-47520 : les clients perdent des points de récompense lors de la création d&#39;un avoir

Le correctif ACSD-47520 corrige le problème où les clients perdent des points de récompense lors de la création d&#39;un avoir. Ce correctif est disponible lorsque la version 1.1.25 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-47520. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les clients perdent des points de récompense lors de la création d&#39;un avoir.

<u>Procédure à suivre </u> :

1. Accédez à Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward Points]**.
1. Modifiez le paramètre :
   * **[!UICONTROL Enable Reward Points Functionality]** = _Oui_
   * **[!UICONTROL Enable Reward Points Functionality on Storefront]** = _Oui_
   * **[!UICONTROL Customers May See Reward Points History]** = _Oui_
   * **[!UICONTROL Refund Reward Points Automatically]** = _Non_
   * **[!UICONTROL Deduct Reward Points from Refund Amount Automatically]** = _Oui_
1. Accédez à Admin > **[!UICONTROL Store]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** et cliquez sur **[!UICONTROL Add New Rate]**.
1. Ajoutez un nouveau taux (1:1) et videz le cache.
1. Créez un client et ajoutez 10 points de récompense à ce compte.
1. Accédez à Admin > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]** > Sélectionnez le client ou la cliente créé(e) à l’étape précédente.
1. Sélectionnez un produit dont le prix est supérieur aux points de récompense.
1. Passez une commande via n&#39;importe quel mode de paiement et les points de récompense.
1. Créez une facture pour la commande.
1. Créez un avoir, mais ne remboursez pas les points de récompense.

<u>Résultats attendus</u> :

* L’administrateur peut rembourser les points de récompense.

* Le statut de la commande sera clôturé.

<u>Résultats réels</u> :

* Il n&#39;y a aucun moyen de rembourser les points de récompense.

* Le statut de la commande est **[!UICONTROL Completed]**.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
