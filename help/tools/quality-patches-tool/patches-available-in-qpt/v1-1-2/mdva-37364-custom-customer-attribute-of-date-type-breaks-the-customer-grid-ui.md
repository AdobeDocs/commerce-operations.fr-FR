---
title: 'MDVA-37364 : l’attribut client personnalisé de type date rompt l’interface utilisateur de la grille.'
description: Le correctif MDVA-37364 résout le problème en raison duquel l’attribut client personnalisé de type date rompt l’interface utilisateur de la grille client. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID du correctif est MDVA-37364. Notez que le problème est planifié pour être corrigé dans la version 2.4.4 d’Adobe Commerce.
feature: Attributes, Cache
role: Developer
exl-id: 5bd64004-06c4-49fd-8e56-e2c44008ca82
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-37364 : l’attribut client personnalisé de type date rompt l’interface utilisateur de la grille.

Le correctif MDVA-37364 résout le problème en raison duquel l’attribut client personnalisé de type date rompt l’interface utilisateur de la grille client. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID du correctif est MDVA-37364. Notez que le problème est planifié pour être corrigé dans la version 2.4.4 d’Adobe Commerce.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0-2.4.2-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’attribut client personnalisé de type date rompt l’interface utilisateur de grille client.

<u>Procédure à suivre </u> :

1. Créez un attribut personnalisé avec le type de date :
   * Accédez à **Magasins** > **Attributs** > **Ajouter un attribut**.
   * Définissez le Type d’entrée sur Date.
   * Définissez les options Ajouter à la colonne sur Oui.
   * Enregistrez l’attribut.
1. Accédez à **Admin** > **Clients** > **Tous les clients**.
   * Ajoutez l’attribut personnalisé nouvellement ajouté à la grille à partir de l’option Colonnes .
1. Créez/modifiez un client et définissez la valeur du champ d’attribut de date personnalisé créé.
1. Enregistrez, réindexez et effacez le cache.
1. Accédez à **Clients** > **Tous les clients**.
   * Vérifiez la grille client.

<u>Résultats attendus</u> :

La grille client d’administration affiche toutes les données, y compris le nouvel attribut personnalisé de date, sans rompre l’interface utilisateur de la grille client.

<u>Résultats réels</u> :

L’interface utilisateur de la grille cliente d’administration est endommagée.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* [Publication de l’outil de correctifs de qualité : un nouvel outil pour appliquer des correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
