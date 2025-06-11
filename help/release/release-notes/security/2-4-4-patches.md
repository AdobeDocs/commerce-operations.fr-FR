---
title: Notes De Mise À Jour Du Correctif De Sécurité D’Adobe Commerce 2.4.4
description: Découvrez les correctifs de sécurité, les améliorations de sécurité et les autres mises à jour liées à la sécurité inclus dans les versions des correctifs de sécurité pour Adobe Commerce version 2.4.4.
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: 309aff13295256deba2c1c4365156405fb042060
workflow-type: tm+mt
source-wordcount: '1609'
ht-degree: 0%

---


# Notes de mise à jour des correctifs de sécurité d’Adobe Commerce 2.4.4

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.4-p14

La version de sécurité 2.4.4-p14 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.4.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-50](https://helpx.adobe.com/fr/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Faits saillants

{{$include /help/_includes/release-notes/highlights/security-2025-06.md}}

## 2.4.4-p13

La version de sécurité 2.4.4-p13 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.4.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-26](https://helpx.adobe.com/fr/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### Faits saillants

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.4-p12

La version de sécurité 2.4.4-p12 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.4.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-08](https://helpx.adobe.com/fr/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Faits saillants

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.4-p11

La version de sécurité 2.4.4-p11 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.4.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB24-73](https://helpx.adobe.com/fr/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Faits saillants

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

## 2.4.4-p10

La version de sécurité 2.4.4-p10 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.4.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB24-61](https://helpx.adobe.com/fr/security/products/magento/apsb24-61.html).

### Faits saillants

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Correctifs inclus dans cette version

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.4-p9

La version de sécurité 2.4.4-p9 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités qui ont été identifiées dans les versions précédentes de 2.4.4.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB24-40](https://helpx.adobe.com/fr/security/products/magento/apsb24-40.html).

### Appliquer un correctif pour CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Mises à niveau de Platform

* **Prise en charge de MariaDB 10.5**. Cette version de correctif introduit la compatibilité avec la version 10.5 de MariaDB. Adobe Commerce est toujours compatible avec la version 10.4 de MariaDB, mais Adobe recommande d’utiliser Adobe Commerce 2.4.4-p9 et toutes les prochaines versions de correctifs de sécurité uniquement 2.4.4 uniquement avec la version 10.5 de MariaDB, car la maintenance de MariaDB 10.4 se termine le 18 juin 2024. <!--AC-11530-->

### Faits saillants

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.4-p8

La version de sécurité Adobe Commerce 2.4.4-p8 fournit des correctifs de sécurité pour votre déploiement d’Adobe Commerce 2.4.4. Ces mises à jour corrigent les vulnérabilités qui ont été identifiées dans les versions précédentes.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB24-18](https://helpx.adobe.com/fr/security/products/magento/apsb24-18.html).

## 2.4.4-p7

La version de sécurité 2.4.4-p7 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités qui ont été identifiées dans les versions précédentes. Cette version comprend également des améliorations de sécurité qui améliorent la conformité aux dernières bonnes pratiques de sécurité.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB24-03](https://helpx.adobe.com/fr/security/products/magento/apsb24-03.html).

### Faits saillants

Cette version introduit deux améliorations importantes de la sécurité :

* **Modification du comportement des clés de cache non générées** :

   * Les clés de cache non générées pour les blocs incluent désormais des préfixes qui diffèrent des préfixes des clés générées automatiquement. (Les clés de cache non générées sont des clés définies par le biais de la syntaxe de la directive du modèle ou des méthodes `setCacheKey` ou `setData`.)
   * Les clés de cache non générées pour les blocs ne doivent désormais contenir que des lettres, des chiffres, des tirets (-) et des traits de soulignement (_). <!-- AC-9831 -->

* **Limitations du nombre de codes de coupon générés automatiquement**. Commerce limite désormais le nombre de codes coupon générés automatiquement. La valeur maximale par défaut est de 250 000. Les commerçants peuvent utiliser la nouvelle option de configuration des **[!UICONTROL Code Quantity Limit]** (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) pour contrôler cette nouvelle limite. <!-- AC-8753 -->

## 2.4.4-p6

La version de sécurité 2.4.4-p6 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités qui ont été identifiées dans les versions précédentes. Cette version comprend également des améliorations de sécurité qui améliorent la conformité aux dernières bonnes pratiques de sécurité.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB23-50](https://helpx.adobe.com/fr/security/products/magento/apsb23-50.html).

Cette version comprend également des améliorations de sécurité qui améliorent la conformité aux dernières bonnes pratiques de sécurité.

### Faits saillants

Cette version introduit un nouveau paramètre de configuration du cache de page complète qui permet de réduire les risques associés au point d’entrée `{BASE-URL}/page_cache/block/esi HTTP`. Ce point d’entrée prend en charge des fragments de contenu chargés dynamiquement et sans restriction à partir des poignées de disposition et des structures de bloc Commerce. Le nouveau paramètre de configuration de **[!UICONTROL Handles Param]** définit la valeur du paramètre `handles` de ce point d’entrée, qui détermine le nombre maximal autorisé de descripteurs par API. La valeur par défaut de cette propriété est 100. Les commerçants peuvent modifier cette valeur depuis l&#39;Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Problèmes connus

**Problème** : Adobe Commerce affiche une erreur **somme de contrôle incorrecte** lors du téléchargement par le compositeur depuis `repo.magento.com`, et le téléchargement du package est interrompu. Ce problème peut se produire lors du téléchargement des packages de version rendus disponibles lors de la version préliminaire et est dû à un reconditionnement du package `magento/module-page-cache`.

**Solution** : les commerçants qui voient cette erreur lors du téléchargement peuvent suivre les étapes suivantes :

1) Supprimez le répertoire `/vendor` dans le projet, le cas échéant.
2) Exécutez la commande `bin/magento composer update magento/module-page-cache`. Cette commande met uniquement à jour le package `page cache`.

Si le problème de somme de contrôle persiste, supprimez le fichier `composer.lock` avant de réexécuter la commande `bin/magento composer update` pour mettre à jour chaque package.

## 2.4.4-p5

La version de sécurité 2.4.4-p5 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités qui ont été identifiées dans les versions précédentes.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB23-42](https://helpx.adobe.com/fr/security/products/magento/apsb23-42.html).

### Appliquer un correctif pour CVE-2022-31160

`jQuery-UI` version 1.13.1 de la bibliothèque comporte une vulnérabilité de sécurité connue (CVE-2022-31160) qui affecte plusieurs versions d’Adobe Commerce et de Magento Open Source. Cette bibliothèque est une dépendance d’Adobe Commerce et Magento Open Source 2.4.4, 2.4.5 et 2.4.6. Les commerçants exécutant les déploiements affectés doivent appliquer le correctif spécifié dans l’article de la base de connaissances [ Vulnérabilité de sécurité de l’interface utilisateur jQuery CVE-2022-31160 pour les versions 2.4.4, 2.4.5 et 2.4.6 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=fr) .

## 2.4.4-p4

La version de sécurité 2.4.4-p4 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités qui ont été identifiées dans les versions précédentes. Cette version comprend également des améliorations de la sécurité et des mises à niveau de la plateforme pour améliorer la conformité aux dernières bonnes pratiques de sécurité.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB23-35](https://helpx.adobe.com/fr/security/products/magento/apsb23-35.html).

### Appliquer un correctif pour CVE-2022-31160

`jQuery-UI` version 1.13.1 de la bibliothèque comporte une vulnérabilité de sécurité connue (CVE-2022-31160) qui affecte plusieurs versions d’Adobe Commerce et de Magento Open Source. Cette bibliothèque est une dépendance d’Adobe Commerce et Magento Open Source 2.4.4, 2.4.5 et 2.4.6. Les commerçants exécutant les déploiements affectés doivent appliquer le correctif spécifié dans l’article de la base de connaissances [ Vulnérabilité de sécurité de l’interface utilisateur jQuery CVE-2022-31160 pour les versions 2.4.4, 2.4.5 et 2.4.6 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=fr) .

### Faits saillants

Le comportement par défaut de la requête [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL et du point d’entrée REST ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) a changé. Par défaut, l’API renvoie désormais toujours `true`. Les commerçants peuvent activer le comportement d’origine, qui consiste à renvoyer un `true` si l’e-mail n’existe pas dans la base de données et à `false` s’il existe. <!-- AC-6695 -->

### Mises à niveau de Platform

Les mises à niveau de Platform pour cette version améliorent la conformité aux dernières bonnes pratiques de sécurité.

* **Prise en charge du cache de vernis 7.3**. Cette version est compatible avec la dernière version de Varnish Cache 7.3. La compatibilité reste assurée avec les versions 6.0.x et 7u.2.x, mais Adobe recommande de n’utiliser Adobe Commerce 2.4.4-p4 qu’avec la version 7.3 ou 6.0 LTS de Varnish Cache.

* **Prise en charge de RabbitMQ 3.11**. Cette version est compatible avec la dernière version de RabbitMQ 3.11. La compatibilité reste avec RabbitMQ 3.9, pris en charge jusqu’en août 2023, mais Adobe recommande d’utiliser Adobe Commerce 2.4.4-p4 uniquement avec RabbitMQ 3.11.

* **Bibliothèques JavaScript**. Les bibliothèques JavaScript obsolètes ont été mises à niveau vers les dernières versions mineures ou correctives, y compris la bibliothèque `moment.js` (v2.29.4), la bibliothèque `jQuery UI` (v1.13.2) et la bibliothèque de modules externes de validation `jQuery` (v1.19.5).

## 2.4.4-p3

La version de sécurité 2.4.4-p3 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités qui ont été identifiées dans les versions précédentes.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB23-17](https://helpx.adobe.com/fr/security/products/magento/apsb23-17.html).

## 2.4.4-p2

La version de sécurité 2.4.4-p2 d’Adobe Commerce fournit des correctifs pour les vulnérabilités qui ont été identifiées dans les versions précédentes. Un correctif comprend la création d’un paramètre de configuration. Le paramètre de configuration [!UICONTROL **Exiger une confirmation par e-mail si l’e-mail a été modifié**] permet aux administrateurs d’exiger une confirmation par e-mail lorsqu’un utilisateur administrateur modifie son adresse e-mail. <!-- AC-6292-->

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB22-48](https://helpx.adobe.com/fr/security/products/magento/apsb22-48.html).

### Appliquer AC-3022.patch pour continuer à offrir DHL comme transporteur

DHL a introduit la version 6.2 du schéma et abandonnera la version 6.0 dans un avenir proche. Adobe Commerce 2.4.4 et les versions antérieures qui prennent en charge l’intégration DHL ne prennent en charge que la version 6.0. Les commerçants qui déploient ces mainlevées devraient appliquer `AC-3022.patch` dès que possible pour continuer à offrir DHL en tant que transporteur. Consultez l’article de la base de connaissances [Appliquer un correctif pour continuer à proposer DHL en tant que transporteur](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481) pour plus d’informations sur le téléchargement et l’installation du correctif.

## 2.4.4-p1

La version de sécurité 2.4.4-p1 d’Adobe Commerce fournit des correctifs pour les vulnérabilités qui ont été identifiées dans les versions précédentes. Cette version comprend également des améliorations de sécurité visant à améliorer la conformité aux dernières bonnes pratiques de sécurité.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité d’Adobe](https://helpx.adobe.com/fr/security/products/magento/apsb22-38.html).t

### Appliquez `AC-3022.patch` pour continuer à proposer DHL comme transporteur

DHL a introduit la version 6.2 du schéma et abandonnera la version 6.0 dans un avenir proche. Adobe Commerce 2.4.4 et les versions antérieures qui prennent en charge l’intégration DHL ne prennent en charge que la version 6.0. Les commerçants qui déploient ces mainlevées devraient appliquer `AC-3022.patch` dès que possible pour continuer à offrir DHL en tant que transporteur. Consultez l’article de la base de connaissances [Appliquer un correctif pour continuer à proposer DHL en tant que transporteur](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) pour plus d’informations sur le téléchargement et l’installation du correctif.

### Faits saillants

Les améliorations apportées à la sécurité dans cette version améliorent la conformité aux dernières bonnes pratiques de sécurité, notamment :

* Les ressources ACL ont été ajoutées à l&#39;inventaire.
* La sécurité des modèles d&#39;inventaire a été améliorée.

### Problèmes connus

**Problème** : l’API Web et les tests d’intégration affichent cette erreur lors de l’exécution sur le package 2.4.4-p1 : `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`. **Solution** : installez la version précédente de Monolog en exécutant la commande `require monolog/monolog:2.6.0`. <!-- AC-3651-->

**Problème** : les commerçants peuvent remarquer des avis de rétrogradation de version de package lors d’une mise à niveau d’Adobe Commerce 2.4.4 vers Adobe Commerce 2.4.4-p1. Ces messages peuvent être ignorés. La différence dans les versions de package résulte d’anomalies lors de la génération du package. Aucune fonctionnalité du produit n’a été affectée. Consultez l’article de la base de connaissances [Packages rétrogradés après la mise à niveau de la version 2.4.4 vers la version 2.4.4-p1](https://support.magento.com/hc/en-us/articles/8214752983949) pour une discussion sur les scénarios et solutions de contournement concernés.
