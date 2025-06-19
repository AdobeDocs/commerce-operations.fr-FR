---
title: 'ACSD-65195 : la mutation GraphQL « createCompany » renvoie une erreur pour un pays sans région requise'
description: Appliquez le correctif ACSD-65195 pour résoudre le problème d’Adobe Commerce où la mutation « createCompany » de GraphQL renvoie une erreur pour les pays qui ne nécessitent pas de région.
feature: B2B, Companies, GraphQL
role: Admin, Developer
exl-id: b9eed00c-26f2-47fe-b1a0-6b020527f0c1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-65195 : la mutation `createCompany` de GraphQL renvoie une erreur pour un pays sans région requise

Le correctif ACSD-65195 corrige le problème où la mutation [!UICONTROL GraphQL] `createCompany` génère une erreur pour les pays qui n&#39;ont pas besoin d&#39;une région. Ce correctif est disponible lorsque la version 1.1.63 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-65195. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p9, 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mutation [!UICONTROL GraphQL] `createCompany` renvoie une erreur lorsqu’une région est spécifiée pour un pays qui n’en a pas besoin.

<u>Procédure à suivre </u> :

1. Activez **[!UICONTROL B2B Companies]**.
1. Envoyez la mutation `createCompany` [!UICONTROL GraphQL] avec un champ de région spécifié pour un pays qui n’en a pas besoin. Par exemple : [!UICONTROL country_id] : *AE* et [!UICONTROL region] : *Dubaï*.
1. Vérifiez la réponse de GraphQL.

<u>Résultats attendus</u> :

La société doit être créée avec succès sans renvoyer d’erreur lorsqu’une région est spécifiée pour un pays qui n’en a pas besoin.

<u>Résultats réels</u> :

La société n’est pas créée et l’erreur suivante est renvoyée :
`Error: Invalid value of "Dubai" provided for the region field.`

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : mises à niveau et correctifs > Appliquer des correctifs dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
