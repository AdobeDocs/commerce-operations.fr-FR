---
title: Données nécessitant une migration manuelle
description: Découvrez les données qui doivent être migrées manuellement lors d’une migration de données Magento 1 vers Magento 2 et comment le faire.
exl-id: 830abd81-4c6d-418b-9da4-b6acd95f5ec8
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%
---
# Données nécessitant une migration manuelle

Il existe quatre types de données qui doivent être migrées manuellement :

* Média

* Conception de storefront

* Comptes utilisateur d’administration

* Liste de contrôle d’accès (ACL)

## Média

Cette section explique comment migrer manuellement des fichiers multimédias.

### Fichiers multimédias stockés dans la base de données

>[!WARNING]
>
>La méthode de stockage des médias de base de données est obsolète depuis Magento 2.4.3.


Cette section s’applique *uniquement* si vous stockez des fichiers multimédias dans la base de données Magento. Cette étape doit être effectuée avant la [migration des données](data.md) :

1. Connectez-vous au Panneau d’administration de Magento 1 en tant qu’administrateur.

1. Cliquez sur **Système** > **Configuration** > AVANCÉ > **Système**.

1. Dans le volet de droite, faites défiler l’écran jusqu’à **Configuration de stockage pour les médias**.

1. Dans la liste **Sélectionner la base de données des médias**, cliquez sur le nom de votre base de données de stockage des médias.

1. Cliquez sur **Synchroniser**.

Répétez ensuite les mêmes étapes dans votre panneau d’administration Magento 2.

### Fichiers multimédias dans le système de fichiers

Tous les fichiers multimédias (images pour les produits, les catégories, l’éditeur WYSIWYG, etc.) doivent être copiés manuellement de `<your Magento 1 install dir>/media` vers `<your Magento 2 install dir>/pub/media`.

Toutefois, ne copiez *pas* les fichiers `.htaccess` situés dans le dossier `media` de Magento 1. Magento 2 possède son propre `.htaccess` qui doit être préservé.

## Conception de storefront

* La conception dans les fichiers (CSS, JS, modèles, mises en page XML) a modifié son emplacement et son format

* Mises à jour de disposition stockées dans la base de données. Placé via Magento 1 Admin dans les pages CMS, les widgets CMS, les pages de catégories et les pages de produits

## Liste de contrôle d’accès (ACL)

Vous devez tout recréer manuellement :

* Informations d’identification pour les API de service web (SOAP, XML-RPC et REST)

* comptes utilisateur administratifs et leur associer des privilèges d’accès

>[!NOTE]
>
>Vous pouvez ajuster le fuseau horaire d&#39;une entité de base de données à l&#39;aide du gestionnaire `\Migration\Handler\Timezone`. Voir la section [suivi](follow-up.md) pour plus d’informations.
