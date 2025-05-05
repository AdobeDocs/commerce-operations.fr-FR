---
title: 'ACSD-60441 : la mise à jour des clients via le point d’entrée V1/customers [!DNL REST] API renvoie une erreur'
description: Appliquez le correctif ACSD-60441 pour résoudre le problème Adobe Commerce en raison duquel la mise à jour des clients via l’API V1/customers [!DNL REST] lors de l’utilisation d’un jeton d’accès à l’intégration généré à partir du serveur principal renvoie une erreur.
feature: REST, Customers
role: Admin, Developer
exl-id: 3936c065-41a6-4860-8313-e054f9b23ac7
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-60441 : la mise à jour des clients via le point d’entrée de l’API `V1/customers` [!DNL REST] renvoie une erreur

Le correctif ACSD-60441 corrige le problème en raison duquel la mise à jour des clients via l’API `V1/customers` [!DNL REST] lors de l’utilisation du jeton d’accès d’intégration généré à partir du serveur principal entraîne une erreur. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 est installé. L’ID de correctif est ACSD-60441. Veuillez noter que ce problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p8

**Compatible avec les versions Adobe Commerce**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p9, 2.4.5-p8, 2.4.6-p6, 2.4.7-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mise à jour des clients via le point d’entrée de l’API `V1/customers` [!DNL REST] lors de l’utilisation du jeton d’accès à l’intégration généré à partir du serveur principal renvoie une erreur.

<u>Étapes à reproduire</u> :

1. Créez une intégration à partir de l’administrateur.
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

    &quot;json
    &lbrace;
    &quot;message&quot; : &quot;Un client avec la même adresse électronique existe déjà dans un site Web associé.&quot;,
    &quot;trace&quot;: ...
    
    &quot;

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
