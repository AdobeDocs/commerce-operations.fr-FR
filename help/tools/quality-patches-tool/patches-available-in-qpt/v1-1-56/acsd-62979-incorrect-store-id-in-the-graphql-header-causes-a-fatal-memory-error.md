---
title: 'ACSD-62979 : un ID de magasin incorrect dans l’en-tête GraphQL entraîne une erreur de mémoire fatale'
description: Appliquez le correctif ACSD-62979 pour résoudre le problème d’Adobe Commerce où l’utilisation d’un ID de magasin incorrect dans l’en-tête du GraphQL provoque une erreur de mémoire fatale
feature: GraphQL
role: Admin, Developer
exl-id: 832baae1-34b4-4ca8-bfa9-221aa60da67e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-62979 : un ID de magasin incorrect dans l’en-tête GraphQL entraîne une erreur de mémoire fatale

Le correctif ACSD-62979 corrige le problème en raison duquel l’utilisation d’un ID de magasin incorrect dans l’en-tête de GraphQL provoque une erreur de mémoire fatale. Ce correctif est disponible lorsque la version 1.1.56 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62979. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6, 2.4.6-p7, 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Correction d’un problème en raison duquel l’utilisation d’un ID de magasin incorrect dans l’en-tête GraphQL entraînait une erreur de mémoire fatale.

<u>Procédure à suivre </u> :

1. Sélectionnez **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL Url Options]**). Activez **[!UICONTROL Add Store Code to Urls]**.
1. Exécutez sous la requête GraphQL avec une valeur incorrecte pour l’en-tête du magasin.

```graphql
{
  categoryList(filters: { ids: { eq: "2" } }) {
    uid
    level
    name
    url_path
    image
    children {
      uid
      level
      name
      url_path
      image
      children {
        uid
        level
        name
        url_path
        image
        children {
          uid
          level
          name
          url_path
          image
        }
      }
    }
  }
}
```

<u>Résultats attendus</u> :

Message d’erreur : « Le magasin demandé est introuvable. Vérifiez le magasin et réessayez. »

<u>Résultats réels</u> :

Erreur fatale telle que :

```Allowed memory size of 792723456 bytes exhausted```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
