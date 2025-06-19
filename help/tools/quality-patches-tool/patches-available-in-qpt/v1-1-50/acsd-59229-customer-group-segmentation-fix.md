---
title: 'ACSD-59229 : mauvaise affectation des données du groupe client en raison d’une valeur X-Magento-Vary obsolète'
description: Appliquez le correctif ACSD-59229 pour résoudre le problème d’Adobe Commerce où les informations relatives au groupe de clients sont enregistrées dans le mauvais segment en raison d’une valeur X-Magento-Vary obsolète dans la requête.
feature: Customers, Personalization, Marketing Tools
role: Admin, Developer
exl-id: c039c114-d920-4b05-b5e9-3e9b73490ee0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-59229 : mauvaise affectation des données du groupe client en raison d’une valeur X-Magento-Vary obsolète

Le correctif ACSD-59229 corrige le problème d’enregistrement des informations relatives au groupe de clients dans le mauvais segment en raison d’une valeur X-Magento-Vary obsolète dans la requête. Ce correctif est disponible lorsque la version 1.1.50 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-59229. Notez que le problème a été résolu dans la version 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les informations relatives au groupe de clients sont enregistrées dans le mauvais segment en raison d’une valeur X-Magento-Vary obsolète dans la requête.

<u>Conditions préalables</u> :

Assurez-vous qu’Adobe Commerce B2B avec des exemples de données est installé et que [!DNL Varnish] est configuré.

<u>Procédure à suivre </u> :

1. Configurez une tarification avancée pour le [!DNL SKU 24-MB01] :
   1. [!UICONTROL Regular price] = *9999$*
   1. [!UICONTROL Catalog and Tier Price] :
      * *En gros* = *200 $*
      * *Retailer* = *$30*

1. Créez deux comptes client.
1. Affectez les deux clients au groupe **en gros**.
1. Ouvrez deux sessions de navigateur différentes et connectez-vous avec chaque client.
1. Accédez à la page produit **[!UICONTROL 24-MB01]** pour chaque client et vérifiez que le prix affiché est de 200 **.
1. Remplacez le groupe de clients de l’un des clients par **Vente au détail**.
1. Effacez le cache à l’aide de la commande : `bin/magento cache:flush full_page`.
1. Actualisez la page produit pour chaque client.

<u>Résultats attendus</u> :

1. Le client au détail peut voir le prix correct de *$30* pour le produit.
1. Le client en gros peut voir le prix correct de *$200* pour le produit.

<u>Résultats réels</u> :

1. Le client au détail peut voir le prix correct de *$30* pour le produit.
1. Le client en gros voit un prix incorrect de *$30* (prix de détail) pour le produit.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
