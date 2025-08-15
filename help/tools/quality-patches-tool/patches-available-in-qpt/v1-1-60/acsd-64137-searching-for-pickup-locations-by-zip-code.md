---
title: 'ACSD-64137 : la recherche d''emplacements de retrait par code postal ne fonctionne pas correctement pour la localisation en néerlandais'
description: Appliquez le correctif ACSD-64137 pour résoudre le problème où la recherche de lieux de retrait par code postal ne fonctionne pas correctement pour la localisation en néerlandais.
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 86c28b6d-6584-4caf-bd35-13e0c1bdcf1d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-64137 : La recherche de lieux de retrait par code postal ne fonctionne pas correctement pour la localisation en néerlandais

Le correctif ACSD-64137 corrige le problème en raison duquel la recherche d&#39;emplacements de retrait par code postal ne fonctionne pas correctement pour la localisation en néerlandais. Ce correctif est disponible lorsque la version 1.1.60 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-64137. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La recherche de code postal pour les Pays-Bas n’affiche pas de résultats sur la page de passage en caisse front-end. Toutefois, il fonctionne par ville et affiche l’adresse correspondante sans recherche.

<u>Procédure à suivre </u> :

1. Installez une instance propre avec les modules d’inventaire.
1. Créez un stock personnalisé.
1. Créez deux sources avec des adresses Pays-Bas et affectez-les au stock (codes postaux 7311ER et 7311AE).
1. Créez un produit simple et ajoutez un inventaire.
1. Activez **[!UICONTROL In-Store Delivery]** en accédant à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]**.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Distance Provider for Distance Based SSA]**. Définissez **[!UICONTROL Provider]** sur *Calcul hors ligne*.
1. Exécutez la commande suivante pour importer des noms géographiques pour le pays NL.

   ```bash
   bin/magento inventory-geonames:import NL
   ```

1. Ajoutez le produit au panier et passez à l’étape d’expédition.
1. Sélectionnez **[!UICONTROL Pick In Store]**. Cliquez ensuite sur **[!UICONTROL Select Other]** pour sélectionner d’autres magasins.
1. Saisissez *7311* ou *7311AE* dans le formulaire de recherche **[!UICONTROL Select Store]**.


**Résultats attendus** :

* Les magasins correspondants doivent être renseignés.

**Résultats réels** :

* Aucun résultat trouvé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
