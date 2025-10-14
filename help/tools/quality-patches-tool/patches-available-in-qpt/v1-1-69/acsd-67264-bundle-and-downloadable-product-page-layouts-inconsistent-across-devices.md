---
title: 'ACSD-67264 : offres groupées et mises en page de produits téléchargeables incohérentes entre les appareils'
description: Appliquez le correctif ACSD-67264 pour corriger le bundle Adobe Commerce et les pages téléchargeables ont rencontré des problèmes de mise en page en raison d’un réarrangement du bloc de médias d’informations sur le produit.
feature: Page Content, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9b6794366ba552d86cdfc6a3d6f699c307fcd8f6
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---


# ACSD-67264 : offres groupées et mises en page de produits téléchargeables incohérentes entre les appareils

Le correctif ACSD-67264 corrige le problème d’incohérence des mises en page des lots et des pages de produits téléchargeables entre les appareils. Ce correctif est disponible lorsque la version 1.1.69 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-67264. Ce problème a été résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Des problèmes de mise en page se sont produits lors du regroupement et du téléchargement des pages produit en raison d’un réarrangement du bloc de médias d’informations sur le produit.

<u>Procédure à suivre </u> :

1. Installez les données d’exemple.
1. Ouvrez la page du bundle de produits et vérifiez la mise en page sur le bureau.
1. Ajoutez la page du bundle de produits à la liste de souhaits, accédez à la liste de souhaits, cliquez sur l’icône de modification, puis vérifiez la mise en page.
1. Répétez les étapes 2 et 3 pour un produit téléchargeable.

<u>Résultats attendus</u> :

La PDP du produit groupé est générée sans aucun problème.

<u>Résultats réels</u> :

La PDP du produit groupé est rendue avec des espaces aléatoires.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool]
* Adobe Commerce sur les infrastructures cloud : [&#x200B; Mises à niveau et correctifs > Appliquer des correctifs &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
