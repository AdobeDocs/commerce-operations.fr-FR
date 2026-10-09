---
title: 'ACSD-54418 : montant de remise fixe ajouté de manière incorrecte au produit enfant d''une offre groupée tarifée dynamiquement'
description: Appliquez le correctif ACSD-54418 pour résoudre le problème d’Adobe Commerce en raison duquel le montant de remise fixe est incorrectement appliqué à chaque produit enfant du lot à prix dynamique.
feature: Shopping Cart
role: Admin, Developer
exl-id: f7b57361-9056-4eec-a393-dadb65aa595b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
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
source-wordcount: '403'
ht-degree: 0%
---
# ACSD-54418 : montant de remise fixe ajouté de manière incorrecte au produit enfant d&#39;une offre groupée à prix dynamique.

Le correctif ACSD-54418 corrige le problème où le montant de remise fixe est incorrectement appliqué à chaque produit enfant du lot à prix dynamique. Ce correctif est disponible lorsque la version 1.1.42 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-54418. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le montant de remise fixe est incorrectement appliqué à chaque produit enfant du lot à prix dynamique.

<u>Procédure à suivre </u> :

1. Créez un **[!UICONTROL bundle product]** avec une tarification dynamique et des options de bundle *2*.
1. Créez un **[!UICONTROL cart price rule]** avec un code de coupon spécifique qui s’applique uniquement au **[!UICONTROL SKU]** de produits groupés et qui bénéficie d’une remise fixe.
1. Ajoutez le produit groupé au panier.
1. Appliquez le **[!UICONTROL coupon code]** .
1. Vérifiez la remise appliquée au panier.

<u>Résultats attendus</u> :

La remise n’est appliquée qu’une seule fois à l’ensemble du produit groupé.

<u>Résultats réels</u> :

La remise est appliquée à chaque produit enfant du lot.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
