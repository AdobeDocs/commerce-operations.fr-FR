---
title: 'ACSD-51845 : impossible de mettre à jour les produits suivants avec des prix de niveau et différents jeux d’attributs via le [!DNL API] en bloc asynchrone'
description: Appliquez le correctif ACSD-51845 pour résoudre le problème d’Adobe Commerce en raison duquel vous ne pouvez pas mettre à jour les produits suivants avec des prix de niveau et différents jeux d’attributs par le biais de [!DNL REST API] en bloc asynchrones.
feature: REST, Products
role: Admin
exl-id: 83d97946-83da-4c1b-8f2a-21a64ee84e93
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%
---
# ACSD-51845 : impossible de mettre à jour les produits suivants avec des prix de niveau et différents jeux d’attributs via le [!DNL API] en bloc asynchrone

Le correctif ACSD-51845 corrige le problème en raison duquel vous ne pouvez pas mettre à jour les produits suivants avec des prix de niveau et différents ensembles d’attributs par le biais de [!DNL REST API] en bloc asynchrones. Ce correctif est disponible lorsque la version 1.1.35 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-51845. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mise à jour échoue pour les produits suivants avec des prix de niveau et différents jeux d’attributs via des [!DNL REST API] en bloc asynchrones.

<u>Procédure à suivre </u> :

1. Configurez [!DNL RabbitMQ].
1. Créez deux jeux d’attributs.
1. Créez deux **Produits simples**, en attribuant à chaque produit un jeu d’attributs différent.
1. Ajoutez un **prix du groupe client** pour chaque produit.
1. Mettez à jour les deux produits dans la même mise à jour de [!DNL API] en bloc.
1. Vérifiez que la commande `bin/magento queue:consumers:start async.operations.all` est en cours d’exécution.
1. Vérifiez le statut du [!DNL API] en bloc.

<u>Résultats attendus</u> :

L’exécution du service a réussi.

<u>Résultats réels</u> :

Le système renvoie le message d’erreur suivant : *Le produit n’a pas pu être enregistré. Veuillez réessayer.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
