---
title: Plusieurs sites web ou magasins
description: Découvrez comment lancer plusieurs sites web ou implémenter des vues de magasin avec différentes options, domaines et contenus.
exl-id: 724d75d9-13fc-40f9-951a-69aa407adb6f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Plusieurs sites web ou magasins

Une seule instance du logiciel Adobe Commerce vous permet de démarrer plusieurs sites web ou de stocker des vues qui utilisent différents attributs et contenus, tels que :

- Langues par défaut
- Noms de domaine
- Catégories
- Produits
- Devises

Cette solution flexible permet à un seul code Commerce et à un seul administrateur d’administrer et d’afficher différents magasins. Vous configurez les sites web, les magasins et les vues de magasin dans l’administrateur. Utilisez certaines variables dans les hôtes virtuels pour démarrer l’application Commerce à l’aide de ces sites web ou vues de magasin.

Une utilisation type consiste à configurer des magasins avec différentes options dans différents domaines. Par exemple, vous pouvez avoir un ensemble de catégories et de produits sur un domaine et un autre ensemble de catégories et de produits sur un domaine distinct dans une autre langue.

Vous configurez les sites web, les magasins et les vues de magasin dans l’administrateur Commerce. Utilisez la variable `MAGE_RUN_TYPE` et `MAGE_RUN_CODE` dans les hôtes virtuels pour démarrer l’application Commerce à l’aide de ces sites web ou vues de magasin.

Tenez compte des termes suivants :

- **Site Web**: conteneur de niveau supérieur pour les sites, les méthodes de diffusion, les méthodes de paiement, etc. Pour créer des sites complètement distincts qui ne partagent pas de panier, de méthodes de diffusion ou d’autres, vous devez créer des sites Web distincts.

  Les comptes clients de site web peuvent être partagés entre plusieurs sites web au sein d’une seule instance Commerce. Un site web contient au moins un magasin. Les prix du catalogue doivent être gérés au niveau du site web.

- **Magasin**: est contenu par un site web. En retour, un magasin contient au moins une *vue de magasin*.

  Plusieurs magasins peuvent partager des paniers, des sessions utilisateurs, des passerelles de paiement, etc., mais ils disposent de structures de catalogue et de prix de catalogue distincts.

  La quantité de catalogue (inventaire) ne peut pas être gérée au niveau du magasin. L’inventaire est géré au niveau du site web ou au niveau global uniquement.

  Les vues des magasins modifient la présentation des pages. Elles sont généralement utilisées pour afficher un magasin avec différentes mises en page ou langues. Vous pouvez gérer différentes devises par vue de magasin.

  Chaque site web et chaque vue de magasin doivent comporter un identifiant unique. Cet identifiant est nécessaire pour utiliser la variable `MAGE_RUN_TYPE` et `MAGE_RUN_CODE` comme suit :

- `MAGE_RUN_TYPE` peut être `store` ou `website`

   - Utilisation `website` pour charger un site web dans votre vitrine.
   - Utilisation `store` pour charger n’importe quelle vue de magasin dans votre storefront.

- `MAGE_RUN_CODE` est le code d’affichage unique du site web ou du magasin qui correspond à `MAGE_RUN_TYPE`

Voici un résumé des tâches que vous devez effectuer :

1. [Configurez les sites web, les magasins et les vues de magasin dans l’administrateur.](ms-admin.md)
1. Créez un hôte virtuel pour charger de nombreux sites web ou un hôte virtuel par site web ou vue de magasin Commerce afin d’autoriser des directives spécifiques pour chaque magasin.
1. Transmettre les valeurs de `MAGE_RUN_TYPE` et `MAGE_RUN_CODE` sur le serveur web.
