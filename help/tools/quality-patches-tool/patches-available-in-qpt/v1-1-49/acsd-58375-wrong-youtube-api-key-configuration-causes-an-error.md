---
title: 'ACSD-58375 : une clé API YouTube mal configurée entraîne une erreur lors de l’ajout de vidéo au niveau de la vue du magasin'
description: Appliquez le correctif ACSD-58375 pour résoudre le problème d’Adobe Commerce où une configuration incorrecte de la clé API YouTube provoque une erreur lors de l’ajout d’une vidéo YouTube au niveau de la vue du magasin.
feature: Catalog Management, Configuration
role: Admin, Developer
exl-id: 24187308-d9dc-4ce2-9cfa-70ccb7726a5b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-58735 : une clé API YouTube mal configurée entraîne une erreur lors de l’ajout de vidéo au niveau de la vue du magasin

Le correctif ACSD-58735 corrige le problème en raison duquel une configuration incorrecte de la clé API YouTube provoque une erreur lors de l’ajout d’une vidéo YouTube au niveau de la vue du magasin. Ce correctif est disponible lorsque la version 1.1.49 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-58735. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une mauvaise configuration de la clé API YouTube entraîne une erreur lors de l’ajout d’une vidéo YouTube au niveau de l’affichage du magasin.

<u>Procédure à suivre </u> :

1. Accédez à Admin > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Video]**.
1. Remplacez *Portée* par le niveau *[!UICONTROL Main Website]*.
1. Ajoutez la clé API YouTube.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Sélectionnez un produit et faites défiler l’écran jusqu’à *[!UICONTROL Images and Video]*. Cliquez sur **[!UICONTROL Add Video]**.
1. Copiez un lien vidéo YouTube et collez-le dans le champ Lien vidéo . Sortez du champ .

<u>Résultats attendus</u> :

La clé API YouTube a une portée globale et est masquée au niveau du site web.

<u>Résultats réels</u> :

L’erreur suivante est générée : *La vidéo n’est pas affichée pour la raison suivante : clé API non valide. Transmettez une clé API valide*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
