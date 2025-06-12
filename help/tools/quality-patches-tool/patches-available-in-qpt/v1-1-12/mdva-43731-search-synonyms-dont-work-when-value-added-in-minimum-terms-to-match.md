---
title: 'MDVA-43731 : les synonymes de recherche ne fonctionnent pas lorsque la valeur est ajoutée dans « Termes minimum à faire correspondre »'
description: Le correctif MDVA-43731 corrige le problème où les synonymes de recherche cessent de fonctionner lorsqu’une valeur est ajoutée dans « Termes minimum à faire correspondre ». Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-43731. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Cache, Marketing Tools, Search
role: Admin
exl-id: 1eada0cd-c0ab-4f0f-b6bf-7c10e1df07ce
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# MDVA-43731 : les synonymes de recherche ne fonctionnent pas lorsque la valeur est ajoutée dans « Termes minimum à faire correspondre »

Le correctif MDVA-43731 corrige le problème où les synonymes de recherche cessent de fonctionner lorsqu’une valeur est ajoutée dans « Termes minimum à faire correspondre ». Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-43731. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les synonymes de recherche ne fonctionnent plus lorsqu’une valeur est ajoutée dans « Termes à faire correspondre au minimum ».

<u>Procédure à suivre </u> :

1. Installez Adobe Commerce avec des exemples de données.
1. Configurez Elasticsearch7 comme moteur de recherche.
1. Recherchez le mot « Veste ». Une liste de produits s’affiche.
1. Ajoutez le paramètre [4&lt;60 %] dans **Configuration** > **Catalogue** > **Recherche catalogue** > **Nombre minimum de termes à faire correspondre**.
1. Effacez le cache de configuration et effectuez une réindexation.
1. Recherchez à nouveau le mot « Veste » et notez qu’une liste de produits s’affiche.
1. Accédez à **Marketing** > **SEO et recherche** > **Synonymes de recherche**.
1. Créez des synonymes de recherche en ajoutant les synonymes suivants : veste, bagtecs, express plus.
1. Effectuez une réindexation.
1. Effectuez une recherche de produits à l’aide de l’un des synonymes. Par ex., veste.

<u>Résultats attendus</u> :

Vous obtenez la même liste de produits qu’auparavant dans les résultats de la recherche.

<u>Résultats réels</u> :

Aucun produit ne s’affiche dans les résultats de la recherche.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
