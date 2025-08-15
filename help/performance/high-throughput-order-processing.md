---
title: Bonnes pratiques relatives aux performances de passage en caisse
description: Découvrez comment optimiser les performances des expériences de passage en caisse sur votre site Adobe Commerce.
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '1121'
ht-degree: 0%

---


# Bonnes pratiques relatives aux performances de passage en caisse

Le processus [passage en caisse](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process) dans Adobe Commerce est un aspect essentiel de l’expérience storefront. Il repose sur les fonctionnalités intégrées [panier](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#shopping-cart) et [passage en caisse](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#checkout-page).

Les performances sont essentielles pour maintenir une bonne expérience utilisateur. Vous pouvez optimiser les performances de passage en caisse en configurant les options suivantes pour le **traitement des commandes à débit élevé** :

- [AsyncOrder](#asynchronous-order-placement) : traite les commandes de manière asynchrone à l&#39;aide d&#39;une file d&#39;attente.
- [Calcul du total différé](#deferred-total-calculation) : différez les calculs des totaux des commandes jusqu&#39;au début de l&#39;extraction.
- [Vérification de l&#39;inventaire au chargement du panier](#disable-inventory-check)—Choisissez d&#39;ignorer la validation de l&#39;inventaire des articles du panier.
- [Équilibrage de charge](#load-balancing) : activez les connexions secondaires pour la base de données MySQL et l’instance Redis.

Les options de configuration AsyncOrder, Calcul du total différé et Vérification de l’inventaire sur le chargement du panier fonctionnent toutes indépendamment. Vous pouvez utiliser les trois fonctionnalités simultanément ou activer et désactiver les fonctionnalités dans n’importe quelle combinaison.

>[!NOTE]
>
>N’utilisez pas de code PHP personnalisé pour personnaliser les fonctionnalités de panier et de passage en caisse intégrées. Outre les problèmes de performances potentiels, l’utilisation de code PHP personnalisé peut entraîner des mises à niveau et des défis de maintenance complexes. Ces problèmes augmentent le coût total de possession. Si la personnalisation du panier et du passage en caisse basée sur PHP est inévitable, utilisez uniquement les extensions approuvées par [Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/). Toutes les extensions de Marketplace font l’objet d’un [ examen approfondi ](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program/) afin de vérifier qu’elles répondent aux normes de codage et aux bonnes pratiques d’Adobe Commerce.

## Passation de commande asynchrone

Le module _Ordre asynchrone_ permet le placement asynchrone des commandes, qui marque la commande comme `received`, la place dans une file d’attente et traite les commandes de la file d’attente selon le principe du premier entré, premier sorti. Par défaut, AsyncOrder est **désactivé**.

Par exemple, un client ajoute un produit à son panier et le sélectionne **[!UICONTROL Proceed to Checkout]**. Il remplit le formulaire de **[!UICONTROL Shipping Address]**, sélectionne son **[!UICONTROL Shipping Method]** préféré, sélectionne un mode de paiement et passe la commande. Le panier est effacé, la commande est marquée comme **[!UICONTROL Received]**, mais la quantité de produit n’est pas encore ajustée et aucun e-mail de vente n’est envoyé au client. La commande est reçue, mais les détails de la commande ne sont pas encore disponibles, car elle n’a pas été entièrement traitée. Il reste dans la file d’attente jusqu’à ce que le client `placeOrderProcess` commence. Il vérifie la commande à l’aide de la fonction [vérification d’inventaire](#disable-inventory-check) (activée par défaut) et la met à jour comme suit :

- **Produit disponible** : le statut de la commande passe à _En attente_, la quantité de produit est ajustée, un e-mail contenant les détails de la commande est envoyé au client et les détails de la commande réussie sont disponibles pour consultation dans la liste **Commandes et retours** avec des options activables, telles que la réorganisation.
- **Produit en rupture de stock ou approvisionnement faible** : le statut de la commande passe à _Rejeté_, la quantité de produit n&#39;est pas ajustée, un e-mail contenant les détails de la commande concernant le problème est envoyé au client et les détails de la commande rejetée sont disponibles dans la liste **Commandes et retours** sans aucune option exploitable.

Utilisez l’interface de ligne de commande pour activer ces fonctionnalités ou modifiez le fichier `app/etc/env.php` en fonction des fichiers README correspondants définis dans le Guide de référence du [_module_](https://developer.adobe.com/commerce/php/module-reference/).

**Pour activer AsyncOrder** :

Vous pouvez activer AsyncOrder à l’aide de l’interface de ligne de commande :

```bash
bin/magento setup:config:set --checkout-async 1
```

La commande `set` écrit les éléments suivants dans le fichier `app/etc/env.php` :

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

Voir [AsyncOrder](https://developer.adobe.com/commerce/php/module-reference/module-async-order/) dans le _Guide de référence des modules_.

**Pour désactiver AsyncOrder** :

>[!WARNING]
>
>Avant de désactiver le module AsyncOrder, vous devez vérifier que _tous_ les processus de commande asynchrones sont terminés.

Vous pouvez désactiver AsyncOrder à l’aide de l’interface de ligne de commande :

```bash
bin/magento setup:config:set --checkout-async 0
```

La commande `set` écrit les éléments suivants dans le fichier `app/etc/env.php` :

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### Compatibilité AsyncOrder

AsyncOrder prend en charge un ensemble limité de fonctionnalités Adobe Commerce.

| Catégorie | Fonctionnalité prise en charge |
|------------------|--------------------------------------------------------------------------|
| Types de passage en caisse | Devis négociable OnePage Checkout<br>Standard Checkout<br>B2B |
| Modes de paiement | Chèque/mandat<br>espèces à la livraison<br>Braintree<br>PayPal PayFlow Pro |
| Modes d’expédition | Toutes les méthodes d’expédition sont prises en charge. |

Les fonctionnalités suivantes ne sont **pas** prises en charge par AsyncOrder, mais continuent à fonctionner de manière synchrone :

- Modes de paiement non inclus dans la liste des fonctionnalités prises en charge
- Passage en caisse à adresses multiples
- Création de commande admin

#### Prise en charge des API web

Lorsque le module AsyncOrder est activé, les points d’entrée REST suivants et les mutations GraphQL s’exécutent de manière asynchrone :

**REST:**

- [`POST /V1/carts/mine/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/cartsminepayment-information#operation/PostV1CartsMinePaymentinformation)
- [`POST /V1/guest-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/guest-cartscartIdpayment-information#operation/PostV1GuestcartsCartIdPaymentinformation)
- [`POST /V1/negotiable-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/negotiable-cartscartIdpayment-information#operation/PostV1NegotiablecartsCartIdPaymentinformation)

**GraphQL:**

- [`placeOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/)
- [`setPaymentMethodAndPlaceOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/set-payment-place-order/)

>[!INFO]
>
>GraphQL ne prend pas en charge le placement asynchrone de commandes de devis négociables.

#### Exclusion des modes de paiement

L’équipe de développement peut exclure explicitement certaines méthodes de paiement du placement asynchrone des commandes en les ajoutant au tableau `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` . Les commandes qui utilisent des modes de paiement exclus sont traitées de manière synchrone.

### Commande asynchrone de devis négociable

Le module B2B _Commande asynchrone de devis négociable_ vous permet d’enregistrer les articles de commande de manière asynchrone pour la fonctionnalité de `NegotiableQuote`. AsyncOrder et NegotiableQuote doivent être activés.

## Calcul du total différé

Le module _Calcul total différé_ optimise le processus de passage en caisse en différant le calcul total jusqu’à ce qu’il soit demandé pour le panier ou lors des étapes de passage en caisse finales. Lorsqu’il est activé, seul le sous-total est calculé comme un client qui ajoute des produits au panier.

Le calcul des totaux différés est **désactivé** par défaut. Utilisez l’interface de ligne de commande pour activer ces fonctionnalités ou modifiez le fichier `app/etc/env.php` en fonction des fichiers README correspondants définis dans le Guide de référence du [_module_](https://developer.adobe.com/commerce/php/module-reference/).

**Pour activer DeferredTotalCalculation** :

Vous pouvez activer DeferredTotalCalculation à l&#39;aide de l&#39;interface de ligne de commande :

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

La commande `set` écrit les éléments suivants dans le fichier `app/etc/env.php` :

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**Pour désactiver DeferredTotalCalculation** :

Vous pouvez désactiver DeferredTotalCalculation à l&#39;aide de l&#39;interface de ligne de commande :

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

La commande `set` écrit les éléments suivants dans le fichier `app/etc/env.php` :

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

Voir [DeferredTotalCalculating](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/) dans le _Guide de référence des modules_.

### Taxe fixe sur les produits

Lorsque le calcul du total différé est activé, la taxe sur les produits fixe (FPT) n’est pas incluse dans le prix du produit et le sous-total du panier du mini panier après l’ajout du produit au panier. Le calcul FPT est différé lors de l’ajout d’un produit au mini panier. Le FPT s’affiche correctement dans le panier après avoir effectué la commande finale.

## Désactiver la vérification de l&#39;inventaire

Le paramètre global _Activer l’inventaire au chargement du panier_ détermine s’il faut effectuer une vérification de l’inventaire lors du chargement d’un produit dans le panier. La désactivation du processus de vérification de l’inventaire améliore les performances de toutes les étapes de passage en caisse, en particulier lorsque vous traitez des produits en masse dans le panier.

Lorsqu’elle est désactivée, la vérification de l’inventaire ne se produit pas lors de l’ajout d’un produit au panier. Si cette vérification d’inventaire est ignorée, certains scénarios de rupture de stock peuvent générer d’autres types d’erreurs. Une vérification d’inventaire _toujours_ a lieu à l’étape de validation de la commande, même si elle est désactivée.

**Activer la vérification de l’inventaire au chargement du panier** est activé (défini sur Oui) par défaut. Pour désactiver la vérification de l’inventaire lors du chargement du panier, définissez **[!UICONTROL Enable Inventory Check On Cart Load]** sur `No` dans la section IU d’administration **Magasins** > **Configuration** > **Catalogue** > **Inventaire** > **Options de stock**. Voir [Configuration des options globales](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/global-options) et [Inventaire des catalogues](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview) dans le _Guide de l’utilisateur_.

## Équilibrage de charge

Vous pouvez aider à équilibrer la charge sur différents nœuds en activant des connexions secondaires pour la base de données MySQL et l’instance Redis.

Adobe Commerce peut lire plusieurs bases de données ou instances Redis de manière asynchrone. Si vous utilisez Commerce sur une infrastructure cloud, vous pouvez configurer les connexions secondaires en modifiant les valeurs [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection) et [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) dans le fichier `.magento.env.yaml`. Un seul nœud doit gérer le trafic en lecture-écriture. Par conséquent, la définition des variables sur `true` entraîne la création d’une connexion secondaire pour le trafic en lecture seule. Définissez les valeurs sur `false` pour supprimer tout tableau de connexion en lecture seule existant du fichier `env.php`.

Exemple de fichier `.magento.env.yaml` :

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
