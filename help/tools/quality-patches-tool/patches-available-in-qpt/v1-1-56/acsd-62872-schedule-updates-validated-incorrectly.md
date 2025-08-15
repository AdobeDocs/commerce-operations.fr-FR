---
title: 'ACSD-62872 : les mises à jour de planification ne sont pas validées correctement'
description: Appliquez le correctif ACSD-62872 pour résoudre le problème d’Adobe Commerce avec la validation d’attribut unique où les mises à jour planifiées sont validées de manière incorrecte.
feature: Catalog Management, Admin Workspace
role: Admin, Developer
exl-id: bd0d452b-aae3-4682-8a2c-471a7f8bf132
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# ACSD-62872 : les mises à jour de planification ne sont pas validées correctement

Le correctif ACSD-62872 corrige le problème lié à la validation d’attributs uniques lorsque les mises à jour planifiées sont validées de manière incorrecte. Ce correctif est disponible lorsque la version 1.1.56 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62872. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif est marqué comme obsolète pour les versions 2.4.4 à 2.4.6-p8 dans la version 1.1.58 de QPT.

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mise à jour planifiée d’un attribut personnalisé est incorrectement validée.

<u>Procédure à suivre </u> :

1. Créez un attribut personnalisé pour les catégories.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Créez une nouvelle catégorie.
1. Dans la même catégorie, accédez à la section **[!UICONTROL Scheduled Updates]** .
1. Configurez une nouvelle mise à jour pour cette catégorie à tout moment ultérieur.
1. Avant de commencer la mise à jour planifiée, essayez de modifier la mise à jour planifiée créée pour la catégorie.

<u>Résultats attendus</u> :

Doit pouvoir mettre à jour la mise à jour planifiée.

<u>Résultats réels</u> :

Une erreur est générée : *La valeur de l’attribut « Attribut personnalisé » n’est pas unique. Définissez une valeur unique et réessayez.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
