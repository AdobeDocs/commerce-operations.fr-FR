---
title: 'ACSD-51890 : [!UICONTROL Submit review] bouton peut être cliqué plusieurs fois'
description: Appliquez le correctif ACSD-51890 pour résoudre le problème d’Adobe Commerce en raison duquel il est possible de cliquer plusieurs fois sur le bouton [!UICONTROL Submit Review] sans  [!DNL Google reCAPTCHA v3] .
feature: Products
role: Admin
exl-id: db69ccdc-c66e-4bdb-9783-772f2af0d33f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-51890 : **[!UICONTROL Submit Review]** bouton peut être cliqué plusieurs fois sans validation **[!DNL Google reCAPTCHA v3]**

>[!NOTE]
>
>Ce correctif est remplacé par [ACSD-55112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md).

Le correctif ACSD-51890 corrige le problème en raison duquel il est possible de cliquer plusieurs fois sur le bouton **[!UICONTROL Submit Review]** sans validation **[!DNL Google reCAPTCHA v3]**. Ce correctif est disponible lorsque la version 1.1.35 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-51890. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Vous pouvez cliquer plusieurs fois sur le bouton **[!UICONTROL Submit Review]** sans la validation **[!DNL Google reCAPTCHA v3]**.

<u>Procédure à suivre </u> :

1. Activez **[!DNL Google reCAPTCHA v3]** pour la révision du produit.
1. Ouvrez la page produit et accédez à la section **[!UICONTROL Review]** , puis assurez-vous que le [!DNL reCAPTCHA] est visible.
1. Remplissez le formulaire de révision et cliquez plusieurs fois sur le bouton **[!UICONTROL Submit Review]** aussi rapidement que possible.
1. Ouvrez la section **[!UICONTROL Review]** à partir de l’Administration.

<u>Résultats attendus</u>

Les révisions en double ne sont pas créées.

<u>Résultats réels</u>

Les révisions en double sont créées.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le guide de [!DNL Quality Patches Tool].
