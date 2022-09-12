---
title: Vérifier la base de données partagée
description: Découvrez comment vérifier qu’une configuration de base de données de partage Commerce fonctionne correctement.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---


# Vérifier la base de données partagée

{{ee-only}}

{{deprecate-split-db}}

Après la configuration, les bases de données maîtres sont configurées comme suit :

- Base de données Commerce principale : 369 tables
- Commerce [guillemet](https://glossary.magento.com/quote) base de données : 11 tables
- Base de données commerciale des ventes : 55 tables

Pour vérifier que vos bases de données partagées fonctionnent correctement, effectuez les tâches suivantes et vérifiez que les données sont ajoutées aux tables de base de données à l’aide d’un outil de base de données tel que [phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

| Eléments à vérifier | Comment vérifier |
| -------------- | ------------- |
| base de données de devis fonctionne | Ajoutez des éléments à un panier. Vérifiez que des lignes ont été ajoutées à la base de données de guillemets. `quote`, `quote_address`, et `quote_item` des tables. |
| la base de données des ventes fonctionne | Remplir une commande (tout mode de paiement, y compris les chèques et les paiements). Vérifiez que des lignes ont été ajoutées à la base de données de ventes. `sales_order_address`, `sales_order_item`, et `sales_order_payment` des tables. |

>[!WARNING]
>
>Vous devez sauvegarder manuellement les deux instances de base de données supplémentaires. Commerce sauvegarde uniquement l’instance de base de données principale. Le [`magento setup:backup --db`](../../installation/tutorials/backup.md) Les options Commande et Admin ne sauvegardent pas les tables additionnelles.
