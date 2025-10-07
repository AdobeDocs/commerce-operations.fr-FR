---
title: Démarrage rapide de l’installation locale
description: Découvrez comment installer Adobe Commerce sur votre propre infrastructure à l’aide du compositeur. Découvrez les étapes de démarrage rapide et les exigences de configuration.
exl-id: a93476e8-2b30-461a-91df-e73eb1a14d3c
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 0%

---

# Démarrage rapide de l’installation locale

Les instructions de cette page décrivent comment installer Adobe Commerce sur une infrastructure auto-hébergée. Pour obtenir des conseils sur la mise à niveau d’une installation existante, consultez le [_Guide de mise à niveau_](../upgrade/overview.md).

Adobe utilise [Composer](https://getcomposer.org/) pour gérer les composants Adobe Commerce et leurs dépendances. L’utilisation du compositeur pour obtenir le métapaquet Adobe Commerce offre les avantages suivants :

- Réutiliser des bibliothèques tierces sans les regrouper avec du code source
- Réduisez les conflits d’extension et les problèmes de compatibilité en utilisant une architecture basée sur des composants avec une gestion robuste des dépendances
- Respectez les normes [PHP-Framework Interoperability Group (FIG)](https://www.php-fig.org/)
- Recompressez Magento Open Source avec d’autres composants.
- Utilisation du logiciel Adobe Commerce dans un environnement de production

>[!NOTE]
>
>Les développeurs qui contribuent à Magento Open Source doivent utiliser la méthode d’installation [basée sur Git](https://developer.adobe.com/commerce/contributor/guides/install/).

## Conditions préalables

Avant de continuer, vous devez effectuer les opérations suivantes :

- Effectuez toutes les [tâches préalables](system-requirements.md).
- [Installez le compositeur](https://getcomposer.org/download/).
- Obtenez les [clés d’authentification](prerequisites/authentication-keys.md) dans le référentiel du compositeur Adobe Commerce.

## Connexion en tant que propriétaire du système de fichiers

Découvrez la propriété, les autorisations et le propriétaire du système de fichiers dans la rubrique [Présentation de la propriété et des autorisations](prerequisites/file-system/overview.md).

Pour passer au propriétaire du système de fichiers :

1. Connectez-vous au serveur d’applications en tant qu’utilisateur ou en tant qu’utilisateur disposant des autorisations d’écriture sur le système de fichiers.

   Si vous utilisez le shell bash, vous pouvez utiliser la syntaxe suivante pour passer au propriétaire du système de fichiers et saisir simultanément la commande :

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Si le propriétaire du système de fichiers n’autorise pas les connexions, vous pouvez effectuer les opérations suivantes :

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Pour exécuter des commandes d’interface de ligne de commande à partir de n’importe quel répertoire, ajoutez `<app_root>/bin` à votre `PATH` système.

   Comme les shell ont des syntaxes différentes, consultez une référence comme [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Exemple de shell Bash pour CentOS :

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Vous pouvez éventuellement exécuter les commandes des manières suivantes :

   - `cd <app_root>/bin` et exécutez-les en tant que `./magento <command name>`
   - `app_root>/bin/magento <command name>`
   - `<app_root>` est un sous-répertoire de votre serveur web docroot

## Obtenir le métapaquet

Pour obtenir le métapaquet Adobe Commerce :

1. Connectez-vous au serveur d’applications en tant que [propriétaire du système de fichiers](prerequisites/file-system/overview.md) ou passez à ce serveur.
1. Passez au répertoire docroot du serveur web ou à un répertoire que vous avez configuré en tant qu&#39;hôte virtuel docroot.
1. Créez un projet Composer à l’aide d’un métapaquet Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   A l’invite, saisissez vos clés d’authentification. Les clés publiques et privées sont créées et configurées à partir de [Commerce Marketplace - Access Keys](https://commercemarketplace.adobe.com/customer/account/login/). Pour le `[!UICONTROL username]`, copiez et collez la valeur de la clé publique. Pour le `[!UICONTROL password]`, copiez et collez la valeur de la clé privée.

   >[!NOTE]
   >
   > Si vous utilisez un fichier `[auth.json](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/authentication-keys)` du compositeur ou une variable d’environnement configurée avec vos clés d’authentification Commerce, vous n’êtes pas invité à saisir les clés d’authentification.

   Si vous rencontrez des erreurs, telles que `Could not find package...` ou `...no matching package found`, assurez-vous qu’il n’y a aucune faute de frappe dans votre commande. Si vous rencontrez toujours des erreurs, il se peut que vous ne soyez pas autorisé à télécharger Adobe Commerce. Contactez [l’assistance Adobe Commerce](https://support.magento.com/hc/en-us) pour obtenir de l’aide.

   Voir [Dépannage](https://support.magento.com/hc/en-us/articles/360033818091) pour obtenir de l’aide sur d’autres erreurs.

### Exemple - Version mineure

Les versions mineures contiennent de nouvelles fonctionnalités, des correctifs de qualité et des correctifs de sécurité. Utilisez le compositeur pour spécifier une version mineure. Par exemple, pour spécifier le métapaquet Adobe Commerce 2.4.6 :

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### Exemple - Correctif de qualité

Les correctifs de qualité contiennent principalement des correctifs de sécurité _et_ fonctionnels. Cependant, ils peuvent également parfois contenir de nouvelles fonctionnalités rétrocompatibles. Utilisez le compositeur pour télécharger un correctif de qualité. Par exemple, pour spécifier le métapaquet Adobe Commerce 2.4.6 :

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### Exemple - Correctif de sécurité

Les correctifs de sécurité contiennent uniquement des correctifs de sécurité. Ils sont conçus pour accélérer et faciliter le processus de mise à niveau.

Les correctifs de sécurité utilisent la `2.4.6-px` de convention de nommage du compositeur. Utilisez le compositeur pour spécifier un correctif. Par exemple, pour télécharger le métapaquet Adobe Commerce 2.4.6-p1 :

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6-p1 <install-directory-name>
```

## Définition des autorisations de fichier

Vous devez définir des autorisations de lecture et d’écriture pour le groupe de serveurs web avant d’installer Adobe Commerce. Cela est nécessaire pour que la ligne de commande puisse écrire des fichiers dans le système de fichiers.

```bash
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## Installation de l’application

Vous devez utiliser la ligne de commande pour installer Adobe Commerce.

Cet exemple suppose que le répertoire d’installation est nommé `magento2ee`, que le `db-host` se trouve sur le même ordinateur (`localhost`) et que les `db-name`, `db-user` et `db-password` sont tous `magento` :

```bash
bin/magento setup:install \
--base-url=http://localhost/magento2ee \
--db-host=localhost \
--db-name=magento \
--db-user=magento \
--db-password=magento \
--admin-firstname=admin \
--admin-lastname=admin \
--admin-email=admin@admin.com \
--admin-user=admin \
--admin-password=admin123 \
--language=en_US \
--currency=USD \
--timezone=America/Chicago \
--use-rewrites=1 \
--search-engine=opensearch \
--opensearch-host=os-host.example.com \
--opensearch-port=9200 \
--opensearch-index-prefix=magento2 \
--opensearch-timeout=15
```

>[!TIP]
>
>Vous pouvez personnaliser l’URI d’administration avec l’option `--backend-frontname` . Cependant, Adobe recommande d’omettre cette option et de permettre à la commande d’installation de générer automatiquement un URI aléatoire. Un URI aléatoire est plus difficile à exploiter pour les pirates ou les logiciels malveillants. L’URI s’affiche dans la console une fois l’installation terminée.

>[!TIP]
>
>Pour obtenir une description complète des options d’installation de l’interface en ligne de commande, voir [ Installer l’application à partir de la ligne de commande ](advanced.md).

## Résumé des commandes

Pour afficher la liste complète des commandes, saisissez :

```bash
bin/magento list
```

Pour obtenir de l’aide sur une commande spécifique, saisissez :

```bash
bin/magento help <command>
```

Par exemple :

```bash
bin/magento help setup:install
```

```bash
bin/magento help cache:enable
```

Le tableau suivant résume les commandes disponibles. Les commandes sont présentées sous forme de résumé uniquement. Pour plus d&#39;informations sur une commande, cliquez sur le lien dans la colonne Commande.

| Commande | Description | Conditions préalables |
|--- |--- |--- |
| `magento setup:install` | Installe l’application | Aucune |
| `magento setup:uninstall` | Supprime l’application. | Application installée |
| `magento setup:upgrade` | Met à jour l’application. | Configuration du déploiement |
| `magento maintenance:{enable/disable}` | Active ou désactive le mode de maintenance (en mode de maintenance, seules les adresses IP exemptées peuvent accéder à Admin ou Storefront). | Application installée |
| `magento setup:config:set` | Crée ou met à jour la configuration de déploiement. | Aucune |
| `magento module:{enable/disable}` | Activez ou désactivez les modules. | Aucune |
| `magento setup:store-config:set` | Définit les options liées au storefront, telles que l’URL de base, la langue et le fuseau horaire. | Configuration du déploiement |
| `magento setup:db-schema:upgrade` | Met à jour le schéma de la base de données. | Configuration du déploiement |
| `magento setup:db-data:upgrade` | Met à jour les données de la base. | Configuration du déploiement |
| `magento setup:db:status` | Vérifie si la base de données est à jour avec le code. | Configuration du déploiement |
| `magento admin:user:create` | Crée un utilisateur administrateur. | Vous pouvez créer des utilisateurs pour les éléments suivants :<br><br>Configuration du déploiement<br><br>Activez au minimum les modules `Magento_User` et `Magento_Authorization`Base de données<br><br>la façon la plus simple d’utiliser `bin/magento setup:upgrade`) |
| `magento list` | Répertorie toutes les commandes disponibles. | Aucune |
| `magento help` | Fournit de l’aide pour la commande spécifiée. | Aucune |

### Arguments courants

Les arguments suivants sont communs à toutes les commandes. Ces commandes peuvent être exécutées avant ou après l’installation de l’application :

| Version longue | Version courte | Signification |
|--- |--- |--- |
| `--help` | `-h` | Obtenez de l’aide pour n’importe quelle commande. Par exemple, `./magento help setup:install` ou `./magento help setup:config:set`. |
| `--quiet` | `-q` | Mode silencieux ; aucune sortie. |
| `--no-interaction` | `-n` | Aucune question interactive. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Niveau de détail. Par exemple, `--verbose=3` ou `-vvv` affiche le niveau de détail du débogage, qui est la sortie la plus détaillée. La valeur par défaut est `--verbose=1` ou `-v`. |
| `--version` | `-V` | Afficher cette version de l&#39;application |
| `--ansi` | s.o. | Forcer la sortie ANSI |
| `--no-ansi` | s.o. | Désactiver la sortie ANSI |

>[!NOTE]
>
>Félicitations ! Vous avez terminé l’installation rapide. Besoin d&#39;une aide plus avancée ? Consultez le guide [Installation avancée](advanced.md).
