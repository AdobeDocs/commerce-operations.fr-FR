---
title: "ACSD-49389 : Prêt pour l’e-mail de récupération envoyé par l’API lorsqu’il n’est pas prêt pour la récupération"
description: Appliquez le correctif ACSD-49389 pour résoudre le problème Adobe Commerce en raison duquel un email prêt à être récupéré est envoyé par l’API lorsque la commande n’est pas prête pour la récupération.
feature: REST, Communications
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49389 : Prêt pour l’envoi d’un email de récupération par l’API lorsqu’il n’est pas prêt pour la récupération

Le correctif ACSD-49389 corrige le problème en raison duquel un email prêt à l’emploi est envoyé par l’API lorsque la commande n’est pas prête pour la récupération. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 est installé. L’ID de correctif est ACSD-49389. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [page d’entrée QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un message électronique prêt à l’emploi est envoyé par l’API lorsque la commande n’est pas prête pour la récupération.

<u>Étapes à reproduire</u> :

1. Activez la méthode *[!UICONTROL In-Store Delivery]*.
1. Créez une source de stock dont l’emplacement de récupération est activé.
1. Créez un nouveau stock à l&#39;aide du site web principal avec la source créée ci-dessus.
1. Créez un produit affectant la même source.
1. Définissez la quantité de stock = 1.
1. Consultez le produit créé à l’étape 4 à l’aide de la méthode *[!UICONTROL In-Store Delivery]* du storefront.
1. Créez une facture pour la commande.
1. Définissez la quantité du produit sur *0* et faites-la partir du stock.
1. Publiez la requête API suivante :

```
{
    "orderIds": [
        1
    ]
}
```

<u>Résultats attendus</u> :

Les emails prêts pour la récupération ne sont pas envoyés.

<u>Résultats réels</u> :

L’API renvoie *La commande n’est pas prête pour la récupération*, mais un courrier électronique prêt à être récupéré est envoyé.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) du guide [!DNL Quality Patches Tool].
