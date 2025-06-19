---
title: 'ACSD-49480 : ignorer les règles suivantes qui ne fonctionnent pas'
description: Appliquez le correctif ACSD-49480 pour résoudre le problème d’Adobe Commerce en raison duquel le [!UICONTROL Cart Price Rule - Discard Subsequent Rules] ne fonctionne pas comme prévu.
feature: Price Rules
role: Admin
exl-id: 1919043b-99a8-46a2-94df-9285c05bec7b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-49480 : [!UICONTROL Cart Price Rule - Discard Subsequent Rules] ne fonctionne pas comme prévu

Le correctif ACSD-49480 corrige le problème en raison duquel le [!UICONTROL Cart Price Rule - Discard Subsequent Rules] ne fonctionne pas comme prévu. Ce correctif est disponible lorsque la version 1.1.32 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-49480. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] ne fonctionne pas comme prévu.

<u>Procédure à suivre </u> :

1. Créez un **[!UICONTROL Cart Price Rule]** avec un code de coupon (nommez-le *TEST*) qui accorde une remise de 10 $ au *ID de produit 1* dans l’onglet **[!UICONTROL Actions]** avec [!UICONTROL Discard Subsequent Rules] défini sur *[!UICONTROL Yes]* et [!UICONTROL Priority] défini sur *1*.
1. Créez un autre **[!UICONTROL Cart Price Rule]** sans code de coupon qui accorde une remise de 5 $ à *ID de produit 2* dans l’onglet **[!UICONTROL Actions]** avec [!UICONTROL Priority] défini sur *2*. Ici, nous supposons qu’il s’agit d’une vente mondiale pour *ID de produit 2*.
1. Accédez au site frontal et ajoutez *ID de produit 1* et *ID de produit 2* dans le panier.
1. Appliquez le code de coupon *TEST*.

<u>Résultats attendus</u>

* La *remise 1* est appliquée à *ID de produit 1*.
* La *remise 2* est appliquée à *ID de produit 2*.

<u>Résultats réels</u>

* Seule la *remise 1* est appliquée à *ID de produit 1*.
* *La remise 2* n’est pas appliquée à *ID de produit 2*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
