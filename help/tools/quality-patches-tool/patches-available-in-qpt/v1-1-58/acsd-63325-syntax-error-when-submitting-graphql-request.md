---
title: 'ACSD-63325 : erreur de syntaxe : erreur inattendue &lt;EOF&gt; lors de l’envoi d’une requête vide [!DNL GraphQL] gt'
description: Appliquez le correctif ACSD-63325 pour résoudre le problème d’Adobe Commerce où une erreur de syntaxe se produit lors de l’envoi d’une requête  [!DNL GraphQL] .
feature: GraphQL
Role: Admin, Developer
exl-id: a83a8c5f-a43a-4733-a601-7b92656e5325
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# ACSD-63325 : erreur « Erreur de syntaxe : erreur inattendue &lt; EOF > » lors de l’envoi d’une demande de [!DNL GraphQL] vide

Le correctif ACSD-63325 corrige le problème où une erreur « Syntaxe Error: Unexpected &lt; EOF > » et un code de réponse non 200 étaient renvoyés lors de l’envoi d’une requête [!DNL GraphQL] vide. Ce correctif est disponible lorsque la version 1.1.58 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63325. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de l’envoi d’une requête [!DNL GraphQL] vide, une erreur de serveur interne HTTP se produit au lieu d’un code de réponse 200.

<u>Procédure à suivre </u> :

1. Envoi d’une requête GraphQL vide

   ```graphql
   curl -i -X OPTIONS http://commerce.local/graphql
   ```

<u>Résultats attendus</u> :

Le code de réponse est 200 pour la requête.

```
curl -i -X OPTIONS http://commerce.local/graphql
```

<u>Résultats réels</u> :

Une erreur de serveur interne 500 se produit, comme illustré ci-dessous :

```
HTTP/1.1 500 Internal Server Error
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
