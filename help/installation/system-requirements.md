---
title: Configuration requise
description: Utilisez cette référence pour identifier les dépendances logicielles requises qui ont été testées avec Adobe Commerce et les versions de Magento Open Source.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 4087d5f5de0bc11ce120d61a539800a3533893f0
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 0%

---

# Configuration requise

Vous trouverez ci-dessous un résumé des dépendances logicielles et des services testés pour Adobe Commerce et Magento Open Source.

Il existe certaines différences dans les dépendances de Commerce à l’infrastructure cloud. La prise en charge de la version et de la compatibilité des services pour Adobe Commerce sur l’infrastructure cloud est déterminée par les services testés et déployés dans les environnements cloud hébergés. Elle diffère parfois des versions prises en charge par les déploiements sur site d’Adobe Commerce. Par exemple, Elasticsearch 7.17 est pris en charge pour Commerce 2.4.4 pour les déploiements on-premise, mais OpenSearch 1.2 est pris en charge pour Commerce 2.4.4 sur les infrastructures cloud.

Les tableaux ci-dessous présentent les versions des dépendances de logiciels tiers qu’Adobe a testées avec des versions spécifiques d’Adobe Commerce et de Magento Open Sources.

Adobe ne prend en charge que la configuration système requise décrite dans les tableaux ci-après. Par exemple, la version 2.4.5 est entièrement testée avec MariaDB 10.4. Adobe vous recommande d’effectuer une mise à niveau vers MariaDB 10.4 avant la mise à niveau vers la version 2.4.5.

>[!BEGINTABS]

>[!TAB Commerce sur le cloud]

Le [Modèle Commerce sur cloud](https://github.com/magento/magento-cloud) fournit une configuration par défaut pour les services compatibles avec une version de Commerce spécifique.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

Les services et versions sont définis dans [le `services.yaml` fichier](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). Voici la configuration de service par défaut pour Commerce 2.4.6 sur l’infrastructure cloud :

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

Voir [Configuration des services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) dans le _Commerce sur les infrastructures cloud_ guide.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## Paramètres PHP

Il existe des paramètres de configuration PHP particuliers, tels que `memory_limit` , ce qui peut vous aider à éviter des problèmes courants lors de l’utilisation d’Adobe Commerce et de Magento Open Source. Voir [Paramètres PHP requis](prerequisites/php-settings.md).

Pour obtenir des conseils sur la configuration du cloud, voir [Paramètres PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) dans le _Commerce sur les infrastructures cloud_ guide.

### PHP OPcache

Il est recommandé de vérifier que : [PHP OPcache](https://www.php.net/manual/en/intro.opcache.php) est activé pour des raisons de performances. Le cache OP est activé dans de nombreuses distributions PHP. Le `opcache` L’extension est installée par défaut dans Commerce sur l’infrastructure cloud.

Pour les opérations on-premise, vérifiez que PHP OPcache est installé, voir [Paramètres PHP](prerequisites/php-settings.md). Ou pour obtenir des conseils spécifiques sur les paramètres de performance, consultez les recommandations logicielles pour [Paramètres PHP](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings) dans le _Bonnes pratiques en matière de performances_ guide.

Si vous devez installer OPcache séparément, voir le [Documentation PHP OPcache](https://www.php.net/manual/en/opcache.setup.php).

### Contrôle de processus PHP

{{php-process-control}}

### PHPUnit

PHPUnit v9 (comme outil de ligne de commande).

### Extensions PHP

Le [Instructions d’installation PHP](prerequisites/php-settings.md) inclure une étape pour installer ces extensions.

>[!TIP]
>
>Pour les extensions PHP dans l&#39;infrastructure Cloud, voir [Activer les extensions PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions) dans le _Commerce sur les infrastructures cloud_ guide.

>[!BEGINTABS]

>[!TAB Commerce sur le cloud]

Le tableau suivant présente les extensions PHP prises en charge lors du déploiement d’Adobe Commerce sur la plateforme Cloud.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce local]

{{$include /help/_includes/templated/php-extensions.md}}

Voir [documentation officielle PHP](https://www.php.net/manual/en/extensions.php) pour plus d’informations sur l’installation.

>[!ENDTABS]

## Divers

Cette section décrit la prise en charge et la compatibilité de tous les autres types de logiciels requis et facultatifs.

>[!NOTE]
>
>Les exigences suivantes s’appliquent à la dernière version 2.4.x du correctif d’Adobe Commerce et de Magento Open Source. Le cas échéant, des conseils sur l’infrastructure cloud de Commerce sont fournis.

### Navigateurs

Storefront et Admin :

- Microsoft Edge (dernière et précédente version majeure)
- Firefox (dernière et précédente version majeure ; tout système d’exploitation)
- Chrome (dernière et précédente version majeure ; tout système d’exploitation)
- Safari (dernière et précédente version majeure ; macOS uniquement)
- Safari pour iOS (dernière et précédente version majeure, pour storefront)
- Chrome pour Android (dernière et précédente version majeure, pour storefront)

### Serveur de messagerie

Mail Transfer Agent (MTA) ou un serveur SMTP. Commerce sur les infrastructures cloud utilise le [Service de messagerie SendGrid](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html).

### Mémoire

La mise à niveau des applications et des extensions obtenues à partir du Commerce Marketplace et d’autres sources peut nécessiter jusqu’à 2 Go de RAM. Si vous utilisez un système avec moins de 2 Go de RAM, créez un [permuter le fichier](https://support.magento.com/hc/en-us/articles/360032980432); sinon, la mise à niveau risque d’échouer.

### Systèmes d&#39;exploitation (Linux x86-64)

les distributions Linux, telles que RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian, etc. Microsoft Windows et macOS ne sont pas pris en charge.

Adobe Commerce et Magento Open Source nécessitent les outils système suivants pour certaines opérations :

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
- Exigences de TLS (Transport Layer Security) - PayPal et `repo.magento.com` tous deux nécessitent TLS 1.2 ou une version ultérieure.

Pour Commerce sur les infrastructures cloud, voir [Configuration Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) dans le _Commerce sur les infrastructures cloud_ guide.

### Xdebug

Pour Adobe Commerce et Magento Open Source, utilisez [php_xdebug 2.5.x](https://xdebug.org/download) ou plus tard (environnements de développement uniquement ; peuvent avoir un effet négatif sur les performances).

Pour Adobe Commerce on Cloud, voir [Configurer Xdebug](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html) dans le _Commerce sur les infrastructures cloud_ guide.

>[!NOTE]
>
>Il existe un problème connu avec `xdebug` qui peuvent affecter les installations d’Adobe Commerce ou du Magento Open Source, ou l’accès au storefront ou à Admin après l’installation. Voir [Problème connu affectant `xdebug` installation](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html) dans le _Base de connaissances de la prise en charge de Commerce_.
