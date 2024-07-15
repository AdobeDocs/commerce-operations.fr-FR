---
title: Démarrage rapide de l’installation sur site
description: Pour installer Adobe Commerce sur une infrastructure que vous détenez, procédez comme suit.
exl-id: a93476e8-2b30-461a-91df-e73eb1a14d3c
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---

# Démarrage rapide de l’installation sur site

Les instructions de cette page décrivent comment installer Adobe Commerce sur l’infrastructure [auto-hébergée](../implementation-playbook/infrastructure/self-hosting/overview.md). Pour plus d&#39;informations sur la mise à niveau d&#39;une installation existante, consultez le [_Guide de mise à niveau_](../upgrade/overview.md).

Adobe utilise [Composer](https://getcomposer.org/) pour gérer les composants Adobe Commerce et leurs dépendances. L’utilisation du compositeur pour obtenir le métappackage Adobe Commerce offre les avantages suivants :

- Réutilisation de bibliothèques tierces sans les regrouper avec du code source
- Réduisez les conflits d’extension et les problèmes de compatibilité en utilisant une architecture basée sur des composants avec une gestion robuste des dépendances.
- Découvrez les normes [PHP-Framework Interoperability Group (FIG)](https://www.php-fig.org/)
- Magento Open Source de package avec d’autres composants
- Utiliser le logiciel Adobe Commerce dans un environnement de production

>[!NOTE]
>
>Les développeurs contribuant à Magento Open Source doivent utiliser la méthode d’installation [git-based](https://developer.adobe.com/commerce/contributor/guides/install/) .

## Conditions préalables

Avant de poursuivre, vous devez effectuer les opérations suivantes :

- Effectuez toutes les [tâches préalables requises](system-requirements.md).
- [Installer le compositeur](https://getcomposer.org/download/).
- Procurez-vous les [clés d’authentification](prerequisites/authentication-keys.md) au référentiel du compositeur Adobe Commerce.

## Connexion en tant que propriétaire du système de fichiers

Découvrez la propriété, les autorisations et le propriétaire du système de fichiers dans la [rubrique Présentation de la propriété et des autorisations](prerequisites/file-system/overview.md).

Pour passer au propriétaire du système de fichiers :

1. Connectez-vous au serveur d’applications en tant qu’utilisateur ou passez à un utilisateur autorisé à écrire sur le système de fichiers.

   Si vous utilisez le shell bash, vous pouvez utiliser la syntaxe suivante pour basculer vers le propriétaire du système de fichiers et saisir la commande en même temps :

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Si le propriétaire du système de fichiers n’autorise pas les connexions, vous pouvez effectuer les opérations suivantes :

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Pour exécuter des commandes d’interface de ligne de commande à partir de n’importe quel répertoire, ajoutez `<app_root>/bin` à votre système `PATH`.

   Comme les shells ont des syntaxes différentes, consultez une référence comme [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Exemple de shell bash pour CentOS :

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Vous pouvez éventuellement exécuter les commandes comme suit :

   - `cd <app_root>/bin` et exécutez-les comme `./magento <command name>`
   - `app_root>/bin/magento <command name>`
   - `<app_root>` est un sous-répertoire de votre serveur web docroot

## Obtention du métappackage

Pour obtenir le métappackage Adobe Commerce :

1. Connectez-vous à votre serveur d’applications en tant que [propriétaire du système de fichiers](prerequisites/file-system/overview.md) ou basculez-vous vers cette application.
1. Modifiez le répertoire docroot du serveur web ou un répertoire que vous avez configuré comme docroot d’hôte virtuel.
1. Créez un projet Composer à l’aide d’un métapaquet Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Lorsque vous y êtes invité, saisissez vos clés d’authentification. Les clés publique et privée sont créées et configurées dans votre [Commerce Marketplace](https://commercemarketplace.adobe.com/customer/account/login/).

   >[!NOTE]
   >
   > Lors de l’utilisation d’un fichier de compositeur `auth.json` ou d’une variable d’environnement, vous ne serez pas invité à saisir vos clés d’authentification.

   Si vous rencontrez des erreurs, telles que `Could not find package...` ou `...no matching package found`, assurez-vous qu’il n’y a pas de fautes de frappe dans votre commande. Si vous rencontrez toujours des erreurs, il se peut que vous ne soyez pas autorisé à télécharger Adobe Commerce. Contactez le [support Adobe Commerce](https://support.magento.com/hc/en-us) pour obtenir de l’aide.

   Voir [Dépannage](https://support.magento.com/hc/en-us/articles/360033818091) pour obtenir de l’aide avec plus d’erreurs.

### Exemple - Version mineure

Les versions mineures contiennent de nouvelles fonctionnalités, des correctifs de qualité et des correctifs de sécurité. Utilisez le compositeur pour spécifier une version mineure. Par exemple, pour spécifier le métappackage Adobe Commerce 2.4.6 :

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### Exemple - Correctif de qualité

Les correctifs de qualité contiennent principalement des correctifs de sécurité _fonctionnels et_. Cependant, elles peuvent également parfois contenir de nouvelles fonctionnalités rétrocompatibles. Utilisez le compositeur pour télécharger un correctif de qualité. Par exemple, pour spécifier le métappackage Adobe Commerce 2.4.6 :

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### Exemple - Correctif de sécurité

Les correctifs de sécurité contiennent uniquement des correctifs de sécurité. Ils sont conçus pour faciliter et accélérer le processus de mise à niveau.

Les correctifs de sécurité utilisent la convention d’affectation des noms du compositeur `2.4.6-px`. Utilisez le compositeur pour spécifier un correctif. Par exemple, pour télécharger le métappackage Adobe Commerce 2.4.6-p1 :

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6-p1 <install-directory-name>
```

## Définition des autorisations de fichier

Avant d’installer Adobe Commerce, vous devez définir des autorisations de lecture-écriture pour le groupe de serveurs web. Cela est nécessaire afin que la ligne de commande puisse écrire des fichiers dans le système de fichiers.

```terminal
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## Installation de l’application

Vous devez utiliser la ligne de commande pour installer Adobe Commerce.

Cet exemple suppose que le répertoire d’installation est nommé `magento2ee`, que `db-host` se trouve sur le même ordinateur (`localhost`) et que les répertoires `db-name`, `db-user` et `db-password` sont tous `magento` :

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
>Vous pouvez personnaliser l’URI d’administration à l’aide de l’option `--backend-frontname` . Cependant, Adobe recommande d’ignorer cette option et de permettre à la commande d’installation de générer automatiquement un URI aléatoire. Un URI aléatoire est plus difficile à exploiter pour les hackers ou les logiciels malveillants. L’URI s’affiche dans la console lorsque l’installation est terminée.

>[!TIP]
>
>Pour une description complète des options d’installation de l’interface de ligne de commande, voir [Installation de l’application à partir de la ligne de commande](advanced.md).

## Synthèse des commandes

Pour afficher une liste complète des commandes, saisissez :

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

Le tableau suivant résume les commandes disponibles. Les commandes sont présentées sous forme de résumé uniquement. Pour plus d’informations sur une commande, cliquez sur le lien dans la colonne Commande .

| Commande | Description | Conditions préalables |
|--- |--- |--- |
| `magento setup:install` | Installation de l’application | Aucun |
| `magento setup:uninstall` | Supprime l’application. | Application installée |
| `magento setup:upgrade` | Met à jour l’application. | Configuration du déploiement |
| `magento maintenance:{enable/disable}` | Active ou désactive le mode de maintenance (en mode de maintenance, seules les adresses IP exemptées peuvent accéder à l’administrateur ou au storefront). | Application installée |
| `magento setup:config:set` | Crée ou met à jour la configuration du déploiement. | Aucun |
| `magento module:{enable/disable}` | Activez ou désactivez les modules. | Aucun |
| `magento setup:store-config:set` | Définit les options liées au storefront, telles que l’URL de base, la langue, le fuseau horaire. | Configuration du déploiement |
| `magento setup:db-schema:upgrade` | Met à jour le schéma de la base de données. | Configuration du déploiement |
| `magento setup:db-data:upgrade` | Met à jour les données de la base. | Configuration du déploiement |
| `magento setup:db:status` | Vérifie si la base de données est à jour avec le code. | Configuration du déploiement |
| `magento admin:user:create` | Crée un utilisateur administrateur. | Vous pouvez créer des utilisateurs pour les éléments suivants : <br><br>Configuration de déploiement<br><br>Activez au minimum les `Magento_User` et `Magento_Authorization` modules<br><br>Base de données (la façon la plus simple est d&#39;utiliser `bin/magento setup:upgrade`) |
| `magento list` | Répertorie toutes les commandes disponibles. | Aucun |
| `magento help` | Fournit de l’aide pour la commande spécifiée. | Aucun |

### Arguments courants

Les arguments suivants sont communs à toutes les commandes. Ces commandes peuvent être exécutées avant ou après l’installation de l’application :

| Version longue | Version courte | Signification |
|--- |--- |--- |
| `--help` | `-h` | Obtenez de l’aide pour n’importe quelle commande. Par exemple, `./magento help setup:install` ou `./magento help setup:config:set`. |
| `--quiet` | `-q` | Mode silencieux ; pas de sortie. |
| `--no-interaction` | `-n` | Aucune question interactive. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Niveau de verbosité. Par exemple, `--verbose=3` ou `-vvv` affiche la verbosité de débogage, qui est la sortie la plus détaillée. La valeur par défaut est `--verbose=1` ou `-v`. |
| `--version` | `-V` | Afficher cette version de l’application |
| `--ansi` | n/a | Forcer la sortie ANSI |
| `--no-ansi` | n/a | Désactiver la sortie ANSI |

>[!NOTE]
>
>Félicitations ! Vous avez terminé l’installation rapide. Besoin d’aide plus avancée ? Consultez le guide [Advanced install](advanced.md) .
