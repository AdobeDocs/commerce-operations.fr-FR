---
title: 'ACSD-49389 : prêt pour l’e-mail de collecte envoyé par l’API lorsque non prêt pour la collecte'
description: Appliquez le correctif ACSD-49389 pour résoudre le problème d’Adobe Commerce où un e-mail prêt pour le retrait est envoyé par l’API lorsque la commande n’est pas prête pour le retrait.
feature: REST, Communications
role: Admin
exl-id: d1bc430a-3021-40d1-9091-db8ed9125619
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49389 : prêt pour l’e-mail de collecte envoyé par l’API lorsque non prêt pour la collecte

Le correctif ACSD-49389 corrige le problème en raison duquel un e-mail prêt pour le retrait est envoyé par l’API lorsque la commande n’est pas prête pour le retrait. Ce correctif est disponible lorsque la version 1.1.29 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-49389. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page de destination [QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un e-mail de prêt pour le retrait est envoyé par l’API lorsque la commande n’est pas prête pour le retrait.

<u>Procédure à suivre </u> :

1. Activez la méthode *[!UICONTROL In-Store Delivery]*.
1. Créez une source de stock avec l’emplacement de prélèvement activé.
1. Créez un nouveau stock à l’aide du site web principal avec la source créée ci-dessus.
1. Créez un produit affectant la même source.
1. Définir la quantité de stock = 1.
1. Consultez le produit créé à l’étape 4 à l’aide de la méthode *[!UICONTROL In-Store Delivery]* sur le storefront.
1. Créez une facture pour la commande.
1. Définissez la quantité du produit sur *0* et faites-le en rupture de stock.
1. Publiez la requête API suivante :

```
{
    "orderIds": [
        1
    ]
}
```

<u>Résultats attendus</u> :

L’e-mail Prêt pour la cueillette n’est pas envoyé.

<u>Résultats réels</u> :

L’API renvoie *La commande n’est pas prête pour l’enlèvement*, mais un e-mail prêt à l’enlèvement est envoyé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Patchs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
