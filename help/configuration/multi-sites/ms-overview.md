---
title: Plusieurs sites web ou magasins
description: Découvrez comment démarrer plusieurs sites web ou implémenter des affichages de boutique avec différents domaines, options et contenus.
exl-id: 724d75d9-13fc-40f9-951a-69aa407adb6f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Plusieurs sites web ou magasins

Une seule instance du logiciel Adobe Commerce vous permet de démarrer plusieurs sites web ou de stocker des vues qui utilisent différents attributs et contenus, par exemple :

- Langues par défaut
- Noms de domaine
- Catégories
- Produits
- Devises

Cette solution flexible permet à une base de code Commerce et à un administrateur d’administrer et d’afficher différents magasins. Vous configurez les sites web, les boutiques et les vues de boutique dans l’Administration. Utilisez certaines variables dans les hôtes virtuels pour démarrer l’application Commerce à l’aide de ces sites web ou vues de magasin.

Une utilisation type consiste à configurer des magasins avec différentes options dans différents domaines. Par exemple, vous pouvez avoir un ensemble de catégories et de produits sur un domaine et un autre ensemble de catégories et de produits sur un domaine distinct dans une langue différente.

Vous configurez les sites web, les boutiques et les vues de boutique dans l’administration Commerce. Utilisez les variables `MAGE_RUN_TYPE` et `MAGE_RUN_CODE` dans les hôtes virtuels pour démarrer l’application Commerce à l’aide de ces sites web ou vues de magasin.

Tenez compte des termes suivants :

- **Site Web** : est le conteneur de niveau supérieur pour les sites, les modes de diffusion, les modes de paiement, etc. Pour créer des sites complètement distincts qui ne partagent pas le panier, les méthodes de diffusion, etc., vous devez créer des sites web distincts.

  Les comptes clients de site web peuvent être partagés entre plusieurs sites web au sein d’une seule instance Commerce. Un site Web contient au moins un magasin. Les prix des catalogues doivent être gérés au niveau du site web.

- **Store** : est contenu par un site web. À son tour, un magasin contient au moins une vue *magasin*.

  Plusieurs magasins peuvent partager le panier, les sessions utilisateur, les passerelles de paiement, etc., mais ils disposent de structures de catalogue et d’un prix de catalogue distincts.

  La quantité du catalogue (stock) ne peut pas être gérée au niveau du magasin. L’inventaire est géré uniquement au niveau du site web ou au niveau mondial.

  Les vues de la boutique modifient la façon dont les pages sont présentées et sont généralement utilisées pour afficher une boutique avec différentes dispositions ou langues. Vous pouvez gérer différentes devises par vue de magasin.

  Chaque site web et chaque vue de magasin doivent avoir un identifiant unique. Cet identifiant est nécessaire pour utiliser les variables `MAGE_RUN_TYPE` et `MAGE_RUN_CODE` comme suit :

- `MAGE_RUN_TYPE` peut être `store` ou `website`

   - Utilisez `website` pour charger un site web dans votre storefront.
   - Utilisez `store` pour charger n’importe quelle vue de magasin dans votre storefront.

- `MAGE_RUN_CODE` est le code d’affichage unique du site web ou du magasin qui correspond à `MAGE_RUN_TYPE`

Voici un résumé des tâches que vous devez effectuer :

1. [Configurez des sites web, des boutiques et des affichages de boutique dans l’Administration.](ms-admin.md)
1. Créez un hôte virtuel pour charger de nombreux sites web ou un hôte virtuel par site web ou vue de magasin Commerce afin d’autoriser des directives spécifiques pour chaque magasin.
1. Transmettez les valeurs de `MAGE_RUN_TYPE` et `MAGE_RUN_CODE` au serveur web.
