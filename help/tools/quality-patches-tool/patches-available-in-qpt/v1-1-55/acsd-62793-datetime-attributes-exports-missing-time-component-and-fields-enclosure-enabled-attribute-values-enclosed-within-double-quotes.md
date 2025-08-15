---
title: 'ACSD-62793 : les attributs Datetime dans les exportations ont un composant time manquant. En outre, si **[!UICONTROL Fields Enclosure]** est activé, les valeurs d’attribut sont placées entre guillemets doubles'
description: Appliquez le correctif ACSD-62793 pour résoudre le problème d’Adobe Commerce en raison duquel les attributs datetime dans les données exportées ne comportent pas le composant time. En outre, si **[!UICONTROL Fields Enclosure]** est activé, les valeurs d’attribut de la colonne *additional_attributes* sont placées entre guillemets doubles.
feature: Attributes, Data Import/Export, Catalog Service
role: Admin, Developer
exl-id: 340dcc84-dcb8-40ed-b2ab-2d950d1dd1ca
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-62793 : les attributs Datetime dans les exportations ont un composant time manquant. De plus, si **[!UICONTROL Fields Enclosure]** est activé, les valeurs d’attribut sont placées entre guillemets doubles

Le correctif ACSD-62793 corrige le problème en raison duquel les attributs datetime dans les données exportées ne contiennent pas le composant time. En outre, si **[!UICONTROL Fields Enclosure]** est activé, les valeurs d’attribut de la colonne *additional_attributes* sont placées entre guillemets doubles. Ce correctif est disponible lorsque la version 1.1.55 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62793. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les attributs Datetime des données exportées n’incluent pas le composant Heure. En outre, si **[!UICONTROL Fields Enclosure]** est activé, les valeurs d’attribut de la colonne *additional_attributes* sont placées entre guillemets doubles.

<u>Procédure à suivre </u> :

1. Créez un attribut de produit avec **[!UICONTROL Catalog Input Type for Store Owner]** = **[!UICONTROL Date and Time]**.
1. Attribuez l’attribut au jeu d’attributs **[!UICONTROL Default]**.
1. Créez un produit simple avec une valeur de date et d’heure pour le nouvel attribut.
1. Exportez le produit dans un fichier CSV depuis **[!UICONTROL System]** > *Transfert de données* > **[!UICONTROL Export]**.
1. Vérifiez la valeur de l’attribut dans la colonne *additional_attributes*. Il ne comporte que la partie date, mais pas l’heure.
1. Mettez à jour la valeur de l’attribut pour utiliser l’heure, par exemple « 08/10/22, 15:20 ».
1. Importez le fichier CSV.
1. Vérifiez la table *catalog_product_entity_datetime*.

<u>Résultats attendus</u> :

La date et l’heure sont correctement exportées et importées.

<u>Résultats réels</u> :

Seule la partie de date est exportée et importée.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
