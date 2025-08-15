---
title: 'ACSD-51845 : impossible de mettre à jour les produits suivants avec des prix de niveau et différents jeux d’attributs via un bloc asynchrone [!DNL API]'
description: Appliquez le correctif ACSD-51845 pour résoudre le problème Adobe Commerce en raison duquel vous ne pouvez pas mettre à jour les produits suivants avec des prix de niveau et différents jeux d’attributs par le biais d’une mise à jour en bloc asynchrone [!DNL REST API].
feature: REST, Products
role: Admin
exl-id: 83d97946-83da-4c1b-8f2a-21a64ee84e93
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
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
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

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
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
