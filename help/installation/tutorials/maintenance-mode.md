---
title: Activation ou désactivation du mode de maintenance
description: Suivez ces étapes pour personnaliser ce que les clients voient lorsque votre déploiement Adobe Commerce est arrêté pour maintenance.
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: a5dbefda6b77d993756143ef0e7270425f824c44
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---

# Activation ou désactivation du mode de maintenance

Le guide suivant fait référence à une page de mode de maintenance standard. Si vous devez utiliser une page de maintenance personnalisée, reportez-vous à la rubrique [Création d’une page de maintenance personnalisée](../../upgrade/troubleshooting/maintenance-mode-options.md).

Adobe Commerce utilise le [mode de maintenance](../../configuration/bootstrap/application-modes.md#maintenance-mode) pour désactiver le démarrage. La désactivation du démarrage est utile lorsque vous maintenez, mettez à niveau ou reconfigurez votre site.

L’application détecte le mode de maintenance comme suit :

* Si `var/.maintenance.flag` existe, le mode de maintenance est activé et l’application renvoie une page de maintenance 503.
* Si `var/.maintenance.ip` existe et que l’adresse IP du client correspond à l’une des entrées d’adresse IP de ce fichier, la page de maintenance est ignorée pour la requête.

## Installation de l’application

Avant d’utiliser cette commande pour activer ou désactiver le mode de maintenance, vous devez [installer l’application](../advanced.md).

## Activation ou désactivation du mode de maintenance

Utilisez la commande `magento maintenance` CLI pour activer ou désactiver le mode de maintenance.

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

L’option `--ip=<ip address>` est une adresse IP à exclure du mode de maintenance (par exemple, les développeurs qui effectuent la maintenance). Pour exempter plusieurs adresses IP dans la même commande, utilisez l’option plusieurs fois.

>[!NOTE]
>
>L’utilisation de `--ip=<ip address>` avec `magento maintenance:disable` enregistre la liste des adresses IP en vue d’une utilisation ultérieure. Pour effacer la liste des adresses IP exemptées, utilisez `magento maintenance:enable --ip=none` ou consultez [Tenir à jour la liste des adresses IP exemptées](#maintain-the-list-of-exempt-ip-addresses).

La commande `bin/magento maintenance:status` affiche l&#39;état du mode de maintenance.

Par exemple, pour activer le mode de maintenance sans exemption d’adresse IP :

```bash
bin/magento maintenance:enable
```

Pour activer le mode de maintenance pour tous les clients, à l’exception de 192.0.2.10 et 192.0.2.11 :

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

Après avoir placé l’application en mode de maintenance, vous devez arrêter tous les processus consommateurs de file d’attente de messages.
Pour trouver ces processus, vous pouvez exécuter la commande `ps -ef | grep queue:consumers:start`, puis exécuter la commande `kill <process_id>` pour chaque client. Dans un environnement à plusieurs nœuds, répétez cette tâche sur chaque nœud.

## Tenir à jour la liste des adresses IP exemptées

Pour gérer la liste des adresses IP exemptées, vous pouvez utiliser l’option `[--ip=<ip list>]` dans les commandes précédentes ou les méthodes suivantes :

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

La syntaxe `<ip address> .. <ip address>` est une liste facultative d’adresses IP délimitées par des espaces à exempter.

L’option `--none` efface la liste.

## Configurations multi-magasin

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

Si vous souhaitez configurer plusieurs magasins, chacun avec une disposition et un contenu localisé différents, transmettez le paramètre `$_GET['skin']` au processeur prévu.

Dans l’exemple suivant, nous utilisons un fichier de modèle d’erreur de type `503`, qui nécessite du contenu localisé.

Le constructeur de la classe `Error_Processor` accepte un paramètre GET `skin` pour modifier la disposition :

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

Elle peut également être ajoutée à une règle de réécriture dans le fichier `.htaccess` qui ajoute un paramètre `skin` à l’URL.

### Paramètre $_GET[&#39;skin&#39;]

Pour utiliser le paramètre `skin` :

1. Vérifiez si le `.maintenance.flag` existe.
1. Notez l’adresse de l’hôte, qui fait référence au `HTTP_HOST`, ou toute autre variable telle que les variables ENV.
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

1. Modifiez ces fichiers pour fournir du contenu localisé dans le fichier `503.phtml` et un style personnalisé dans le fichier `styles.css`.

   Assurez-vous que vos chemins d’accès pointent vers votre répertoire `errors`. Le nom du répertoire doit correspondre au paramètre d’URL indiqué dans le `RewriteRule`. Dans l’exemple précédent, le répertoire `sub` est utilisé, qui est spécifié comme paramètre dans le `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>Le paramètre [nginx](../../configuration/multi-sites/ms-nginx.md) doit être ajouté pour les configurations multi-magasin.
