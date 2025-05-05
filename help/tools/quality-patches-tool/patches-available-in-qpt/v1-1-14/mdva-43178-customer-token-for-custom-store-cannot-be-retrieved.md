---
title: "MDVA-43178 : le jeton client de la boutique personnalisée ne peut pas être récupéré dans GraphQL"
description: Le correctif MDVA-43178 corrige le problème en raison duquel le jeton client d’un magasin personnalisé ne peut pas être récupéré dans GraphQL. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 est installé. L’ID de correctif est MDVA-43178. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: GraphQL
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-43178 : le jeton client de la boutique personnalisée ne peut pas être récupéré dans GraphQL

Le correctif MDVA-43178 corrige le problème en raison duquel le jeton client d’un magasin personnalisé ne peut pas être récupéré dans GraphQL. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 est installé. L’ID de correctif est MDVA-43178. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le jeton client d’un magasin personnalisé ne peut pas être récupéré dans GraphQL.

<u>Étapes à reproduire</u> :

1. Créez deux vues de magasin pour le magasin par défaut.
1. Créez un site Web, un magasin et un magasin. Nommez cette vue de magasin &quot;test3&quot;.
1. Créez un client pour le nouveau site web.
1. Générer un jeton d’administration API :

   `http://domain/rest/all/V1/integration/admin/token`

   <pre>
    <code class="language-graphql">
    &lbrace;
      "username": "login",
      "password": "password"
    &rbrace;
    </code>
    </pre>

1. Envoyez GraphQL pour récupérer le jeton client en tant qu’administrateur, utilisez le jeton d’administration pour l’autorisation, avec &quot;store&quot; = &quot;test3&quot; dans l’en-tête :

   <pre>
    <customer_email>
      </pre>

<u>Résultats attendus</u> :

Le jeton client est généré.

<u>Résultats réels</u> :

Le jeton client n’est pas généré. Les commerçants obtiennent *l’e-mail du client fourni n’existe pas* en réponse.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
