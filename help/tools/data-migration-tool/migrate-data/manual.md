---
title: Données nécessitant une migration manuelle
description: Découvrez les données qui doivent être migrées manuellement au cours d’une migration de données Magento 1 vers Magento 2 et comment procéder.
exl-id: 830abd81-4c6d-418b-9da4-b6acd95f5ec8
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Données nécessitant une migration manuelle

Il existe quatre types de données qui doivent être migrées manuellement :

* Média

* Conception Storefront

* Comptes d’utilisateurs administrateurs

* Listes de contrôle d’accès (ACL)

## Média

Cette section explique comment migrer manuellement les fichiers multimédias.

### Fichiers multimédias stockés dans la base de données

>[!WARNING]
>
>La méthode de stockage des médias dans la base de données est obsolète depuis Magento 2.4.3.


Cette section s’applique *uniquement* si vous stockez des fichiers multimédias dans la base de données du Magento. Cette étape doit être effectuée avant la [migration des données](data.md) :

1. Connectez-vous au panneau d’administration Magento 1 en tant qu’administrateur.

1. Cliquez sur **Système** > **Configuration** > AVANCÉ > **Système**.

1. Dans le volet de droite, faites défiler l’écran jusqu’à **Configuration de stockage pour Media**.

1. Dans la liste **Select Media Database**, cliquez sur le nom de votre base de données de stockage de médias.

1. Cliquez sur **Synchroniser**.

Répétez ensuite les mêmes étapes dans le panneau d’administration de Magento 2.

### Fichiers multimédias dans le système de fichiers

Tous les fichiers multimédias (images pour les produits, les catégories, l’éditeur WYSIWYG, etc.) doivent être copiés manuellement de `<your Magento 1 install dir>/media` vers `<your Magento 2 install dir>/pub/media`.

Cependant, ne copiez pas *et non* les fichiers `.htaccess` situés dans le dossier Magento 1 `media`. Le Magento 2 possède son propre `.htaccess` qui doit être conservé.

## Conception Storefront

* La conception dans les fichiers (CSS, JS, modèles, mises en page XML) a modifié son emplacement et son format.

* Mise en page Mises à jour stockées dans la base de données. Transmis par l’administrateur Magento 1 dans les pages CMS, widgets CMS, pages de catégorie et pages de produit

## Listes de contrôle d’accès (ACL)

Vous devez recréer manuellement tous les éléments suivants :

* informations d’identification pour les API de service Web (SOAP, XML-RPC et REST)

* administrateurs de comptes utilisateur et les associer à des privilèges d’accès ;

>[!NOTE]
>
>Vous pouvez ajuster le fuseau horaire d’une entité de base de données à l’aide du gestionnaire `\Migration\Handler\Timezone`. Pour plus d’informations, consultez la section [relance](follow-up.md) .
