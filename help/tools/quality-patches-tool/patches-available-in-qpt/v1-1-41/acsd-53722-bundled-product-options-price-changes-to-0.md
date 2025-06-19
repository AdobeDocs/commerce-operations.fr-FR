---
title: 'ACSD-53722 : modifications du prix des options de produits groupés à 0 $'
description: Appliquez le correctif ACSD-53722 pour résoudre le problème d’Adobe Commerce où le prix des options de produit groupées passe à 0 $ lorsque les mises à jour planifiées pour différentes portées deviennent actives.
feature: Products
role: Admin, Developer
exl-id: 2e974a6a-0c79-442f-9b45-b4edf831a052
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-53722 : modifications du prix des options de produits groupés à 0 $

Le correctif ACSD-53722 corrige le problème en raison duquel le prix des options de produits groupées passe à 0 $ lorsque les mises à jour planifiées pour différentes portées deviennent actives. Ce correctif est disponible lorsque la version 1.1.41 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-53722. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le prix des options de produit groupées passe à 0 $ lorsque les mises à jour planifiées pour différentes portées deviennent actives.

<u>Procédure à suivre </u> :

1. Créez deux sites web, A et B.
1. Définissez la configuration sous **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]** = **[!UICONTROL Website]**.
1. Créez un produit groupé à un prix fixe sur les sites A et B :

   * Prix du produit groupé = Fixe = *0*

1. Ajoutez un produit simple comme option de liste déroulante pour le lot. Fixez les prix suivants :

   * Prix à l&#39;intérieur de l&#39;option groupée = *120*
   * Un prix à l&#39;intérieur de l&#39;option groupée = *130*
   * Site web du produit simple B prix à l&#39;intérieur de l&#39;option groupée = *140*

1. Planifiez une mise à jour pour désactiver le produit groupé sur le site Web A.

<u>Résultats attendus</u> :

La mise à jour prévue pour le site Web A n’a aucune incidence sur le prix du site Web B.

<u>Résultats réels</u> :

Après la mise à jour planifiée, le prix de l’option de produit groupé sur le site Web B est modifié à **$0**.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
