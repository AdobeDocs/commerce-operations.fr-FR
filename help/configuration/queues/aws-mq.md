---
title: Configuration de la file d’attente des messages Amazon
description: Découvrez comment configurer Commerce pour utiliser le service AWS MQ.
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Configuration de la file d’attente des messages Amazon

Depuis Commerce 2.4.3, la file d’attente des messages Amazon (MQ) est disponible en tant que remplacement prêt pour le cloud pour les instances de file d’attente des messages sur site.

Pour créer une file de messages sur AWS, voir [Configuration d’Amazon MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) dans la _documentation AWS_.

## Configuration de Commerce pour AWS MQ

Pour vous connecter au service AWS MQ, configurez l’objet `queue.amqp` dans le fichier `env.php`.
La file d’attente des messages AWS requiert une connexion SSL/TLS.

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

- `host` : URL du point de terminaison AMQP ; disponible en cliquant sur le nom du courtier dans AWS (supprimez &quot;https://&quot; et le numéro de port de fin)
- `user` : valeur du nom d’utilisateur saisie lors de la création du courtier AWS MQ
- `password` : valeur du mot de passe saisie lors de la création du courtier AWS MQ

>[!INFO]
>
>Amazon MQ prend uniquement en charge les connexions TLS. La vérification par les pairs n’est pas prise en charge.

Après avoir modifié le fichier `env.php`, exécutez la commande suivante pour terminer la configuration :

```bash
bin/magento setup:upgrade
```

## Utilisation du service AWS MQ par Commerce

Le consommateur de file d’attente de messages `async.operations.all` utilise la connexion AMQP.

Ce consommateur achemine tout nom de rubrique précédé du préfixe `async` par le biais de la connexion AWS MQ.

Par exemple, dans `InventoryCatalog`, il existe :

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

La configuration par défaut de `InventoryCatalog` ne publie pas de messages sur [!DNL RabbitMQ] ; le comportement par défaut consiste à effectuer l’action dans le même thread d’utilisateur. Pour indiquer à `InventoryCatalog` de publier des messages, activez `cataloginventory/bulk_operations/async`. À partir de l’administrateur, accédez à **Magasins** > Configuration > **Catalogue** > **Inventaire** > Opérations en masse de l’administrateur et définissez `Run asynchronously` sur **Oui**.

## Test de la file d’attente des messages

Pour tester l&#39;envoi des messages de Commerce vers [!DNL RabbitMQ] :

1. Connectez-vous à la console web [!DNL RabbitMQ] dans AWS pour surveiller les files d’attente.
1. Dans l’Admin, créez un produit.
1. Créez une source d’inventaire.
1. Activez **Magasins** > Configuration > **Catalogue** > **Inventaire** > Opérations en bloc d’administration > Exécuter de manière asynchrone.
1. Accédez à **Catalogue** > Produits. Dans la grille, sélectionnez le produit créé ci-dessus et cliquez sur **Attribuer le Source d’inventaire**.
1. Cliquez sur **Enregistrer et fermer** pour terminer le processus.

   Vous devriez maintenant voir les messages s’afficher dans la console web [!DNL RabbitMQ].

1. Démarrez le consommateur de file d’attente de messages `async.operations.all`.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

Vous devriez maintenant voir le message en file d’attente être traité dans la console web [!DNL RabbitMQ].
Vérifiez que les sources d’inventaire ont changé sur le produit dans Admin.
