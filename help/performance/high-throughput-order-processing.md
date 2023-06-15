---
title: Traitement des commandes à haut débit
description: Optimisez l’emplacement des commandes et l’expérience de passage en caisse pour votre déploiement Adobe Commerce ou Magento Open Source.
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: 012cba58b336b032b1c911539008c1fb961c2e07
workflow-type: tm+mt
source-wordcount: '1048'
ht-degree: 0%

---

# Traitement des commandes à haut débit

Vous pouvez optimiser le placement des commandes et l’expérience de passage en caisse en configurant l’ensemble de modules suivant pour **traitement des commandes à haut débit**:

- [AsyncOrder](#asynchronous-order-placement): traite les commandes de manière asynchrone à l’aide d’une file d’attente.
- [Calcul total différé](#deferred-total-calculation): renverse les calculs pour les totaux de commande jusqu’au début du passage en caisse.
- [Contrôle de l’inventaire lors du chargement des citations](#disable-inventory-check): choisissez d’ignorer la validation de l’inventaire des articles du panier.

Toutes les fonctionnalités (commande asynchrone, calcul total différé et vérification de l’inventaire) fonctionnent indépendamment. Vous pouvez utiliser les trois fonctions simultanément ou activer et désactiver les fonctions dans n’importe quelle combinaison.

## Placement de l’ordre asynchrone

Le _Ordre asynchrone_ Le module active le placement de commande asynchrone, qui marque l’ordre comme `received`, place la commande dans une file d’attente et traite les commandes de la file d’attente de la façon &quot;premier entré&quot;. AsyncOrder est **disabled** par défaut.

Par exemple, un client ajoute un produit à son panier et sélectionne **[!UICONTROL Proceed to Checkout]**. Ils remplissent les **[!UICONTROL Shipping Address]** formulaire, sélectionnez leurs préférences **[!UICONTROL Shipping Method]**, sélectionnez un mode de paiement et passez la commande. Le panier est effacé, la commande est marquée comme **[!UICONTROL Received]**, mais la quantité du produit n’est pas encore ajustée, pas plus qu’un email de vente n’est envoyé au client. La commande est reçue, mais les détails de la commande ne sont pas encore disponibles, car elle n’a pas été entièrement traitée. Il reste dans la file d’attente jusqu’à ce que la fonction `placeOrderProcess` Le consommateur commence, vérifie la commande avec la variable [vérification de stock](#disable-inventory-check) (activée par défaut) et met à jour l’ordre comme suit :

- **Produit disponible**: l’état de la commande passe à _En attente_, la quantité du produit est ajustée, un e-mail contenant les détails de la commande est envoyé au client et les détails de la commande réussie peuvent être affichés dans la variable **Commandes et retours** liste avec des options exploitables, telles que réorganiser.
- **Produit en rupture de stock ou faible approvisionnement**: l’état de la commande passe à _Rejetés_, la quantité de produit n’est pas ajustée, un e-mail contenant des détails sur la commande est envoyé au client et les détails de la commande rejetée sont disponibles dans la variable **Commandes et retours** liste sans options exploitables.

Utilisez l’interface de ligne de commande pour activer ces fonctionnalités ou modifiez la variable `app/etc/env.php` en fonction des fichiers LISEZMOI correspondants définis dans la variable [_Guide de référence du module_][mrg].

**Pour activer AsyncOrder**:

Vous pouvez activer AsyncOrder à l’aide de l’interface de ligne de commande :

```bash
bin/magento setup:config:set --checkout-async 1
```

Le `set` La commande écrit ce qui suit dans la fonction `app/etc/env.php` fichier :

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

Voir [AsyncOrder] dans le _Guide de référence du module_.

**Pour désactiver AsyncOrder**:

>[!WARNING]
>
>Avant de désactiver le module AsyncOrder, vous devez vérifier que _all_ les processus de commande asynchrones sont terminés.

Vous pouvez désactiver AsyncOrder à l’aide de l’interface de ligne de commande :

```bash
bin/magento setup:config:set --checkout-async 0
```

Le `set` La commande écrit ce qui suit dans la fonction `app/etc/env.php` fichier :

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### Compatibilité d’AsyncOrder

AsyncOrder prend en charge un ensemble limité de [!DNL Commerce] fonctions.

| Catégorie | Fonctionnalité prise en charge |
|------------------|--------------------------------------------------------------------------|
| Types de passage en caisse | Passage en caisse sur une seule page<br>Passage en caisse standard<br>Devis négociable B2B |
| Modes de paiement | Commande d’archivage/d’argent<br>Espèces à la livraison<br>Braintree<br>PayPal PayFlow Pro |
| Méthodes de livraison | Toutes les méthodes de livraison sont prises en charge. |

Les fonctionnalités suivantes sont disponibles : **not** pris en charge par AsyncOrder, mais continuez à fonctionner de manière synchrone :

- Modes de paiement non inclus dans la liste des fonctionnalités prises en charge
- Passage en caisse multi-adresses
- Création des commandes d’administration

#### Prise en charge des API web

Lorsque le module AsyncOrder est activé, les points de terminaison REST suivants et les mutations GraphQL s’exécutent de manière asynchrone :

**REST :**

- `POST /V1/carts/mine/payment-information`
- `POST /V1/guest-carts/:cartId/payment-information`
- `POST /V1/negotiable-carts/:cartId/payment-information`

**GraphQL :**

- [`placeOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/place-order.html)
- [`setPaymentMethodAndPlaceOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/set-payment-place-order.html)

>[!INFO]
>
>GraphQL ne prend pas en charge le placement asynchrone d’ordres de devis négociables.

#### Exclusion des modes de paiement

Les développeurs peuvent exclure explicitement certaines méthodes de paiement de l’emplacement de commande asynchrone en les ajoutant à la variable `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` tableau. Les commandes qui utilisent des méthodes de paiement exclues sont traitées de manière synchrone.

### Ordre asynchrone des citations négociables

Le _Ordre asynchrone des citations négociables_ Le module B2B vous permet d’enregistrer les éléments de commande de manière asynchrone pour le `NegotiableQuote` . AsyncOrder et NégociableQuote doivent être activés.

## Calcul total différé

Le _Calcul total différé_ optimise le processus de passage en caisse en différant le calcul total jusqu’à ce qu’il soit demandé pour le panier ou lors des étapes finales de passage en caisse. Lorsqu’il est activé, seul le sous-total est calculé lorsqu’un client ajoute des produits au panier.

DeferredTotalCalcul **disabled** par défaut. Utilisez l’interface de ligne de commande pour activer ces fonctionnalités ou modifiez la variable `app/etc/env.php` en fonction des fichiers LISEZMOI correspondants définis dans la variable [_Guide de référence du module_][mrg].

**Pour activer DeferredTotalCalcul**:

Vous pouvez activer DeferredTotalCalcul à l’aide de l’interface de ligne de commande :

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

Le `set` La commande écrit ce qui suit dans la fonction `app/etc/env.php` fichier :

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**Pour désactiver DeferredTotalCalcul**:

Vous pouvez désactiver DeferredTotalCalcul à l’aide de l’interface de ligne de commande :

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

Le `set` La commande écrit ce qui suit dans la fonction `app/etc/env.php` fichier :

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

Voir [DeferredTotalCalculating] dans le _Guide de référence du module_.

### Taxe sur les produits fixe

Lorsque DeferredTotalCalcul est activé, la taxe sur les produits fixes (FPT) n’est pas incluse dans le prix du produit et le sous-total du panier du mini-panier après l’ajout du produit au panier. Le calcul FPT est différé lors de l’ajout d’un produit au mini panier. Le FPT s’affiche correctement dans le panier après le passage en caisse final.

## Désactiver la vérification du stock

Le _Activation de l’inventaire au chargement du panier_ paramètre global détermine s’il faut effectuer une vérification de stock lors du chargement d’un produit dans le panier. La désactivation du processus de vérification des stocks améliore les performances de toutes les étapes de passage en caisse, en particulier lorsque vous traitez des produits en vrac dans le panier.

Lorsque cette option est désactivée, la vérification de stock ne se produit pas lors de l’ajout d’un produit au panier. Si cette vérification de stock est ignorée, certains scénarios en rupture de stock peuvent générer d’autres types d’erreurs. Vérification de stock _always_ se produit à l’étape d’emplacement de la commande, même lorsqu’elle est désactivée.

**Activer Contrôle De L’Inventaire Lors Du Chargement Du Panier** est activée (définie sur Oui) par défaut. Pour désactiver la vérification de stock lors du chargement du panier, définissez **[!UICONTROL Enable Inventory Check On Cart Load]** to `No` dans l’interface utilisateur d’administration **Magasins** > **Configuration** > **Catalogue** > **Inventaire** > **Options Stock** . Voir [Configuration des options globales][global] et [Inventaire du catalogue][inventory] dans le _Guide de l’utilisateur_.

## Equilibrage de la charge

Vous pouvez équilibrer la charge entre les différents noeuds en activant les connexions secondaires pour la base de données MySQL et l’instance Redis.

Adobe Commerce peut lire plusieurs bases de données ou instances Redis de manière asynchrone. Si vous utilisez Commerce sur l’infrastructure cloud, vous pouvez configurer les connexions secondaires en modifiant la variable [MYSQL_USE_SECONDAIRE_CONNECTION](https://devdocs.magento.com/cloud/env/variables-deploy.html#mysql_use_slave_connection) et [REDIS_USE_SECONDAIRE_CONNECTION](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_use_slave_connection) dans la variable `.magento.env.yaml` fichier . Un seul noeud doit gérer le trafic de lecture-écriture. Par conséquent, la définition des variables sur `true` entraîne la création d’une connexion secondaire pour le trafic en lecture seule. Définissez les valeurs sur `false` pour supprimer tout tableau de connexion en lecture seule existant du `env.php` fichier .

Exemple de `.magento.env.yaml` fichier :

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

<!-- link definitions -->

[global]: https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/global-options.html
[inventory]: https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html
[mrg]: https://developer.adobe.com/commerce/php/module-reference/
[AsyncOrder]: https://developer.adobe.com/commerce/php/module-reference/module-async-order/
[DeferredTotalCalculating]: https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/
