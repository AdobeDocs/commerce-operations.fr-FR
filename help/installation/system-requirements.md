---
title: Configuration requise
description: Utilisez cette référence pour identifier les dépendances logicielles requises qui ont été testées avec Adobe Commerce et les versions Magento Open Source.
source-git-commit: 3692dcfd5b50c2f036b005d40a22db061b9ea5fd
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---


# Configuration requise

Ce tableau présente les versions des dépendances logicielles tierces que Adobe a testées avec des versions Adobe Commerce et Magento Open Source spécifiques. Adobe ne prend en charge que la combinaison de la configuration requise décrite dans le tableau suivant.

Par exemple, la version 2.4.5 est entièrement testée avec MariaDB 10.4. Adobe vous recommande de mettre à niveau vers MariaDB 10.4 avant de passer à la version 2.4.5.

{{$include /help/_includes/templated/system-requirements-table.md}}

## Divers

Cette section décrit la prise en charge et la compatibilité de tous les autres types de logiciels requis et facultatifs.

>[!NOTE]
>
>Les exigences suivantes s’appliquent à la dernière version de correctif 2.4.x d’Adobe Commerce et de Magento Open Source.

### Serveur de messagerie

Mail Transfer Agent (MTA) ou un serveur SMTP

### Systèmes d’exploitation (Linux x86-64)

distributions Linux, telles que RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian, etc. Microsoft Windows et macOS ne sont pas pris en charge.

### Extensions PHP

>[!NOTE]
>
>Le [Instructions d’installation PHP](prerequisites/php-settings.md) incluez une étape pour installer ces extensions.

{{$include /help/_includes/templated/php-extensions.md}}

Voir [documentation PHP officielle](https://php.net/manual/en/extensions.php) pour plus d’informations sur l’installation.

### OPcache PHP

Nous vous recommandons vivement de vérifier que [OPcache PHP](https://php.net/manual/en/intro.opcache.php) est activée pour des raisons de performances. Le OPcache est activé dans de nombreuses distributions PHP. Pour vérifier s’il est installé, voir notre [documentation PHP](prerequisites/php-settings.md).

Si vous devez l’installer séparément, reportez-vous à la section [Documentation du fichier OPcache PHP](https://php.net/manual/en/opcache.setup.php).

### paramètres PHP

Nous recommandons des paramètres de configuration PHP particuliers, tels que `memory_limit`, ce qui peut éviter des problèmes courants lors de l’utilisation d’Adobe Commerce et de Magento Open Source.

Pour plus d’informations, voir [Paramètres PHP requis](prerequisites/php-settings.md).

### PHPUnit

PHPUnit (en tant qu’outil de ligne de commande) 9.0.0

### RAM

La mise à niveau des applications et des extensions que vous obtenez du Commerce Marketplace et d’autres sources peut nécessiter jusqu’à 2 Go de mémoire vive. Si vous utilisez un système avec moins de 2 Go de RAM, nous vous recommandons de créer une [fichier swap](https://support.magento.com/hc/en-us/articles/360032980432); sinon, votre mise à niveau peut échouer.

### Dépendances système

Adobe Commerce et Magento Open Source nécessitent les outils système suivants pour certaines opérations :

- [bash](https://www.gnu.org/software/bash/)
- [gzip](https://www.gzip.org/)
- [lsof](https://linux.die.net/man/8/lsof)
- [mysql](https://www.mysql.com/)
- [mysqldump](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [chouette](https://linux.die.net/man/1/nice)
- [php](https://www.php.net/)
- [sed](https://www.gnu.org/software/sed/manual/sed.html)
- [tar](https://linux.die.net/man/1/tar)

### SSL

- Un valide [certificat de sécurité](https://glossary.magento.com/security-certificate) est requis pour HTTPS.
- Les certificats SSL auto-signés ne sont pas pris en charge.
- Exigences liées à Transport Layer Security (TLS) - PayPal et `repo.magento.com` tous deux requièrent TLS 1.2 ou version ultérieure.

### Navigateurs pris en charge

Storefront et Admin :

- Microsoft Edge (dernière version et version majeure précédente)
- Firefox (dernière version et version majeure précédente) ; tout système d’exploitation)
- Chrome (dernière version et version majeure précédente) ; tout système d’exploitation)
- Safari (dernière version et version majeure précédente) ; macOS uniquement)
- Safari Mobile pour iPad 2, iPad Mini, iPad avec affichage Retina (iOS 12 ou version ultérieure), pour vitrine de bureau
- Safari Mobile pour iPhone 6 ou version ultérieure ; iOS 12 ou version ultérieure, pour le storefront mobile
- Chrome pour mobile (dernière version et version majeure précédente) [Android 4 ou version ultérieure] pour mobile storefront)

### Xdebug

[php_xdebug 2.5.x](https://xdebug.org/download) ou version ultérieure (environnements de développement uniquement) ; peut avoir un effet négatif sur les performances)

>[!NOTE]
>
>Il existe un problème connu avec `xdebug` qui peuvent affecter les installations Adobe Commerce ou Magento Open Source ou l’accès au storefront ou à l’administrateur après l’installation. Pour plus d’informations, voir [Problème connu avec xdebug](https://support.magento.com/hc/en-us/articles/360034242212).
