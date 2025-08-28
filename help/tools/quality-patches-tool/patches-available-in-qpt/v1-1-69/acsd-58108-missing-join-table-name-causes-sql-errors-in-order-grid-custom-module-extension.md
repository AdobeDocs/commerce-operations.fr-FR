---
title: 'ACSD-58108 : des erreurs SQL se produisent dans l’extension du module personnalisé de la grille de commande en raison d’un nom de table de jointure manquant'
description: Appliquez le correctif ACSD-58108 pour résoudre le problème d’Adobe Commerce où un nom de table de jointure manquant dans l’extension du module personnalisé de grille de commande provoque des erreurs SQL lors du filtrage de certaines colonnes.
feature: Orders, System
role: Admin, Developer
type: Troubleshooting
source-git-commit: 26009fee51fb81e2517ad09319bac1190d127564
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# ACSD-58108 : des erreurs SQL se produisent dans l’extension du module personnalisé de la grille de commande en raison d’un nom de table de jointure manquant

Le correctif ACSD-58108 corrige le problème où un nom de table de jointure manquant dans l’extension du module personnalisé de grille de commande provoque des erreurs SQL lors du filtrage de certaines colonnes. Ce correctif est disponible lorsque la version 1.1.69 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-58108. Notez que ce problème doit être résolu dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.7-p6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le nom de la table de jointure manquant dans la table de récupération d&#39;origine entraîne des erreurs SQL dans la grille de commande lors de l&#39;utilisation d&#39;une extension de module personnalisé. Ce problème se produit, car la fonction `addFilterToMap` ne fonctionne pas pour certaines colonnes après la jonction de la table **[!UICONTROL sales_order_item]**, ce qui entraîne des erreurs lors du filtrage.

<u>Procédure à suivre </u> :

&#x200B;01. Installez une instance de développement 2.4.
&#x200B;02. Créez une commande.
&#x200B;03. Installez un module personnalisé avec une extension SQL.
&#x200B;04. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
&#x200B;05. Appliquez le filtre **[!UICONTROL Purchase Date]** et attendez le résultat.
&#x200B;06. Appliquez **[!UICONTROL Product SKU]** filtre .

<u>Résultats attendus</u> :

Le filtrage des ordres dans la grille de commandes fonctionne sans erreur.

<u>Résultats réels</u> :

Une erreur se produit lors de l’application de filtres dans la grille de commande.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
