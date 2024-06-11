---
title: Notes de mise à jour du correctif de sécurité Adobe Commerce 2.4.5
description: Découvrez les correctifs de sécurité, les améliorations de sécurité et d’autres mises à jour relatives à la sécurité inclus dans les versions des correctifs de sécurité pour Adobe Commerce version 2.4.5.
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: 7705e750a466ab134ae2616a40a32880ee0c45de
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 0%

---


# Notes de mise à jour des correctifs de sécurité d’Adobe Commerce 2.4.5

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.5-p8

La version de sécurité Adobe Commerce 2.4.5-p7 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.5.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, voir [Bulletin de sécurité Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Mises à niveau de la plateforme

* **Prise en charge de MariaDB 10.5**. Ce correctif introduit la compatibilité avec MariaDB version 10.5. Adobe Commerce est toujours compatible avec la version 10.4 de MariaDB, mais Adobe recommande d’utiliser Adobe Commerce 2.4.5-p8 et toutes les versions de correctifs de sécurité 2.4.5 à venir uniquement avec la version 10.5 de MariaDB, car la maintenance de MariaDB 10.4 se termine le 18 juin 2024. <!--AC-11530-->

## Adobe Commerce 2.4.5-p7

La version de sécurité Adobe Commerce 2.4.5-p7 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, voir [Bulletin de sécurité Adobe APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## Adobe Commerce 2.4.5-p6

La version de sécurité Adobe Commerce 2.4.5-p6 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes. Cette version comprend également des améliorations de sécurité afin d’améliorer la conformité aux dernières bonnes pratiques en matière de sécurité.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, voir [Bulletin de sécurité Adobe APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Mise en évidence de la sécurité

Cette version s’accompagne de deux améliorations importantes au niveau de la sécurité :

* **Modifications du comportement des clés de cache non générées**:

   * Les clés de cache non générées pour les blocs incluent désormais des préfixes différents des préfixes pour les clés générées automatiquement. (Les clés de cache non générées sont des clés définies par le biais de la syntaxe de directive de modèle ou de la fonction `setCacheKey` ou `setData` méthodes.)
   * Les clés de cache non générées pour les blocs ne doivent désormais contenir que des lettres, des chiffres, des tirets (-) et des traits de soulignement (_).  <!-- AC-9831 -->

* **Limites du nombre de codes de bon générés automatiquement**. Commerce limite désormais le nombre de codes de bon générés automatiquement. La valeur par défaut maximale est de 250 000. Les vendeurs peuvent utiliser la nouvelle **[!UICONTROL Code Quantity Limit]** option de configuration (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) pour contrôler cette nouvelle limite. <!-- AC-8753 -->



## Adobe Commerce 2.4.5-p5

La version de sécurité Adobe Commerce 2.4.5-p5 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes. Cette version comprend également des améliorations de sécurité afin d’améliorer la conformité aux dernières bonnes pratiques en matière de sécurité.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, voir [Bulletin de sécurité Adobe APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Mise en évidence de la sécurité

Cette version introduit un nouveau paramètre de configuration du cache de la page entière qui permet d’atténuer les risques associés à la variable `{BASE-URL}/page_cache/block/esi HTTP` point de terminaison . Ce point de terminaison prend en charge les fragments de contenu sans restriction et chargés dynamiquement à partir des poignées de disposition Commerce et des structures de bloc. La nouvelle **[!UICONTROL Handles Param]** paramètre de configuration définit la valeur de ce point de terminaison. `handles` qui détermine le nombre maximal autorisé de gestionnaires par API. La valeur par défaut de cette propriété est 100. Les vendeurs peuvent modifier cette valeur à partir de l’option Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Problème connu

**Problème**: Adobe Commerce affiche une **checksum incorrect** erreur lors du téléchargement depuis le compositeur `repo.magento.com`et le téléchargement du package est interrompu. Ce problème peut se produire lors du téléchargement des modules de version qui ont été mis à disposition lors de la version préliminaire et qui est dû à un reconditionnement de la fonction `magento/module-page-cache` module.

**Solution**: les commerçants qui voient cette erreur lors du téléchargement peuvent procéder comme suit :

1) Supprimez le `/vendor` dans le projet, le cas échéant.
2) Exécutez la variable `bin/magento composer update magento/module-page-cache` . Cette commande ne met à jour que la fonction `page cache` module.

Si le problème de somme de contrôle persiste, supprimez la variable `composer.lock` avant de réexécuter la variable `bin/magento composer update` pour mettre à jour chaque module.

## Adobe Commerce 2.4.5-p4

La version de sécurité Adobe Commerce 2.4.5-p4 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, voir [Bulletin de sécurité Adobe APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Application d’un correctif pour résoudre la vulnérabilité de sécurité CVE-2022-31160 dans la bibliothèque jQuery-UI

`jQuery-UI` La version 1.13.1 de la bibliothèque comporte une vulnérabilité de sécurité connue (CVE-2022-31160) qui affecte plusieurs versions d’Adobe Commerce et de Magento Open Source. Cette bibliothèque est une dépendance d’Adobe Commerce et de Magento Open Source 2.4.4, 2.4.5 et 2.4.6. Les marchands exécutant les déploiements affectés doivent appliquer le correctif spécifié dans la variable [Correctif de la vulnérabilité de sécurité de l’interface utilisateur de jQuery CVE-2022-31160 pour les versions 2.4.4, 2.4.5 et 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Article de la base de connaissances.

## Adobe Commerce 2.4.5-p3

La version de sécurité Adobe Commerce 2.4.5-p3 fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes. Cette version comprend également des améliorations de sécurité qui améliorent la conformité aux dernières bonnes pratiques en matière de sécurité.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, voir [Bulletin de sécurité Adobe](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Application d’un correctif pour résoudre la vulnérabilité de sécurité CVE-2022-31160 dans la bibliothèque jQuery-UI

`jQuery-UI` La version 1.13.1 de la bibliothèque comporte une vulnérabilité de sécurité connue (CVE-2022-31160) qui affecte plusieurs versions d’Adobe Commerce et de Magento Open Source. Cette bibliothèque est une dépendance d’Adobe Commerce et de Magento Open Source 2.4.4, 2.4.5 et 2.4.6. Les marchands exécutant les déploiements affectés doivent appliquer le correctif spécifié dans la variable [Correctif CVE-2022-31160 pour la sécurité de l’interface utilisateur de requête pour les versions 2.4.4, 2.4.5 et 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Article de la base de connaissances.

### Mise en évidence de la sécurité

Le comportement par défaut de la variable [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) Requête GraphQL et ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) Le point de terminaison REST a changé. Par défaut, l’API renvoie désormais toujours `true`. Les vendeurs peuvent activer le comportement d’origine, qui consiste à renvoyer la variable `true` si l’email n’existe pas dans la base de données et `false` s’il existe. <!-- AC-6695 -->

### Mises à niveau de la plateforme

Les mises à niveau de plateforme de cette version améliorent la conformité aux dernières bonnes pratiques en matière de sécurité.

* **Prise en charge du cache 7.3 de vernis**. Cette version est compatible avec la dernière version de Varnish Cache 7.3. La compatibilité reste avec les versions 6.0.x et 7.2.x, mais nous vous recommandons d’utiliser Adobe Commerce 2.4.5-p3 uniquement avec la version 7.3 ou la version 6.0 LTS du cache de vernis.

* **Prise en charge de RabbitMQ 3.11**. Cette version est compatible avec la dernière version de RabbitMQ 3.11. La compatibilité reste avec RabbitMQ 3.9, qui est pris en charge jusqu’en août 2023, mais nous vous recommandons d’utiliser Adobe Commerce 2.4.5-p3 uniquement avec RabbitMQ 3.11.

* **Bibliothèques JavaScript**. Les bibliothèques JavaScript obsolètes ont été mises à niveau vers les dernières versions mineures ou de correctif, y compris `moment.js` library (v2.29.4), `jQuery UI` bibliothèque (v1.13.2) et `jQuery` bibliothèque de modules externes de validation (v1.19.5).

## Notes de mise à jour d’Adobe Commerce 2.4.5-p2

La version de sécurité Adobe Commerce 2.4.5-p2 fournit trois correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, voir [Bulletin de sécurité Adobe APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## Adobe Commerce 2.4.5-p1

La version de sécurité Adobe Commerce 2.4.5-p1 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans la version précédente (Adobe Commerce 2.4.5 et Magento Open Source 2.4.5).

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, voir [Bulletin de sécurité Adobe APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

L’un des correctifs de sécurité a inclus la création d’un nouveau paramètre de configuration. La variable **Demande de confirmation d’email si l’email a été modifié** configuration permet aux administrateurs d’avoir besoin d’une confirmation par courrier électronique lorsqu’un utilisateur administrateur modifie son adresse électronique. <!-- AC-6292-->
