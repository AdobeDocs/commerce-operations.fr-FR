---
title: Données nécessitant une migration manuelle
description: 'Découvrez les données qui doivent être migrées manuellement au cours d’une migration de données Magento 1 vers Magento 2 et comment procéder. '
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# Données nécessitant une migration manuelle

Il existe quatre types de données qui doivent être migrées manuellement :

* Média

* [Storefront](https://glossary.magento.com/storefront) design

* [Administration](https://glossary.magento.com/admin) comptes utilisateur

* Listes de contrôle d’accès (ACL)

## Média

Cette section explique comment migrer manuellement les fichiers multimédias.

### Fichiers multimédias stockés dans la base de données

>[!WARNING]
>
>La méthode de stockage des médias dans la base de données est obsolète depuis Magento 2.4.3.


Cette section vous concerne *only* si vous stockez des fichiers multimédias dans la base de données du Magento. Cette étape doit être effectuée avant [migration des données](data.md):

1. Connectez-vous au panneau d’administration Magento 1 en tant qu’administrateur.

1. Cliquez sur **Système** > **Configuration** > AVANCÉ > **Système**.

1. Dans le volet de droite, faites défiler l’écran jusqu’à **Configuration de stockage pour Media**.

1. Dans la **Sélectionner la base de données multimédia** , cliquez sur le nom de votre [stockage multimédia](https://glossary.magento.com/media-storage) base de données.

1. Cliquez sur **Synchroniser**.

Répétez ensuite les mêmes étapes dans le panneau d’administration de Magento 2.

### Fichiers multimédias dans le système de fichiers

Tous les fichiers multimédias (images pour les produits, les catégories, la variable [WYSIWYG](https://glossary.magento.com/wysiwyg) , etc.) doit être copié manuellement à partir de `<your Magento 1 install dir>/media` to `<your Magento 2 install dir>/pub/media`.

Toutefois, la méthode *not* Copiez le `.htaccess` fichiers situés dans le Magento 1 `media` dossier. Le Magento 2 a sa propre `.htaccess` qui doivent être préservées.

## Conception Storefront

* Conception dans des fichiers (CSS, JS, modèles, [XML](https://glossary.magento.com/xml) dispositions) a modifié son emplacement et son format.

* [Disposition](https://glossary.magento.com/layout) Mises à jour stockées dans la base de données. Transmis par l’administrateur Magento 1 dans [CMS](https://glossary.magento.com/cms) Pages, widgets CMS, [Catégorie](https://glossary.magento.com/category) Pages et pages de produits

## Listes de contrôle d’accès (ACL)

Vous devez recréer manuellement tous les éléments suivants :

* informations d’identification pour les API de service Web (SOAP, XML-RPC et REST)

* administrateurs de comptes utilisateur et les associer à des privilèges d’accès ;

>[!NOTE]
>
>Vous pouvez ajuster le fuseau horaire d’une entité de base de données à l’aide de la variable `\Migration\Handler\Timezone` gestionnaire. Voir [suivi](follow-up.md) pour plus d’informations.
