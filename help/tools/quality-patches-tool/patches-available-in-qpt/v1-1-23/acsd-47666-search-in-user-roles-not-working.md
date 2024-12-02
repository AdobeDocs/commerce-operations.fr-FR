---
title: 'ACSD-47666 : la recherche dans [!UICONTROL User Roles] ne fonctionne pas'
description: Appliquez le correctif ACSD-47666 pour résoudre le problème Adobe Commerce où la fonction de filtrage sur [!UICONTROL User Roles] ne fonctionne pas comme prévu.
feature: Roles/Permissions, Search
role: Admin
exl-id: fb66f114-b95c-402e-a35a-e552f264966c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-47666 : la recherche dans **[!UICONTROL User Roles]** ne fonctionne pas

Le correctif ACSD-47666 résout le problème où la recherche dans **[!UICONTROL User Roles]** ne fonctionne pas. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23 est installé. L’ID de correctif est ACSD-47666. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La fonction de filtre sur **[!UICONTROL User Roles]** ne fonctionne pas comme prévu.

<u>Étapes à reproduire</u> :

1. Connectez-vous à l’administrateur Adobe Commerce > **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**.
1. Ouvrez un rôle existant dans la liste.
1. Ouvrez l’onglet **[!UICONTROL Role Users]** .
1. Saisissez une requête dans une colonne.
1. Appuyez sur Entrée.

<u>Résultats attendus</u> :

La fonction de filtre **[!UICONTROL User Roles]** doit filtrer les résultats en fonction de la requête.

<u>Résultats réels</u> :

Chargement infini avec l’erreur de console _(index):9 Uncaught TypeError: Cannot read properties of null (lecture de &#39;down&#39;)_.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure. 

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
