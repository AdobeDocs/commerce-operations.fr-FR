---
title: 'MDVA-42046 : valeur incorrecte affectée à l’attribut de produit'
description: Le correctif MDVA-42046 corrige le problème d’affectation d’une valeur incorrecte à l’attribut de produit lors de la mise à jour d’un produit qui comporte un champ de saisie de date. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID du correctif est MDVA-42046. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Attributes, Products
role: Admin
exl-id: ff5903ff-70b3-4274-a8a1-450c2fde9750
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-42046 : valeur incorrecte affectée à l’attribut de produit

Le correctif MDVA-42046 corrige le problème d’affectation d’une valeur incorrecte à l’attribut de produit lors de la mise à jour d’un produit qui comporte un champ de saisie de date. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID du correctif est MDVA-42046. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4 - 2.3.5-p2 et 2.4.0 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Après avoir enregistré un produit avec des champs `news_from_date` et/ou `news_to_date`, les valeurs de ces champs sont réinitialisées aux valeurs par défaut.

<u>Procédure à suivre </u> :

1. Créez un produit simple.
1. Exportez le produit créé à l’étape 1.
1. Dans le fichier CSV exporté, placez certaines valeurs dans les champs `news_from_date` et `news_to_date`. Par exemple, 2021-05-15 et 2021-06-18.
1. Importez le produit à l’aide du fichier CSV modifié.
1. Ajoutez les colonnes supplémentaires « Définir le produit comme nouveau à partir de la date » et « Définir le produit comme nouveau à la date » à la grille de produits.
1. Ouvrez la page de modification du produit, puis, sans modification, cliquez sur **Enregistrer**.
1. Revenez à la grille de produits et vérifiez les données du produit.

<u>Résultats attendus</u> :

Les options « Définir le produit comme nouveau à partir de la date » et « Définir le produit comme nouveau à la date » sont les mêmes qu’avant l’enregistrement.

<u>Résultats réels</u> :

* Les valeurs des colonnes « Définir le produit comme nouveau à partir de la date » et « Définir le produit comme nouveau à la date » ont été modifiées.

* La colonne « Définir le produit comme nouveau à partir de la date » affiche la date actuelle et la colonne « Définir le produit comme nouveau à la date » est vide.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
