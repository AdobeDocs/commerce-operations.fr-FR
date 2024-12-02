---
title: 'MDVA-37364 : l’attribut client personnalisé de type date rompt l’interface utilisateur de la grille'
description: Le correctif MDVA-37364 résout le problème en raison duquel l’attribut client personnalisé de type date rompt l’interface utilisateur de la grille client. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID de correctif est MDVA-37364. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.4.
feature: Attributes, Cache
role: Developer
exl-id: 5bd64004-06c4-49fd-8e56-e2c44008ca82
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-37364 : l’attribut client personnalisé de type date rompt l’interface utilisateur de la grille

Le correctif MDVA-37364 résout le problème en raison duquel l’attribut client personnalisé de type date rompt l’interface utilisateur de la grille client. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID de correctif est MDVA-37364. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0-2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’attribut client personnalisé de type date rompt l’interface utilisateur de la grille client.

<u>Étapes à reproduire</u> :

1. Créez un attribut personnalisé de type date :
   * Accédez à **Magasins** > **Attributs** > **Ajouter un attribut**.
   * Définissez le Type d’entrée sur Date.
   * Définissez l’option Ajouter à la colonne sur Oui.
   * Enregistrez l’attribut .
1. Allez à **Admin** > **Clients** > **Tous les Clients**.
   * Ajoutez l’attribut personnalisé nouvellement ajouté à la grille à partir de l’option Colonnes.
1. Créez/Modifiez un client et définissez la valeur du champ d’attribut de date personnalisé créé.
1. Enregistrez, réindexez et effacez le cache.
1. Accédez à **Customers** > **Tous les clients**.
   * Vérifiez la grille client.

<u>Résultats attendus</u> :

La grille d’administration du client affiche toutes les données, y compris la nouvelle date et le nouvel attribut personnalisé, sans interrompre l’interface utilisateur de la grille client.

<u>Résultats réels</u> :

L’interface utilisateur de la grille client d’administration est rompue.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [Outil de correctifs de qualité publié : un nouvel outil pour appliquer des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
