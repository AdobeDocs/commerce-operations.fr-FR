---
title: Activer ou désactiver le mode de maintenance
description: Suivez ces étapes pour personnaliser ce que voient les clients lorsque votre déploiement Adobe Commerce est arrêté pour maintenance.
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: a5dbefda6b77d993756143ef0e7270425f824c44
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Activer ou désactiver le mode de maintenance

Le guide suivant fait référence à une page de mode de maintenance standard. Si vous devez utiliser une page de maintenance personnalisée, consultez la rubrique [Création de la page de maintenance personnalisée](../../upgrade/troubleshooting/maintenance-mode-options.md) .

Adobe Commerce utilise le [mode de maintenance](../../configuration/bootstrap/application-modes.md#maintenance-mode) pour désactiver le démarrage. La désactivation de l’amorçage s’avère utile lorsque vous maintenez, mettez à niveau ou reconfigurez votre site.

L&#39;application détecte le mode de maintenance comme suit :

* Si `var/.maintenance.flag` existe, le mode de maintenance est activé et l’application renvoie une page de maintenance 503.
* Si `var/.maintenance.ip` existe et que l’adresse IP du client correspond à l’une des entrées d’adresse IP dans ce fichier, la page de maintenance est ignorée pour la requête.

## Installation de l’application

Avant d&#39;utiliser cette commande pour activer ou désactiver le mode de maintenance, vous devez [installer l&#39;application](../advanced.md).

## Activer ou désactiver le mode de maintenance

Utilisez la commande d&#39;interface de ligne de commande `magento maintenance` pour activer ou désactiver le mode de maintenance.

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

L’option `--ip=<ip address>` est une adresse IP qui permet d’exempter le mode de maintenance (par exemple, les développeurs effectuant la maintenance). Pour exempter plusieurs adresses IP dans la même commande, utilisez l’option plusieurs fois.

>[!NOTE]
>
>L’utilisation de `--ip=<ip address>` avec `magento maintenance:disable` enregistre la liste des adresses IP en vue d’une utilisation ultérieure. Pour effacer la liste des adresses IP exemptées, utilisez `magento maintenance:enable --ip=none` ou reportez-vous à la section [Maintenance de la liste des adresses IP exemptées](#maintain-the-list-of-exempt-ip-addresses).

La commande `bin/magento maintenance:status` affiche l’état du mode de maintenance.

Par exemple, pour activer le mode de maintenance sans dispenses d’adresses IP :

```bash
bin/magento maintenance:enable
```

Pour activer le mode de maintenance pour tous les clients, à l’exception des versions 192.0.2.10 et 192.0.2.11 :

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

Après avoir mis l’application en mode de maintenance, vous devez arrêter tous les processus consommateurs de la file d’attente des messages.
Une méthode pour trouver ces processus consiste à exécuter la commande `ps -ef | grep queue:consumers:start`, puis à exécuter la commande `kill <process_id>` pour chaque consommateur. Dans un environnement à plusieurs noeuds, répétez cette tâche sur chaque noeud.

## Maintenir la liste des adresses IP exemptées

Pour conserver la liste des adresses IP exemptées, vous pouvez utiliser l’option `[--ip=<ip list>]` dans les commandes précédentes ou utiliser les éléments suivants :

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

La syntaxe `<ip address> .. <ip address>` est une liste facultative délimitée par des espaces d’adresses IP à exempter.

L’option `--none` efface la liste.

## Configurations multi-magasin

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

Si vous souhaitez configurer plusieurs magasins, chacun avec une disposition différente et un contenu localisé, transmettez le paramètre `$_GET['skin']` au processeur prévu.

Dans l’exemple suivant, nous utilisons un fichier de modèle d’erreur de type `503` qui nécessite du contenu localisé.

Le constructeur de la classe `Error_Processor` accepte un paramètre de GET `skin` pour modifier la mise en page :

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

Vous pouvez également l’ajouter à une règle de réécriture dans le fichier `.htaccess` qui ajoute un paramètre `skin` à l’URL.

### Paramètre $_GET[&#39;peau&#39;]

Pour utiliser le paramètre `skin` :

1. Vérifiez si le `.maintenance.flag` existe.
1. Notez l’adresse de l’hôte, qui fait référence à `HTTP_HOST`, ou toute autre variable telle que les variables ENV.
1. Vérifiez si le paramètre `skin` existe.
1. Définissez le paramètre à l’aide des règles de réécriture ci-dessous.

   Voici quelques exemples de règles de réécriture :

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. Copiez les fichiers suivants :

   * `pub/errors/default/503.phtml` à `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` à `pub/errors/sub/styles.css`

1. Modifiez ces fichiers pour fournir du contenu localisé dans le fichier `503.phtml` et des styles personnalisés dans le fichier `styles.css`.

   Vérifiez que vos chemins d’accès pointent vers votre répertoire `errors`. Le nom du répertoire doit correspondre au paramètre d’URL indiqué dans le `RewriteRule`. Dans l’exemple précédent, le répertoire `sub` est utilisé, qui est spécifié comme paramètre dans le `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>Le paramètre [nginx](../../configuration/multi-sites/ms-nginx.md) doit être ajouté pour les configurations multi-magasin.
