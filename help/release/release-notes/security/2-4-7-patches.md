---
title: Notes De Mise À Jour Du Correctif De Sécurité D’Adobe Commerce 2.4.7
description: Découvrez les correctifs de sécurité, les améliorations de sécurité et les autres mises à jour liées à la sécurité inclus dans les versions des correctifs de sécurité pour Adobe Commerce version 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: f731debd7e0734d1bb1b8c821149ffafea735337
workflow-type: tm+mt
source-wordcount: '1390'
ht-degree: 0%

---


# Notes de mise à jour des correctifs de sécurité d’Adobe Commerce 2.4.7

{{$include /help/_includes/release-notes/security-patch-intro.md}}

>[!IMPORTANT]
>
>MySQL 8.0 atteindra la fin de la prise en charge (EOS) à partir du 30 avril 2026.
>
>À compter de cette date, Adobe Commerce version 2.4.7 ne fournira plus de compatibilité ou>Prise en charge de toutes les versions de MySQL publiées après MySQL 8.0. Adobe ne le fera pas>valider ou fournir la prise en charge des versions majeures MySQL plus récentes sur cette Adobe>Ligne de version de Commerce.
>
>Tous les clients et clientes Adobe Commerce On-Premise exécutant la version 2.4.7 ont une>a conseillé de migrer ses serveurs de base de données vers une version MariaDB compatible.

## 2.4.7-p10

La version de sécurité 2.4.7-p10 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.7.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB26-49](https://helpx.adobe.com/security/products/magento/apsb26-49.html).

{{b2b-patches}}

### Faits saillants

Les points forts de cette version sont les suivants :

#### Compatibilité avec MariaDB 11.8

Adobe Commerce 2.4.7-p10 introduit la compatibilité avec MariaDB version 11.8. MariaDB 11.8 introduit des changements dans le comportement SQL, les valeurs par défaut, les dépréciations et les optimisations de performances. Cette mise à jour résout de manière proactive les problèmes potentiels afin de maintenir la stabilité de la plateforme et la préparation future.

#### Prise en charge de la dernière version mineure d’OpenSearch 3

Adobe Commerce 2.4.7 prend désormais en charge la dernière version mineure d’OpenSearch 3 sur Adobe Commerce pour les déploiements sur l’infrastructure cloud, Cloud Native et On-Premise. La compatibilité avec OpenSearch 2 est conservée.

#### Prise en charge de Valkey 8.1 LTS

Adobe Commerce 2.4.7 est désormais compatible avec Valkey 8.1 LTS, fournissant une option de serveur principal de cache de prise en charge à long terme, prise en charge sur Adobe Commerce sur les infrastructures cloud.

#### Prise en charge de RabbitMQ 4.2

Adobe Commerce 2.4.7 est désormais compatible avec RabbitMQ 4.2, qui tient compte de la date de fin de prise en charge de RabbitMQ 4.1 prévue pour février 2026. La compatibilité avec les artéfacts Apache ActiveMQ est conservée et ActiveMQ reste le service de file d’attente de messages par défaut pour cette ligne de mise à jour de sécurité uniquement.

#### Prise en charge de l’API REST USPS

L’intégration d’expédition USPS prend désormais en charge les API RESTful USPS modernisées, en plus des API des outils web hérités. Les administrateurs peuvent sélectionner l’API d’intégration USPS à utiliser dans la configuration d’administration. Cette mise à jour prépare l’obsolescence de l’API Web Tools d’USPS.

#### Branchement MVC Laminas appartenant à Magento

Pour gérer la mise hors service de Laminas MVC, Adobe Commerce utilise désormais un formulaire de `laminas-mvc` détenu par Magento (publié en tant que `magento/magento-zf-mvc`). Ce branchement assure la conformité continue des correctifs et de la sécurité à long terme pour Adobe Commerce 2.4.7.

## 2.4.7-p9

La version de sécurité 2.4.7-p9 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.7.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB26-05](https://helpx.adobe.com/security/products/magento/apsb26-05.html).

{{b2b-patches}}

### Faits saillants

Les points forts de cette version sont les suivants :

#### Prise en charge de l’API REST MyDHL pour l’intégration de l’expédition DHL

L&#39;intégration d&#39;expédition DHL prend désormais en charge les API REST MyDHL en plus de l&#39;intégration XML DHL Express existante. Cette mise à jour s’aligne sur la pile d’API actuelle de DHL et prépare l’obsolescence des anciennes API XML.

#### Ajouter la compatibilité avec la dernière version du compositeur

Adobe Commerce 2.4.7 a été mis à jour pour prendre en charge le compositeur 2.9.x tout en restant compatible avec le compositeur 2.2 LTS.

## 2.4.7-p8

La version de sécurité 2.4.7-p8 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.7.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-94](https://helpx.adobe.com/security/products/magento/apsb25-94.html).

{{b2b-patches}}

Les points forts de cette version sont les suivants :

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

{{oct-2025-backports}}

### Problèmes connus

#### La page d’extraction ne parvient pas à charger static.min.js et mixins.min.js.

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.7-p7

La version de sécurité 2.4.7-p7 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.7.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.7-p6

La version de sécurité 2.4.7-p6 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.7.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Faits saillants

Les points forts de cette version sont les suivants :

* **Prise en charge de MariaDB**—Ajout de la prise en charge de MariaDB 10.11.

* **Amélioration des performances de l’API** : résout la dégradation des performances des points d’entrée d’API web asynchrones en bloc introduits après le correctif de sécurité précédent<!-- AC-14078 -->.

* **Correctif des blocs d’accès CMS**—Résout un problème en raison duquel les utilisateurs administrateurs disposant d’autorisations limitées (comme un accès au marchandisage uniquement) ne pouvaient pas afficher la page de liste [!UICONTROL CMS Blocks].

  Auparavant, ces utilisateurs rencontraient une erreur en raison de paramètres de configuration manquants après l’installation des correctifs de sécurité précédents.<!-- AC-14087 -->

* **Compatibilité des limites de cookies** : résout une modification non rétrocompatible impliquant la constante `MAX_NUM_COOKIES` dans le framework. Cette mise à jour restaure le comportement attendu et assure la compatibilité des extensions ou des personnalisations qui interagissent avec les limites de cookies.<!-- AC-14475 -->

* **Opérations asynchrones** : opérations asynchrones restreintes pour remplacer les commandes précédentes de clients.<!-- AC-13917 -->

## 2.4.7-p5

La version de sécurité 2.4.7-p5 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.7.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### Faits saillants

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

>[!BEGINSHADEBOX]

Cette version introduit également la prise en charge de l’extension Adobe Commerce [conforme à la norme HIPAA](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview).

>[!ENDSHADEBOX]

### Problèmes connus

**Problème** : lors de l’installation de la version 2.4.7-p5 avec PHP 8.2 ou une version ultérieure, le système installe `paypal/module-braintree` version 4.7.0, qui est prévue pour la version 2.4.8 et les versions ultérieures. Pour PHP 8.1, la version correcte de Braintree 4.6.1-p5 est utilisée. Cette incohérence est due à la dépendance lâche sur `adobe-commerce/extensions-metapackage: ~2.0` dans le métapaquet. Cela a un impact sur la compatibilité et les fonctionnalités prises en charge pour les déploiements PHP 8.2+.<!-- ACPLTSRV-6276) -->

En outre, pour les versions 2.4.7-p3, 2.4.7-p4 et 2.4.7-p5, l’extension Braintree version 4.6.1-p5 peut être installée, tandis que certains utilisateurs et utilisatrices s’attendent à une version 4.6.1-p3 ou p4, en raison de dépendances plus strictes qui ont été assouplies pour permettre les mises à niveau d’extension dans une ligne de version. <!-- AC-14430 -->

**Solution** : Pour vous assurer que vous disposez de la version Braintree correcte pour votre version PHP, exécutez `composer update` pour installer la version appropriée comme dicté par la dépendance `adobe-commerce/extensions-metapackage:2.0.0`.

## 2.4.7-p4

La version de sécurité 2.4.7-p4 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.7.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Faits saillants

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.7-p3

La version de sécurité 2.4.7-p3 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.7.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Faits saillants

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Correctifs inclus dans cette version

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.7-p2

La version de sécurité 2.4.7-p2 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.7.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### Faits saillants

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Correctifs inclus dans cette version

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.7-p1

La version de sécurité 2.4.7-p1 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités qui ont été identifiées dans les versions précédentes de 2.4.7.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Appliquer un correctif pour CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Faits saillants

Les points forts de cette version sont les suivants :

* **Mise à jour [paramètres de mot de passe à usage unique (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/config/security/2fa) pour l’authentificateur Google**-Cette mise à jour est nécessaire pour résoudre une erreur introduite par une [modification rétrocompatible](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) dans la version 2.4.7. La description du champ **[!UICONTROL OTP Window]** fournit désormais une explication précise du paramètre et la valeur par défaut a été modifiée de `1` en `29`.

* **Compatibilité des versions B2B** : pour des raisons de compatibilité avec la version 2.4.7-p1 de Commerce, les commerçants qui disposent de l’extension Adobe Commerce B2B doivent effectuer la mise à niveau vers la version 1.4.2-p1 de [B2B](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Correctifs inclus dans cette version

Adobe Commerce 2.4.7-p1 résout un problème introduit dans le cadre de la migration de l’intégration UPS de SOAP vers l’API REST. Ce problème affectait les clients qui expédiaient à l&#39;extérieur des États-Unis et les empêchait d&#39;utiliser les mesures du système métrique/SI de kilogrammes et de centimètres pour les colis afin de créer des expéditions avec UPS. Consultez l’article de la base de connaissances [ Migration de l’intégration de la méthode d’expédition UPS de l’API SOAP vers l’API RESTful ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) pour plus d’informations.

<!-- Last updated from includes: 2026-04-08 15:01:38 -->
