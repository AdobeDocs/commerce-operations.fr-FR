---
title: "ACSD-61199 : l’onglet de la page CMS [!UICONTROL Hierarchy] n’affiche pas la structure arborescente appropriée"
description: Appliquez le correctif ACSD-61199 pour résoudre le problème Adobe Commerce en raison duquel l’onglet *[!UICONTROL Hierarchy]* de la page CMS n’affiche pas une arborescence correcte lors de la modification d’une page CMS avec une *[!UICONTROL Hierarchy]* existante.
feature: Page Content
role: Admin, Developer
source-git-commit: bbe4e272d3a8bd82163bdd718d006a314287b650
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-61199 : l’onglet [!UICONTROL Hierarchy] de la page CMS n’affiche pas la structure arborescente appropriée

Le correctif ACSD-61199 corrige le problème en raison duquel l’onglet *[!UICONTROL Hierarchy]* de la page CMS n’affiche pas une arborescence correcte lors de la modification d’une page CMS avec un *[!UICONTROL Hierarchy]* existant. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 est installé. L’ID de correctif est ACSD-61199. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’onglet *[!UICONTROL Hierarchy]* de la page CMS n’affiche pas une arborescence correcte lors de la modification d’une page CMS avec un *[!UICONTROL Hierarchy]* existant.

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Créez un **[!UICONTROL CMS page]**. Il est ajouté à la racine du site web à l’emplacement *[!UICONTROL Hierarchy]*.
1. Enregistrez la page.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Hierarchy]**.
1. Ajoutez d’autres pages existantes à la *[!UICONTROL Hierarchy]*.
1. Enregistrez le *[!UICONTROL Hierarchy]*.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Modifiez l’une des pages existantes et ouvrez le *[!UICONTROL Hierarchy]*.

<u>Résultats attendus</u> :

Le *[!UICONTROL Hierarchy]* se charge comme prévu.

<u>Résultats réels</u> :

*[!UICONTROL Hierarchy]* n’est pas chargé dans l’onglet .

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

[[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
