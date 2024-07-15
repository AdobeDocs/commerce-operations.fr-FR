---
title: Configuration requise
description: Utilisez cette référence pour identifier les dépendances logicielles requises qui ont été testées avec les versions d’Adobe Commerce.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# Configuration requise

Le tableau suivant résume les dépendances logicielles et les services testés pour Adobe Commerce.

Il existe des différences dans les dépendances de Commerce sur l’infrastructure cloud. La prise en charge de la version de service et de la compatibilité d’Adobe Commerce sur l’infrastructure cloud est déterminée par les services testés et déployés dans les environnements cloud hébergés et parfois différente des versions prises en charge par les déploiements sur site d’Adobe Commerce. Par exemple, Elasticsearch 7.17 est pris en charge pour Commerce 2.4.4 pour les déploiements on-premise, mais OpenSearch 1.2 est pris en charge pour Commerce 2.4.4 sur l’infrastructure cloud.

Les tableaux ci-dessous montrent les versions des dépendances de logiciels tiers testées par Adobe avec des versions Adobe Commerce spécifiques.

Adobe ne prend en charge que la combinaison de la configuration requise décrite dans les tableaux suivants. Par exemple, la version 2.4.5 est entièrement testée avec MariaDB 10.4. Adobe vous recommande de mettre à niveau vers MariaDB 10.4 avant de passer à la version 2.4.5.

>[!BEGINTABS]

>[!TAB Commerce on Cloud]

Le [ modèle Commerce on Cloud](https://github.com/magento/magento-cloud) fournit une configuration par défaut pour les services compatibles avec une version Commerce spécifique.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

Les services et versions sont définis dans [le fichier `services.yaml`](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). Voici la configuration de service par défaut pour Commerce 2.4.6 sur l’infrastructure cloud :

```yaml
mysql:
    type: mysql:10.6
    disk: 5120

redis:
    type: redis:7.0

opensearch:
    type: opensearch:2
    disk: 1024
```

Voir [Configuration des services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) dans le guide _Commerce on Cloud Infrastructure_.

>[!TAB Commerce sur site]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## paramètres PHP

Il existe des paramètres de configuration PHP spécifiques, tels que le paramètre `memory_limit`, qui peuvent vous aider à éviter les problèmes courants lors de l’utilisation d’Adobe Commerce. Voir [Paramètres PHP requis](prerequisites/php-settings.md).

Pour obtenir des instructions sur la configuration du cloud, reportez-vous à la section [Paramètres PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) du guide _Commerce on Cloud Infrastructure_.

### OPcache PHP

Il est recommandé de vérifier que [PHP OPcache](https://www.php.net/manual/en/intro.opcache.php) est activé pour des raisons de performances. Le OPcache est activé dans de nombreuses distributions PHP. L’extension `opcache` est installée par défaut dans l’infrastructure Commerce on Cloud.

Pour les paramètres on-premise, vérifiez que PHP OPcache est installé, voir [Paramètres PHP](prerequisites/php-settings.md). Ou pour obtenir des conseils spécifiques sur les paramètres de performances, consultez les recommandations logicielles pour les [paramètres PHP](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings) dans le guide _Bonnes pratiques de performances_ .

Si vous devez installer OPcache séparément, consultez la [documentation PHP OPcache](https://www.php.net/manual/en/opcache.setup.php).

### Contrôle de processus PHP

{{php-process-control}}

### PHPUnit

PHPUnit v9 (comme outil de ligne de commande).

### Extensions PHP

Les [instructions d’installation PHP](prerequisites/php-settings.md) incluent une étape pour l’installation de ces extensions.

>[!TIP]
>
>Pour les extensions PHP dans l’infrastructure cloud, voir [Activation des extensions PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions) dans le guide _Commerce on Cloud Infrastructure_ .

>[!BEGINTABS]

>[!TAB Commerce on Cloud]

Le tableau suivant présente les extensions PHP prises en charge lors du déploiement d’Adobe Commerce sur la plateforme Cloud.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce sur site]

{{$include /help/_includes/templated/php-extensions.md}}

Pour plus d’informations sur l’installation, reportez-vous à la [documentation PHP officielle](https://www.php.net/manual/en/extensions.php).

>[!ENDTABS]

## Divers

Cette section décrit la prise en charge et la compatibilité de tous les autres types de logiciels requis et facultatifs.

>[!NOTE]
>
>Les exigences suivantes s’appliquent à la dernière version de correctif 2.4.x d’Adobe Commerce. Lorsque cela est pertinent, Commerce on Cloud fournit des conseils sur l’infrastructure.

### Navigateurs

Storefront et Admin :

- Microsoft Edge (dernière version et version majeure précédente)
- Firefox (dernière version et version majeure précédente ; système d’exploitation)
- Chrome (dernière version et version majeure précédente ; système d’exploitation)
- Safari (dernière version et version majeure précédente ; macOS uniquement)
- Safari pour iOS (dernière version et version majeure précédente, pour storefront)
- Chrome pour Android (dernière version et version majeure précédente, pour storefront)

### Serveur de messagerie

Mail Transfer Agent (MTA) ou un serveur SMTP. Commerce sur l’infrastructure cloud utilise le [service de messagerie SendGrid](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html).

### Mémoire

La mise à niveau des applications et des extensions que vous obtenez du Commerce Marketplace et d’autres sources peut nécessiter jusqu’à 2 Go de mémoire vive. Si vous utilisez un système avec moins de 2 Go de mémoire vive, créez un [fichier de permutation](https://support.magento.com/hc/en-us/articles/360032980432). Sinon, votre mise à niveau risque d’échouer.

### Systèmes d’exploitation (Linux x86-64)

distributions Linux, telles que RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian, etc. Microsoft Windows et macOS ne sont pas pris en charge.

Adobe Commerce nécessite les outils système suivants pour certaines opérations :

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gzip.org/)
- [[!DNL lsof]](https://linux.die.net/man/8/lsof)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [[!DNL nice]](https://linux.die.net/man/1/nice)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://linux.die.net/man/1/tar)

### SSL

- Un certificat de sécurité valide est requis pour HTTPS.
- Les certificats SSL auto-signés ne sont pas pris en charge.
- Exigences liées à Transport Layer Security (TLS) - PayPal et `repo.magento.com` requièrent tous deux TLS 1.2 ou version ultérieure.

Pour l’infrastructure Commerce on Cloud, reportez-vous à la section [ Configuration rapide ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) du guide _Commerce on Cloud Infrastructure_ .

### Xdebug

Pour Adobe Commerce, utilisez [php_xdebug 2.5.x](https://xdebug.org/download) ou une version ultérieure (environnements de développement uniquement ; cela peut avoir un effet négatif sur les performances).

Pour Adobe Commerce on Cloud, voir [Configuration de Xdebug](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html) dans le guide _Commerce on Cloud Infrastructure_ .

>[!NOTE]
>
>Il existe un problème connu avec `xdebug` qui peut affecter les installations Adobe Commerce ou l’accès au storefront ou à l’administrateur après l’installation. Voir [Problème connu qui affecte l’ `xdebug` installation](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html) dans la _base de connaissances de prise en charge de Commerce_.
