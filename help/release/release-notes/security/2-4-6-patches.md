---
title: Notes de mise à jour du correctif de sécurité Adobe Commerce 2.4.6
description: Découvrez les correctifs de sécurité, les améliorations de sécurité et d’autres mises à jour relatives à la sécurité inclus dans les versions des correctifs de sécurité pour Adobe Commerce version 2.4.6.
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: 2269c99908c0f8292ad62bd5837b1b8cebd50cb3
workflow-type: tm+mt
source-wordcount: '1166'
ht-degree: 0%

---


# Notes de mise à jour des correctifs de sécurité d’Adobe Commerce 2.4.6

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.6-p6

La version de sécurité Adobe Commerce 2.4.6-p6 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes de la version 2.4.6.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, reportez-vous à la section [Bulletin de sécurité Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Correctif pour CVE-2024-34102

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

### Points phares de la sécurité

Pour des raisons de compatibilité avec Commerce version 2.4.6-p6, les commerçants qui disposent de l’extension Adobe Commerce B2B doivent effectuer la mise à niveau vers [B2B version 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Améliorations supplémentaires de la sécurité

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## Adobe Commerce 2.4.6-p5

La version de sécurité Adobe Commerce 2.4.6-p5 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes de la version 2.4.6.

Pour obtenir les informations les plus récentes sur ces correctifs, reportez-vous au [Bulletin de sécurité Adobe APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## Adobe Commerce 2.4.6-p4

La version de sécurité Adobe Commerce 2.4.6-p4 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes. Cette version comprend également des améliorations de sécurité qui améliorent la conformité aux dernières bonnes pratiques en matière de sécurité.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, voir [Bulletin de sécurité Adobe APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Mise en évidence de la sécurité

Cette version s’accompagne de deux améliorations importantes au niveau de la sécurité :

* **Modifications du comportement des clés de cache non générées** :

   * Les clés de cache non générées pour les blocs incluent désormais des préfixes différents des préfixes pour les clés générées automatiquement. (Les clés de cache non générées sont des clés définies par le biais de la syntaxe de directive de modèle ou des méthodes `setCacheKey` ou `setData`.)
   * Les clés de cache non générées pour les blocs ne doivent désormais contenir que des lettres, des chiffres, des tirets (-) et des caractères de soulignement (_). <!-- AC-9831 -->

* **Limites du nombre de codes de bon générés automatiquement**. Commerce limite désormais le nombre de codes de bon générés automatiquement. La valeur par défaut maximale est de 250 000. Les commerçants peuvent utiliser la nouvelle option de configuration **[!UICONTROL Code Quantity Limit]** (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) pour contrôler cette nouvelle limite. <!-- AC-8753 -->

## Adobe Commerce 2.4.6-p3

La version de sécurité Adobe Commerce 2.4.6-p3 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes. Cette version comprend également des améliorations de sécurité afin d’améliorer la conformité aux dernières bonnes pratiques en matière de sécurité.

Pour obtenir les dernières informations sur les correctifs de sécurité, reportez-vous au [Bulletin de sécurité Adobe APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Mise en évidence de la sécurité

Cette version introduit un nouveau paramètre de configuration du cache de la page entière qui permet d’atténuer les risques associés au point de terminaison `{BASE-URL}/page_cache/block/esi HTTP`. Ce point de terminaison prend en charge les fragments de contenu sans restriction et chargés dynamiquement à partir des poignées de disposition Commerce et des structures de bloc. Le nouveau paramètre de configuration **[!UICONTROL Handles Param]** définit la valeur du paramètre `handles` de ce point de terminaison, qui détermine le nombre maximal autorisé de gestionnaires par API. La valeur par défaut de cette propriété est 100. Les vendeurs peuvent modifier cette valeur à partir de l’administrateur (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**. <!-- AC-9113 -->

### Correctifs inclus dans cette version

Adobe Commerce 2.4.6-p3 inclut la résolution de la dégradation des performances corrigée par le correctif ACSD-51892. Les commerçants ne sont pas affectés par le problème résolu par ce correctif, qui est décrit dans l’article [ACSD-51892 : Problème de performance où les fichiers de configuration se chargent plusieurs fois](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) de la base de connaissances.

### Problème connu

**Problème** : Adobe Commerce affiche une erreur `wrong checksum` lors du téléchargement par le compositeur à partir de `repo.magento.com`, et le téléchargement du package est interrompu. Ce problème peut se produire lors du téléchargement des packages de version mis à disposition pendant la période de pré-version et est dû à un reconditionnement du package `magento/module-page-cache`.

**Solution** : les vendeurs qui voient cette erreur lors du téléchargement peuvent procéder comme suit :

1) Supprimez le répertoire `/vendor` dans le projet, le cas échéant.
2) Exécutez la commande `bin/magento composer update magento/module-page-cache`. Cette commande ne met à jour que le package `page cache`.

Si le problème de somme de contrôle persiste, supprimez le fichier `composer.lock` avant de réexécuter la commande `bin/magento composer update` pour mettre à jour chaque package.

## 2.4.6-p2

La version de sécurité Adobe Commerce 2.4.6-p2 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes. Cette version contient également des améliorations de sécurité afin d’améliorer la conformité aux dernières bonnes pratiques en matière de sécurité.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, reportez-vous à la section [Bulletin de sécurité Adobe APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Application d’un correctif pour résoudre la vulnérabilité de sécurité CVE-2022-31160 dans la bibliothèque jQuery-UI

`jQuery-UI` La version 1.13.1 de la bibliothèque comporte une vulnérabilité de sécurité connue (CVE-2022-31160) qui affecte plusieurs versions d’Adobe Commerce et de Magento Open Source. Cette bibliothèque est une dépendance d’Adobe Commerce et de Magento Open Source 2.4.4, 2.4.5 et 2.4.6. Les marchands exécutant les déploiements affectés doivent appliquer le correctif spécifié dans la vulnérabilité de sécurité de l’interface utilisateur [jQuery CVE-2022-31160 pour les versions 2.4.4, 2.4.5 et 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) de la base de connaissances.

### Mise en évidence de la sécurité

La valeur de `fastcgi_pass` dans le fichier `nginx.sample` a été renvoyée à sa valeur précédente (pré-2.4.6-p1) de `fastcgi_backend`. Cette valeur a été remplacée par `php-fpm:9000` dans Adobe Commerce 2.4.6-p1 par inadvertance.

### Correctifs inclus dans cette version

Adobe Commerce 2.4.6-p2 comprend la résolution de la dégradation des performances qui a été corrigée par le correctif ACSD-51892. Les commerçants ne sont pas affectés par le problème résolu par ce correctif, qui est décrit dans l’article [ACSD-51892 : Problème de performance où les fichiers de configuration se chargent plusieurs fois](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) de la base de connaissances.

## Adobe Commerce 2.4.6-p1

La version de sécurité Adobe Commerce 2.4.6-p1 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes. Cette version comprend également des améliorations de sécurité et des mises à niveau de la plateforme afin d’améliorer la conformité aux dernières bonnes pratiques en matière de sécurité.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, reportez-vous à la section [Bulletin de sécurité Adobe APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Application d’un correctif pour résoudre la vulnérabilité de sécurité CVE-2022-31160 dans la bibliothèque jQuery-UI

`jQuery-UI` La version 1.13.1 de la bibliothèque comporte une vulnérabilité de sécurité connue (CVE-2022-31160) qui affecte plusieurs versions d’Adobe Commerce et de Magento Open Source. Cette bibliothèque est une dépendance d’Adobe Commerce et de Magento Open Source 2.4.4, 2.4.5 et 2.4.6. Les marchands exécutant les déploiements affectés doivent appliquer le correctif spécifié dans la vulnérabilité de sécurité de l’interface utilisateur de requête CVE-2022-31160 pour les versions 2.4.4, 2.4.5 et 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) de la base de connaissances.[

#### Mise en évidence de la sécurité

Le comportement par défaut de la requête GraphQL [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) et du point de terminaison REST ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) a changé. Par défaut, l’API renvoie désormais toujours `true`. Les vendeurs peuvent activer le comportement d’origine, qui consiste à renvoyer `true` si l’email n’existe pas dans la base de données et `false` s’il existe. <!-- AC-6695 -->

### Mises à niveau de la plateforme

Les mises à niveau de plateforme de cette version améliorent la conformité aux dernières bonnes pratiques en matière de sécurité.

* **Prise en charge du cache de vernis 7.3**. Cette version est compatible avec la dernière version de Varnish Cache 7.3. La compatibilité reste assurée avec les versions 6.0.x et 7.2.x, mais l’Adobe recommandé avec Adobe Commerce 2.4.6-p1 est uniquement recommandé avec la version 7.3 ou la version 6.0 LTS du cache de vernis.

* **Prise en charge de RabbitMQ 3.11**. Cette version est compatible avec la dernière version de RabbitMQ 3.11. La compatibilité reste avec RabbitMQ 3.9, qui est pris en charge jusqu’en août 2023, mais l’Adobe recommandé avec Adobe Commerce 2.4.6-p1 uniquement avec RabbitMQ 3.11.

* **Bibliothèques JavaScript**. Les bibliothèques JavaScript obsolètes ont été mises à niveau vers les dernières versions mineures ou de correctif, y compris la bibliothèque `moment.js` (v2.29.4), la bibliothèque `jQuery UI` (v1.13.2) et la bibliothèque de modules externes de validation `jQuery` (v1.19.5).

### Problèmes connus

* Le fichier `nginx.sample` a été mis à jour par inadvertance avec une modification qui modifie la valeur de `fastcgi_pass` de `fastcgi_backend` à `php-fpm:9000`. Cette modification peut être annulée ou ignorée en toute sécurité. <!-- AC-8992 -->

* Les dépendances manquantes pour le package de sécurité B2B provoquent l’erreur d’installation suivante lors de l’installation ou de la mise à niveau de l’extension B2B vers la version 1.4.0.

  ```terminal
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  Ce problème peut être résolu en ajoutant des dépendances manuelles pour le package de sécurité B2B avec une [balise de stabilité](https://getcomposer.org/doc/04-schema.md#package-links). Pour plus d’informations, voir les [notes de mise à jour B2B](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html#known-issue).
