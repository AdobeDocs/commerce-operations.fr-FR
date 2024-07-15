---
title: Définir la valeur des paramètres de bootstrap
description: Découvrez comment définir les paramètres de bootstrap pour l’application Commerce.
exl-id: 4e1e4e5e-e1bc-49a5-8a2a-2e6b91ca9175
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 1%

---

# Paramètres du Bootstrap

Cette rubrique explique comment définir les valeurs des paramètres de bootstrap de l’application Commerce. Voir [Présentation de l’initialisation et de l’amorçage de l’application](initialization.md).

Le tableau suivant décrit les paramètres de bootstrap que vous pouvez définir :

| Paramètre du Bootstrap | Description |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | Spécifie les chemins d’URL et de répertoire personnalisés |
| MAGE_PROFILER | Active les graphiques de dépendances et le profilage des HTMLS |

>[!INFO]
>
>- Tous les paramètres de bootstrap ne sont pas documentés.
>- Vous définissez maintenant le mode de l&#39;application (développeur, valeur par défaut, production) à l&#39;aide de la commande [`magento deploy:mode:set {mode}`](../cli/set-mode.md).

## Définition de paramètres à l’aide d’une variable d’environnement

Cette section explique comment définir les valeurs des paramètres de bootstrap à l’aide de variables d’environnement.

### Définir le mode d’application

Vous pouvez spécifier des variables d’amorçage en tant que variables d’environnement à l’échelle du système, ce qui permet à tous les processus de les utiliser.

Par exemple, vous pouvez utiliser la variable d’environnement système `MAGE_PROFILER` pour spécifier un mode comme suit :

```terminal
MAGE_PROFILER={firebug|csv|<custom value>}
```

Définissez la variable à l’aide d’une commande spécifique au shell. Les shells ayant une syntaxe différente, consultez une référence telle que [unix.stackexchange.com][unix-stackx].

Exemple de shell Bash pour CentOS :

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>Si un `PHP Fatal error` s’affiche dans le navigateur après avoir défini une valeur de profileur, redémarrez votre serveur web. La raison peut être liée à la mise en cache des bytecode PHP, qui met en cache les bytecodes et les classpaths PHP.

## Définition de paramètres pour Apache ou Nginx

Cette section explique comment spécifier le mode pour Apache ou Nginx.

### Paramètre Nginx

Consultez l’ [exemple de configuration Nginx] sur _GitHub_.

### Paramètre Apache .htaccess

Pour définir le mode de l’application, modifiez `.htaccess`. Ainsi, vous n’avez pas à modifier les paramètres Apache.

Vous pouvez modifier `.htaccess` aux emplacements suivants, en fonction du point d’entrée de l’application Commerce :

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**Pour définir une variable** :

1. Ouvrez l’un des fichiers précédents dans un éditeur de texte et ajoutez ou annulez la mise en commentaire du paramètre souhaité.

   Par exemple, pour spécifier un [mode](application-modes.md), annulez la mise en commentaire des éléments suivants :

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. Définissez la valeur de `MAGE_PROFILER` sur l’une des valeurs suivantes :

   ```terminal
   firebug
   csvfile
   <custom value>
   ```

1. Enregistrez vos modifications sur `.htaccess` ; vous n’avez pas besoin de redémarrer Apache pour que la modification soit prise en compte.

### Paramètre Apache

Le serveur web Apache prend en charge le paramétrage du mode d&#39;application à l&#39;aide des directives `mod_env`.

La directive Apache `mod_env` est légèrement différente dans [Apache version 2.2] et [Apache version 2.4].

Les procédures ci-dessous montrent comment définir le mode d’application dans un hôte virtuel Apache. Ce n&#39;est pas la seule façon d&#39;utiliser les directives `mod_env` ; consultez la documentation Apache pour plus de détails.

>[!TIP]
>
>La section suivante suppose que vous avez déjà configuré votre hôte virtuel. Si ce n’est pas le cas, consultez une ressource telle que [ce tutoriel DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**Pour spécifier une variable bootstrap pour Apache sur Ubuntu,** :

1. En tant qu’utilisateur disposant des privilèges `root`, ouvrez votre fichier de configuration d’hôte virtuel dans un éditeur de texte.

   Par exemple, si votre hôte virtuel est nommé `my.magento`,

   - Apache 2.4 : `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2 : `vim /etc/apache2/sites-available/my.magento`

1. N&#39;importe où dans la configuration de l&#39;hôte virtuel, ajoutez la ligne suivante :

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   Par exemple,

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. Enregistrez vos modifications et quittez l’éditeur de texte.
1. Activez votre hôte virtuel si vous ne l’avez pas déjà fait :

   ```bash
   a2ensite <virtual host config file name>
   ```

   Par exemple,

   ```bash
   a2ensite my.magento.conf
   ```

1. Après avoir défini le mode, redémarrez le serveur web :

   - Ubuntu : `service apache2 restart`
   - CentOS : `service httpd restart`

>[!TIP]
>
>Cette section suppose que vous avez déjà configuré votre hôte virtuel. Si ce n’est pas le cas, consultez une ressource telle que [ce tutoriel DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**Pour spécifier une variable bootstrap pour Apache sur CentOS** :

1. En tant qu&#39;utilisateur disposant de droits `root`, ouvrez `/etc/httpd/conf/httpd.conf` dans un éditeur de texte.

1. N&#39;importe où dans la configuration de l&#39;hôte virtuel, ajoutez la ligne suivante :

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   Par exemple,

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. Enregistrez vos modifications et quittez l’éditeur de texte.

1. Après avoir défini le mode, redémarrez le serveur web :

   - Ubuntu : `service apache2 restart`
   - CentOS : `service httpd restart`

<!-- link definitions -->

[Apache version 2.2]: https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache version 2.4]: https://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Exemple de configuration Nginx]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables
