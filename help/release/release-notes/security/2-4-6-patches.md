---
title: Notes De Mise À Jour Du Correctif De Sécurité D’Adobe Commerce 2.4.6
description: Découvrez les correctifs de sécurité, les améliorations de sécurité et les autres mises à jour liées à la sécurité inclus dans les versions des correctifs de sécurité pour Adobe Commerce version 2.4.6.
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: a5cdc9ee2d8c8632c40e0ced62182d5275b8b942
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 0%

---


# Notes de mise à jour des correctifs de sécurité d’Adobe Commerce 2.4.6

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.6-p12

La version de sécurité 2.4.6-p12 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.6.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-71](https://helpx.adobe.com/fr/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.6-p11

La version de sécurité 2.4.6-p11 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.6.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-50](https://helpx.adobe.com/fr/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Faits saillants

Les points forts de cette version sont les suivants :

* **Prise en charge de MariaDB**—Ajout de la prise en charge de MariaDB 10.11.

* **Amélioration des performances de l’API** : résout la dégradation des performances des points d’entrée d’API web asynchrones en bloc introduits après le correctif de sécurité précédent<!-- AC-14078 -->.

* **Correctif des blocs d’accès CMS**—Résout un problème en raison duquel les utilisateurs administrateurs disposant d’autorisations limitées (comme un accès au marchandisage uniquement) ne pouvaient pas afficher la page de liste [!UICONTROL CMS Blocks].

  Auparavant, ces utilisateurs rencontraient une erreur en raison de paramètres de configuration manquants après l’installation des correctifs de sécurité précédents.<!-- AC-14087 -->

* **Compatibilité des limites de cookies** : résout une modification non rétrocompatible impliquant la constante `MAX_NUM_COOKIES` dans le framework. Cette mise à jour restaure le comportement attendu et assure la compatibilité des extensions ou des personnalisations qui interagissent avec les limites de cookies.<!-- AC-14475 -->

* **Opérations asynchrones** : opérations asynchrones restreintes pour remplacer les commandes précédentes de clients.<!-- AC-13917 -->

## 2.4.6-p10

La version de sécurité 2.4.6-p10 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.6.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-26](https://helpx.adobe.com/fr/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### Faits saillants

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.6-p9

La version de sécurité 2.4.6-p9 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.6.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-08](https://helpx.adobe.com/fr/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Faits saillants

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.6-p8

La version de sécurité 2.4.6-p8 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.6.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB24-73](https://helpx.adobe.com/fr/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Faits saillants

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Correctifs inclus dans cette version

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.6-p7

La version de sécurité 2.4.6-p7 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.6.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB24-61](https://helpx.adobe.com/fr/security/products/magento/apsb24-61.html).

### Faits saillants

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Correctifs inclus dans cette version

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.6-p6

La version de sécurité 2.4.6-p6 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités qui ont été identifiées dans les versions précédentes de 2.4.6.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB24-40](https://helpx.adobe.com/fr/security/products/magento/apsb24-40.html).

Pour des raisons de compatibilité avec Commerce version 2.4.6-p6, les commerçants qui disposent de l’extension Adobe Commerce B2B doivent effectuer la mise à niveau vers [B2B version 1.4.2-p1](https://experienceleague.adobe.com/fr/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Appliquer un correctif pour CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

Pour des raisons de compatibilité avec Commerce version 2.4.6-p6, les commerçants qui disposent de l’extension Adobe Commerce B2B doivent effectuer la mise à niveau vers [B2B version 1.4.2-p1](https://experienceleague.adobe.com/fr/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Faits saillants

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.6-p5

La version de sécurité 2.4.6-p5 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités qui ont été identifiées dans les versions précédentes de 2.4.6.

Pour obtenir les dernières informations sur ces correctifs, consultez le [Bulletin de sécurité Adobe APSB24-18](https://helpx.adobe.com/fr/security/products/magento/apsb24-18.html).

## 2.4.6-p4

La version de sécurité 2.4.6-p4 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités qui ont été identifiées dans les versions précédentes. Cette version comprend également des améliorations de sécurité qui améliorent la conformité aux dernières bonnes pratiques de sécurité.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB24-03](https://helpx.adobe.com/fr/security/products/magento/apsb24-03.html).

### Faits saillants

Cette version introduit deux améliorations importantes de la sécurité :

* **Modification du comportement des clés de cache non générées** :

   * Les clés de cache non générées pour les blocs incluent désormais des préfixes qui diffèrent des préfixes des clés générées automatiquement. (Les clés de cache non générées sont des clés définies par le biais de la syntaxe de la directive du modèle ou des méthodes `setCacheKey` ou `setData`.)
   * Les clés de cache non générées pour les blocs ne doivent désormais contenir que des lettres, des chiffres, des tirets (-) et des traits de soulignement (_). <!-- AC-9831 -->

* **Limitations du nombre de codes de coupon générés automatiquement**. Commerce limite désormais le nombre de codes coupon générés automatiquement. La valeur maximale par défaut est de 250 000. Les commerçants peuvent utiliser la nouvelle option de configuration des **[!UICONTROL Code Quantity Limit]** (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) pour contrôler cette nouvelle limite. <!-- AC-8753 -->

## 2.4.6-p3

La version de sécurité 2.4.6-p3 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités qui ont été identifiées dans les versions précédentes. Cette version comprend également des améliorations de sécurité visant à améliorer la conformité aux dernières bonnes pratiques de sécurité.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB23-50](https://helpx.adobe.com/fr/security/products/magento/apsb23-50.html).

### Faits saillants

Cette version introduit un nouveau paramètre de configuration du cache de page complète qui permet de réduire les risques associés au point d’entrée `{BASE-URL}/page_cache/block/esi HTTP`. Ce point d’entrée prend en charge des fragments de contenu chargés dynamiquement et sans restriction à partir des poignées de disposition et des structures de bloc Commerce. Le nouveau paramètre de configuration de **[!UICONTROL Handles Param]** définit la valeur du paramètre `handles` de ce point d’entrée, qui détermine le nombre maximal autorisé de descripteurs par API. La valeur par défaut de cette propriété est 100. Les commerçants peuvent modifier cette valeur à partir de Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**. <!-- AC-9113 -->

### Correctifs inclus dans cette version

Adobe Commerce 2.4.6-p3 inclut la résolution de la dégradation des performances corrigée par le correctif ACSD-51892. Les commerçants ne sont pas affectés par le problème résolu par ce correctif, qui est décrit dans l’article [ACSD-51892 : Problème de performance où les fichiers config se chargent plusieurs fois](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html?lang=fr) de la base de connaissances.

### Problèmes connus

**Problème** : Adobe Commerce affiche une erreur `wrong checksum` lors du téléchargement par le compositeur à partir de `repo.magento.com`, et le téléchargement du package est interrompu. Ce problème peut se produire lors du téléchargement des packages de version rendus disponibles pendant la période de version préliminaire et est dû à un reconditionnement du package `magento/module-page-cache`.

**Solution** : les commerçants qui voient cette erreur lors du téléchargement peuvent suivre les étapes suivantes :

1) Supprimez le répertoire `/vendor` dans le projet, le cas échéant.
2) Exécutez la commande `bin/magento composer update magento/module-page-cache`. Cette commande met uniquement à jour le package `page cache`.

Si le problème de somme de contrôle persiste, supprimez le fichier `composer.lock` avant de réexécuter la commande `bin/magento composer update` pour mettre à jour chaque package.

## 2.4.6-p2

La version de sécurité 2.4.6-p2 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités qui ont été identifiées dans les versions précédentes. Cette version comprend également des améliorations de la sécurité afin de garantir une meilleure conformité aux dernières bonnes pratiques en matière de sécurité.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB23-42](https://helpx.adobe.com/fr/security/products/magento/apsb23-42.html).

### Appliquer un correctif pour CVE-2022-31160

`jQuery-UI` version 1.13.1 de la bibliothèque comporte une vulnérabilité de sécurité connue (CVE-2022-31160) qui affecte plusieurs versions d’Adobe Commerce et de Magento Open Source. Cette bibliothèque est une dépendance d’Adobe Commerce et Magento Open Source 2.4.4, 2.4.5 et 2.4.6. Les commerçants exécutant les déploiements affectés doivent appliquer le correctif spécifié dans l’article de la base de connaissances [ Vulnérabilité de sécurité de l’interface utilisateur jQuery CVE-2022-31160 pour les versions 2.4.4, 2.4.5 et 2.4.6 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=fr) .

### Faits saillants

La valeur de `fastcgi_pass` dans le fichier `nginx.sample` a été renvoyée à sa valeur précédente (antérieure à 2.4.6-p1) de `fastcgi_backend`. Cette valeur a été modifiée par inadvertance en `php-fpm:9000` dans Adobe Commerce 2.4.6-p1.

### Correctifs inclus dans cette version

Adobe Commerce 2.4.6-p2 inclut la résolution de la dégradation des performances qui a été corrigée par le correctif ACSD-51892. Les commerçants ne sont pas affectés par le problème résolu par ce correctif, qui est décrit dans l’article [ACSD-51892 : Problème de performance où les fichiers config se chargent plusieurs fois](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html?lang=fr) de la base de connaissances.

## 2.4.6-p1

La version de sécurité Adobe Commerce 2.4.6-p1 fournit des correctifs de sécurité pour les vulnérabilités qui ont été identifiées dans les versions précédentes. Cette version comprend également des améliorations de la sécurité et des mises à niveau de la plateforme pour améliorer la conformité aux dernières bonnes pratiques de sécurité.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB23-35](https://helpx.adobe.com/fr/security/products/magento/apsb23-35.html).

### Appliquer un correctif pour CVE-2022-31160

`jQuery-UI` version 1.13.1 de la bibliothèque comporte une vulnérabilité de sécurité connue (CVE-2022-31160) qui affecte plusieurs versions d’Adobe Commerce et de Magento Open Source. Cette bibliothèque est une dépendance d’Adobe Commerce et Magento Open Source 2.4.4, 2.4.5 et 2.4.6. Les commerçants qui exécutent les déploiements affectés doivent appliquer le correctif spécifié dans l’article de la base de connaissances [Vulnérabilité de sécurité de l’interface utilisateur de requête CVE-2022-31160 pour les versions 2.4.4, 2.4.5 et 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=fr).

#### Surbrillance

Le comportement par défaut de la requête [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL et du point d’entrée REST ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) a changé. Par défaut, l’API renvoie désormais toujours `true`. Les commerçants peuvent activer le comportement d’origine, qui consiste à renvoyer un `true` si l’e-mail n’existe pas dans la base de données et à `false` s’il existe. <!-- AC-6695 -->

### Mises à niveau de Platform

Les mises à niveau de Platform pour cette version améliorent la conformité aux dernières bonnes pratiques de sécurité.

* **Prise en charge du cache de vernis 7.3**. Cette version est compatible avec la dernière version de Varnish Cache 7.3. La compatibilité reste avec les versions 6.0.x et 7.2.x, mais Adobe recommande d’utiliser Adobe Commerce 2.4.6-p1 uniquement avec Varnish Cache version 7.3 ou version 6.0 LTS.

* **Prise en charge de RabbitMQ 3.11**. Cette version est compatible avec la dernière version de RabbitMQ 3.11. La compatibilité reste avec RabbitMQ 3.9, pris en charge jusqu’en août 2023, mais Adobe a recommandé d’utiliser Adobe Commerce 2.4.6-p1 uniquement avec RabbitMQ 3.11.

* **Bibliothèques JavaScript**. Les bibliothèques JavaScript obsolètes ont été mises à niveau vers les dernières versions mineures ou correctives, y compris la bibliothèque `moment.js` (v2.29.4), la bibliothèque `jQuery UI` (v1.13.2) et la bibliothèque de modules externes de validation `jQuery` (v1.19.5).

### Problèmes connus

* Le fichier `nginx.sample` a été mis à jour par inadvertance avec une modification qui modifie la valeur de `fastcgi_pass` de `fastcgi_backend` en `php-fpm:9000`. Cette modification peut être annulée ou ignorée en toute sécurité. <!-- AC-8992 -->

* Les dépendances manquantes pour le package de sécurité B2B provoquent l’erreur d’installation suivante lors de l’installation ou de la mise à niveau de l’extension B2B vers la version 1.4.0.

  ```
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  Ce problème peut être résolu en ajoutant des dépendances manuelles pour le package de sécurité B2B avec une [ balise de stabilité ](https://getcomposer.org/doc/04-schema.md#package-links). Pour plus d’informations, consultez les notes de mise à jour de [B2B](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html?lang=fr#known-issue).
