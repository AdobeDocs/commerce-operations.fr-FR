---
title: 'ACSD-58739 : La réindexation partielle renvoie une erreur'
description: Appliquez le correctif ACSD-55241 pour résoudre le problème Adobe Commerce où la réindexation partielle renvoie une erreur.
feature: Inventory, Products
role: Admin, Developer
exl-id: b4e6b8b4-43de-4434-94fb-6269a75e1c28
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# ACSD-58739 : La réindexation partielle renvoie une erreur

Le correctif ACSD-58739 corrige le problème lorsque la réindexation partielle renvoie une erreur. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49 est installé. L’ID de correctif est ACSD-58739. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 à 2.4.8

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La réindexation partielle renvoie une erreur.

<u>Étapes à reproduire</u> :

1. Ajoutez des paramètres de connexion esclave à `app/etc/ev.php`.
1. Générez jusqu’à 1 000 produits et exécutez la commande suivante :

   ```
   bin/magento index:reindex
   ```

1. Ajoutez les ID de produit générés dans la table `catalogsearch_fulltext_cl` DB.

   ```
   insert into catalogsearch_fulltext_cl (entity_id) select entity_id from catalog_product_entity;
   ```

1. Exécutez la commande suivante pour déclencher la réindexation partielle :

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1 
   ```

1. Vérifiez le fichier `var/log/support_report.log`.

<u>Résultats attendus</u>

Aucune erreur.

<u>Résultats réels</u> :

*Erreur de table ou de vue de base introuvable* lors de l’exécution de la réindexation partielle.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool]
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide d’infrastructure Commerce on Cloud

## Lecture connexe

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].
* [ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
