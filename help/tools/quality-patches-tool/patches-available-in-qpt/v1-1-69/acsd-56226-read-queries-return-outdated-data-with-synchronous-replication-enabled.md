---
title: 'ACSD-56226 : les requêtes de LECTURE renvoient des données obsolètes avec « synchronous_replication » activé'
description: Appliquez le correctif ACSD-56226 pour résoudre le problème d’Adobe Commerce où les requêtes READ renvoient des données obsolètes lorsque l’indicateur « synchronous_replication » est activé pour une connexion esclave sur le cloud.
feature: System
role: Admin, Developer
type: Troubleshooting
source-git-commit: a45cef14b7b37f1112d2ef82adf29b09d63b8e2b
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---


# ACSD-56226 : les requêtes de LECTURE renvoient des données obsolètes avec l’option `synchronous_replication` activée

Le correctif ACSD-56226 corrige le problème où les requêtes READ renvoient des données obsolètes lorsque l’indicateur `synchronous_replication` est activé pour la connexion esclave sur le cloud. Ce correctif est disponible lorsque la version 1.1.69 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-56226. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les requêtes READ renvoient des données obsolètes lorsque l’indicateur `synchronous_replication` est activé. La connexion esclave est alors désactivée, ce qui entraîne une surcharge de la base de données.

<u>Procédure à suivre </u> :

1. Définissez `MYSQL_USE_SLAVE_CONNECTION` sur *true* dans les variables d’environnement d’Adobe Commerce sur l’infrastructure cloud.
1. Ajoutez la configuration suivante à `.magento.env.yaml` pour définir `synchronous_replication` sur *false* :

   ```
   DATABASE_CONFIGURATION:
     _merge: true
     slave_connection:
       default:
         synchronous_replication: false
   ```

1. Redéployez et effectuez des actions front-end telles que la connexion, l’ajout au panier ou la commande.

<u>Résultats attendus</u> :

La connexion esclave reste activée lorsque `synchronous_replication` est défini sur *false*.

<u>Résultats réels</u> :

La connexion esclave est désactivée lorsque `synchronous_replication` est défini sur *false*, ce qui entraîne une surcharge de la base de données.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
