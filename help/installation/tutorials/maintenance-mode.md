---
title: Activation ou désactivation du mode de maintenance
description: Suivez ces étapes pour personnaliser ce que voient les clients lorsque votre déploiement Adobe Commerce ou Magento Open Source est arrêté pour maintenance.
source-git-commit: bc025217ed7bc2195c0a2d919139abe13d184259
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---


# Activation ou désactivation du mode de maintenance

Le guide suivant fait référence à une page de mode de maintenance standard. Si vous devez utiliser une page de maintenance personnalisée, reportez-vous à la section [Création d’une page de maintenance personnalisée](../../upgrade/troubleshooting/maintenance-mode-options.md) rubrique.

Utilisation d’Adobe Commerce et de Magento Open Source [mode de maintenance](../../configuration/bootstrap/application-modes.md#maintenance-mode) pour désactiver l’amorçage. La désactivation de l’amorçage s’avère utile lorsque vous maintenez, mettez à niveau ou reconfigurez votre site.

L&#39;application détecte le mode de maintenance comme suit :

* If `var/.maintenance.flag` n’existe pas, le mode de maintenance est désactivé et l’application fonctionne normalement.
* Sinon, le mode de maintenance est activé, sauf si `var/.maintenance.ip` existe.

   `var/.maintenance.ip` peut contenir une liste d’adresses IP. Si un point d’entrée est accessible en HTTP et que l’adresse IP du client correspond à l’une des entrées de cette liste, le mode de maintenance est désactivé.

## Installation de l’application

Avant d’utiliser cette commande pour activer ou désactiver le mode de maintenance, vous devez : [installation de l’application](../advanced.md).

## Activation ou désactivation du mode de maintenance

Utilisez la variable `magento maintenance` Commande de l’interface de ligne de commande pour activer ou désactiver le mode de maintenance.

Utilisation des commandes :

```bash
bin/magento maintenance:enable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:disable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:status
```

Le `--ip=<ip address>` est une adresse IP qui permet d’exempter le mode de maintenance (par exemple, les développeurs effectuant la maintenance). Pour exempter plusieurs adresses IP dans la même commande, utilisez l’option plusieurs fois.

>[!NOTE]
>
>Utilisation `--ip=<ip address>` avec `magento maintenance:disable` enregistre la liste des adresses IP en vue d’une utilisation ultérieure. Pour effacer la liste des adresses IP exemptées, utilisez `magento maintenance:enable --ip=none` ou voir [Maintenir la liste des adresses IP exemptées](#maintain-the-list-of-exempt-ip-addresses).

Le `bin/magento maintenance:status` affiche l’état du mode de maintenance.

Par exemple, pour activer le mode de maintenance sans dispenses d’adresses IP :

```bash
bin/magento maintenance:enable
```

Pour activer le mode de maintenance pour tous les clients, à l’exception des versions 192.0.2.10 et 192.0.2.11 :

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

Après avoir mis l’application en mode de maintenance, vous devez arrêter tous les processus consommateurs de la file d’attente des messages.
L’une des manières de trouver ces processus consiste à exécuter la variable `ps -ef | grep queue:consumers:start` puis exécutez la commande `kill <process_id>` pour chaque consommateur. Dans un environnement à plusieurs noeuds, répétez cette tâche sur chaque noeud.

## Maintenir la liste des adresses IP exemptées

Pour conserver la liste des adresses IP exemptées, vous pouvez utiliser la variable `[--ip=<ip list>]` dans les commandes précédentes ou vous pouvez utiliser les options suivantes :

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

Le `<ip address> .. <ip address>` La syntaxe est une liste facultative d’adresses IP à exempter délimitée par des espaces.

Le `--none` efface la liste.

## Configurations multi-magasin

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

Si vous souhaitez configurer plusieurs magasins, chacun avec une disposition différente et un contenu localisé, transmettez la variable `$_GET['skin']` au processeur prévu.

Dans l’exemple suivant, nous utilisons une `503` type fichier de modèle d’erreur, qui nécessite du contenu localisé.

Le constructeur de la variable `Error_Processor` accepte une classe `skin` paramètre de GET pour modifier la mise en page :

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

Vous pouvez également l’ajouter à une règle de réécriture dans la variable `.htaccess` qui ajoute un `skin` à l’URL.

### $_GET[&#39;peau&#39;] parameter

Pour utiliser la variable `skin` parameter:

1. Vérifiez si la variable `.maintenance.flag` existe.
1. Notez l’adresse de l’hôte, qui fait référence au `HTTP_HOST`ou toute autre variable telle que les variables ENV.
1. Vérifiez si la variable `skin` existe.
1. Définissez le paramètre à l’aide des règles de réécriture ci-dessous.

   Voici quelques exemples de règles de réécriture :

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. Copiez les fichiers suivants :

   * `pub/errors/default/503.phtml` to `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` to `pub/errors/sub/styles.css`

1. Modifiez ces fichiers pour fournir du contenu localisé dans la `503.phtml` et le style personnalisé dans la variable `styles.css` fichier .

   Assurez-vous que vos chemins pointent vers vos `errors` répertoire . Le nom du répertoire doit correspondre au paramètre d’URL indiqué dans la variable `RewriteRule`. Dans l’exemple précédent, la variable `sub` est utilisé, qui est spécifié en tant que paramètre dans la variable `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>Le [nginx](../../configuration/multi-sites/ms-nginx.md) doit être ajouté pour les configurations multi-magasin.
