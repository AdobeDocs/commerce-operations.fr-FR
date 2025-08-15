---
title: Configurer la file d’attente des messages Amazon
description: Découvrez comment configurer Commerce pour utiliser le service AWS MQ.
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Configurer la file d’attente des messages Amazon

Depuis Commerce version 2.4.3, la file d’attente des messages (MQ) d’Amazon est disponible en tant que remplacement prêt pour le cloud pour les instances de file d’attente des messages sur site.

Pour créer une file d’attente de messages sur AWS, voir [Configuration d’Amazon MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) dans la _documentation AWS_.

## Configuration de Commerce pour AWS MQ

Pour vous connecter au service AWS MQ, configurez l’objet `queue.amqp` dans le fichier `env.php`.
AWS Message Queue requiert une connexion SSL/TLS.

```php
'queue' => [
    'amqp' => [
        'host' => '[host]', //example: c-bf4kk1c5-5gcc-4b43-9b9e-8f5b54d234.mq.us-west-3.amazonaws.com
        'port' => 5671,
        'user' => 'yourusername',
        'password' => 'yourpassword',
        'virtualhost' => '/',

        // AWS fields to add
        'ssl' => 'true'
    ]
],
```

Où :

- `host` : URL du point d’entrée AMQP ; disponible en cliquant sur le nom du courtier dans AWS (supprimez « https:// » et le numéro de port de fin)
- `user` : valeur de nom d&#39;utilisateur saisie lors de la création du courtier AWS MQ
- `password` : valeur de mot de passe saisie lors de la création du courtier AWS MQ

>[!INFO]
>
>Amazon MQ prend uniquement en charge les connexions TLS. La vérification par les pairs n’est pas prise en charge.

Après modification du fichier `env.php`, exécutez la commande suivante pour terminer la configuration :

```bash
bin/magento setup:upgrade
```

## Utilisation du service AWS MQ par Commerce

Le client de file d’attente de messages `async.operations.all` utilise la connexion AMQP.

Ce client achemine tout nom de rubrique précédé de `async` via la connexion AWS MQ.

Par exemple, dans `InventoryCatalog`, il existe :

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

La configuration par défaut de `InventoryCatalog` ne publie pas de messages sur [!DNL RabbitMQ] ; le comportement par défaut consiste à effectuer l’action dans le même thread d’utilisateur. Pour `InventoryCatalog` indiquer de publier des messages, activez `cataloginventory/bulk_operations/async`. Depuis l’administration, accédez à **Magasins** > Configuration > **Catalogue** > **Inventaire** > Opérations en bloc d’administration et définissez `Run asynchronously`sur **Oui**.

## Test de la file d&#39;attente des messages

Pour tester l’envoi de messages de Commerce vers [!DNL RabbitMQ] :

1. Connectez-vous à la console web [!DNL RabbitMQ] dans AWS pour surveiller les files d’attente.
1. Dans Admin, créez un produit.
1. Créez une source d’inventaire.
1. Activez **Magasins** > Configuration > **Catalogue** > **Inventaire** > Admin > Opérations en bloc > Exécuter de manière asynchrone.
1. Accédez à **Catalogue** > Produits. Dans la grille, sélectionnez le produit créé ci-dessus et cliquez sur **Attribuer le Source d’inventaire**.
1. Cliquez sur **Enregistrer et fermer** pour terminer le processus.

   Vous devriez maintenant voir des messages apparaître dans la console web [!DNL RabbitMQ].

1. Démarrez le client de file d’attente de messages `async.operations.all`.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

Le message mis en file d’attente doit maintenant être traité dans la console web [!DNL RabbitMQ].
Vérifiez que les sources d&#39;inventaire ont changé sur le produit dans l&#39;administrateur.
