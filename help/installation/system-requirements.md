---
title: Configuration requise
description: Découvrez les dépendances logicielles et la configuration requise pour Adobe Commerce. Voir les configurations testées pour assurer la compatibilité avec votre environnement de déploiement.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
last-update: 2026-09-18
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '1614'
ht-degree: 0%
---
# Configuration requise

Les informations suivantes résument les dépendances logicielles et les services testés pour Adobe Commerce.

Les dépendances logicielles d’Adobe Commerce sur les infrastructures cloud sont différentes de celles des déploiements sur site. Adobe détermine les versions de service et la compatibilité prises en charge en fonction des services testés et déployés dans les environnements cloud hébergés. Ces versions diffèrent parfois de celles prises en charge pour les déploiements sur site.

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

Le modèle [Commerce on Cloud](https://github.com/magento/magento-cloud) fournit une configuration par défaut pour les services compatibles avec la dernière version de Commerce pour chaque ligne de version.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

Le fichier [`services.yaml` définit ](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml) services et versions par défaut.
Voir [Configuration des services](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) dans le guide *Commerce sur les infrastructures cloud*.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table.md}}

**MySQL 8.0 a atteint la fin de la prise en charge (EOS) le 30 avril 2026.**
Passée cette date, Adobe Commerce 2.4.7, 2.4.6, 2.4.5 et 2.4.4 ne fournissent ni compatibilité ni prise en charge des versions de MySQL publiées après MySQL 8.0.
Adobe ne valide ni ne prend en charge les versions majeures MySQL plus récentes pour ces versions de Commerce.
Si vous exécutez les versions sur site 2.4.7, 2.4.6, 2.4.5 ou 2.4.4 d’Adobe Commerce, Adobe recommande vivement de migrer vos serveurs de base de données vers une version MariaDB compatible.

Les clients Adobe Commerce on Cloud doivent conserver les dépendances de la plateforme sur les versions prises en charge. Voir [Dépendances de Platform](../release/lifecycle-policy.md#platform-dependencies) dans la politique de cycle de vie.

**Elasticsearch 7.17 a atteint la fin de la prise en charge (EOS) le 15 janvier 2026.**
Passée cette date, Adobe Commerce 2.4.6, 2.4.5 et 2.4.4 ne fournissent ni compatibilité ni prise en charge des versions d’Elasticsearch publiées après Elasticsearch 7.
Adobe ne valide pas et ne prend pas en charge les versions Elasticsearch majeures plus récentes pour ces versions de Commerce.
Si vous exécutez les versions 2.4.6, 2.4.5 ou 2.4.4 d’Adobe Commerce On-Premise, Adobe recommande vivement de migrer votre infrastructure de recherche vers une version d’OpenSearch compatible.

>[!ENDTABS]

## Configuration requise pour la version 2.4.10 alpha de Commerce

>[!BEGINTABS]

>[!TAB Commerce sur le cloud]

{{$include /help/_includes/templated/cloud-requirements-table-alpha.md}}

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table-alpha.md}}

>[!ENDTABS]

## Configuration requise pour les versions antérieures de Commerce

Les tableaux suivants répertorient la configuration requise pour les versions d’Adobe Commerce, y compris celles avec prise en charge étendue. Utilisez ces tableaux à titre de référence uniquement. Adobe déconseille d’utiliser des versions non prises en charge des dépendances logicielles. Avant que l’assistance Adobe n’enquête, ne dépannage ou ne valide le comportement signalé, vous devez aligner votre environnement avec une configuration prise en charge.

>[!NOTE]
>
>Adobe Commerce 2.4.6 bénéficie d’une [prise en charge étendue](../release/lifecycle-policy.md#extended-support) jusqu’au **30 août 2027**, suivie d’une [période de transition axée uniquement sur la sécurité](../release/lifecycle-policy.md#security-only-transitional-period) jusqu’au **31 mai 2028**. Ces fonctions ne sont disponibles que pour les clients Adobe Commerce. Ils n’étendent pas la prise en charge des dépendances tierces telles que MySQL.
>
>Si vous exécutez Adobe Commerce sur le cloud, vous devez effectuer une mise à niveau vers une version prise en charge ou migrer vers [!DNL Adobe Commerce as a Cloud Service] avant les **exigences et échéances de sécurité du 1er juin 2028** [](../release/security-enforcement-policy.md). Consultez le tableau [dates de fin de prise en charge](../release/lifecycle-policy.md#end-of-support-dates) pour connaître les dates de cycle de vie complet.
>
>Le tableau est réduit afin de réduire la longueur de cet article. Sélectionnez l’en-tête pour le développer.

+++Conditions requises pour les versions antérieures

>[!BEGINTABS]

>[!TAB Commerce sur le cloud]

Le modèle [Commerce sur le cloud](https://github.com/magento/magento-cloud) fournit une configuration par défaut pour les services compatibles avec une version spécifique de Commerce.

{{$include /help/_includes/templated/cloud-requirements-table-old-releases.md}}

Le fichier [`services.yaml` définit ](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml) services et versions par défaut.
Voir [Configuration des services](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) dans le guide *Commerce sur les infrastructures cloud*.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table-old-releases.md}}

**MySQL 8.0 a atteint la fin de la prise en charge (EOS) le 30 avril 2026.**
Passée cette date, Adobe Commerce 2.4.7, 2.4.6, 2.4.5 et 2.4.4 ne fournissent ni compatibilité ni prise en charge des versions de MySQL publiées après MySQL 8.0.
Adobe ne valide ni ne prend en charge les versions majeures MySQL plus récentes pour ces versions de Commerce.
Si vous exécutez les versions sur site 2.4.7, 2.4.6, 2.4.5 ou 2.4.4 d’Adobe Commerce, Adobe recommande vivement de migrer vos serveurs de base de données vers une version MariaDB compatible.

Les clients Adobe Commerce on Cloud doivent conserver les dépendances de la plateforme sur les versions prises en charge. Voir [Dépendances de Platform](../release/lifecycle-policy.md#platform-dependencies) dans la politique de cycle de vie.

**Elasticsearch 7.17 a atteint la fin de la prise en charge (EOS) le 15 janvier 2026.**
Passée cette date, Adobe Commerce 2.4.6, 2.4.5 et 2.4.4 ne fournissent ni compatibilité ni prise en charge des versions d’Elasticsearch publiées après Elasticsearch 7.
Adobe ne valide pas et ne prend pas en charge les versions Elasticsearch majeures plus récentes pour ces versions de Commerce.
Si vous exécutez les versions 2.4.6, 2.4.5 ou 2.4.4 d’Adobe Commerce On-Premise, Adobe recommande vivement de migrer votre infrastructure de recherche vers une version d’OpenSearch compatible.

>[!ENDTABS]

+++

## Paramètres PHP

Configurez les paramètres PHP, tels que `memory_limit`, pour éviter les problèmes courants lors de l&#39;utilisation d&#39;Adobe Commerce. Voir [Paramètres PHP requis](prerequisites/php-settings.md).

Pour obtenir des conseils sur la configuration du cloud, consultez [Paramètres PHP](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings) dans le guide *Commerce sur les infrastructures cloud*.

### PHP OPcache

Adobe recommande de vérifier que [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) est activé pour améliorer les performances. De nombreuses distributions PHP activent OPcache.

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

Voir la [documentation officielle PHP](https://www.php.net/manual/en/extensions.php) pour les détails d&#39;installation.

>[!ENDTABS]

## Autres configurations logicielles requises

Cette section décrit la prise en charge et la compatibilité de tous les autres types de logiciels requis et facultatifs.

>[!NOTE]
>
>Les exigences suivantes s’appliquent à la dernière version 2.4.x du correctif d’Adobe Commerce. Le cas échéant, des conseils sur Commerce en matière d’infrastructure cloud sont fournis.

### Navigateurs

Adobe Commerce prend en charge les versions majeures les plus récentes et précédentes des navigateurs ci-après pour le storefront et l’admin, sauf indication contraire :

- Microsoft Edge
- Firefox (tout système d’exploitation)
- Chrome (tout système d’exploitation)
- Safari (macOS uniquement)
- Safari pour iOS (storefront uniquement)
- Chrome pour Android (storefront uniquement)

### Serveur de messagerie

Mail Transfer Agent (MTA) ou un serveur SMTP. L’infrastructure de Commerce sur le cloud utilise le service de messagerie [SendGrid](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/sendgrid).

### Mémoire

La mise à niveau des applications et des extensions à partir de Commerce Marketplace et d’autres sources peut nécessiter jusqu’à 2 Go de RAM. Si votre système dispose de moins de 2 Go de RAM, créez un fichier [swap](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade). Sans fichier d’échange, la mise à niveau peut échouer.

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

Pour les environnements de développement Adobe Commerce uniquement, utilisez [php_xdebug 2.5.x](https://xdebug.org/download) ou une version ultérieure. Xdebug peut nuire aux performances.

Pour Adobe Commerce sur le cloud, consultez [Configuration de Xdebug](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/debug) dans le guide *Commerce sur les infrastructures cloud*.

>[!NOTE]
>
>Un problème connu avec Xdebug peut affecter les installations d’Adobe Commerce ou l’accès au storefront ou à l’administrateur après l’installation. Voir [Problème connu affectant `xdebug` installation](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation) dans la base de connaissances de la prise en charge de _Commerce_.

<!-- Last updated from includes: 2026-10-07 13:03:29 -->
