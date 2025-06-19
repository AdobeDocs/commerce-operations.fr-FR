---
title: 'ACSD-56886 : le produit configurable est en rupture de stock lorsque les produits enfants sont désactivés'
description: Appliquez le correctif ACSD-56886 pour résoudre le problème d’Adobe Commerce en raison duquel le produit configurable est en rupture de stock enfant lorsque les produits sont désactivés.
feature: Products
role: Admin, Developer
exl-id: 5e9c1fd4-b56a-42c0-83e7-75e868213124
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-56886 : le produit configurable est en rupture de stock lorsque les produits enfants sont désactivés

Le correctif ACSD-56886 corrige le problème où le produit configurable devient en rupture de stock lorsque les produits enfants sont désactivés. Ce correctif est disponible lorsque la version 1.1.45 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-56886. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le produit configurable est en rupture de stock lorsque les produits enfants sont désactivés.

<u>Procédure à suivre </u> :

1. Connectez-vous en tant qu’administrateur.
1. Définissez tous les indexeurs en mode **[!UICONTROL Update By Schedule]**.
1. Créez le produit configurable suivant :

   * Nom = *TEST CONFIGURABLE 1*
   * Attribut = *color*
   * Valeurs = *rouge* et *noir*
   * Prix du produit **rouge** enfant = *$100*;
   * Prix du produit enfant « noir » = *$200*.

1. Créez la mise à jour planifiée suivante pour le produit configurable :

   * Date de début = *3* minutes à partir de maintenant.
   * Date de fin = *5* minutes après la date de début.
   * Nom du produit = *TEST CONFIGURABLE 1 modifié*.
   * Désactivez le produit enfant **rouge** dans la section **Configurable**.

1. Attendez la date de début.
1. Ouvrez les détails configurables du produit sur le Storefront.

<u>Résultats attendus</u> :

Le produit configurable s’affiche sous la forme **En stock** avec le libellé **Aussi bas que 200**.

<u>Résultats réels</u> :

Le produit configurable s’affiche comme **En rupture de stock**.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
