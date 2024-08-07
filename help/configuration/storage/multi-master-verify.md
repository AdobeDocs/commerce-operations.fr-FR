---
title: Vérifier la base de données partagée
description: Découvrez comment vérifier qu’une configuration de base de données partagée Commerce fonctionne correctement.
recommendations: noCatalog
exl-id: 36295240-6521-4f3e-9ea3-f35b73de672d
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Vérifier la base de données partagée

{{ee-only}}

{{deprecate-split-db}}

Après la configuration, les bases de données maîtres sont configurées comme suit :

- Base de données Commerce principale : 369 tables
- Base de données de devis Commerce : 11 tables
- Base de données des ventes Commerce : 55 tables

Pour vérifier que vos bases de données partagées fonctionnent correctement, effectuez les tâches suivantes et vérifiez que les données sont ajoutées aux tables de base de données à l’aide d’un outil de base de données tel que [phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin) :

| Eléments à vérifier | Comment vérifier |
| -------------- | ------------- |
| base de données de devis fonctionne | Ajoutez des éléments à un panier. Vérifiez que des lignes ont été ajoutées aux tables `quote`, `quote_address` et `quote_item` de votre base de données de guillemets. |
| la base de données des ventes fonctionne | Remplir une commande (tout mode de paiement, y compris les chèques et les paiements). Vérifiez que des lignes ont été ajoutées aux tables `sales_order_address`, `sales_order_item` et `sales_order_payment` de votre base de données de ventes. |

>[!WARNING]
>
>Vous devez sauvegarder manuellement les deux instances de base de données supplémentaires. Commerce sauvegarde uniquement l’instance de base de données principale. La commande [`magento setup:backup --db`](../../installation/tutorials/backup.md) et les options d&#39;administration ne sauvegardent pas les tables supplémentaires.
