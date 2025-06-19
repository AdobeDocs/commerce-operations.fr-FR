---
title: 'ACSD-51884 : chemin d’accès au cache de l’image du produit incorrect sur la commande de redimensionnement'
description: Appliquez le correctif ACSD-51884 pour résoudre le problème d’Adobe Commerce en raison duquel le chemin d’accès au cache de l’image du produit devient incorrect après l’exécution de la commande de redimensionnement.
feature: Products
role: Admin
exl-id: a3779e4b-2749-460e-a0a8-656b26bb06fa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-51884 : chemin d’accès au cache de l’image du produit incorrect sur la commande de redimensionnement

Le correctif ACSD-51884 corrige le problème d’erreur interne où le chemin d’accès au cache de l’image du produit devient incorrect après l’exécution de la commande de redimensionnement. Ce correctif est disponible lorsque la version 1.1.37 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-51884. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 à 2.4.7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le chemin d’accès au cache de l’image du produit devient incorrect lors de la commande de redimensionnement.

<u>Procédure à suivre </u> :

1. Créez un site web/magasin/magasin.
1. Créez un produit, affectez-le aux deux sites web et chargez l’image du produit.
1. Créez un thème (voir le fichier Adobe.zip joint).
1. Dans `app/design/Adobe/theme/etc/view.xml` modification :

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">1</var>
</vars>
```

vers

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">0</var>
</vars>
```

1. Appliquez le thème au magasin créé précédemment.
1. Consultez la page produit sur le 2e site web. L’image du produit s’affiche correctement.
1. Utiliser le cache de vidage :
   `bin/magento cache:flush`
1. Consultez la page produit sur le 2e site web.

<u>Résultats attendus</u> :

L’image du produit s’affiche correctement.

<u>Résultats réels</u> :

L’image du produit n’existe pas.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
