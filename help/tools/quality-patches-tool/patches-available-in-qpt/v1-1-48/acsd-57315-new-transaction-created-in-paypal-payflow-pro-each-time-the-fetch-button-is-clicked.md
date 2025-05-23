---
title: 'ACSD-57315 : Une nouvelle transaction est créée dans  [!DNL PayPal Payflow Pro]  chaque fois que l’utilisateur clique sur le bouton de récupération.'
description: Appliquez le correctif ACSD-57315 pour corriger le problème Adobe Commerce en raison duquel une nouvelle transaction est créée dans  [!DNL PayPal Payflow Pro]  chaque fois que l’utilisateur clique sur le bouton de récupération dans l’écran d’affichage des transactions dans [!UICONTROL Admin].
feature: Payments
role: Admin, Developer
exl-id: 1fb8a5af-fda1-4c24-859d-d45424bde12f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-57315 : Une nouvelle transaction est créée dans [!DNL PayPal Payflow Pro] à chaque clic sur le bouton de récupération.

Le correctif ACSD-57315 corrige le problème en raison duquel une nouvelle transaction est créée dans [!DNL PayPal Payflow Pro] chaque fois que l’utilisateur clique sur le bouton de récupération dans l’écran d’affichage des transactions dans [!UICONTROL Admin]. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.48 est installé. L’ID de correctif est ACSD-57315. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une nouvelle transaction est créée dans [!DNL PayPal Payflow Pro] chaque fois que l’utilisateur clique sur le bouton de récupération dans l’écran d’affichage des transactions de [!UICONTROL Admin].

<u>Étapes à reproduire</u> :

1. Configurez [!DNL PayPal Payflow Pro].
1. Définissez la méthode de transaction sur *[!UICONTROL Sale]*.
1. Passez une commande à l’aide de la *carte de crédit*.
1. Ouvrez la transaction à partir de [!UICONTROL Admin].
1. Cliquez sur le bouton **[!UICONTROL Fetch]** .
1. Vérifiez le compte [!DNL PayPal] pour les transactions liées à la commande passée.

<u>Résultats attendus</u> :

Une nouvelle transaction de paiement n’est pas créée.

<u>Résultats réels</u> :

Une nouvelle transaction de paiement est créée pour une commande déjà payée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
