---
title: 'ACSD-52202 : La quantité de stock vendable par défaut passe à 0 par erreur lorsque le stock non par défaut est défini à 0 qté dans l''ordre'
description: Appliquez le correctif ACSD-52202 pour résoudre le problème d'Adobe Commerce où une quantité vendable de stock par défaut passe à 0 par erreur lorsque le stock non par défaut est défini sur 0 dans une commande.
feature: Inventory, Products
role: Admin
exl-id: 2ba5cc3b-9774-49f6-948f-371ab3c0c9df
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%
---
# ACSD-52202 : La quantité de stock vendable par défaut passe à 0 par erreur lorsque le stock non par défaut est défini sur 0 dans une commande

Le correctif ACSD-52202 corrige le problème où une quantité disponible en stock par défaut (qty) passe à 0 par erreur lorsque le stock non par défaut est défini sur 0 dans une commande. Ce correctif est disponible lorsque la version 1.1.35 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-52202. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La quantité disponible en stock par défaut passe à 0 en erreur lorsque le stock non par défaut est défini sur 0 dans une commande.

<u>Procédure à suivre </u> :

1. Connectez-vous à l’[!DNL Admin] .
1. Créez **website2**.
1. Créez une **source2** personnalisée.
1. Créez un **stock2** personnalisé.
1. Affectez les **source2** et **stock2** au **site web1** et la source et le stock par défaut au site web par défaut.
1. Créez un produit simple et attribuez **qty** = *10* pour la source par défaut et **qty** = *1* pour la source **source2**.
1. Passez une commande avec **qty** = *1* pour **website2**.
1. Créez une facture et une expédition.
1. Vérifiez le produit simple **quantité commercialisable**.

<u>Résultats attendus</u> :

La **quantité vendable** = *10* pour **source2**.

<u>Résultats réels</u> :

**quantité vendable** = *0* pour les deux sources.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
