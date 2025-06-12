---
title: 'ACSD-46988 : la requête d’API de devise GraphQL renvoie des valeurs nulles'
description: Le correctif ACSD-46988 corrige le problème en raison duquel la requête de l’API de devise GraphQL renvoie des valeurs nulles pour une devise personnalisée. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21 est installé. L’ID du correctif est ACSD-46988. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.
feature: REST, GraphQL
role: Admin
exl-id: 276d2c75-6e7f-4888-b4d2-ac96bea93fc1
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-46988 : la requête d’API de devise GraphQL renvoie des valeurs nulles

Le correctif ACSD-46988 corrige le problème en raison duquel la requête de l’API de devise GraphQL renvoie des valeurs nulles pour une devise personnalisée. Ce correctif est disponible lorsque la version 1.1.21 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-46988. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La requête d’API de devise GraphQL renvoie des valeurs nulles pour une devise personnalisée.

<u>Procédure à suivre </u> :

1. Configurez la devise personnalisée dans l’administrateur. Accédez à **Système** > **Configuration** > **Général** > **Configuration de la devise**.
1. Envoyez une requête GraphQL avec la payload suivante :

<pre>
<code class="language-graphql">
{
    currency {
        base_currency_code
        base_currency_symbol
        default_display_currency_code
        default_display_currency_symbol
        available_currency_codes
        exchange_rates {
            currency_to
            rate
        }
    }
}
</code>
</pre>

<u>Résultats attendus</u> :

La requête renvoie des valeurs de devise au lieu de valeurs nulles.

<u>Résultats réels</u> :

La requête renvoie plusieurs valeurs nulles.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [Outils de correctifs de qualité > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de l’outil de correctifs de qualité.
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Étapes supplémentaires requises après l’installation du correctif

Pour les utilisateurs On-premise :

* Exécuter : `composer require symfony/intl:"~5.4.11"`

Pour les utilisateurs de Cloud :

* Exécuter : `composer require symfony/intl:"~5.4.11"`
* Envoyez les fichiers `composer.json` et `composer.lock` au référentiel Git avec le fichier de correctif.

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide Outil de correctifs de qualité..
