---
title: Vérifier la base de données fractionnée
description: Découvrez comment vérifier le bon fonctionnement d’une configuration de base de données partagée Commerce.
recommendations: noCatalog
exl-id: 36295240-6521-4f3e-9ea3-f35b73de672d
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Vérifier la base de données fractionnée

{{ee-only}}

{{deprecate-split-db}}

Après la configuration, les bases de données principales sont configurées comme suit :

- Base de données Commerce principale : 369 tables
- Base de données des devis Commerce : 11 tables
- Base de données des ventes Commerce : 55 tables

Pour vérifier que vos bases de données fractionnées fonctionnent correctement, effectuez les tâches suivantes et vérifiez que les données sont ajoutées aux tables de base de données à l&#39;aide d&#39;un outil de base de données tel que [phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin) :

| Éléments à vérifier | Comment vérifier |
| -------------- | ------------- |
| la base de données de devis fonctionne | Ajoutez des articles à un panier. Vérifiez que des lignes ont été ajoutées aux tables `quote`, `quote_address` et `quote_item` de votre base de données de devis. |
| la base de données des ventes fonctionne | Compléter une commande (tout mode de paiement, y compris chèque/mandat). Vérifiez que des lignes ont été ajoutées aux tables `sales_order_address`, `sales_order_item` et `sales_order_payment` de votre base de données de ventes. |

>[!WARNING]
>
>Vous devez sauvegarder manuellement les deux instances de base de données supplémentaires. Commerce ne sauvegarde que l’instance de base de données principale. La commande [`magento setup:backup --db`](../../installation/tutorials/backup.md) et les options d’administration ne sauvegardent pas les tableaux supplémentaires.
