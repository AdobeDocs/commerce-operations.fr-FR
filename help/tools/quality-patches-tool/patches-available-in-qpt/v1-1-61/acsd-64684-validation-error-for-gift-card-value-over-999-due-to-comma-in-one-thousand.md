---
title: 'ACSD-64684 : erreur de validation lors de l''enregistrement d''une carte cadeau d''une valeur supérieure à 999 en raison de la virgule en mille (1 000)'
description: Appliquez le correctif ACSD-64684 pour résoudre le problème Adobe Commerce où une erreur de validation se produit lors de l’enregistrement d’une carte cadeau d’une valeur supérieure à 999 en raison de la virgule « mille » (1 000).
feature: Catalog Management
role: Admin, Developer
source-git-commit: 58d385c0e3479f5f9d826dc6e892c8ec2ebfdbb5
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# ACSD-64684 : erreur de validation lors de l&#39;enregistrement d&#39;une carte cadeau d&#39;une valeur supérieure à 999 en raison de la virgule en mille (1 000)

Le correctif ACSD-64684 corrige le problème où une erreur de validation se produit lors de l&#39;enregistrement d&#39;une carte cadeau d&#39;une valeur supérieure à 999 en raison de la virgule dans « mille » (1 000). Ce correctif est disponible lorsque la version 1.1.61 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-64684. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur de validation se produit lors de l’édition et de l’enregistrement d’une carte cadeau d’une valeur supérieure à 999 en raison de la virgule (séparateur des milliers) dans le nombre, par exemple « mille » (1 000).

<u>Procédure à suivre </u> :

1. Créez un produit de carte cadeau.
   1. Saisissez 1 000 comme [!UICONTROL Amount].
   1. Cliquez sur **[!UICONTROL Save]**.

<u>Résultats attendus</u> :

* La nouvelle carte cadeau d&#39;un montant de 1 000 est économisée.

<u>Résultats réels</u> :

* Une erreur de validation se produit lorsque le montant de la carte cadeau est supérieur à 999.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
