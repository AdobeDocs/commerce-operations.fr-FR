---
title: Modifier l’ID d’incrément
description: Modifiez l’ID d’incrément d’une entité de base de données Commerce.
exl-id: 039fc34c-d9cf-42f4-af5d-16a26a3e8171
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Modifier l’ID d’incrément

Cet article explique comment modifier l’ID d’incrément d’une entité de base de données Commerce (commande, facture, note de crédit, etc.) sur une boutique Commerce spécifique à l’aide de la variable `ALTER TABLE` Instruction SQL.

## Versions affectées

- Adobe Commerce (sur site) : 2.x.x
- Adobe Commerce sur l’infrastructure cloud : 2.x.x
- MySQL : [toute version prise en charge](../../installation/prerequisites/database/mysql.md)

## Quand devez-vous modifier l’ID d’incrément ?

Vous devrez peut-être modifier l’ID d’incrément pour les nouvelles entités de base de données dans les cas suivants :

- Après une restauration sur un site Live
- Certains enregistrements de commande ont été perdus, mais leurs identifiants sont déjà utilisés par les passerelles de paiement (comme PayPal) pour votre compte marchand actuel. Dans ce cas, les passerelles de paiement arrêtent le traitement de nouvelles commandes ayant les mêmes identifiants, renvoyant l’erreur &quot;Dupliquer l’identifiant de facture&quot;.

>[!INFO]
>
>Vous pouvez également résoudre le problème de passerelle de paiement pour PayPal en autorisant plusieurs paiements par identifiant de facture dans les préférences de réception des paiements de PayPal. Voir [Demande de rejet de la passerelle PayPal - problème de facture en double] dans le _Base de connaissances_.

## Étapes préalables

1. Recherchez les magasins et les entités pour lesquels le nouvel ID d’incrément doit être modifié.
1. Connectez-vous à votre base de données MySQL.
Pour Adobe Commerce sur l’infrastructure cloud, vous devez d’abord vous connecter à votre environnement à l’aide de SSH.
1. Vérifier la variable actuelle `auto_increment` valeur de la table de séquence d’entités à l’aide de la requête suivante :

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

Si vous cochez une incrémentation automatique pour une commande sur le magasin avec ID=1, le nom de la table sera &#39;sequence_order_1&#39;.

Si la valeur de la variable `auto_increment` est 1234, la commande suivante placée dans le magasin avec `ID=1` aura l&#39;identifiant &#39;#100001234&#39;.

## Mettre à jour l’entité pour modifier l’ID d’incrément

Mettez à jour l’entité à l’aide de la requête suivante :

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
>
Important : La nouvelle valeur d’incrément doit être supérieure à la valeur actuelle.

Après avoir exécuté la requête suivante :

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

La commande suivante placée dans le magasin avec `ID=1` aura l&#39;identifiant &#39;#100002000&#39;.

## Autres étapes recommandées pour les environnements de production cloud

Avant d’exécuter la fonction `ALTER TABLE` sur un environnement de production d’Adobe Commerce sur l’infrastructure cloud, il est vivement recommandé d’effectuer les étapes suivantes :

- Testez l’ensemble de la procédure de modification de l’identifiant d’incrément dans votre environnement d’évaluation.
- [Création d’une sauvegarde de base de données] pour restaurer la base de données de production en cas d’échec

<!-- Link Definitions -->

[Demande de rejet de la passerelle PayPal - problème de facture en double]: https://support.magento.com/hc/en-us/articles/115002457473
[Création d’une sauvegarde de base de données]: https://support.magento.com/hc/en-us/articles/360003254334
[toute version prise en charge]
