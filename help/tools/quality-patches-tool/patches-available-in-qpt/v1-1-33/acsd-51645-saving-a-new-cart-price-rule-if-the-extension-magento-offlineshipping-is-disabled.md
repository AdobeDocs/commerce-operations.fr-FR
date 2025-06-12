---
title: 'ACSD-51645 : enregistrement d’une nouvelle règle de prix de panier si l’extension Magento_OfflineShipping est désactivée'
description: Appliquez le correctif ACSD-51645 pour résoudre le problème d’Adobe Commerce en raison duquel une erreur se produit lors de l’enregistrement d’une nouvelle règle de prix de panier si l’extension Magento_OfflineShipping est désactivée.
exl-id: ce747ae4-6d2f-41c0-ba75-7da72be359c7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-51645 : enregistrement d’une nouvelle règle de prix de panier si l’extension Magento_OfflineShipping est désactivée

Le correctif ACSD-51645 corrige le problème où une erreur se produit lors de l’enregistrement d’une nouvelle règle de prix de panier si l’extension Magento_OfflineShipping est désactivée. Ce correctif est disponible lorsque la version 1.1.33 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-51645. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Obtention d’une erreur lors de l’enregistrement d’une nouvelle règle de prix de panier si le `Magento_OfflineShipping` d’extension est désactivé.

<u>Procédure à suivre </u> :

1. Désactivez le module `Magento_OfflineShipping`.
1. Connectez-vous à **Admin**.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**.
1. Créez un nouveau **[!UICONTROL Cart Price Rule]**.
1. Renseignez les champs obligatoires.
1. Enregistrez le **[!UICONTROL Cart Price Rule]**.

<u>Résultats attendus</u> :

La règle de prix du panier a été enregistrée.

<u>Résultats réels</u> :

L’erreur suivante se produit :
`report.ERROR: Warning: Undefined array key "simple_free_shipping" in app/code/Magento/SalesRule/Controller/Adminhtml/Promo/Quote/Save.php on line 67 [] []`

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le guide de [!DNL Quality Patches Tool].
