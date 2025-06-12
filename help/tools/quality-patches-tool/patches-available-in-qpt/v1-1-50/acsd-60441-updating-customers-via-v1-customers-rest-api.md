---
title: 'ACSD-60441 : la mise à jour des clients via le point d’entrée V1/customers [!DNL REST] API renvoie une erreur'
description: Appliquez le correctif ACSD-60441 pour résoudre le problème d’Adobe Commerce où la mise à jour des clients via V1/customers [!DNL REST] API lors de l’utilisation du jeton d’accès à l’intégration généré à partir du serveur principal renvoie une erreur.
feature: REST, Customers
role: Admin, Developer
exl-id: 3936c065-41a6-4860-8313-e054f9b23ac7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-60441 : la mise à jour des clients via `V1/customers` point d’entrée de [!DNL REST] API renvoie une erreur

Le correctif ACSD-60441 corrige le problème en raison duquel la mise à jour des clients via `V1/customers` API [!DNL REST] lors de l’utilisation du jeton d’accès à l’intégration généré à partir du serveur principal entraînait une erreur. Ce correctif est disponible lorsque la version 1.1.50 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-60441. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p8

**Compatible avec les versions Adobe Commerce**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p9, 2.4.5-p8, 2.4.6-p6, 2.4.7-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mise à jour des clients via `V1/customers` point d’entrée de l’API [!DNL REST] lors de l’utilisation du jeton d’accès à l’intégration généré depuis le serveur principal renvoie une erreur.

<u>Procédure à suivre </u> :

1. Créez une intégration à partir de l’administration.
1. Envoyez une requête [!DNL POST] à `rest/default/V1/customers/<customer_id>` à l’aide du jeton d’intégration.

   ```json
   {
     "customer": {
       "email": "roni_cost@example.com",
       "firstname": "Veronica",
       "lastname": "Costello"
     }
   }
   ```

<u>Résultats attendus</u> :

Les données client sont mises à jour.

<u>Résultats réels</u> :

Vous obtenez l’erreur suivante :

    «json
    &lbrace;
    « message »: « Un client avec la même adresse e-mail existe déjà dans un site web associé. »,
    « trace »: ...
    &rbrace;
     »

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
