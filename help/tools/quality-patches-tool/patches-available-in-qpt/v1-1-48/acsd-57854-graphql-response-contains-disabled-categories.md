---
title: 'ACSD-57854 : la réponse *GraphQL* contient des catégories désactivées qui ne doivent pas être répertoriées dans les agrégations de catégories'
description: Appliquez le correctif ACSD-57854 pour résoudre le problème d’Adobe Commerce où la réponse *GraphQL* contient des catégories désactivées qui ne doivent pas être répertoriées dans les agrégations de catégories.
feature: GraphQL
role: Admin, Developer
exl-id: 216aad2a-f470-49f9-b8ca-79107ca07891
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-57854 : la réponse *GraphQL* contient des catégories désactivées qui ne doivent pas être répertoriées dans les agrégations de catégories

Le correctif ACSD-57854 corrige le problème où la réponse *GraphQL* contient des catégories désactivées qui ne doivent pas être répertoriées dans les agrégations de catégories. Ce correctif est disponible lorsque la version 1.1.48 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-57854. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La réponse *GraphQL* contient des catégories désactivées qui ne doivent pas être répertoriées dans les agrégations de catégories.

<u>Procédure à suivre </u> :

1. Créez deux catégories.
1. Créez un produit (test de produit Adobe) et affectez-le aux deux catégories.
1. Désactivez l’une des catégories qui ont été créées.
1. Utilisez les produits *GraphQL* pour rechercher le produit.
1. Vérifiez la liste des catégories de produits dans la réponse *GraphQL*.

<u>Résultats attendus</u> :

Les catégories désactivées ne sont pas répertoriées dans la réponse *GraphQL*.

<u>Résultats réels</u> :

Les catégories désactivées sont répertoriées dans la réponse d’agrégation des catégories *GraphQL*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
