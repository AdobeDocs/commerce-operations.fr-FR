---
title: Remplir les prérequis
description: Préparez votre projet Adobe Commerce pour une mise à niveau en suivant ces étapes préalables.
exl-id: f7775900-1d10-4547-8af0-3d1283d9b89e
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '1866'
ht-degree: 0%

---

# Conditions préalables à la mise à niveau complètes

Il est important de comprendre ce qui est nécessaire pour exécuter Adobe Commerce. Vous devez d’abord consulter la [configuration requise](../../installation/system-requirements.md) pour la version vers laquelle vous prévoyez d’effectuer la mise à niveau.

Après avoir consulté la configuration requise, vous devez remplir les conditions préalables suivantes avant de mettre à niveau votre système :

* Mettre à jour tous les logiciels
* Vérifier qu’un moteur de recherche pris en charge est installé
* Convertir le format de la table de base de données
* Définir la limite des fichiers ouverts
* Vérifiez que les tâches cron sont en cours d’exécution.
* Définir les `DATA_CONVERTER_BATCH_SIZE`
* Vérification des autorisations du système de fichiers
* Définition de la racine du répertoire `pub/`
* Installation du plug-in de mise à jour du compositeur

## Mettre à jour tous les logiciels

La [configuration requise](../../installation/system-requirements.md) décrit exactement les versions de logiciels tiers qui ont été testées avec les versions d’Adobe Commerce.

Assurez-vous d’avoir mis à jour toutes les exigences système et dépendances de votre environnement. Voir PHP [7.4](https://www.php.net/manual/en/migration74.php), PHP [8.0](https://www.php.net/manual/en/migration80.php), PHP [8.1](https://www.php.net/manual/en/migration81.php), et [les paramètres PHP requis](../../installation/prerequisites/php-settings.md#php-settings).

>[!NOTE]
>
>Pour les projets Pro d’Adobe Commerce sur les infrastructures cloud, vous devez créer un ticket [Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) pour installer ou mettre à jour les services dans les environnements d’évaluation et de production. Indiquez les changements de service nécessaires et incluez vos fichiers `.magento.app.yaml` et `services.yaml` mis à jour ainsi que la version PHP dans le ticket. La mise à jour de votre projet par l’équipe en charge de l’infrastructure cloud peut prendre jusqu’à 48 heures. Voir [Logiciels et services pris en charge](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#supported-software-and-services).

## Vérifier qu’un moteur de recherche pris en charge est installé

Adobe Commerce nécessite l’installation préalable d’Elasticsearch ou d’OpenSearch pour pouvoir utiliser le logiciel.

**Si vous effectuez une mise à niveau de 2.3.x vers 2.4**, vous devez vérifier si vous utilisez MySQL, Elasticsearch ou une extension tierce comme moteur de recherche de catalogue dans votre instance 2.3.x. Le résultat détermine ce que vous devez faire _avant_ la mise à niveau vers la version 2.4.

**Si vous effectuez une mise à niveau des versions de correctif dans les lignes de version 2.3.x ou 2.4.x**, si Elasticsearch 7.x est déjà installé, vous pouvez éventuellement [migrer vers OpenSearch](opensearch-migration.md).

Vous pouvez utiliser la ligne de commande ou l’Administration pour déterminer votre moteur de recherche catalogue :

* Saisissez la commande `bin/magento config:show catalog/search/engine`. La commande renvoie une valeur de `mysql`, `elasticsearch` (qui indique qu’Elasticsearch 2 est configuré), `elasticsearch5`, `elasticsearch6`, `elasticsearch7` ou une valeur personnalisée, indiquant que vous avez installé un moteur de recherche tiers. Pour les versions antérieures à la version 2.4.6, utilisez la valeur `elasticsearch7` pour le moteur Elasticsearch 7 ou OpenSearch. Pour les versions 2.4.6 et ultérieures, utilisez la valeur `opensearch` pour le moteur OpenSearch.

* Dans l’administration, vérifiez la valeur du champ **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** .

Les sections suivantes décrivent les actions à effectuer avant la mise à niveau vers la version 2.4.0.

### MySQL

Depuis la version 2.4, MySQL n’est plus un moteur de recherche catalogue pris en charge. Vous devez installer et configurer Elasticsearch ou OpenSearch avant la mise à niveau. Utilisez les ressources suivantes pour vous guider tout au long de ce processus :

* [Installation et configuration d’Elasticsearch](../../configuration/search/overview-search.md)
* [Installation d’Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* Configurez [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) ou [Apache](../../installation/prerequisites/search-engine/configure-apache.md) pour l’utiliser avec votre moteur de recherche.
* [Configurer Commerce pour utiliser Elasticsearch](../../configuration/search/configure-search-engine.md) et la réindexation

Certains moteurs de recherche catalogue tiers s’exécutent sur le moteur de recherche Adobe Commerce. Contactez votre fournisseur pour déterminer si vous devez mettre à jour votre extension.

### Modifications dans MySQL 8.4

Adobe a ajouté la prise en charge de MySQL 8.4 dans la version 2.4.8.
Cette section décrit les modifications majeures apportées à MySQL 8.4 que les développeurs doivent connaître.

#### Clé non standard obsolète

L’utilisation de clés non uniques ou partielles comme clés étrangères n’est pas standard et est obsolète dans MySQL 8.4. À partir de MySQL 8.4.0, vous devez activer explicitement ces clés en définissant [`restrict_fk_on_non_standard_key`](https://dev.mysql.com/doc/refman/8.4/en/server-system-variables.html#sysvar_restrict_fk_on_non_standard_key) sur `OFF` ou en démarrant le serveur avec l’option `--skip-restrict-fk-on-non-standard-key`.

#### Mise à niveau de MySQL 8.0 ( ou versions antérieures ) vers MySQL 8.4

Pour mettre correctement à niveau MySQL de la version 8.0 vers la version 8.4, vous devez suivre les étapes suivantes dans l’ordre :

1. Activez le mode de maintenance :

   ```bash
   bin/magento maintenance:enable
   ```

1. Effectuez une sauvegarde de la base de données :

   ```bash
   bin/magento setup:backup --db
   ```

1. Mettez à niveau MySQL vers la version 8.4.
1. Définissez `restrict_fk_on_non_standard_key` sur `OFF` dans `[mysqld]` dans le fichier `my.cnf`.

   ```bash
   [mysqld]
   restrict_fk_on_non_standard_key = OFF 
   ```

   >[!WARNING]
   >
   >Si vous ne modifiez pas la valeur de `restrict_fk_on_non_standard_key` en `OFF`, l’erreur suivante s’affiche lors de l’importation :
   >
   >```sql
   > ERROR 6125 (HY000) at line 2164: Failed to add the foreign key constraint. Missing unique key for constraint 'CAT_PRD_FRONTEND_ACTION_PRD_ID_CAT_PRD_ENTT_ENTT_ID' in the referenced table 'catalog_product_entity'
   >```
1. Redémarrez le serveur MySQL.
1. Importez les données sauvegardées dans MySQL.
1. Nettoyez le cache :

   ```bash
   bin/magento cache:clean
   ```

1. Désactivez le mode de maintenance :

   ```bash
   bin/magento maintenance:disable
   ```

#### MariaDB

{{$include /help/_includes/maria-db-config.md}}

### Moteur de recherche

Vous devez installer et configurer Elasticsearch 7.6 ou une version ultérieure ou OpenSearch 1.2 avant d’effectuer la mise à niveau vers la version 2.4.0. Adobe ne prend plus en charge Elasticsearch 2.x, 5.x et 6.x. Le [Configuration du moteur de recherche](../../configuration/search/configure-search-engine.md) du _Guide de configuration_ décrit les tâches que vous devez effectuer après la mise à niveau d’Elasticsearch vers une version prise en charge.

Consultez la section [Mise à niveau d’Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) pour obtenir des instructions complètes sur la sauvegarde de vos données, la détection de problèmes de migration potentiels et le test des mises à niveau avant le déploiement en production. Selon la version d’Elasticsearch que vous utilisez, un redémarrage complet du cluster peut être requis.

Elasticsearch nécessite Java Development Kit (JDK) 1.8 ou une version ultérieure. Consultez [Installation du kit de développement logiciel Java (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) pour vérifier quelle version du JDK est installée.

#### OpenSearch

OpenSearch est un branchement open source d’Elasticsearch 7.10.2, suite au changement de licence d’Elasticsearch. Les versions suivantes d’Adobe Commerce prennent désormais en charge OpenSearch :

* 2.4.6 (OpenSearch comporte un module et des paramètres distincts)
* 2.4.5
* 2.4.4
* 2.4.3-p2
* 2.3.7-p3

Vous pouvez [migrer d’Elasticsearch vers OpenSearch](opensearch-migration.md) uniquement si vous effectuez une mise à niveau vers une version d’Adobe Commerce répertoriée ci-dessus (ou une version ultérieure).

OpenSearch nécessite JDK 1.8 ou une version ultérieure. Consultez [Installation du kit de développement logiciel Java (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) pour vérifier quelle version du JDK est installée.

[Configuration du moteur de recherche](../../configuration/search/configure-search-engine.md) décrit les tâches que vous devez effectuer après avoir modifié les moteurs de recherche.

#### Mettre à niveau Elasticsearch

La prise en charge d’Elasticsearch 8.x a été introduite dans Adobe Commerce 2.4.6. Les instructions suivantes présentent un exemple de mise à niveau d’Elasticsearch de la version 7.x vers la version 8.x :

>[!NOTE]
>
>Dans la prochaine version 2.4.8, ces étapes ne seront pas nécessaires, car le module Elasticsearch 8 est inclus par défaut et vous n’aurez pas besoin de l’installer séparément.

1. Mettez à niveau le serveur Elasticsearch 7.x vers la version 8.x et assurez-vous que est en cours d’exécution. Voir la [documentation Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Activez le champ `id_field_data` en ajoutant la configuration suivante à votre fichier `elasticsearch.yml` et en redémarrant le service Elasticsearch 8.x.

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >Pour prendre en charge Elasticsearch 8.x, Adobe Commerce 2.4.6 désactive par défaut la propriété `indices.id_field_data` et utilise le champ `_id` dans la propriété `docvalue_fields` .

1. Dans le répertoire racine de votre projet Adobe Commerce, mettez à jour les dépendances du compositeur afin de supprimer le module `Magento_Elasticsearch7` et d’installer le module `Magento_Elasticsearch8`.

   ```bash
   composer require magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

   Si vous rencontrez une erreur de dépendance pour `psr/http-message`, cliquez sur pour développer la section de dépannage suivante :

   +++Dépannage

   Si vous rencontrez des conflits de dépendance lors de l’installation d’Elasticsearch 8, en particulier avec `psr/http-message`, vous pouvez les résoudre en procédant comme suit :

   1. Tout d’abord, exiger le module Elasticsearch 8 sans mettre à jour les autres dépendances :

      ```bash
      composer require magento/module-elasticsearch-8 --no-update
      ```

   1. Mettez ensuite à jour le module Elasticsearch 8 et les packages `aws/aws-sdk-php` :

      ```bash
      composer update magento/module-elasticsearch-8 aws/aws-sdk-php -W
      ```

   Cette approche fonctionne pour 2.4.7-p4 avec PHP 8.3. Le problème se produit car `aws/aws-sdk-php` nécessite des `psr/http-message >= 2.0`, ce qui peut entraîner des conflits. Les étapes ci-dessus permettent de résoudre ces problèmes de dépendance.

   +++

1. Mettez à jour les composants de votre projet.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Configurez Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) dans le [!DNL Admin].

1. Réindexez l’index de catalogue.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Supprimez tous les éléments des types de cache activés.

   ```bash
   bin/magento cache:clean
   ```

#### Rétrograder Elasticsearch

Si vous mettez par inadvertance à niveau la version d’Elasticsearch sur votre serveur ou déterminez que vous devez la rétrograder pour toute autre raison, vous devez également mettre à jour les dépendances de vos projets Adobe Commerce. Par exemple, pour rétrograder d’Elasticsearch 8.x vers 7.x

1. Rétrogradez le serveur Elasticsearch 8.x vers la version 7.x et assurez-vous que est en cours d’exécution. Voir la [documentation Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Dans le répertoire racine de votre projet Adobe Commerce, mettez à jour les dépendances du compositeur pour supprimer le module `Magento_Elasticsearch8` et ses dépendances du compositeur et installer le module `Magento_Elasticsearch7`.

   ```bash
   composer remove magento/module-elasticsearch-8
   ```

1. Mettez à jour les composants de votre projet.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Configurez Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) dans le [!DNL Admin].

1. Réindexez l’index de catalogue.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Supprimez tous les éléments des types de cache activés.

   ```bash
   bin/magento cache:clean
   ```

### Extensions tierces

Nous vous recommandons de contacter le fournisseur de votre moteur de recherche pour déterminer si votre extension est entièrement compatible avec une version d’Adobe Commerce.

## Convertir le format de la table de base de données

Vous devez convertir le format de toutes les tables de base de données de `COMPACT` en `DYNAMIC`. Vous devez également convertir le type de moteur de stockage de `MyISAM` en `InnoDB`. Voir [Bonnes pratiques](../../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md).

## Définir la limite des fichiers ouverts

La définition de la limite des fichiers ouverts (ulimit) peut permettre d’éviter l’échec de plusieurs appels récursifs de chaînes de requête longues ou des problèmes liés à l’utilisation de la commande `bin/magento setup:rollback`. Cette commande est différente pour différents shell UNIX. Consultez votre propre version pour plus d’informations sur la commande `ulimit`.

Adobe recommande de définir les fichiers ouverts [ulimit](https://ss64.com/bash/ulimit.html) sur une valeur de `65536` ou plus, mais vous pouvez utiliser une valeur plus élevée si nécessaire. Vous pouvez définir ulimit sur la ligne de commande ou en faire un paramètre permanent pour le shell de l’utilisateur.

Pour définir ulimit à partir de la ligne de commande :

1. Passez au [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).
1. Définissez ulimit sur `65536`.

   ```bash
   ulimit -n 65536
   ```

Pour définir la valeur dans votre shell Bash :

1. Passez au [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).
1. Ouvrez `/home/<username>/.bashrc` dans un éditeur de texte.
1. Ajoutez la ligne suivante :

   ```bash
   ulimit -n 65536
   ```

1. Enregistrez vos modifications dans le fichier `.bashrc` et quittez l’éditeur de texte.

>[!IMPORTANT]
>
>Nous vous recommandons d’éviter de définir une valeur pour la propriété `pcre.recursion_limit` dans le fichier `php.ini`, car cela peut entraîner des restaurations incomplètes sans avertissement d’échec.

## Vérifiez que les tâches cron sont en cours d’exécution.

Le planificateur de tâches UNIX `cron` est essentiel aux opérations quotidiennes d’Adobe Commerce. Il planifie des éléments tels que la réindexation, les newsletters, les e-mails et les plans de site. Plusieurs fonctionnalités nécessitent au moins une tâche cron s’exécutant en tant que propriétaire du système de fichiers.

Pour vérifier que votre tâche cron est configurée correctement, vérifiez le crontab en saisissant la commande suivante en tant que propriétaire du système de fichiers :

>[!NOTE]
>
>crontab est le fichier de configuration chargé d’exécuter les tâches cron.

```bash
crontab -l
```

Les résultats similaires aux suivants doivent s’afficher :

```cron
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

Un autre symptôme de cron qui n’est pas en cours d’exécution est l’erreur suivante dans Admin :

![Messages système - cron non exécuté](../../assets/upgrade-guide/cron-not-running.png)

Pour afficher l’erreur, cliquez sur **Messages système** dans la partie supérieure de la fenêtre comme suit :

![Notification des messages système](../../assets/upgrade-guide/system-messages.png)

Pour plus d’informations, consultez [Configuration et exécution de cron](../../configuration/cli/configure-cron-jobs.md).

## Définir DATA_CONVERTER_BATCH_SIZE

Adobe Commerce 2.4 comprend des améliorations de la sécurité qui nécessitent que certaines données soient converties de sérialisées en JSON. Cette conversion a lieu pendant la mise à niveau et peut prendre beaucoup de temps, selon la quantité de données présentes dans votre base de données.

Les tableaux suivants sont les plus concernés :

* `catalogrule`
* `core_config_data`
* `magento_reward_history`
* `quote_payment`
* `quote`
* `sales_order_payment`
* `sales_order`
* `salesrule`
* `url_rewrite`

Si vous disposez d’une grande quantité de données, vous pouvez améliorer les performances en définissant la valeur d’une variable d’environnement, `DATA_CONVERTER_BATCH_SIZE`. Par défaut, la valeur est définie sur `50,000`.

Pour définir la variable d’environnement :

1. Passez au [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).
1. Définissez la variable :

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` nécessite de la mémoire ; évitez de la définir sur une valeur élevée (environ 1 Go) sans l’avoir testée au préalable.

1. Une fois la mise à niveau terminée, vous pouvez dédéfinir la variable :

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## Vérification des autorisations du système de fichiers

Pour des raisons de sécurité, Adobe Commerce nécessite certaines autorisations sur le système de fichiers. Les autorisations sont différentes de la _[propriété](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_. La propriété détermine qui peut effectuer des actions sur le système de fichiers ; les autorisations déterminent ce que l’utilisateur peut faire.

Les répertoires du système de fichiers doivent pouvoir être écrits par le groupe [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).

Pour vérifier que les autorisations de votre système de fichiers sont correctement définies, connectez-vous au serveur d’applications ou utilisez l’application de gestion de fichiers de votre fournisseur d’hébergement.

Par exemple, saisissez la commande suivante si l&#39;application est installée dans `/var/www/html/magento2` :

```bash
ls -l /var/www/html/magento2
```

Exemple de sortie :

```console
total 1028
drwxrwx---. 12 magento_user apache   4096 Jun  7 07:55 .
drwxr-xr-x.  3 root         root     4096 May 11 14:29 ..
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 app
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 bin
-rw-rw----.  1 magento_user apache 439792 Apr 27 21:23 CHANGELOG.md
-rw-rw----.  1 magento_user apache   3422 Apr 27 21:23 composer.json
-rw-rw----.  1 magento_user apache 425214 Apr 27 21:27 composer.lock
-rw-rw----.  1 magento_user apache   3425 Apr 27 21:23 CONTRIBUTING.md
-rw-rw----.  1 magento_user apache  10011 Apr 27 21:23 CONTRIBUTOR_LICENSE_AGREEMENT.html
-rw-rw----.  1 magento_user apache    631 Apr 27 21:23 COPYING.txt
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 dev
-rw-rw----.  1 magento_user apache   2926 Apr 27 21:23 Gruntfile.js
-rw-rw----.  1 magento_user apache   7592 Apr 27 21:23 .htaccess
-rw-rw----.  1 magento_user apache   6419 Apr 27 21:23 .htaccess.sample
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 lib
-rw-rw----.  1 magento_user apache  10376 Apr 27 21:23 LICENSE_AFL.txt
-rw-rw----.  1 magento_user apache  30634 Apr 27 21:23 LICENSE_EE.txt
-rw-rw----.  1 magento_user apache  10364 Apr 27 21:23 LICENSE.txt
-rw-rw----.  1 magento_user apache   4108 Apr 27 21:23 nginx.conf.sample
-rw-rw----.  1 magento_user apache   1427 Apr 27 21:23 package.json
-rw-rw----.  1 magento_user apache   1659 Apr 27 21:23 .php_cs
-rw-rw----.  1 magento_user apache    804 Apr 27 21:23 php.ini.sample
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 phpserver
drwxrwx---.  6 magento_user apache   4096 Jun  7 07:53 pub
-rw-rw----.  1 magento_user apache   2207 Apr 27 21:23 README_EE.md
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 setup
-rw-rw----.  1 magento_user apache   3731 Apr 27 21:23 .travis.yml
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 update
drwxrws---. 11 magento_user apache   4096 Jun 13 16:05 var
drwxrws---. 29 magento_user apache   4096 Jun  7 07:53 vendor
```

Consultez les sections suivantes pour obtenir une explication de l’exemple de sortie :

* La plupart des fichiers sont `-rw-rw----`, ce qui est `660`
* `drwxrwx---` = `770`
* `-rw-rw-rw-` = `666`
* Le propriétaire du système de fichiers est `magento_user`

Pour obtenir des informations plus détaillées, vous pouvez saisir la commande suivante :

```bash
ls -la /var/www/html/magento2/pub
```

Comme Adobe Commerce déploie des ressources de fichiers statiques sur des sous-répertoires de `pub`, il est recommandé de vérifier également les autorisations et la propriété de ces éléments.

Pour plus d’informations, voir [Autorisations et propriété du système de fichiers](../../installation/prerequisites/file-system/overview.md).

## Définition de la racine du répertoire `pub/`

Voir [Modifier docroot pour améliorer la sécurité](../../installation/tutorials/docroot.md) pour plus d’informations.

## Installation du plug-in de mise à jour du compositeur

Le module externe [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) Composer résout les modifications qui doivent être apportées au fichier de `composer.json` du projet racine avant la mise à jour vers une nouvelle exigence du produit.

Le plug-in automatise partiellement la mise à niveau manuelle en identifiant et en vous aidant à résoudre les conflits de dépendance au lieu d’avoir à les identifier et à les corriger manuellement.

Pour installer le plug-in :

1. Ajoutez le package à votre fichier `composer.json`.

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. Mettez à jour les dépendances :

   ```bash
   composer update
   ```

<!-- Last updated from includes: 2024-02-12 09:51:27 -->
