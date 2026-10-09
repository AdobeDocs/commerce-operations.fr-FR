---
title: 'ACSD-47669 : erreur de serveur interne lors de l’importation de produits avec des options personnalisables'
description: Appliquez le correctif ACSD-47669 pour résoudre le problème d’Adobe Commerce en raison d’une erreur de serveur interne lors de l’importation de produits avec des options personnalisables.
feature: Products
role: Admin, Developer
exl-id: e1a3b3b4-0392-4325-9766-a83276c1a593
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%
---
# ACSD-47669 : erreur de serveur interne lors de l’importation de produits avec des options personnalisables

Le correctif ACSD-47669 corrige le problème d’erreur de serveur interne lors des importations de produits avec des options personnalisables. Ce correctif est disponible lorsque la version 1.1.38 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-47669. Notez que le problème est déjà résolu dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur de serveur interne se produit lors de l’importation de produits avec des options personnalisables.

<u>Procédure à suivre </u> :

1. Créez une vue de magasin supplémentaire. Assurez-vous d’avoir 2 vues de magasin, par exemple, en, UK.
1. Créez deux produits simples, par exemple prod1 et prod2.
1. Préparez un fichier CSV qui ajoute des options personnalisées pour les deux produits dans chaque vue de magasin et pour la portée **Toutes les vues de magasin**. Importez ce fichier CSV.
1. Préparez un autre fichier CSV contenant deux enregistrements. Le premier enregistrement doit servir à mettre à jour les options personnalisées de &#39;prod1&#39; spécifiquement pour la portée d&#39;affichage du magasin au Royaume-Uni et le second enregistrement doit servir à mettre à jour les options personnalisées de &#39;prod2&#39; pour la portée **All Store View**. Importez ce deuxième fichier CSV.

<u>Résultats attendus</u> :

Vous devriez être en mesure de personnaliser les options sans erreur.

<u>Résultats réels</u> :

Une erreur de violation de contrainte d’intégrité se produit.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
