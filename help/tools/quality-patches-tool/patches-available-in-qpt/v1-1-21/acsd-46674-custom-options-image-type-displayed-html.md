---
title: "ACSD-46674 : options personnalisées de type d’image affichées en tant qu’HTML dans les emails des clients"
description: Appliquez le correctif ACSD-46674 pour résoudre le problème Adobe Commerce en raison duquel les options personnalisées de type d’image s’affichaient comme HTML dans les emails des clients.
feature: Communications, Personalization
role: Developer
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-46674 : options personnalisées de type d’image affichées en tant qu’HTML dans les emails des clients

Le correctif ACSD-46674 corrige le problème en raison duquel les options personnalisées d’un type d’image s’affichent comme HTML dans les emails des clients. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.21 est installé. L’ID de correctif est ACSD-46674. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les options personnalisées d’un type d’image s’affichent en tant qu’HTML dans les emails des clients.

<u>Étapes à reproduire</u> :

1. Créez un produit avec une option personnalisée.
   * Type d’option : *File*
   * Extensions de fichiers compatibles : *png, jpg, gif*
   * Obligatoire : *Oui*
1. Placez une commande pour ce produit avec une image téléchargée en tant qu’option personnalisée.
1. Créez une facture pour la commande créée à l&#39;étape 2.
1. Créez un avoir.
1. Vérifiez tous les emails de confirmation.

<u>Résultats attendus</u> :

Les emails de confirmation affichent l’image téléchargée.

<u>Résultats réels</u> :

Les emails de confirmation contiennent du code HTML brut au lieu de l’image d’option personnalisée du produit.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tools] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans [!DNL QPT], reportez-vous à la section [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) du guide [!DNL Quality Patches Tool].
