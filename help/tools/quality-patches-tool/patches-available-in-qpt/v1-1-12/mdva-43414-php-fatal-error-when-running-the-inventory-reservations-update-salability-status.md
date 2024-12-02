---
title: 'MDVA-43414 : erreur fatale PHP lors de l’exécution de "inventory.reserve.updateSalabilityStatus"'
description: Le correctif MDVA-43414 résout l’erreur fatale PHP qui se produit lors de l’exécution du consommateur de file d’attente `inventory.reserve.updateSalabilityStatus` sur les SKU numériques. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID de correctif est MDVA-43414. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.
feature: Inventory, Orders
role: Admin
exl-id: 893a5665-ff1b-4862-a984-d9abf642fba3
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-43414 : erreur fatale PHP lors de l’exécution de &quot;inventory.reserve.updateSalabilityStatus&quot;

Le correctif MDVA-43414 résout l’erreur fatale PHP qui se produit lors de l’exécution du consommateur de file d’attente `inventory.reservations.updateSalabilityStatus` sur les SKU numériques. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID de correctif est MDVA-43414. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.6 - 2.3.7-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur fatale PHP se produit lors de l’exécution du consommateur de file d’attente &quot;inventory.reserve.updateSalabilityStatus&quot; sur des SKU numériques.

<u>Conditions préalables</u> :

Modules d’inventaire installés.

<u>Étapes à reproduire</u> :

1. Créez une source de stock personnalisée et affectez-la à un nouveau stock de stock.
1. Créez un produit avec la source d’inventaire personnalisée.
1. Assurez-vous que le SKU du produit est une valeur entière.
1. passé une commande ;
1. Exécutez la commande `bin/magento queue:consumer:start inventory.reservations.updateSalabilityStatus`.

<u>Résultats attendus</u> :

La file d’attente démarre sans erreur.

<u>Résultats réels</u> :

Une erreur fatale PHP se produit :

```PHP
PHP Fatal error:  Uncaught TypeError: Argument 1 passed to Magento\InventoryIndexer\Model\Queue\UpdateIndexSalabilityStatus\IndexProcessor::getIndexSalabilityStatus() must be of the type string, int given, called in /vendor/magento/module-inventory-indexer/Model/Queue/UpdateIndexSalabilityStatus/IndexProcessor.php on line 119 and defined in /vendor/magento/module-inventory-indexer/Model/Queue/UpdateIndexSalabilityStatus/IndexProcessor.php:136
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
