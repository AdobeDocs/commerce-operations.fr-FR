---
title: 'MDVA-43731 : les synonymes de recherche ne fonctionnent pas lorsque la valeur est ajoutée dans "Termes minimum à faire correspondre".'
description: Le correctif MDVA-43731 corrige le problème en raison duquel les Synonymes de recherche ne fonctionnent plus lorsqu’une valeur est ajoutée dans "Termes minimum à faire correspondre". Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID de correctif est MDVA-43731. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: Cache, Marketing Tools, Search
role: Admin
exl-id: 1eada0cd-c0ab-4f0f-b6bf-7c10e1df07ce
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# MDVA-43731 : les synonymes de recherche ne fonctionnent pas lorsque la valeur est ajoutée dans &quot;Termes minimum à faire correspondre&quot;.

Le correctif MDVA-43731 corrige le problème en raison duquel les Synonymes de recherche ne fonctionnent plus lorsqu’une valeur est ajoutée dans &quot;Termes minimum à faire correspondre&quot;. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID de correctif est MDVA-43731. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les Synonymes de recherche cessent de fonctionner lorsqu’une valeur est ajoutée dans &quot;Termes minimum à faire correspondre&quot;.

<u>Étapes à reproduire</u> :

1. Installez Adobe Commerce avec des exemples de données.
1. Configurez Elasticsearch7 comme moteur de recherche.
1. Recherchez le mot &quot;Jacket&quot;. Une liste de produits s’affiche.
1. Ajoutez le paramètre [4&lt;60%] dans **Configuration** > **Catalogue** > **Recherche catalogue** > **Termes minimum à faire correspondre**.
1. Effacez le cache de configuration et effectuez une réindexation.
1. Recherchez à nouveau le mot &quot;Jacket&quot; et notez qu’une liste de produits s’affiche.
1. Accédez à **Marketing** > **SEO &amp; Search** > **Recherche de synonymes**.
1. Créez des synonymes de recherche en ajoutant les synonymes suivants : veste, bagtecs, express plus.
1. Effectuez une réindexation.
1. Effectuez une recherche de produit à l’aide de n’importe lequel des synonymes. Par exemple, veste.

<u>Résultats attendus</u> :

Vous obtenez la même liste de produits qu’auparavant dans les résultats de recherche.

<u>Résultats réels</u> :

Aucun produit n’est affiché dans les résultats de recherche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
