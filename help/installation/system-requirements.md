---
title: Configuration requise
description: Découvrez les dépendances logicielles et la configuration requise pour Adobe Commerce. Voir les configurations testées pour assurer la compatibilité avec votre environnement de déploiement.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: e77a19ce01fb0dd650aee3e8ec5f86375b429451
workflow-type: tm+mt
source-wordcount: '1249'
ht-degree: 0%

---

# Configuration requise

Les informations suivantes résument les dépendances logicielles et les services testés pour Adobe Commerce.

Il existe quelques différences dans les dépendances de Commerce on Cloud. La prise en charge de la compatibilité et des versions des services pour Adobe Commerce on Cloud est déterminée par les services testés et déployés dans les environnements cloud hébergés. Elle diffère parfois des versions prises en charge par les déploiements sur site d’Adobe Commerce.

>[!IMPORTANT]
>
>Les tableaux de configuration requise répertorient les versions d’Adobe Commerce auxquelles elles s’appliquent, y compris les versions étiquetées bêta ou accès anticipé.
>Voir les [notes de mise à jour](../release/release-notes/overview.md) pour connaître les dernières versions de Commerce publiées.
>
>Lorsque les versions de vos services ne correspondent pas à la configuration prise en charge pour votre version de Commerce, le comportement peut différer de ce qu’Adobe peut reproduire dans les tests. L’assistance d’Adobe peut vous demander d’aligner votre environnement avec une configuration prise en charge avant d’étudier, de résoudre les problèmes ou de valider le comportement signalé. Une fois votre environnement aligné, l’assistance d’Adobe peut continuer l’enquête.

Les tableaux suivants présentent les versions des dépendances de logiciels tiers qu’Adobe a testées avec des versions Adobe Commerce spécifiques.

Adobe prend uniquement en charge les combinaisons d’exigences système répertoriées dans les tableaux ci-dessous. Adobe ne valide ni ne prend en charge les configurations qui ne correspondent pas à une combinaison répertoriée. Par exemple, Adobe Commerce 2.4.9 est testé avec MariaDB 12.3. Effectuez la mise à niveau vers MariaDB 12.3 avant d’effectuer la mise à niveau vers la version 2.4.9.

## Configuration requise pour les dernières versions de Commerce

Les tableaux ci-dessous résument la configuration requise pour la dernière version de toutes les versions de Commerce prises en charge. Adobe recommande à tous les clients d’effectuer une mise à niveau vers ces versions.

>[!BEGINTABS]

>[!TAB Commerce sur le cloud]

Le modèle [Commerce sur le cloud](https://github.com/magento/magento-cloud) fournit une configuration par défaut pour les services compatibles avec une version spécifique de Commerce.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

**<sup>1</sup>Compatibilité entre MariaDB 12.3 et Adobe Commerce 2.4.9**
La compatibilité entre MariaDB 12.3 et Adobe Commerce 2.4.9 sera confirmée suite à la publication officielle de MariaDB 12.3, prévue pour mai et juin.

Pour la configuration par défaut, les services et versions sont définis dans [le fichier `services.yaml`](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml).
Pour plus d’informations, consultez la section [Configurer les services](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) dans le guide *Commerce sur les infrastructures cloud*.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table.md}}

**MySQL 8.0 a atteint la fin de la prise en charge (EOS) le 30 avril 2026.**
À compter de cette date, Adobe Commerce 2.4.7, 2.4.6, 2.4.5 et 2.4.4 ne fournira pas de compatibilité ou
Prise en charge de toutes les versions de MySQL publiées après MySQL 8.0. Adobe ne le fera pas
valider ou fournir la prise en charge des versions majeures MySQL plus récentes sur cette Adobe
Ligne de version de Commerce.
Tous les clients et clientes Adobe Commerce On-Premise exécutant les versions 2.4.7, 2.4.6, 2.4.5 et 2.4.4 ont un niveau de sécurité élevé
a conseillé de migrer ses serveurs de base de données vers une version MariaDB compatible.

**Elasticsearch 7.17 a atteint la fin de la prise en charge (EOS) le 15 janvier 2026.**
À compter de cette date, Adobe Commerce 2.4.6, 2.4.5 et 2.4.4 ne fournira pas de compatibilité ou
la prise en charge de toutes les versions d’Elasticsearch publiées après Elasticsearch 7. Adobe ne le fera pas
valider ou fournir la prise en charge des versions Elasticsearch majeures plus récentes sur cette Adobe
Ligne de version de Commerce.
Tous les clients et clientes Adobe Commerce On-Premise exécutant les versions 2.4.6, 2.4.5 et 2.4.4 ont un niveau de sécurité élevé
Il est conseillé de migrer leur infrastructure de recherche vers une version OpenSearch compatible.

>[!ENDTABS]

## Configuration requise pour les versions antérieures de Commerce

Les tableaux suivants répertorient la configuration requise pour les versions d’Adobe Commerce, y compris celles avec prise en charge étendue. Ces tableaux sont fournis à titre de référence uniquement. Adobe ne recommande pas d’utiliser des versions non prises en charge des dépendances logicielles. En outre, l’assistance nécessite d’aligner votre environnement sur une configuration prise en charge avant que nous puissions étudier, résoudre les problèmes ou valider les comportements signalés.

>[!NOTE]
>
>Le tableau est réduit afin de réduire la longueur de cet article. Sélectionnez l’en-tête pour le développer.

+++Conditions requises pour les versions antérieures

>[!BEGINTABS]

>[!TAB Commerce sur le cloud]

Le modèle [Commerce sur le cloud](https://github.com/magento/magento-cloud) fournit une configuration par défaut pour les services compatibles avec une version spécifique de Commerce.

{{$include /help/_includes/templated/cloud-requirements-table-old-releases.md}}

Pour la configuration par défaut, les services et versions sont définis dans [le fichier `services.yaml`](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml).
Pour plus d’informations, consultez la section [Configurer les services](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) dans le guide *Commerce sur les infrastructures cloud*.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table-old-releases.md}}

**MySQL 8.0 a atteint la fin de la prise en charge (EOS) le 30 avril 2026.**
À compter de cette date, Adobe Commerce 2.4.7, 2.4.6, 2.4.5 et 2.4.4 ne fournira pas de compatibilité ou
Prise en charge de toutes les versions de MySQL publiées après MySQL 8.0. Adobe ne le fera pas
valider ou fournir la prise en charge des versions majeures MySQL plus récentes sur cette Adobe
Ligne de version de Commerce.
Tous les clients et clientes Adobe Commerce On-Premise exécutant les versions 2.4.7, 2.4.6, 2.4.5 et 2.4.4 ont un niveau de sécurité élevé
a conseillé de migrer ses serveurs de base de données vers une version MariaDB compatible.

**Elasticsearch 7.17 a atteint la fin de la prise en charge (EOS) le 15 janvier 2026.**
À compter de cette date, Adobe Commerce 2.4.6, 2.4.5 et 2.4.4 ne fournira pas de compatibilité ou
la prise en charge de toutes les versions d’Elasticsearch publiées après Elasticsearch 7. Adobe ne le fera pas
valider ou fournir la prise en charge des versions Elasticsearch majeures plus récentes sur cette Adobe
Ligne de version de Commerce.
Tous les clients et clientes Adobe Commerce On-Premise exécutant les versions 2.4.6, 2.4.5 et 2.4.4 ont un niveau de sécurité élevé
Il est conseillé de migrer leur infrastructure de recherche vers une version OpenSearch compatible.

>[!ENDTABS]

+++

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

La version majeure de PHPUnit prise en charge dépend de la version d’Adobe Commerce. Adobe teste les versions 2.4.9 avec PHPUnit 12, 2.4.8-p5 avec PHPUnit 10 et 2.4.7-p10 à 2.4.4-p18 avec PHPUnit 9. Installez PHPUnit comme outil de ligne de commande à la version majeure correspondant aux configurations testées par Adobe pour votre version.

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

## Autres configurations logicielles requises

Cette section décrit la prise en charge et la compatibilité de tous les autres types de logiciels requis et facultatifs.

>[!NOTE]
>
>Les exigences suivantes s’appliquent à la dernière version 2.4.x du correctif d’Adobe Commerce. Le cas échéant, des conseils sur Commerce en matière d’infrastructure cloud sont fournis.

### Navigateurs

Storefront et Admin :

- Microsoft Edge (dernière et précédente version majeure)
- Firefox (dernière version majeure et précédente sur n&#39;importe quel système d&#39;exploitation)
- Chrome (dernière version majeure et précédente sur n’importe quel système d’exploitation)
- Safari (dernière et précédente version majeure sur macOS uniquement)
- Safari pour iOS (dernière et précédente version majeure pour le storefront)
- Chrome pour Android (dernière et précédente version majeure pour le storefront)

### Serveur de messagerie

Mail Transfer Agent (MTA) ou un serveur SMTP. L’infrastructure de Commerce sur le cloud utilise le service de messagerie [SendGrid](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/sendgrid).

### Mémoire

La mise à niveau des applications et des extensions que vous obtenez du Commerce Marketplace et d’autres sources peut nécessiter jusqu’à 2 Go de RAM. Si vous utilisez un système avec moins de 2 Go de RAM, créez un fichier [swap](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade). Sinon, la mise à niveau risque d’échouer.

### Systèmes d&#39;exploitation (Linux x86-64)

les distributions Linux, telles que Red Hat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian, etc.

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

<!-- Last updated from includes: 2026-06-01 15:26:19 -->
