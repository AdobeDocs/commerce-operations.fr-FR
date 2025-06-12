---
title: 'MDVA-43983 : les produits définis comme « Non visibles individuellement » apparaissent dans les résultats de recherche'
description: Le correctif MDVA-43983 résout le problème où les produits définis comme « Non visibles individuellement » apparaissent toujours dans les résultats de la recherche avancée du catalogue. Ce correctif est disponible lorsque l’[Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 est installé. L’ID du correctif est MDVA-43983. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Catalog Management, Products, Search
role: Admin
exl-id: d494d263-016b-43fd-aa87-0d74eadc4a6a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-43983 : les produits définis comme « Non visibles individuellement » apparaissent dans les résultats de recherche

Le correctif MDVA-43983 résout le problème où les produits définis comme « Non visibles individuellement » apparaissent toujours dans les résultats de la recherche avancée du catalogue. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 est installé. L’ID du correctif est MDVA-43983. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits définis comme « Non visibles individuellement » apparaissent toujours dans les résultats de la recherche avancée du catalogue.

<u>Procédure à suivre </u> :

1. Créez un attribut avec **Type d’entrée de catalogue pour le propriétaire de la boutique** comme **Liste déroulante** ou **Échantillon visuel** (par exemple, Couleur).
1. Définissez **Utiliser dans la recherche** sur **Oui** et **Visible dans la recherche avancée** sur **Oui**.
1. Ajoutez des options d’attribut.
1. Créer des produits avec **Visibility** comme **Not Visible individuellement**.
1. Attribuez des options d’attribut de couleur.
1. Accédez à la page **Recherche avancée de catalogue** sur le storefront.
1. Sélectionnez uniquement l’option Attribut de couleur dans le champ Attribut de couleur et laissez les autres champs vides ou inchangés.
1. Envoyez un formulaire de recherche avancée.
1. Observez les résultats de la recherche.

<u>Résultats attendus</u> :

Les produits définis comme « Non visibles individuellement » n’apparaissent pas dans les résultats de la recherche avancée du catalogue.

<u>Résultats réels</u> :

Les produits définis comme « Non visibles individuellement » apparaissent dans les résultats de la recherche avancée du catalogue.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
