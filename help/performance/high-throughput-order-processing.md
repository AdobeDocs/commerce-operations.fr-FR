---
title: Bonnes pratiques relatives aux performances de passage en caisse
description: Découvrez comment optimiser les performances des expériences de passage en caisse sur votre site Adobe Commerce.
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: e4c1832076bb81cd3e70ff279a6921ffb29ea631
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---


# Bonnes pratiques relatives aux performances de passage en caisse

Le processus [checkout](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process) dans Adobe Commerce est un aspect essentiel de l’expérience storefront. Il repose sur les fonctionnalités [cart](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#shopping-cart) et [checkout](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#checkout-page) intégrées.

Les performances sont essentielles pour garantir une expérience utilisateur optimale. Passez en revue le [résumé des performances](../implementation-playbook/infrastructure/performance/benchmarks.md) pour en savoir plus sur les attentes en matière de performances. Vous pouvez optimiser les performances de passage en caisse en configurant les options suivantes pour le **traitement de commande à haut débit** :

- [AsyncOrder](#asynchronous-order-placement) : traite les commandes de manière asynchrone à l’aide d’une file d’attente.
- [Calcul total différé](#deferred-total-calculation) : remplacez les calculs pour les totaux de commande jusqu’au début du passage en caisse.
- [Contrôle de l’inventaire au chargement du panier](#disable-inventory-check) : choisissez d’ignorer la validation de l’inventaire des articles du panier.
- [Équilibrage de la charge](#load-balancing) : activez les connexions secondaires pour la base de données MySQL et l’instance Redis.

Les options de configuration Commande asynchrone, Calcul total différé et Contrôle du stock sur le chargement du panier fonctionnent toutes indépendamment. Vous pouvez utiliser les trois fonctions simultanément ou activer et désactiver les fonctions dans n’importe quelle combinaison.

>[!NOTE]
>
>N’utilisez pas de code PHP personnalisé pour personnaliser les fonctionnalités intégrées de panier et de passage en caisse. Outre les problèmes de performances potentiels, l’utilisation de code PHP personnalisé peut entraîner des mises à niveau et des problèmes de maintenance complexes. Ces problèmes augmentent le coût total de possession. Si la personnalisation du panier et du passage en caisse basée sur PHP est inévitable, utilisez uniquement les extensions approuvées par [Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/). Toutes les extensions Marketplace sont soumises à une [révision approfondie](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program/) pour vérifier qu’elles répondent aux normes de codage Adobe Commerce et aux bonnes pratiques.

## Placement de l’ordre asynchrone

Le module _Commande asynchrone_ active l’emplacement de commande asynchrone, qui marque l’ordre comme `received`, place la commande dans une file d’attente et traite les commandes de la file d’attente de manière prioritaire. AsyncOrder est **désactivé** par défaut.

Par exemple, un client ajoute un produit à son panier et sélectionne **[!UICONTROL Proceed to Checkout]**. Ils remplissent le formulaire **[!UICONTROL Shipping Address]**, choisissent leurs **[!UICONTROL Shipping Method]** préférés, sélectionnent un mode de paiement et passent la commande. Le panier est effacé, la commande est marquée comme **[!UICONTROL Received]**, mais la quantité de produit n’est pas encore ajustée, pas plus qu’un e-mail de vente n’est envoyé au client. La commande est reçue, mais les détails de la commande ne sont pas encore disponibles, car elle n’a pas été entièrement traitée. Il reste dans la file d’attente jusqu’à ce que le consommateur `placeOrderProcess` commence, vérifie la commande avec la fonction [vérification de stock](#disable-inventory-check) (activée par défaut) et met à jour la commande comme suit :

- **Produit disponible** : l’état de la commande passe à _En attente_, la quantité du produit est ajustée, un courrier électronique contenant les détails de la commande est envoyé au client et les détails de la commande réussis peuvent être affichés dans la liste **Commandes et retours** avec des options exploitables, telles que la réorganisation.
- **Produit en rupture de stock ou faible approvisionnement** : l’état de la commande passe à _Refusé_, la quantité de produit n’est pas ajustée, un email contenant les détails de la commande est envoyé au client et les détails de la commande rejetée sont disponibles dans la liste **Commandes et retours** sans options exploitables.

Utilisez l’interface de ligne de commande pour activer ces fonctionnalités ou modifiez le fichier `app/etc/env.php` en fonction des fichiers README correspondants définis dans le [_Guide de référence du module_](https://developer.adobe.com/commerce/php/module-reference/).

**Pour activer AsyncOrder** :

Vous pouvez activer AsyncOrder à l’aide de l’interface de ligne de commande :

```bash
bin/magento setup:config:set --checkout-async 1
```

La commande `set` écrit ce qui suit dans le fichier `app/etc/env.php` :

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

Voir [AsyncOrder](https://developer.adobe.com/commerce/php/module-reference/module-async-order/) dans le _Guide de référence de module_.

**Pour désactiver AsyncOrder** :

>[!WARNING]
>
>Avant de désactiver le module AsyncOrder, vous devez vérifier que les processus de commande asynchrones _all_ sont terminés.

Vous pouvez désactiver AsyncOrder à l’aide de l’interface de ligne de commande :

```bash
bin/magento setup:config:set --checkout-async 0
```

La commande `set` écrit ce qui suit dans le fichier `app/etc/env.php` :

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### Compatibilité d’AsyncOrder

AsyncOrder prend en charge un ensemble limité de fonctionnalités Adobe Commerce.

| Catégorie | Fonctionnalité prise en charge |
|------------------|--------------------------------------------------------------------------|
| Types de passage en caisse | Achat sur une seule page<br>Achat standard<br>Devis négociable B2B |
| Modes de paiement | Bon de commande/paiement<br>espèces à la livraison<br>Braintree<br>PayPal PayFlow Pro |
| Méthodes de livraison | Toutes les méthodes de livraison sont prises en charge. |

Les fonctionnalités suivantes ne sont **pas** prises en charge par AsyncOrder, mais continuent à fonctionner de manière synchrone :

- Modes de paiement non inclus dans la liste des fonctionnalités prises en charge
- Passage en caisse multi-adresses
- Création des commandes d’administration

#### Prise en charge des API web

Lorsque le module AsyncOrder est activé, les points de terminaison REST suivants et les mutations GraphQL s’exécutent de manière asynchrone :

**REST:**

- [`POST /V1/carts/mine/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/cartsminepayment-information#operation/PostV1CartsMinePaymentinformation)
- [`POST /V1/guest-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/guest-cartscartIdpayment-information#operation/PostV1GuestcartsCartIdPaymentinformation)
- [`POST /V1/negotiable-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/negotiable-cartscartIdpayment-information#operation/PostV1NegotiablecartsCartIdPaymentinformation)

**GraphQL:**

- [`placeOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/)
- [`setPaymentMethodAndPlaceOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/set-payment-place-order/)

>[!INFO]
>
>GraphQL ne prend pas en charge le placement asynchrone d’ordres de devis négociables.

#### Exclusion des modes de paiement

Les développeurs peuvent exclure explicitement certaines méthodes de paiement du placement de commande asynchrone en les ajoutant au tableau `Magento\AsyncOrder\Model\OrderManagement::paymentMethods`. Les commandes qui utilisent des méthodes de paiement exclues sont traitées de manière synchrone.

### Ordre asynchrone des citations négociables

Le module _Ordre asynchrone de devis négociable_ B2B vous permet d’enregistrer les éléments de commande de manière asynchrone pour la fonctionnalité `NegotiableQuote`. AsyncOrder et NégociableQuote doivent être activés.

## Calcul total différé

Le module _Calcul total différé_ optimise le processus de passage en caisse en différant le calcul total jusqu’à ce qu’il soit demandé pour le panier ou lors des dernières étapes de passage en caisse. Lorsqu’il est activé, seul le sous-total est calculé lorsqu’un client ajoute des produits au panier.

Le calcul du total différé est **désactivé** par défaut. Utilisez l’interface de ligne de commande pour activer ces fonctionnalités ou modifiez le fichier `app/etc/env.php` en fonction des fichiers README correspondants définis dans le [_Guide de référence du module_](https://developer.adobe.com/commerce/php/module-reference/).

**Pour activer DeferredTotalCalcul** :

Vous pouvez activer DeferredTotalCalcul à l’aide de l’interface de ligne de commande :

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

La commande `set` écrit ce qui suit dans le fichier `app/etc/env.php` :

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**Pour désactiver DeferredTotalCalcul** :

Vous pouvez désactiver DeferredTotalCalcul à l’aide de l’interface de ligne de commande :

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

La commande `set` écrit ce qui suit dans le fichier `app/etc/env.php` :

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

Voir [DeferredTotalCalculating](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/) dans le _Guide de référence du module_.

### Taxe sur les produits fixe

Lorsque l’option Calcul du total différé est activée, la taxe sur les produits fixes (FPT) n’est pas incluse dans le prix du produit et le sous-total du panier du mini-panier après l’ajout du produit au panier. Le calcul FPT est différé lors de l’ajout d’un produit au mini panier. Le FPT s’affiche correctement dans le panier après le passage en caisse final.

## Désactiver la vérification du stock

Le paramètre global _Activer le chargement du panier lors de l’inventaire_ détermine s’il faut effectuer une vérification d’inventaire lors du chargement d’un produit dans le panier. La désactivation du processus de vérification des stocks améliore les performances de toutes les étapes de passage en caisse, en particulier lorsque vous traitez des produits en vrac dans le panier.

Lorsque cette option est désactivée, la vérification de stock ne se produit pas lors de l’ajout d’un produit au panier. Si cette vérification de stock est ignorée, certains scénarios en rupture de stock peuvent générer d’autres types d’erreurs. Une vérification d’inventaire _always_ a lieu à l’étape d’emplacement de la commande, même si elle est désactivée.

**L’option Activer la vérification de l’inventaire au chargement du panier** est activée (définie sur Oui) par défaut. Pour désactiver la vérification d’inventaire lors du chargement du panier, définissez **[!UICONTROL Enable Inventory Check On Cart Load]** sur `No` dans l’interface utilisateur d’administration **Magasins** > **Configuration** > **Catalogue** > **Inventaire** > **Options d’inventaire** . Voir [Configuration des options globales](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/global-options) et [Inventaire du catalogue](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview) dans le _Guide de l’utilisateur_.

## Equilibrage de la charge

Vous pouvez équilibrer la charge entre les différents noeuds en activant les connexions secondaires pour la base de données MySQL et l’instance Redis.

Adobe Commerce peut lire plusieurs bases de données ou instances Redis de manière asynchrone. Si vous utilisez Commerce sur l’infrastructure cloud, vous pouvez configurer les connexions secondaires en modifiant les valeurs [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection) et [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) dans le fichier `.magento.env.yaml`. Un seul noeud doit gérer le trafic en lecture-écriture. Par conséquent, la définition des variables sur `true` entraîne la création d’une connexion secondaire pour le trafic en lecture seule. Définissez les valeurs sur `false` pour supprimer tout tableau de connexion en lecture seule existant du fichier `env.php`.

Exemple du fichier `.magento.env.yaml` :

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
