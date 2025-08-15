---
title: 'MDVA-37984 : le marchandiseur visuel ne fonctionne pas correctement lorsque les mises à jour d’évaluation sont appliquées'
description: Le correctif MDVA-37984 résout le problème en raison duquel la fonctionnalité « Faire correspondre le produit par règle » de Visual Merchandiser ne filtre pas correctement les produits lors de l’application des mises à jour d’évaluation. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 est installé. L’ID du correctif est MDVA-37984. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Categories, Merchandising, Products, Staging
role: Admin
exl-id: 3aeb74a4-b6f7-453a-a8f6-45a345aaa74f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-37984 : le marchandiseur visuel ne fonctionne pas correctement lorsque les mises à jour d’évaluation sont appliquées

Le correctif MDVA-37984 résout le problème en raison duquel la fonctionnalité « Faire correspondre le produit par règle » de Visual Merchandiser ne filtre pas correctement les produits lors de l’application des mises à jour d’évaluation. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 est installé. L’ID du correctif est MDVA-37984. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La fonctionnalité « Correspondre aux produits par règle » de Visual Merchandiser ne filtre pas correctement les produits lorsque les mises à jour d’évaluation sont appliquées.

<u>Procédure à suivre </u> :

1. Créez une mise à jour de planification pour tout produit existant.
   * Définissez des valeurs différentes pour `entity_id` et `row_id`.
1. Créez un nouveau produit configurable, puis un produit simple (de sorte que les nouveaux `entity_id` et `row_ids` de produit soient également différents).
   * Pour faciliter la réplication du problème, définissez une valeur de quantité reconnaissable pour le produit simple, par exemple 5 000.
1. Accédez à une catégorie > **Produits dans la catégorie** et activez **Faire correspondre les produits par règle**.
1. Sélectionnez maintenant « Quantité » comme attribut, « Supérieur » comme opérateur et « 4500 » comme valeur.
1. Cliquez sur **enregistrer**.

<u>Résultats attendus</u> :

Le produit configurable nouvellement créé est répertorié.

<u>Résultats réels</u> :

Le produit configurable nouvellement créé n’est pas répertorié.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
