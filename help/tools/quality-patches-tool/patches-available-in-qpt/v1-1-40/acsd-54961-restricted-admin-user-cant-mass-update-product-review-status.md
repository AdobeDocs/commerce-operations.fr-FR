---
title: 'ACSD-54961 : l’utilisateur administrateur restreint ne peut pas mettre à jour en masse les [!UICONTROL Product Review status]'
description: Appliquez le correctif ACSD-54961 pour résoudre le problème d’Adobe Commerce en raison duquel un utilisateur administrateur restreint ne peut pas mettre à jour en masse le statut de la révision du produit.
feature: Products
role: Admin, Developer
exl-id: d303365c-d7c7-4aca-9f33-75d67bcbe573
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-54961 : l’utilisateur administrateur restreint ne peut pas mettre à jour en masse les [!UICONTROL Product Review status]

Le correctif ACSD-54961 corrige le problème où un utilisateur administrateur restreint ne peut pas mettre à jour en masse les [!UICONTROL Product Review status]. Ce correctif est disponible lorsque la version 1.1.40 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-54961. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une personne en charge de l’administration restreinte ne peut pas mettre à jour [!UICONTROL Product Review status] en masse.

<u>Procédure à suivre </u> :

1. Créez un site web, un magasin et une vue de magasin supplémentaires.
1. Ajoutez un produit au 2e magasin, puis ajoutez une révision.
1. Créez un utilisateur administrateur restreint ayant accès uniquement au deuxième magasin.
1. Connectez-vous en tant qu’utilisateur administrateur restreint, puis accédez à **[!UICONTROL  Marketings]** > **[!UICONTROL Reviews]** > **[!UICONTROL Mass Update]** et définissez le **Statut** sur *Approuvé* ou *En attente*.

<u>Résultats attendus</u> :

L’administrateur restreint peut mettre à jour des révisions à l’aide de l’action **[!UICONTROL Mass Update]**.

<u>Résultats réels</u> :

Une erreur se produit lors de la mise à jour des révisions à l’aide de l’action **[!UICONTROL Mass Update]**.<br>
Le `var/log/exception.log` contient une erreur similaire :

```
report.CRITICAL: TypeError: array_intersect(): Argument #1 ($array) must be of type array, null given in app/code/Magento/AdminGws/Model/Models.php:439
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
