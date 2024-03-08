---
title: Configuration requise
description: Utilisez cette référence pour identifier les dépendances logicielles requises qui ont été testées avec Adobe Commerce et les versions Magento Open Source.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 56052a5777b8719d5a9257d0c48e5640a6812a5f
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 0%

---

# Configuration requise

Le tableau suivant résume les dépendances logicielles et les services testés pour Adobe Commerce et Magento Open Source.

Il existe des différences dans les dépendances de l’infrastructure Commerce on Cloud. La prise en charge de la version de service et de la compatibilité d’Adobe Commerce sur l’infrastructure cloud est déterminée par les services testés et déployés dans les environnements cloud hébergés et parfois différente des versions prises en charge par les déploiements sur site d’Adobe Commerce. Par exemple, Elasticsearch 7.17 est pris en charge pour Commerce 2.4.4 pour les déploiements on-premise, mais OpenSearch 1.2 est pris en charge pour Commerce 2.4.4 sur l’infrastructure cloud.

Les tableaux ci-dessous montrent les versions des dépendances logicielles tierces que Adobe a testées avec des versions Adobe Commerce et Magento Open Source spécifiques.

Adobe ne prend en charge que la combinaison de la configuration requise décrite dans les tableaux suivants. Par exemple, la version 2.4.5 est entièrement testée avec MariaDB 10.4. Adobe vous recommande de mettre à niveau vers MariaDB 10.4 avant de passer à la version 2.4.5.

>[!BEGINTABS]

>[!TAB Commerce sur Cloud]

La variable [Modèle Commerce on Cloud](https://github.com/magento/magento-cloud) fournit une configuration par défaut pour les services compatibles avec une version spécifique de Commerce.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

Les services et versions sont définis dans [la valeur `services.yaml` fichier](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). Voici la configuration de service par défaut pour Commerce 2.4.6 sur l’infrastructure cloud :

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

Voir [Configuration des services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) dans le _Commerce sur l’infrastructure cloud_ guide.

>[!TAB Commerce sur site]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## paramètres PHP

Il existe des paramètres de configuration PHP spécifiques, tels que la fonction `memory_limit` , ce qui peut vous aider à éviter les problèmes courants lors de l’utilisation d’Adobe Commerce et de Magento Open Source. Voir [Paramètres PHP requis](prerequisites/php-settings.md).

Pour obtenir des conseils sur la configuration du cloud, voir [paramètres PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) dans le _Commerce sur l’infrastructure cloud_ guide.

### OPcache PHP

Il est recommandé de vérifier que la variable [OPcache PHP](https://www.php.net/manual/en/intro.opcache.php) est activée pour des raisons de performances. Le OPcache est activé dans de nombreuses distributions PHP. La variable `opcache` est installée par défaut dans l’infrastructure de Commerce on Cloud.

Pour les messages on-premise, vérifiez que PHP OPcache est installé, voir [paramètres PHP](prerequisites/php-settings.md). Ou pour obtenir des conseils spécifiques sur les paramètres de performances, consultez les recommandations logicielles pour [paramètres PHP](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings) dans le _Bonnes pratiques en matière de performances_ guide.

Si vous devez installer OPcache séparément, voir la section [Documentation du fichier OPcache PHP](https://www.php.net/manual/en/opcache.setup.php).

### Contrôle de processus PHP

{{php-process-control}}

### PHPUnit

PHPUnit (en tant qu’outil de ligne de commande) 9.0.0

### Extensions PHP

La variable [Instructions d’installation PHP](prerequisites/php-settings.md) incluez une étape pour installer ces extensions.

>[!TIP]
>
>Pour les extensions PHP dans l’infrastructure cloud, voir [Activation des extensions PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions) dans le _Commerce sur l’infrastructure cloud_ guide.

>[!BEGINTABS]

>[!TAB Commerce sur Cloud]

Le tableau suivant présente les extensions PHP prises en charge lors du déploiement d’Adobe Commerce sur la plateforme Cloud.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce sur site]

{{$include /help/_includes/templated/php-extensions.md}}

Voir [documentation PHP officielle](https://www.php.net/manual/en/extensions.php) pour plus d’informations sur l’installation.

>[!ENDTABS]

## Divers

Cette section décrit la prise en charge et la compatibilité de tous les autres types de logiciels requis et facultatifs.

>[!NOTE]
>
>Les exigences suivantes s’appliquent à la dernière version de correctif 2.4.x d’Adobe Commerce et de Magento Open Source. Le cas échéant, des conseils sur l’infrastructure de Commerce on Cloud sont fournis.

### Navigateurs

Storefront et Admin :

- Microsoft Edge (dernière version et version majeure précédente)
- Firefox (dernière version et version majeure précédente ; système d’exploitation)
- Chrome (dernière version et version majeure précédente ; tout système d’exploitation)
- Safari (dernière version et version majeure précédente ; macOS uniquement)
- Safari pour iOS (dernière version et version majeure précédente, pour storefront)
- Chrome pour Android (dernière et version majeure précédente, pour storefront)

### Serveur de messagerie

Mail Transfer Agent (MTA) ou un serveur SMTP. L’infrastructure Commerce on Cloud utilise la variable [Service de messagerie SendGrid](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html).

### Mémoire

La mise à niveau des applications et des extensions que vous obtenez du Commerce Marketplace et d’autres sources peut nécessiter jusqu’à 2 Go de mémoire vive. Si vous utilisez un système avec moins de 2 Go de mémoire vive, créez une [fichier swap](https://support.magento.com/hc/en-us/articles/360032980432); dans le cas contraire, votre mise à niveau peut échouer.

### Systèmes d’exploitation (Linux x86-64)

distributions Linux, telles que RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian, etc. Microsoft Windows et macOS ne sont pas pris en charge.

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
- Exigences liées au protocole TLS (Transport Layer Security) - PayPal et `repo.magento.com` tous deux requièrent TLS 1.2 ou version ultérieure.

Pour l’infrastructure Commerce on Cloud, voir [Configuration rapide](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) dans le _Commerce sur l’infrastructure cloud_ guide.

### Xdebug

Pour Adobe Commerce et Magento Open Source, utilisez [php_xdebug 2.5.x](https://xdebug.org/download) ou version ultérieure (environnements de développement uniquement ; peut avoir un effet négatif sur les performances).

Pour Adobe Commerce on Cloud, voir [Configuration de Xdebug](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html) dans le _Commerce sur l’infrastructure cloud_ guide.

>[!NOTE]
>
>Il existe un problème connu avec `xdebug` qui peuvent affecter les installations d’Adobe Commerce ou de Magento Open Source ou l’accès au storefront ou à l’administrateur après l’installation. Voir [Problème connu qui affecte `xdebug` installation](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html) dans le _Base de connaissances pour l’assistance commerciale_.
