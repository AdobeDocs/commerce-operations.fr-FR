---
title: 'ACSD-61528 : la récupération de rôles à l’aide de GraphQL ne renvoie aucun résultat'
description: Appliquez le correctif ACSD-61528 pour résoudre le problème d’Adobe Commerce où la récupération de rôles de l’administrateur de l’entreprise à l’aide de GraphQL renvoie toujours un résultat nul.
feature: GraphQL, B2B, Companies, Roles/Permissions
role: Admin, Developer
exl-id: 81d78746-e723-4b18-860c-d973158b469c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61528 : la récupération de rôles à l’aide de GraphQL ne renvoie aucun résultat

Le correctif ACSD-61258 corrige le problème où la récupération de rôles de l’administrateur de l’entreprise à l’aide de GraphQL renvoie toujours un résultat nul. Ce correctif est disponible lorsque la version 1.1.53 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-61528. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p5

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de la récupération de rôles auprès de l’administrateur de l’entreprise à l’aide de GraphQL, le résultat du rôle était toujours nul.

<u>Conditions préalables requises:</u> :

Installation et activation des modules B2B Adobe Commerce.

<u>Procédure à suivre </u> :

1. Créez une entreprise.
1. Connectez-vous en tant qu’administrateur de société sur GraphQL avec la mutation suivante :

   ```GraphQL
      mutation {
          generateCustomerToken(email: "company@admin.com", password: "PASSWORD") {
      token
      }
   }
   ```

1. Ajoutez le jeton obtenu aux en-têtes de requête **Authorization** en tant que jeton de `Bearer` et exécutez la requête GraphQL suivante :

   ```GraphQL
      {
      customer {
      email
      role{
       name
       id
      }
    }
   }
   ```

<u>Résultats attendus</u> :

La requête GraphQL renvoie le rôle.

<u>Résultats réels</u> :

Le rôle de la société est nul.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
