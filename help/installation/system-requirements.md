---
title: Configuration requise
description: Découvrez les dépendances logicielles et la configuration requise pour Adobe Commerce. Découvrez les configurations testées pour garantir la compatibilité avec votre environnement de déploiement.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 107fac05f8e7bcbd66e07187f46a3ffa170a2001
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 0%

---

# Configuration requise

Vous trouverez ci-dessous un résumé des dépendances logicielles et des services testés pour Adobe Commerce.

Il existe quelques différences dans les dépendances de Commerce on Cloud. La prise en charge de la compatibilité et des versions des services pour Adobe Commerce on Cloud est déterminée par les services testés et déployés dans les environnements cloud hébergés. Elle diffère parfois des versions prises en charge par les déploiements sur site d’Adobe Commerce. Par exemple, Elasticsearch 7.17 est pris en charge pour Commerce 2.4.4 pour les déploiements on-premise, mais OpenSearch 1 est pris en charge pour la version 2.4.4 d’Adobe Commerce on Cloud.

>[!NOTE]
>
>Les tableaux de la configuration requise identifient les versions Adobe Commerce spécifiques couvertes, y compris les versions bêta ou à accès anticipé explicitement mentionnées. Voir les [notes de mise à jour](../release/release-notes/overview.md) pour en savoir plus sur les dernières versions publiées d’Adobe Commerce.
>
>Les incohérences de version de service par rapport à votre version de Commerce peuvent introduire un comportement non reproductible dans les environnements pris en charge. Dans ce cas, l’assistance peut vous demander d’aligner l’environnement sur une configuration prise en charge (par exemple, mettre à niveau ou rétrograder la version du service) avant que nous puissions examiner, résoudre les problèmes ou valider le comportement signalé. Une fois les versions alignées, l’assistance peut poursuivre l’enquête.

Les tableaux suivants présentent les versions des dépendances de logiciels tiers qu’Adobe a testées avec des versions Adobe Commerce spécifiques.

Adobe ne prend en charge que la configuration système requise décrite dans les tableaux ci-après. Par exemple, la version 2.4.5 est entièrement testée avec MariaDB 10.4. Adobe vous recommande d’effectuer une mise à niveau vers MariaDB 10.4 avant la mise à niveau vers la version 2.4.5.

Pour garantir un processus de mise à niveau fluide et éviter les échecs de déploiement, Adobe recommande de mettre à niveau les versions de RabbitMQ de manière incrémentielle. Par exemple, lors de la mise à niveau de la version 3.8 vers la version 4.1, vous devez d’abord effectuer la mise à niveau de la version 3.8 vers la version 3.9, puis de la version 3.9 vers la version 3.10, etc. Ce n’est qu’après avoir atteint la version 3.13 que vous devez procéder à la mise à niveau vers la version 4.1.

>[!BEGINTABS]

>[!TAB Commerce sur le cloud]

Le modèle [Commerce sur le cloud](https://github.com/magento/magento-cloud) fournit une configuration par défaut pour les services compatibles avec une version spécifique de Commerce.

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

Voir [Configuration des services](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) dans le guide *Commerce sur les infrastructures cloud*.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## Paramètres PHP

Il existe des paramètres de configuration PHP spécifiques, comme le paramètre `memory_limit`, qui peuvent vous aider à éviter les problèmes courants liés à l&#39;utilisation d&#39;Adobe Commerce. Voir [Paramètres PHP requis](prerequisites/php-settings.md).

Pour obtenir des conseils sur la configuration du cloud, consultez [Paramètres PHP](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings) dans le guide *Commerce sur les infrastructures cloud*.

### PHP OPcache

Adobe vous recommande de vérifier que [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) est activé pour des raisons de performances. Le cache OP est activé dans de nombreuses distributions PHP.
- **Pour les déploiements d’Adobe Commerce sur les infrastructures cloud**, l’extension `opcache` est installée par défaut.
- **Pour les déploiements sur site d’Adobe Commerce :**
   - [Vérifiez que l&#39;extension PHP OPcache est installée](prerequisites/php-settings.md#verify-php-is-installed).
   - Pour obtenir des conseils spécifiques sur les paramètres de performance, consultez les recommandations logicielles pour [les paramètres PHP](../performance/software.md#php-settings) dans le guide *Bonnes pratiques de performance*.


Si vous devez installer OPcache séparément, consultez la documentation [PHP OPcache](https://www.php.net/manual/en/opcache.setup.php).

### Contrôle de processus PHP

{{php-process-control}}

### PHPUnit

PHPUnit v9 (comme outil de ligne de commande).

### Extensions PHP

Les [instructions d’installation de PHP](prerequisites/php-settings.md) incluent une étape pour installer ces extensions.

>[!TIP]
>
>Pour les extensions PHP dans l’infrastructure cloud, voir [Activer les extensions PHP](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions) dans le guide _Commerce sur l’infrastructure cloud_.

>[!BEGINTABS]

>[!TAB Commerce sur le cloud]

Le tableau suivant présente les extensions PHP prises en charge lors du déploiement d’Adobe Commerce sur la plateforme Cloud.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce local]

{{$include /help/_includes/templated/php-extensions.md}}

Reportez-vous à la [documentation officielle PHP](https://www.php.net/manual/en/extensions.php) pour les détails d&#39;installation.

>[!ENDTABS]

## Divers

Cette section décrit la prise en charge et la compatibilité de tous les autres types de logiciels requis et facultatifs.

>[!NOTE]
>
>Les exigences suivantes s’appliquent à la dernière version 2.4.x du correctif d’Adobe Commerce. Le cas échéant, des conseils sur Commerce en matière d’infrastructure cloud sont fournis.

### Navigateurs

Storefront et Admin :

- Microsoft Edge (dernière et précédente version majeure)
- Firefox (dernière et précédente version majeure ; tout système d’exploitation)
- Chrome (dernière et précédente version majeure ; tout système d’exploitation)
- Safari (dernière et précédente version majeure ; macOS uniquement)
- Safari pour iOS (dernière et précédente version majeure, pour storefront)
- Chrome pour Android (dernière et précédente version majeure, pour storefront)

### Serveur de messagerie

Mail Transfer Agent (MTA) ou un serveur SMTP. L’infrastructure de Commerce sur le cloud utilise le service de messagerie [SendGrid](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/sendgrid).

### Mémoire

La mise à niveau des applications et des extensions que vous obtenez du Commerce Marketplace et d’autres sources peut nécessiter jusqu’à 2 Go de RAM. Si vous utilisez un système avec moins de 2 Go de RAM, créez un fichier [swap](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade). Sinon, la mise à niveau risque d’échouer.

### Systèmes d&#39;exploitation (Linux x86-64)

les distributions Linux, telles que RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian, etc.

Microsoft Windows et macOS ne sont **pas pris** charge.

Adobe Commerce requiert les outils système suivants pour certaines opérations :

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gnu.org/software/gzip/manual/gzip.html)
- [[!DNL lsof]](https://lsof.readthedocs.io/en/stable/manpage/)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.4/en/mysqldump.html)
- [[!DNL nice]](https://www.gnu.org/s/coreutils/manual/html_node/nice-invocation.html)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://www.gnu.org/software/tar/manual/tar.html)

### SSL

- Un certificat de sécurité valide est requis pour HTTPS.
- Les certificats SSL auto-signés ne sont pas pris en charge.
- Exigence de TLS (Transport Layer Security) - PayPal et `repo.magento.com` nécessitent tous deux TLS 1.2 ou une version ultérieure.

Pour Commerce sur les infrastructures cloud, consultez la section [Configuration Fastly](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration) dans le guide *Commerce sur les infrastructures cloud*.

### Xdebug

Pour Adobe Commerce, utilisez [php_xdebug 2.5.x](https://xdebug.org/download) ou une version ultérieure (environnements de développement uniquement ; peut avoir un effet négatif sur les performances).

Pour Adobe Commerce sur le cloud, consultez [Configuration de Xdebug](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/debug) dans le guide *Commerce sur les infrastructures cloud*.

>[!NOTE]
>
>Il existe un problème connu avec `xdebug` qui peut affecter les installations d’Adobe Commerce ou l’accès au storefront ou à l’administrateur après l’installation. Voir [Problème connu affectant `xdebug` installation](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation) dans la base de connaissances de la prise en charge de _Commerce_.


<!-- Last updated from includes: 2026-03-13 12:40:18 -->
