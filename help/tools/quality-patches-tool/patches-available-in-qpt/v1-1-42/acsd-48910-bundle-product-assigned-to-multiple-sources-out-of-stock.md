---
title: 'ACSD-48910 : le produit groupé affecté à plusieurs sources est en rupture de stock après la facture et l''expédition'
description: Appliquez le correctif ACSD-48910 pour résoudre le problème d’Adobe Commerce en raison duquel le produit groupé affecté à plusieurs sources est en rupture de stock après la facturation et l’expédition d’une commande, même si elle contient toujours une quantité différente de zéro.
feature: Products, Inventory
role: Admin, Developer
exl-id: c8d86531-2db5-4115-92d5-a8d391c4f75d
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
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
source-wordcount: '460'
ht-degree: 0%
---
# ACSD-48910 : le produit groupé affecté à plusieurs sources est en rupture de stock après la facture et l&#39;expédition

Le correctif ACSD-48910 corrige le problème où le produit groupé affecté à plusieurs sources est en rupture de stock après qu&#39;une commande a été facturée et expédiée, même si elle a toujours une quantité non nulle. Ce correctif est disponible lorsque la version 1.1.42 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-48910. Notez que le problème a été résolu dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le produit groupé affecté à plusieurs sources est en rupture de stock après la facturation et l’expédition, même s’il est toujours disponible.

<u>Procédure à suivre </u> :

1. Créez deux sites web.
1. Créez deux magasins/affichages de magasin (un par site web).
1. Créez deux produits simples (quantité = 10) et affectez-les à la fois aux stocks et aux sites Web.
1. Créez un produit groupé et ajoutez-y ces produits simples. Attribuez le produit groupé aux deux sites web.
1. Accédez à la vitrine et ajoutez le produit groupé au panier.
1. Extrayez et passez la commande.
1. De l’administrateur, facturez et expédiez la commande.

<u>Résultats attendus</u> :

Le produit groupé reste en stock car nous n&#39;avons acheté que 1 des 10 articles.

<u>Résultats réels</u> :

Le produit groupé passe à l’état en rupture de stock.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
