---
title: Conditions préalables complètes
description: Préparez votre projet Adobe Commerce ou Magento Open Source à une mise à niveau en suivant les étapes préalables requises.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '1338'
ht-degree: 0%

---


# Conditions préalables à la mise à niveau

Il est important de comprendre ce qui est nécessaire pour exécuter Adobe Commerce ou Magento Open Source. Vous devez d’abord consulter la section [configuration requise](../../installation/system-requirements.md) pour la version vers laquelle vous envisagez d’effectuer la mise à niveau.

Après avoir examiné la configuration requise, vous devez remplir les conditions préalables suivantes avant de mettre à niveau votre système :

- Mettre à jour tous les logiciels
- Vérification de l’installation d’un moteur de recherche pris en charge
- Définition de la limite des fichiers ouverts
- Vérification de l’exécution des tâches cron
- Définir `DATA_CONVERTER_BATCH_SIZE`
- Vérification des autorisations du système de fichiers
- Définissez la variable `pub/` racine du répertoire
- Installation du module externe de mise à jour du compositeur

## Mettre à jour tous les logiciels

Le [configuration requise](../../installation/system-requirements.md) décrire exactement les versions de logiciels tiers qui ont été testées avec Adobe Commerce et les versions de Magento Open Source.

Veillez à mettre à jour toutes les exigences et dépendances système de votre environnement. Voir PHP [7,4](https://www.php.net/manual/en/migration74.php), PHP [8,0](https://www.php.net/manual/en/migration80.php), PHP [8.1](https://www.php.net/manual/en/migration81.php), et [paramètres PHP requis](../../installation/prerequisites/php-settings.md#php-settings).

## Vérification de l’installation d’un moteur de recherche pris en charge

Adobe Commerce et Magento Open Source nécessitent l’installation d’Elasticsearch ou d’OpenSearch pour pouvoir utiliser le logiciel.

**Si vous effectuez une mise à niveau de 2.3.x vers 2.4**, vous devez vérifier si vous utilisez MySQL, Elasticsearch ou une extension tierce comme moteur de recherche de catalogue dans votre instance 2.3.x. Le résultat détermine ce que vous devez faire. _before_ mise à niveau vers la version 2.4.

**Si vous mettez à niveau des versions de correctif dans les lignes de version 2.3.x ou 2.4.x**, si Elasticsearch 7.x est déjà installé, vous pouvez éventuellement [migrer vers OpenSearch](opensearch-migration.md).

Vous pouvez utiliser la ligne de commande ou l’ administrateur pour déterminer votre moteur de recherche de catalogue :

- Saisissez le `bin/magento config:show catalog/search/engine` . La commande renvoie une valeur de `mysql`, `elasticsearch` (indiquant que l’Elasticsearch 2 est configuré), `elasticsearch5`, `elasticsearch6`, `elasticsearch7`ou une valeur personnalisée, indiquant que vous avez installé un moteur de recherche tiers. Une valeur de `elasticsearch7` indique que Elasticsearch 7 ou OpenSearch est installé.

- Depuis l’administrateur, vérifiez la valeur de la variable **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** champ .

Les sections suivantes décrivent les actions que vous devez entreprendre avant de procéder à la mise à niveau vers la version 2.4.0.

### MySQL

Depuis la version 2.4, MySQL n’est plus un moteur de recherche de catalogue pris en charge. Vous devez installer et configurer Elasticsearch ou OpenSearch avant la mise à niveau. Utilisez les ressources suivantes pour vous aider à accomplir ce processus :

- [Installation et configuration de l’Elasticsearch](../../configuration/search/overview-search.md)
- [Installation de l’Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- Configurer [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) ou [Apache](../../installation/prerequisites/search-engine/configure-apache.md) pour travailler avec votre moteur de recherche
- [Configuration de Commerce pour utiliser Elasticsearch](../../configuration/search/configure-search-engine.md) et réindexer

Certains moteurs de recherche de catalogue tiers s’exécutent sur le moteur de recherche Adobe Commerce. Contactez votre fournisseur pour déterminer si vous devez mettre à jour votre extension.

### Elasticsearch

Vous devez installer et configurer Elasticsearch 7.6 ou version ultérieure ou OpenSearch 1.2 avant la mise à niveau vers la version 2.4.0. Adobe ne prend plus en charge Elasticsearch 2.x, 5.x et 6.x.

Voir [Mise à niveau d’Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) pour obtenir des instructions complètes sur la sauvegarde de vos données, la détection des problèmes de migration potentiels et le test des mises à niveau avant le déploiement en production. Selon votre version actuelle d’Elasticsearch, un redémarrage complet de la grappe peut être nécessaire ou non.

Elasticsearch requiert JDK 1.8 ou version ultérieure. Voir [Installation de Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) pour vérifier quelle version de JDK est installée.

[Configurer l’Elasticsearch](../../configuration/search/configure-search-engine.md) décrit les tâches que vous devez effectuer après la mise à jour d’Elasticsearch 2 vers une version prise en charge.

### OpenSearch

OpenSearch est un double open source de 7.10.2 Elasticsearch, suite à un changement de licence de l’Elasticsearch. Les versions suivantes d’Adobe Commerce et de Magento Open Source introduisent la prise en charge d’OpenSearch :

- 2.4.4
- 2.4.3-p2
- 2.3.7-p3

Vous pouvez [migrer de l’Elasticsearch vers OpenSearch](opensearch-migration.md) uniquement si vous effectuez une mise à niveau vers une version d’Adobe Commerce ou de Magento Open Source répertoriée ci-dessus (ou ultérieure).

OpenSearch requiert JDK 1.8 ou version ultérieure. Voir [Installation de Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) pour vérifier quelle version de JDK est installée.

[Configuration d’un Magento pour l’utilisation de l’Elasticsearch](../../configuration/search/configure-search-engine.md) décrit les tâches que vous devez effectuer après avoir modifié les moteurs de recherche.

### Extensions tierces

Nous vous recommandons de contacter le fournisseur de votre moteur de recherche pour déterminer si votre extension est entièrement compatible avec la version 2.4.

## Définition de la limite des fichiers ouverts

La définition de la limite des fichiers ouverts (ulimit) peut permettre d’éviter l’échec de plusieurs appels récursifs de longues chaînes de requête ou des problèmes liés à l’utilisation de la variable `bin/magento setup:rollback` . Cette commande est différente pour différents shells UNIX. Consultez votre goût individuel pour plus d’informations sur la `ulimit` .

Adobe recommande de définir les fichiers ouverts [ulimit](https://ss64.com/bash/ulimit.html) à une valeur de `65536` ou plus, mais vous pouvez utiliser une valeur plus grande si nécessaire. Vous pouvez définir l’ulimit sur la ligne de commande ou en faire un paramètre permanent pour le shell de l’utilisateur.

Pour définir ulimit à partir de la ligne de commande :

1. Basculez vers le [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).
1. Définissez la ulimit sur `65536`.

   ```bash
   ulimit -s 65536
   ```

   >[!NOTE]
   >
   > La syntaxe de la ulimit des fichiers ouverts dépend du shell UNIX que vous utilisez. Le paramètre précédent doit fonctionner avec CentOS et Ubuntu avec le conteneur Bash. Toutefois, pour Mac OS, le paramètre correct est ulimit -S 65532. Pour plus d’informations, consultez la page de gestion ou la référence du système d’exploitation.

Pour définir la valeur dans votre shell Bash :

1. Basculez vers le [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).
1. Ouvrir `/home/<username>/.bashrc` dans un éditeur de texte.
1. Ajoutez la ligne suivante :

   ```bash
   ulimit -s 65536
   ```

1. Enregistrez vos modifications dans le `.bashrc` et quittez l’éditeur de texte.

>[!IMPORTANT]
>
>Il est recommandé d’éviter de définir une valeur pour la variable `pcre.recursion_limit` dans la propriété `php.ini` car cela peut entraîner des restaurations incomplètes sans préavis d’échec.

## Vérifier que les tâches cron sont en cours d’exécution

Planificateur de tâches UNIX `cron` est essentiel pour les opérations Adobe Commerce et Magento Open Source quotidiennes. Il planifie des choses comme la réindexation, les newsletters, les e-mails, les plans de site, etc. Plusieurs fonctionnalités nécessitent au moins une tâche cron s’exécutant en tant que propriétaire du système de fichiers.

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

![](../../assets/upgrade-guide/cron-not-running.png)

Pour afficher l’erreur, cliquez sur **Messages système** en haut de la fenêtre, comme suit :

![](../../assets/upgrade-guide/system-messages.png)

Voir [Configuration et exécution de cron](../../configuration/cli/configure-cron-jobs.md) pour plus d’informations.

## Set DATA_CONVERTER_BATCH_SIZE

Adobe Commerce 2.4 comprend des améliorations de sécurité qui nécessitent que certaines données soient converties de la version sérialisée vers JSON. Cette conversion survient lors de la mise à niveau et peut prendre du temps, selon la quantité de données contenues dans votre base de données.

Les tableaux suivants sont les plus affectés :

- `catalogrule`
- `core_config_data`
- `magento_reward_history`
- `quote_payment`
- `quote`
- `sales_order_payment`
- `sales_order`
- `salesrule`
- `url_rewrite`

Si vous disposez d’une grande quantité de données, vous pouvez améliorer les performances en définissant la valeur d’une variable d’environnement, `DATA_CONVERTER_BATCH_SIZE`. Par défaut, la valeur est définie sur `50,000`.

Pour définir la variable d’environnement :

1. Basculez vers le [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).
1. Définissez la variable :

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` nécessite de la mémoire ; évitez de le définir sur une valeur élevée (environ 1 Go) sans le tester au préalable.

1. Une fois la mise à niveau terminée, vous pouvez annuler la définition de la variable :

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## Vérification des autorisations du système de fichiers

Pour des raisons de sécurité, Adobe Commerce et Magento Open Source requièrent certaines autorisations sur le système de fichiers. Les autorisations sont différentes de _[propriétaire](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_. La propriété détermine qui peut effectuer des actions sur le système de fichiers. les autorisations déterminent ce que l’utilisateur peut faire.

Les répertoires du système de fichiers doivent pouvoir être écrits par le [du propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md) groupe.

Pour vérifier que les autorisations de votre système de fichiers sont correctement définies, connectez-vous au serveur d’applications ou utilisez l’application de gestionnaire de fichiers de votre fournisseur d’hébergement.

Par exemple, saisissez la commande suivante si l’application est installée dans `/var/www/html/magento2`:

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

- La plupart des fichiers sont `-rw-rw----`, qui est `660`
- `drwxrwx---` = `770`
- `-rw-rw-rw-` = `666`
- Le propriétaire du système de fichiers est `magento_user`

Pour obtenir des informations plus détaillées, vous pouvez saisir la commande suivante :

```bash
ls -la /var/www/html/magento2/pub
```

Parce qu’Adobe Commerce et Magento Open Source déploient des fichiers statiques dans des sous-répertoires de `pub`, il est préférable de vérifier également les autorisations et la propriété dans cette zone.

Pour plus d’informations, voir [Autorisations et propriété du système de fichiers](../../installation/prerequisites/file-system/overview.md).

## Définissez la variable `pub/` racine du répertoire

Voir [Modification de docroot pour améliorer la sécurité](../../installation/tutorials/docroot.md) pour plus d’informations.

## Installation du module externe de mise à jour du compositeur

Le [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) Le module externe Composer résout les modifications qui doivent être apportées au projet racine. `composer.json` avant d’effectuer une mise à jour vers un nouveau produit requis.

Le module externe automatise partiellement la mise à niveau manuelle en identifiant et en vous aidant à résoudre les conflits de dépendance au lieu d’exiger que vous les identifiiez et les corrigiez manuellement.

Pour installer le module externe :

1. Ajoutez le module à votre `composer.json` fichier .

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. Mettez à jour les dépendances :

   ```bash
   composer update
   ```
