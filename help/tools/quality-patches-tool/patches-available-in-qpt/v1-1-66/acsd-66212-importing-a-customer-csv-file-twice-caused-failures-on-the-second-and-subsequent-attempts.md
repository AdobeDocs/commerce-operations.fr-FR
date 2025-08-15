---
title: 'ACSD-66212 : l’importation du fichier CSV du client à deux reprises a provoqué des échecs lors de la deuxième tentative et des tentatives suivantes'
description: Appliquez le correctif ACSD-66212 pour résoudre le problème d’Adobe Commerce où l’importation d’un fichier CSV client provoquait deux fois des échecs lors de la deuxième tentative et des suivantes.
feature: Data Import/Export, Customers
role: Admin, Developer
exl-id: ae41f341-6ca3-405e-877a-35bdc3bc5623
source-git-commit: 5a36d0f0aaa9b7cf0ed30f0da8efac241523cf6b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# ACSD-66212 : l’importation du fichier CSV du client à deux reprises a provoqué des échecs lors de la deuxième tentative et des tentatives suivantes

Le correctif ACSD-66212 corrige le problème en raison duquel l’importation d’un fichier CSV client à deux reprises provoquait des échecs lors de la deuxième tentative et des tentatives suivantes. Ce correctif est disponible lorsque la version 1.1.66 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66212. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’importation d’un fichier CSV client à deux reprises a provoqué des échecs lors de la deuxième tentative et des suivantes.

<u>Procédure à suivre </u> :

Importez un fichier CSV contenant les données du client, y compris le statut du client.

<u>Résultats attendus</u> :

Le statut est correctement importé et exporté.

<u>Résultats réels</u> :

Une erreur se produit lors de l’import :

```
General system exception happened
Additional data: <div class="messages"><div class="message message-error error"><div data-ui-id="messages-message-error" >SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near " at line 1, query was: INSERT INTO company_advanced_customer_entity (customer_id*) VALUES </div></div></div>
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
