---
title: 'ACSD-60673 : [!UICONTROL Cart Price Rule] problème résolu pour plusieurs modes de paiement lors du passage en caisse'
description: Appliquez le correctif ACSD-60673 pour résoudre le problème d'Adobe Commerce où les remises d'un [!UICONTROL Cart Price Rule] qui utilise une condition de mode de paiement ne sont pas toujours répertoriées dans les totaux.
feature: Price Rules
role: Admin, Developer
exl-id: 2fe27959-5e5f-4d25-9f56-b0f8319fd562
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-60673 : [!UICONTROL Cart Price Rule] problème résolu pour plusieurs modes de paiement lors du passage en caisse

Le correctif ACSD-60673 corrige le problème où les escomptes d&#39;un [!UICONTROL Cart Price Rule] qui utilise une condition de mode de paiement ne sont pas toujours répertoriés dans les totaux. Ce correctif est disponible lorsque la version 1.1.52 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-60673. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La [!UICONTROL Cart Price Rule] de plusieurs modes de paiement lors du passage en caisse ne s’applique pas correctement au mode de paiement spécifique.

<u>Conditions préalables</u>

Assurez-vous que dans le **[!UICONTROL Multiple Payment Methods]** > **[!UICONTROL Money Order]** et **[!UICONTROL Bank Transfer]** est activé.

<u>Procédure à suivre </u> :

1. Activez **[!UICONTROL Multiple Payment Methods]**.
1. Créez un *[!UICONTROL Cart Price Rule]*.
   * Définir **[!UICONTROL Conditions]** : mode de paiement à **[!UICONTROL Money Order]** (ou virement bancaire)
   * Sélectionnez **[!UICONTROL Actions]** = *25 %* remise sur tous les produits
1. Créez un produit virtuel.
1. Pour copier un nouveau devis et un *[!UICONTROL Status]* client invité, rendez-vous sur le storefront et effacez les cookies.
1. Ajoutez le produit virtuel au panier.
1. Passez à *passage en caisse*.
1. Cliquez sur le mode de paiement qui a été défini dans le *[!UICONTROL Cart Price Rule]*.
1. Mettez à jour votre *[!UICONTROL Billing Address]*.
1. Assurez-vous que la remise est visible dans le montant total.
1. Cliquez sur la case à cocher pour modifier le mode de paiement.
1. Vérifiez que la remise est visible.

<u>Résultats attendus</u> :

La remise est visible dans *Totaux* après avoir coché la case pour passer à un mode de paiement applicable.

<u>Résultats réels</u> :

La remise n’est pas visible dans les *Totaux*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
