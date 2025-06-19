---
title: 'MDVA-41236 : impossible de créer ou de modifier les mises à jour planifiées existantes pour le produit'
description: Le correctif MDVA-41236 corrige le problème en raison duquel les utilisateurs ne peuvent pas créer de mises à jour planifiées ou en modifier existantes pour le produit si la « Date de fin » a été supprimée précédemment. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 est installé. L’ID du correctif est MDVA-41236. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Products, Staging
role: Admin
exl-id: 82192778-4f25-40a0-882e-d52d32c433c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# MDVA-41236 : impossible de créer ou de modifier les mises à jour planifiées existantes pour le produit

Le correctif MDVA-41236 corrige le problème en raison duquel les utilisateurs ne peuvent pas créer de mises à jour planifiées ou en modifier existantes pour le produit si la « Date de fin » a été supprimée précédemment. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 est installé. L’ID du correctif est MDVA-41236. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs ne peuvent pas créer de nouveaux plannings ni modifier les plannings existants pour les produits si la « Date de fin » a été supprimée précédemment.

<u>Procédure à suivre </u> :

1. Créez un produit dont le Statut est défini sur *désactiver*.
1. Ajoutez une mise à jour planifiée pour activer ce produit.
   * Ajoutez des dates de début et de fin futures.
1. Modifiez la mise à jour planifiée en supprimant la **Date de fin**.
1. Modifiez à nouveau le planning et essayez d’ajouter une **Date de fin**. Une erreur se produira.
1. Actualisez la page et accédez de nouveau à **Modifier la mise à jour planifiée**.
1. Cliquez sur **Supprimer de la mise à jour** > **Supprimer la mise à jour**.
1. Désormais, vous ne devriez pas voir la mise à jour planifiée en haut de la page de modification du produit.
1. Essayez de créer une mise à jour planifiée qui chevauche la durée précédente.

<u>Résultats attendus</u> :

* Il n’y a pas d’erreur à l’étape 4. L’administrateur peut mettre à jour la mise à jour planifiée sans erreur, car le planning n’est pas encore actif.
* L’utilisateur administrateur peut supprimer la mise à jour précédente et en créer une nouvelle.

<u>Résultats réels</u> :

Les utilisateurs reçoivent le message d’erreur suivant :

*erreur : une mise à jour ultérieure existe déjà dans cette période. Définissez une autre plage et réessayez.*


## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
