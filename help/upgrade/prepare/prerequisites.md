---
title: Conditions préalables complètes
description: Préparez votre projet Adobe Commerce pour une mise à niveau en suivant les étapes préalables requises.
exl-id: f7775900-1d10-4547-8af0-3d1283d9b89e
source-git-commit: 4c84710da62fbb31214a0de2adc8adbd68880a76
workflow-type: tm+mt
source-wordcount: '1612'
ht-degree: 0%

---

# Conditions préalables à la mise à niveau

Il est important de comprendre ce qui est nécessaire pour exécuter Adobe Commerce. Vous devez d’abord examiner la [configuration requise](../../installation/system-requirements.md) pour la version vers laquelle vous envisagez d’effectuer la mise à niveau.

Après avoir examiné la configuration requise, vous devez remplir les conditions préalables suivantes avant de mettre à niveau votre système :

* Mettre à jour tous les logiciels
* Vérification de l’installation d’un moteur de recherche pris en charge
* Conversion du format de tableau de la base de données
* Définition de la limite des fichiers ouverts
* Vérification de l’exécution des tâches cron
* Set `DATA_CONVERTER_BATCH_SIZE`
* Vérification des autorisations du système de fichiers
* Définition de la racine du répertoire `pub/`
* Installation du module externe de mise à jour du compositeur

## Mettre à jour tous les logiciels

La [configuration requise](../../installation/system-requirements.md) décrit exactement les versions de logiciels tiers qui ont été testées avec les versions d’Adobe Commerce.

Veillez à mettre à jour toutes les exigences et dépendances du système dans votre environnement. Voir PHP [7.4](https://www.php.net/manual/en/migration74.php), PHP [8.0](https://www.php.net/manual/en/migration80.php), PHP [8.1](https://www.php.net/manual/en/migration81.php) et [paramètres PHP requis](../../installation/prerequisites/php-settings.md#php-settings).

>[!NOTE]
>
>Pour Adobe Commerce sur les projets d’infrastructure cloud Pro, vous devez créer un ticket [Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) pour installer ou mettre à jour les services dans les environnements d’évaluation et de production. Indiquez les modifications de service nécessaires et incluez vos fichiers `.magento.app.yaml` et `services.yaml` mis à jour et la version PHP dans le ticket. La mise à jour de votre projet peut prendre jusqu’à 48 heures pour que l’équipe chargée de l’infrastructure du cloud. Voir [Logiciels et services pris en charge](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#supported-software-and-services).

## Vérification de l’installation d’un moteur de recherche pris en charge

Adobe Commerce nécessite l’installation d’Elasticsearch ou d’OpenSearch pour pouvoir utiliser le logiciel.

**Si vous effectuez une mise à niveau de la version 2.3.x vers la version 2.4**, vous devez vérifier si vous utilisez MySQL, un Elasticsearch ou une extension tierce comme moteur de recherche de catalogue dans votre instance 2.3.x. Le résultat détermine ce que vous devez faire _avant_ la mise à niveau vers la version 2.4.

**Si vous mettez à niveau des versions de correctif dans les lignes de version 2.3.x ou 2.4.x**, si Elasticsearch 7.x est déjà installé, vous pouvez éventuellement [migrer vers OpenSearch](opensearch-migration.md).

Vous pouvez utiliser la ligne de commande ou l’ administrateur pour déterminer votre moteur de recherche de catalogue :

* Saisissez la commande `bin/magento config:show catalog/search/engine` . La commande renvoie une valeur de `mysql`, `elasticsearch` (qui indique que l’Elasticsearch 2 est configuré), `elasticsearch5`, `elasticsearch6`, `elasticsearch7` ou une valeur personnalisée, indiquant que vous avez installé un moteur de recherche tiers. Pour les versions antérieures à la version 2.4.6, utilisez la valeur `elasticsearch7` pour le moteur Elasticsearch 7 ou OpenSearch. Pour les versions 2.4.6 et ultérieures, utilisez la valeur `opensearch` pour le moteur OpenSearch.

* Depuis l’administrateur, vérifiez la valeur du champ **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** .

Les sections suivantes décrivent les actions que vous devez entreprendre avant de passer à la version 2.4.0.

### MySQL

Depuis la version 2.4, MySQL n’est plus un moteur de recherche de catalogue pris en charge. Vous devez installer et configurer Elasticsearch ou OpenSearch avant la mise à niveau. Utilisez les ressources suivantes pour vous aider à accomplir ce processus :

* [Installation et configuration de l’Elasticsearch](../../configuration/search/overview-search.md)
* [Installation de l’Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* Configurez [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) ou [Apache](../../installation/prerequisites/search-engine/configure-apache.md) pour utiliser votre moteur de recherche.
* [Configurer Commerce pour utiliser Elasticsearch](../../configuration/search/configure-search-engine.md) et réindexer

Certains moteurs de recherche de catalogue tiers s’exécutent sur le moteur de recherche Adobe Commerce. Contactez votre fournisseur pour déterminer si vous devez mettre à jour votre extension.

#### MariaDB

{{$include /help/_includes/maria-db-config.md}}

### Moteur de recherche

Vous devez installer et configurer Elasticsearch 7.6 ou version ultérieure ou OpenSearch 1.2 avant de passer à la version 2.4.0. Adobe ne prend plus en charge Elasticsearch 2.x, 5.x et 6.x. La [configuration du moteur de recherche](../../configuration/search/configure-search-engine.md) du _Guide de configuration_ décrit les tâches que vous devez effectuer après la mise à niveau de l’Elasticsearch vers une version prise en charge.

Pour obtenir des instructions complètes sur la sauvegarde de vos données, la détection des problèmes de migration potentiels et le test des mises à niveau avant le déploiement en production, reportez-vous à la section [Mise à niveau d’Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) . Selon votre version actuelle d’Elasticsearch, un redémarrage complet de la grappe peut être nécessaire ou non.

Elasticsearch requiert Java Development Kit (JDK) 1.8 ou version ultérieure. Voir [Installation du Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) pour vérifier quelle version de JDK est installée.

#### OpenSearch

OpenSearch est un double open source de 7.10.2 Elasticsearch, suite à un changement de licence de l’Elasticsearch. Les versions suivantes d’Adobe Commerce prennent en charge OpenSearch :

* 2.4.6 (OpenSearch possède un module et des paramètres distincts)
* 2.4.5
* 2.4.4
* 2.4.3-p2
* 2.3.7-p3

Vous pouvez [migrer d&#39;Elasticsearch vers OpenSearch](opensearch-migration.md) uniquement si vous effectuez une mise à niveau vers une version d&#39;Adobe Commerce répertoriée ci-dessus (ou supérieure).

OpenSearch requiert JDK 1.8 ou version ultérieure. Voir [Installation du Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) pour vérifier quelle version de JDK est installée.

La [configuration du moteur de recherche](../../configuration/search/configure-search-engine.md) décrit les tâches que vous devez effectuer après avoir modifié les moteurs de recherche.

#### Elasticsearch de mise à niveau

La prise en charge d’Elasticsearch 8.x a été introduite dans Adobe Commerce 2.4.6. Les instructions suivantes présentent un exemple de mise à niveau d’Elasticsearch de 7.x vers 8.x :

1. Mettez à niveau le serveur Elasticsearch 7.x vers 8.x et assurez-vous qu’il est en cours d’exécution. Voir la [documentation Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Activez le champ `id_field_data` en ajoutant la configuration suivante à votre fichier `elasticsearch.yml` et en redémarrant le service Elasticsearch 8.x.

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >Pour prendre en charge Elasticsearch 8.x, Adobe Commerce 2.4.6 désactive la propriété `indices.id_field_data` par défaut et utilise le champ `_id` dans la propriété `docvalue_fields`.

1. Dans le répertoire racine de votre projet Adobe Commerce, mettez à jour les dépendances du compositeur pour supprimer le module `Magento_Elasticsearch7` et installer le module `Magento_Elasticsearch8`.

   ```bash
   composer require magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

1. Mettez à jour les composants de votre projet.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Configurez Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) dans [!DNL Admin].

1. Réindexez l’index du catalogue.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Supprimez tous les éléments des types de cache activés.

   ```bash
   bin/magento cache:clean
   ```

#### Rétrogradation d’Elasticsearch

Si vous mettez par inadvertance à niveau la version d’Elasticsearch sur votre serveur ou déterminez que vous devez effectuer une mise à niveau pour toute autre raison, vous devez également mettre à jour les dépendances de votre projet Adobe Commerce. Par exemple, pour passer de Elasticsearch 8.x à 7.x

1. Réduisez le serveur Elasticsearch 8.x à 7.x et assurez-vous qu’il est en cours d’exécution. Voir la [documentation Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Dans le répertoire racine de votre projet Adobe Commerce, mettez à jour les dépendances du compositeur pour supprimer le module `Magento_Elasticsearch8` et ses dépendances du compositeur et installer le module `Magento_Elasticsearch7`.

   ```bash
   composer remove magento/module-elasticsearch-8
   ```

1. Mettez à jour les composants de votre projet.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Configurez Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) dans [!DNL Admin].

1. Réindexez l’index du catalogue.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Supprimez tous les éléments des types de cache activés.

   ```bash
   bin/magento cache:clean
   ```

### Extensions tierces

Nous vous recommandons de contacter le fournisseur de votre moteur de recherche pour déterminer si votre extension est entièrement compatible avec une version d’Adobe Commerce.

## Conversion du format de tableau de la base de données

Vous devez convertir le format de toutes les tables de base de données de `COMPACT` à `DYNAMIC`. Vous devez également convertir le type de moteur de stockage de `MyISAM` en `InnoDB`. Voir [bonnes pratiques](../../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md).

## Définition de la limite des fichiers ouverts

La définition de la limite des fichiers ouverts (ulimit) peut permettre d’éviter l’échec de plusieurs appels récursifs de longues chaînes de requête ou des problèmes liés à l’utilisation de la commande `bin/magento setup:rollback`. Cette commande est différente pour différents shells UNIX. Consultez votre version pour plus d’informations sur la commande `ulimit`.

Adobe recommande de définir la valeur `65536` ou plus des fichiers ouverts [ulimit](https://ss64.com/bash/ulimit.html), mais vous pouvez utiliser une valeur plus grande si nécessaire. Vous pouvez définir l’ulimit sur la ligne de commande ou en faire un paramètre permanent pour le shell de l’utilisateur.

Pour définir ulimit à partir de la ligne de commande :

1. Passez à l’ [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).
1. Définissez la ulimit sur `65536`.

   ```bash
   ulimit -n 65536
   ```

Pour définir la valeur dans votre shell Bash :

1. Passez à l’ [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).
1. Ouvrez `/home/<username>/.bashrc` dans un éditeur de texte.
1. Ajoutez la ligne suivante :

   ```bash
   ulimit -n 65536
   ```

1. Enregistrez vos modifications dans le fichier `.bashrc` et quittez l’éditeur de texte.

>[!IMPORTANT]
>
>Nous vous recommandons d’éviter de définir une valeur pour la propriété `pcre.recursion_limit` dans le fichier `php.ini`, car cela peut entraîner des restaurations incomplètes sans préavis d’échec.

## Vérification de l’exécution des tâches cron

Le planificateur de tâches UNIX `cron` est essentiel pour les opérations Adobe Commerce quotidiennes. Il planifie des choses comme la réindexation, les newsletters, les e-mails et les plans de site. Plusieurs fonctionnalités nécessitent au moins une tâche cron s’exécutant en tant que propriétaire du système de fichiers.

Pour vérifier que votre tâche cron est configurée correctement, vérifiez crontab en saisissant la commande suivante en tant que propriétaire du système de fichiers :

>[!NOTE]
>
>crontab est le fichier de configuration responsable de l’exécution des tâches cron.

```bash
crontab -l
```

Les résultats semblables à ceux-ci doivent s’afficher :

```cron
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

Un autre symptôme de l’inexécution de cron est l’erreur suivante dans l’administrateur :

![Messages système - cron non en cours d’exécution](../../assets/upgrade-guide/cron-not-running.png)

Pour voir l’erreur, cliquez sur **Messages système** en haut de la fenêtre comme suit :

![Notification des messages système](../../assets/upgrade-guide/system-messages.png)

Voir [Configuration et exécution de cron](../../configuration/cli/configure-cron-jobs.md) pour plus d’informations.

## Set DATA_CONVERTER_BATCH_SIZE

Adobe Commerce 2.4 comprend des améliorations de sécurité qui nécessitent que certaines données soient converties de la version sérialisée vers JSON. Cette conversion survient lors de la mise à niveau et peut prendre du temps, selon la quantité de données contenues dans votre base de données.

Les tableaux suivants sont les plus affectés :

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

1. Passez à l’ [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).
1. Définissez la variable :

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` nécessite de la mémoire ; évitez de la définir sur une valeur élevée (environ 1 Go) sans la tester au préalable.

1. Une fois la mise à niveau terminée, vous pouvez annuler la définition de la variable :

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## Vérification des autorisations du système de fichiers

Pour des raisons de sécurité, Adobe Commerce requiert certaines autorisations sur le système de fichiers. Les autorisations sont différentes de _[la propriété](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_. La propriété détermine qui peut effectuer des actions sur le système de fichiers ; les autorisations déterminent ce que l’utilisateur peut faire.

Les répertoires du système de fichiers doivent pouvoir être écrits par le groupe [ du propriétaire du système de fichiers ](../../installation/prerequisites/file-system/overview.md).

Pour vérifier que les autorisations de votre système de fichiers sont correctement définies, connectez-vous au serveur d’applications ou utilisez l’application de gestionnaire de fichiers de votre fournisseur d’hébergement.

Par exemple, saisissez la commande suivante si l’application est installée dans `/var/www/html/magento2` :

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

Pour obtenir une explication de l’exemple de sortie, reportez-vous aux sections suivantes :

* La plupart des fichiers sont `-rw-rw----`, qui est `660`
* `drwxrwx---` = `770`
* `-rw-rw-rw-` = `666`
* Le propriétaire du système de fichiers est `magento_user`

Pour obtenir des informations plus détaillées, saisissez la commande suivante :

```bash
ls -la /var/www/html/magento2/pub
```

Comme Adobe Commerce déploie des ressources de fichiers statiques dans des sous-répertoires de `pub`, il est préférable de vérifier également les autorisations et la propriété dans ce répertoire.

Pour plus d’informations, voir [Autorisations et propriété du système de fichiers](../../installation/prerequisites/file-system/overview.md).

## Définition de la racine du répertoire `pub/`

Voir [Modification de docroot pour améliorer la sécurité](../../installation/tutorials/docroot.md) pour plus d’informations.

## Installation du module externe de mise à jour du compositeur

Le module [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) du compositeur résout les modifications qui doivent être apportées au fichier racine du projet `composer.json` avant de procéder à la mise à jour vers une nouvelle exigence de produit.

Le module externe automatise partiellement la mise à niveau manuelle en identifiant et en vous aidant à résoudre les conflits de dépendance au lieu d’exiger que vous les identifiiez et les corrigiez manuellement.

Pour installer le module externe :

1. Ajoutez le package à votre fichier `composer.json`.

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. Mettez à jour les dépendances :

   ```bash
   composer update
   ```
