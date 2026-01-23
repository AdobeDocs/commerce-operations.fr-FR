---
title: Définir la valeur des paramètres d’amorçage
description: Découvrez comment définir les paramètres d’amorçage pour l’application Commerce.
exl-id: 4e1e4e5e-e1bc-49a5-8a2a-2e6b91ca9175
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 1%

---

# Paramètres de Bootstrap

Cette rubrique explique comment définir les valeurs des paramètres d’amorçage de l’application Commerce. Voir [Aperçu de l&#39;initialisation et du démarrage de l&#39;application](initialization.md).

Le tableau suivant décrit les paramètres d’amorçage que vous pouvez définir :

| Paramètre Bootstrap | Description |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | Spécifie le répertoire personnalisé et les chemins d’URL |
| MAGE_PROFILER | Active les graphiques de dépendance et le profilage HTML |

>[!INFO]
>
>- Tous les paramètres de bootstrap ne sont pas documentés.
>- Vous pouvez maintenant définir le mode d’application (développeur, par défaut, production) à l’aide de la commande [`magento deploy:mode:set {mode}`](../cli/set-mode.md).

## Définition de paramètres à l’aide d’une variable d’environnement

Cette section explique comment définir les valeurs des paramètres de bootstrap à l’aide de variables d’environnement.

### Définir le mode d’application

Vous pouvez spécifier les variables de bootstrap en tant que variables d’environnement à l’échelle du système, ce qui permet à tous les processus de les utiliser.

Par exemple, vous pouvez utiliser la variable d’environnement système `MAGE_PROFILER` pour spécifier un mode comme suit :

```
MAGE_PROFILER={firebug|csv|<custom value>}
```

Définissez la variable à l’aide d’une commande spécifique au shell. Étant donné que les shell ont une syntaxe différente, consultez une référence telle que [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

Exemple de shell Bash pour CentOS :

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>Si un `PHP Fatal error` s’affiche dans le navigateur après avoir défini une valeur de profil, redémarrez votre serveur web. La raison peut être liée à la mise en cache du bytecode PHP, qui met en cache les bytecode et les classes de chemins PHP.

## Définition des paramètres pour Apache ou Nginx

Cette section explique comment spécifier le mode pour Apache ou Nginx.

### Paramètre Nginx

Voir l’exemple de configuration [Nginx](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16) sur _GitHub_.

### Paramètre Apache .htaccess

Vous pouvez définir le mode d’application en modifiant les `.htaccess`. Ainsi, vous n’avez pas à modifier les paramètres Apache.

Vous pouvez modifier les `.htaccess` à l’un des emplacements suivants, en fonction de votre point d’entrée dans l’application Commerce :

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**Pour définir une variable** :

1. Ouvrez l’un des fichiers précédents dans un éditeur de texte et ajoutez ou supprimez les commentaires du paramètre souhaité.

   Par exemple, pour spécifier un [mode](application-modes.md), supprimez les commentaires suivants :

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. Définissez la valeur de `MAGE_PROFILER` sur l’une des valeurs suivantes :

   ```
   firebug
   csvfile
   <custom value>
   ```

1. Enregistrez vos modifications dans `.htaccess` ; il n’est pas nécessaire de redémarrer Apache pour qu’elles soient prises en compte.

### Paramètre Apache

Le serveur web Apache prend en charge la définition du mode d’application à l’aide de directives `mod_env`.

La directive Apache `mod_env` est légèrement différente dans [Apache version 2.2](https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv) et [Apache version 2.4](https://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv).

Les procédures qui suivent montrent comment définir le mode d’application dans un hôte virtuel Apache. Ce n’est pas la seule façon d’utiliser les directives `mod_env`. Pour plus d’informations, consultez la documentation Apache .

>[!TIP]
>
>La section suivante suppose que vous avez déjà configuré votre hôte virtuel. Si ce n’est pas encore fait, consultez une ressource telle que [ce tutoriel DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**Pour spécifier une variable de démarrage pour Apache sur Ubuntu** :

1. En tant qu’utilisateur disposant de privilèges `root`, ouvrez votre fichier de configuration d’hôte virtuel dans un éditeur de texte.

   Par exemple, si votre hôte virtuel est nommé `my.magento`,

   - Apache 2.4 : `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2 : `vim /etc/apache2/sites-available/my.magento`

1. À tout endroit de la configuration de l’hôte virtuel, ajoutez la ligne suivante :

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

1. Après avoir défini le mode , redémarrez le serveur web :

   - Ubuntu : `service apache2 restart`
   - CentOS : `service httpd restart`

>[!TIP]
>
>Cette section suppose que vous avez déjà configuré votre hôte virtuel. Si ce n’est pas encore fait, consultez une ressource telle que [ce tutoriel DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**Pour spécifier une variable de démarrage pour Apache sous CentOS** :

1. En tant qu’utilisateur disposant de droits d’`root`, ouvrez `/etc/httpd/conf/httpd.conf` dans un éditeur de texte.

1. À tout endroit de la configuration de l’hôte virtuel, ajoutez la ligne suivante :

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   Par exemple,

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. Enregistrez vos modifications et quittez l’éditeur de texte.

1. Après avoir défini le mode , redémarrez le serveur web :

   - Ubuntu : `service apache2 restart`
   - CentOS : `service httpd restart`

