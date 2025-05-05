---
title: 'ACSD-60804 : la modification d’un client associé à une société supprimée entraîne une erreur'
description: Appliquez le correctif ACSD-60804 pour résoudre le problème Adobe Commerce en raison duquel la modification d’un client associé à une entreprise supprimée entraîne une erreur *Appelez à une fonction membre getSuperUserId() sur null*.
feature: Companies, Customers, B2B
role: Admin, Developer
exl-id: 09241160-f5ed-41f8-8bb6-2bb8ed5cccd5
source-git-commit: 9d39b1045099a71d23f25ad1ef4932f78b1f33f0
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-60804 : la modification d’un client associé à une société supprimée entraîne une erreur

Le correctif ACSD-60804 corrige le problème en raison duquel la modification d’un client associé à une entreprise supprimée provoquait une erreur *L’appel à une fonction membre getSuperUserId() sur null*. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 est installé. L’ID de correctif est ACSD-60804. Veuillez noter que ce problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La modification d&#39;un client associé à une société supprimée provoque une erreur *L&#39;appel à une fonction membre getSuperUserId() sur null*.

<u>Conditions préalables :</u> :

Installez et activez les modules Adobe Commerce B2B.

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Settings]** > **[!UICONTROL B2B]** > **[!UICONTROL Enable Company]**.
1. Accédez à **[!UICONTROL Customers]** > **[!UICONTROL Company]** > **[!UICONTROL Create New Company]**.
1. Connectez-vous à `mysql` pour l’instance.
1. Supprimez la société où `entity_id` = *1*.
1. Accédez à **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Modifiez le client automatiquement créé lors de la création de la société.

<u>Résultats attendus</u> :

Le client est modifié sans erreur d’exception.

<u>Résultats réels</u> :

Une erreur se produit : *Appelez une fonction membre getSuperUserId() sur null* si aucune société n’est associée au client.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
