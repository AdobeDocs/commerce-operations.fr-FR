---
title: 'ACSD-51230 : le compte de carte cadeau est supprimé'
description: Appliquez le correctif ACSD-51230 pour résoudre le problème d'Adobe Commerce où le compte de carte cadeau est supprimé lorsque le remboursement partiel d'un produit simple est traité à partir d'une commande.
feature: Customer Service, Gift, Marketing Tools
role: Admin
exl-id: a4aed574-3908-42e0-ac32-911f61b44995
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-51230 : le compte de carte cadeau est supprimé

Le correctif ACSD-51230 corrige le problème où le compte de carte cadeau est supprimé lorsque le remboursement partiel d&#39;un produit simple est traité à partir d&#39;une commande. Ce correctif est disponible lorsque la version 1.1.32 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-51230. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le compte de carte cadeau est supprimé lorsque le remboursement partiel d&#39;un produit simple est traité à partir d&#39;une commande.

<u>Procédure à suivre </u> :

1. Créez une commande avec une *Carte cadeau* et un *produit simple* (par exemple, *ajoutez : SKU : GI000XX000XXX, SKU : PC046CP042076*) - (tout mode de paiement et d’expédition fonctionne).
1. Facture la commande.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Un compte est créé pour la carte cadeau.
1. Accédez maintenant à **[!UICONTROL Order]** et créez un **[!UICONTROL Credit Memo]**.
1. Remplacez la quantité de la *Carte cadeau* par 0 et mettez-la à jour. Cela créera un remboursement partiel pour le *produit simple*.
1. Cliquez sur **[!UICONTROL Refund]**.
1. Actualisez maintenant le **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Le compte nouvellement créé est supprimé.

<u>Résultats attendus</u>

Le compte de carte cadeau est disponible car le remboursement n&#39;a pas été créé pour la carte cadeau.

<u>Résultats réels</u>

Le compte de carte cadeau est supprimé et la carte cadeau n&#39;est pas remboursée.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
