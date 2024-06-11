---
title: Notes de mise à jour du correctif de sécurité Adobe Commerce 2.4.6
description: Découvrez les correctifs de sécurité, les améliorations de sécurité et d’autres mises à jour relatives à la sécurité inclus dans les versions des correctifs de sécurité pour Adobe Commerce version 2.4.6.
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: 7705e750a466ab134ae2616a40a32880ee0c45de
workflow-type: tm+mt
source-wordcount: '1134'
ht-degree: 0%

---


# Notes de mise à jour des correctifs de sécurité d’Adobe Commerce 2.4.6

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.6-p6

La version de sécurité Adobe Commerce 2.4.6-p6 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes de la version 2.4.6.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, voir [Bulletin de sécurité Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

## Adobe Commerce 2.4.6-p5

La version de sécurité Adobe Commerce 2.4.6-p5 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes de la version 2.4.6.

Pour obtenir les informations les plus récentes sur ces correctifs, voir [Bulletin de sécurité Adobe APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## Adobe Commerce 2.4.6-p4

La version de sécurité Adobe Commerce 2.4.6-p4 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes. Cette version comprend également des améliorations de sécurité qui améliorent la conformité aux dernières bonnes pratiques en matière de sécurité.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, voir [Bulletin de sécurité Adobe APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Mise en évidence de la sécurité

Cette version s’accompagne de deux améliorations importantes au niveau de la sécurité :

* **Modifications du comportement des clés de cache non générées**:

   * Les clés de cache non générées pour les blocs incluent désormais des préfixes différents des préfixes pour les clés générées automatiquement. (Les clés de cache non générées sont des clés définies par le biais de la syntaxe de directive de modèle ou de la fonction `setCacheKey` ou `setData` méthodes.)
   * Les clés de cache non générées pour les blocs ne doivent désormais contenir que des lettres, des chiffres, des tirets (-) et des traits de soulignement (_).  <!-- AC-9831 -->

* **Limites du nombre de codes de bon générés automatiquement**. Commerce limite désormais le nombre de codes de bon générés automatiquement. La valeur par défaut maximale est de 250 000. Les vendeurs peuvent utiliser la nouvelle **[!UICONTROL Code Quantity Limit]** option de configuration (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) pour contrôler cette nouvelle limite. <!-- AC-8753 -->

## Adobe Commerce 2.4.6-p3

La version de sécurité Adobe Commerce 2.4.6-p3 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes. Cette version comprend également des améliorations de sécurité afin d’améliorer la conformité aux dernières bonnes pratiques en matière de sécurité.

Pour obtenir les informations les plus récentes sur les correctifs de sécurité, voir [Bulletin de sécurité Adobe APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Mise en évidence de la sécurité

Cette version introduit un nouveau paramètre de configuration du cache de la page entière qui permet d’atténuer les risques associés à la variable `{BASE-URL}/page_cache/block/esi HTTP` point de terminaison . Ce point de terminaison prend en charge les fragments de contenu sans restriction et chargés dynamiquement à partir des poignées de disposition Commerce et des structures de bloc. La nouvelle **[!UICONTROL Handles Param]** paramètre de configuration définit la valeur de ce point de terminaison. `handles` qui détermine le nombre maximal autorisé de gestionnaires par API. La valeur par défaut de cette propriété est 100. Les vendeurs peuvent modifier cette valeur à partir de l’option Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**. <!-- AC-9113 -->

### Correctifs inclus dans cette version

Adobe Commerce 2.4.6-p3 inclut la résolution de la dégradation des performances corrigée par le correctif ACSD-51892. Les marchands ne sont pas affectés par le problème résolu par ce correctif, qui est décrit dans la section [ACSD-51892 : problème de performances où les fichiers de configuration se chargent plusieurs fois](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) Article de la base de connaissances.

### Problème connu

**Problème**: Adobe Commerce affiche une `wrong checksum` erreur lors du téléchargement depuis le compositeur `repo.magento.com`et le téléchargement du package est interrompu. Ce problème peut se produire lors du téléchargement des packages de version mis à disposition pendant la période de pré-version et est dû à un reconditionnement de la fonction `magento/module-page-cache` module.

**Solution**: les commerçants qui voient cette erreur lors du téléchargement peuvent procéder comme suit :

1) Supprimez le `/vendor` dans le projet, le cas échéant.
2) Exécutez la variable `bin/magento composer update magento/module-page-cache` . Cette commande ne met à jour que la fonction `page cache` module.

Si le problème de somme de contrôle persiste, supprimez la variable `composer.lock` avant de réexécuter la variable `bin/magento composer update` pour mettre à jour chaque module.

## 2.4.6-p2

La version de sécurité Adobe Commerce 2.4.6-p2 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes. Cette version contient également des améliorations de sécurité afin d’améliorer la conformité aux dernières bonnes pratiques en matière de sécurité.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, voir [Bulletin de sécurité Adobe APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Application d’un correctif pour résoudre la vulnérabilité de sécurité CVE-2022-31160 dans la bibliothèque jQuery-UI

`jQuery-UI` La version 1.13.1 de la bibliothèque comporte une vulnérabilité de sécurité connue (CVE-2022-31160) qui affecte plusieurs versions d’Adobe Commerce et de Magento Open Source. Cette bibliothèque est une dépendance d’Adobe Commerce et de Magento Open Source 2.4.4, 2.4.5 et 2.4.6. Les marchands exécutant les déploiements affectés doivent appliquer le correctif spécifié dans la variable [Correctif de la vulnérabilité de sécurité de l’interface utilisateur de jQuery CVE-2022-31160 pour les versions 2.4.4, 2.4.5 et 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Article de la base de connaissances.

### Mise en évidence de la sécurité

La valeur de `fastcgi_pass` dans le `nginx.sample` a été renvoyé à sa valeur précédente (pré-2.4.6-p1) de `fastcgi_backend`. Cette valeur a été remplacée par `php-fpm:9000` dans Adobe Commerce 2.4.6-p1.

### Correctifs inclus dans cette version

Adobe Commerce 2.4.6-p2 comprend la résolution de la dégradation des performances qui a été corrigée par le correctif ACSD-51892. Les marchands ne sont pas affectés par le problème résolu par ce correctif, qui est décrit dans la section [ACSD-51892 : problème de performances où les fichiers de configuration se chargent plusieurs fois](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) Article de la base de connaissances.

## Adobe Commerce 2.4.6-p1

La version de sécurité Adobe Commerce 2.4.6-p1 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes. Cette version comprend également des améliorations de sécurité et des mises à niveau de la plateforme afin d’améliorer la conformité aux dernières bonnes pratiques en matière de sécurité.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, voir [Bulletin de sécurité Adobe APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Application d’un correctif pour résoudre la vulnérabilité de sécurité CVE-2022-31160 dans la bibliothèque jQuery-UI

`jQuery-UI` La version 1.13.1 de la bibliothèque comporte une vulnérabilité de sécurité connue (CVE-2022-31160) qui affecte plusieurs versions d’Adobe Commerce et de Magento Open Source. Cette bibliothèque est une dépendance d’Adobe Commerce et de Magento Open Source 2.4.4, 2.4.5 et 2.4.6. Les marchands exécutant les déploiements affectés doivent appliquer le correctif spécifié dans la variable [Correctif CVE-2022-31160 pour la sécurité de l’interface utilisateur de requête pour les versions 2.4.4, 2.4.5 et 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Article de la base de connaissances.

#### Mise en évidence de la sécurité

Le comportement par défaut de la variable [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) Requête GraphQL et ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) Le point de terminaison REST a changé. Par défaut, l’API renvoie désormais toujours `true`. Les vendeurs peuvent activer le comportement d’origine, qui consiste à renvoyer la variable `true` si l’email n’existe pas dans la base de données et `false` s’il existe. <!-- AC-6695 -->

### Mises à niveau de la plateforme

Les mises à niveau de plateforme de cette version améliorent la conformité aux dernières bonnes pratiques en matière de sécurité.

* **Prise en charge du cache 7.3 de vernis**. Cette version est compatible avec la dernière version de Varnish Cache 7.3. La compatibilité reste assurée avec les versions 6.0.x et 7.2.x, mais l’Adobe recommandé avec Adobe Commerce 2.4.6-p1 est uniquement recommandé avec la version 7.3 ou la version 6.0 LTS du cache de vernis.

* **Prise en charge de RabbitMQ 3.11**. Cette version est compatible avec la dernière version de RabbitMQ 3.11. La compatibilité reste avec RabbitMQ 3.9, qui est pris en charge jusqu’en août 2023, mais l’Adobe recommandé avec Adobe Commerce 2.4.6-p1 uniquement avec RabbitMQ 3.11.

* **Bibliothèques JavaScript**. Les bibliothèques JavaScript obsolètes ont été mises à niveau vers les dernières versions mineures ou de correctif, y compris `moment.js` library (v2.29.4), `jQuery UI` bibliothèque (v1.13.2) et `jQuery` bibliothèque de modules externes de validation (v1.19.5).

### Problèmes connus

* La variable `nginx.sample` a été mis à jour par inadvertance avec une modification qui modifie la valeur de `fastcgi_pass` de `fastcgi_backend` to `php-fpm:9000`. Cette modification peut être annulée ou ignorée en toute sécurité. <!-- AC-8992 -->

* Les dépendances manquantes pour le package de sécurité B2B provoquent l’erreur d’installation suivante lors de l’installation ou de la mise à niveau de l’extension B2B vers la version 1.4.0.

  ```terminal
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  Ce problème peut être résolu en ajoutant des dépendances manuelles pour le package de sécurité B2B avec une [balise de stabilité](https://getcomposer.org/doc/04-schema.md#package-links). Pour plus d’informations, voir [Notes de mise à jour B2B](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html#known-issue).
