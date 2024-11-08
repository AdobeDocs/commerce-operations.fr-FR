---
title: "ACSD-61528 : la récupération des rôles à l’aide de GraphQL ne renvoie aucun résultat"
description: Appliquez le correctif ACSD-61528 pour résoudre le problème Adobe Commerce en raison duquel la récupération des rôles de l’administrateur de la société à l’aide de GraphQL renvoie toujours un résultat nul.
feature: GraphQL, B2B, Companies, Roles/Permissions
role: Admin, Developer
source-git-commit: 4a02bb524fd8d1caae02d909bc9f2e3fc0112042
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61528 : la récupération des rôles à l’aide de GraphQL ne renvoie aucun résultat

Le correctif ACSD-61258 corrige le problème en raison duquel la récupération des rôles de l’administrateur de la société à l’aide de GraphQL renvoie toujours un résultat nul. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 est installé. L’ID de correctif est ACSD-61528. Veuillez noter que ce problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p5

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de la récupération des rôles de l’administrateur de la société à l’aide de GraphQL, le résultat du rôle était toujours nul.

<u>Conditions préalables :</u> :

Installez et activez les modules Adobe Commerce B2B.

<u>Étapes à reproduire</u> :

1. Créez une société.
1. Connectez-vous en tant qu’administrateur de la société sur GraphQL avec la mutation suivante :

   ```GraphQL
      mutation {
          generateCustomerToken(email: "company@admin.com", password: "PASSWORD") {
      token
      }
   }
   ```

1. Ajoutez le jeton obtenu aux en-têtes de requête **Authorization** en tant que jeton `Bearer` et exécutez sous la requête GraphQL :

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

La requête GraphQL renvoie le rôle .

<u>Résultats réels</u> :

Le rôle de l’entreprise est nul.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.