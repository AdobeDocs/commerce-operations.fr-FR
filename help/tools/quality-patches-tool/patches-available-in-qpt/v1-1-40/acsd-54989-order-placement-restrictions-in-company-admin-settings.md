---
title: 'ACSD-54989 : l’administrateur de la société ne peut pas commander lorsque [!UICONTROL Enable Purchase Orders] avez la valeur Oui et [!UICONTROL Purchase Order] la valeur Non'
description: Appliquez le correctif ACSD-54989 pour résoudre le problème d’Adobe Commerce en raison duquel l’administrateur de la société ne peut pas passer de commandes si [!UICONTROL Enable Purchase Orders] est défini sur Oui et [!UICONTROL Purchase Order] sur Non.
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
exl-id: 13830361-dd0c-486f-b07f-34280a17ab76
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
subfeature_v2:
  - id: 2d6d41d4-a5c1-5baf-8dbe-bf7300b68bb3
    internal-label: Purchase Orders
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
source-wordcount: '413'
ht-degree: 0%
---
# ACSD-54989 : l’administrateur de la société ne peut pas commander lorsque *[!UICONTROL Enable Purchase Orders]* avez la valeur *Oui* et *[!UICONTROL Purchase Order]* la valeur *Non*

Le correctif ACSD-54989 corrige le problème où les commandes ne peuvent pas être passées si **[!UICONTROL Enable Purchase Orders]** avez la valeur *Oui* et **[!UICONTROL Purchase Order]** la valeur *Non*. Ce correctif est disponible lorsque la version 1.1.40 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-54989. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les administrateurs de la société ne peuvent pas passer de commandes lorsque **[!UICONTROL Enable Purchase Orders]** est défini sur *Oui* et **Bon de commande** sur *Non*.

<u>Conditions préalables</u> :

Installez les modules [!DNL B2B].

<u>Procédure à suivre </u> :

1. Activez la société et laissez ** > **[!UICONTROL Purchase Order**] = *Non*.[!UICONTROL **Order Approval Configuration]
1. Créez un produit simple au prix de 100.
1. Créez une nouvelle entreprise via l’Administration.
1. Définissez [!UICONTROL **Activer les commandes fournisseur**] sur *Oui*.
1. Connectez-vous en tant qu’administrateur d’entreprise sur le storefront.
1. Ajoutez le produit simple créé au panier.
1. Accédez à la page de passage en caisse et cliquez sur **[!UICONTROL Place Order]** pour terminer l’achat.

<u>Résultats attendus</u> :

Vous pouvez passer une commande avec succès.

<u>Résultats réels</u> :

La page **[!UICONTROL My Account]** s’ouvre et la commande n’est pas passée.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
