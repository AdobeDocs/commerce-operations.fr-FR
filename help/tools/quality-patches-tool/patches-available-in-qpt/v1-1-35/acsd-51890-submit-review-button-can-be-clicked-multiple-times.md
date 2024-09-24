---
title: 'ACSD-51890 : [!UICONTROL Submit review] vous pouvez cliquer plusieurs fois'
description: Appliquez le correctif ACSD-51890 pour résoudre le problème Adobe Commerce où l’utilisateur peut cliquer plusieurs fois sur le bouton [!UICONTROL Submit Review] sans validation [!DNL Google reCAPTCHA v3] .
feature: Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Le bouton ACSD-51890 : **[!UICONTROL Submit Review]** peut être cliqué plusieurs fois sans validation **[!DNL Google reCAPTCHA v3]**

>[!NOTE]
>
>Ce correctif est remplacé par [ACSD-55112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md).

Le correctif ACSD-51890 corrige le problème en raison duquel il est possible de cliquer plusieurs fois sur le bouton **[!UICONTROL Submit Review]** sans validation **[!DNL Google reCAPTCHA v3]**. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.35 est installé. L’ID de correctif est ACSD-51890. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Vous pouvez cliquer plusieurs fois sur le bouton **[!UICONTROL Submit Review]** sans validation **[!DNL Google reCAPTCHA v3]**.

<u>Étapes à reproduire</u> :

1. Activez **[!DNL Google reCAPTCHA v3]** pour la révision du produit.
1. Ouvrez la page du produit, accédez à la section **[!UICONTROL Review]** et vérifiez que [!DNL reCAPTCHA] est visible.
1. Remplissez le formulaire de révision et cliquez plusieurs fois sur le bouton **[!UICONTROL Submit Review]** aussi rapidement que possible.
1. Ouvrez la section **[!UICONTROL Review]** depuis Admin.

<u>Résultats attendus</u>

Les révisions en double ne sont pas créées.

<u>Résultats réels</u>

Des révisions en double sont créées.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le guide [!DNL Quality Patches Tool].
