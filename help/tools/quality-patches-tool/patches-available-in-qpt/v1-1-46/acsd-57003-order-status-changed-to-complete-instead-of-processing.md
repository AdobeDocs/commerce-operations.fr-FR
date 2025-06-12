---
title: 'ACSD-57003 : le statut de la commande passe de *Terminé* à *Traitement*'
description: Appliquez le correctif ACSD-57003 pour résoudre le problème d’Adobe Commerce où le statut de la commande passe à *Terminé* au lieu de *Traitement*.
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
exl-id: a28ecc35-5c9a-4bba-b0b9-67fbe37ed8c3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-57003 : le statut de la commande passe à *Terminé* au lieu de *Traitement*

Le correctif ACSD-57003 corrige le problème où le statut de la commande passe à *Terminé* au lieu de passer à *Traitement*. Ce correctif est disponible lorsque la version 1.1.46 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-57003. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3, 2.4.6-p8, 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p9, 2.4.7-p2 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le statut de la commande passe à *Terminé* au lieu de *Traitement* lorsqu’une commande est partiellement remboursée et partiellement expédiée.

<u>Procédure à suivre </u> :

1. Créez une commande avec deux produits configurables.
1. Facturer tous les articles.
1. Expédiez uniquement le premier article.
1. Rembourser/créer un avoir uniquement pour l&#39;article expédié (*premier article*).
1. Vérifiez le statut de la commande.

<u>Résultats attendus</u> :

Le statut de la commande doit être à l’état _Traitement_.

<u>Résultats réels</u> :

Le statut de la commande passe à *Terminé* après la création d&#39;un avoir pour l&#39;article partiellement expédié.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
