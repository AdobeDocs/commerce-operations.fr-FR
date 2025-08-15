---
title: 'ACSD-65787 : SchemaBuilder se bloque lors de la création ou de la mise à jour du schéma en raison d’une « colonne » de clé de tableau non définie dans les données du tableau'
description: Appliquez le correctif ACSD-65787 pour résoudre le problème d’Adobe Commerce où la classe SchemaBuilder se bloque lors de la création ou des mises à jour de schémas en raison d’une « colonne » de clé de tableau non définie lors du traitement des données de table.
feature: Backend Development, Deploy
role: Admin, Developer
exl-id: c01d1799-13fe-4657-a480-698efbe45a30
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# ACSD-65787 : `SchemaBuilder` se bloque lors de la création ou de la mise à jour du schéma en raison d’une « colonne » de clé de tableau non définie dans les données du tableau

Le correctif ACSD-65787 corrige le problème où `SchemaBuilder` classe plante lors de la création ou des mises à jour de schémas en raison d’une « colonne » de clé de tableau non définie lors du traitement des données de table. Ce correctif est disponible lorsque la version 1.1.64 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-65787. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La classe `SchemaBuilder` se bloque lors de la création ou des mises à jour du schéma en raison d’une « colonne » de clé de tableau non définie lors du traitement des données de la table.

<u>Procédure à suivre </u> :

1. Exécutez la commande suivante :

```
bin/magento setup:upgrade
```

<u>Résultats attendus</u> :

Aucune erreur.

<u>Résultats réels</u> :

```
Error "Warning: Undefined array key "column" in SchemaBuilder.php on line 90
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
