---
title: Notes De Mise À Jour Du Correctif De Sécurité D’Adobe Commerce 2.4.8
description: Découvrez les correctifs de sécurité, les améliorations de sécurité et les autres mises à jour liées à la sécurité inclus dans les versions des correctifs de sécurité pour Adobe Commerce version 2.4.8.
exl-id: 5f8866ed-9215-4b2e-9c77-b2d474f6c1f9
source-git-commit: a61409b02e612295fb03a42e22dcfdf5c3eb0e57
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 0%

---

# Notes de mise à jour des correctifs de sécurité d’Adobe Commerce 2.4.8

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8-p5

La version de sécurité 2.4.8-p5 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.8.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB26-49](https://helpx.adobe.com/security/products/magento/apsb26-49.html).

{{b2b-patches}}

### Faits saillants

Les points forts de cette version sont les suivants :

#### Compatibilité avec MariaDB 11.8

La compatibilité d’Adobe Commerce 2.4.8 avec MariaDB 11.8 a été validée, tout en conservant la prise en charge de MariaDB 11.4. Cette mise à jour traite des changements de comportement SQL, des mises à jour par défaut et des obsolescence introduits dans MariaDB 11.8 pour maintenir la stabilité de la plateforme.

#### Prise en charge de la dernière version mineure d’OpenSearch 3

Adobe Commerce 2.4.8 prend désormais en charge la dernière version mineure d’OpenSearch 3 sur Adobe Commerce pour les déploiements sur l’infrastructure cloud, Cloud Native et On-Premise. La compatibilité avec OpenSearch 2 est conservée.

#### Prise en charge de Valkey 9.x LTS

Adobe Commerce 2.4.8 est désormais compatible avec Valkey 9.x LTS, fournissant une option de serveur principal de cache de prise en charge à long terme qui est prise en charge sur Adobe Commerce sur l’infrastructure cloud.

#### Prise en charge de RabbitMQ 4.2

Adobe Commerce 2.4.8 est désormais compatible avec RabbitMQ 4.2, qui tient compte de la date de fin de prise en charge de RabbitMQ 4.1 prévue pour février 2026. La compatibilité avec les artéfacts Apache ActiveMQ est conservée et ActiveMQ reste le service de file d’attente de messages par défaut pour cette ligne de mise à jour de sécurité uniquement.

#### Prise en charge de l’API REST USPS

L’intégration d’expédition USPS prend désormais en charge les API RESTful USPS modernisées, en plus des API des outils web hérités. Les administrateurs peuvent sélectionner l’API d’intégration USPS à utiliser dans la configuration d’administration. Cette mise à jour prépare l’obsolescence de l’API Web Tools d’USPS.

#### Branchement MVC Laminas appartenant à Magento

Pour gérer la mise hors service de Laminas MVC, Adobe Commerce utilise désormais un formulaire de `laminas-mvc` détenu par Magento (publié en tant que `magento/magento-zf-mvc`). Ce branchement assure la conformité continue des correctifs et de la sécurité à long terme pour Adobe Commerce 2.4.8.

## 2.4.8-p4

La version de sécurité 2.4.8-p4 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.8.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB26-05](https://helpx.adobe.com/security/products/magento/apsb26-05.html).

{{b2b-patches}}

### Faits saillants

Les points forts de cette version sont les suivants :

#### Prise en charge de l’API REST MyDHL pour l’intégration de l’expédition DHL

L&#39;intégration d&#39;expédition DHL prend désormais en charge les API REST MyDHL en plus de l&#39;intégration XML DHL Express existante. Cette mise à jour s’aligne sur la pile d’API actuelle de DHL et prépare l’obsolescence des anciennes API XML.

#### Ajouter la compatibilité avec la dernière version du compositeur

Adobe Commerce 2.4.8 a été mis à jour pour prendre en charge le compositeur 2.9.x tout en restant compatible avec le compositeur 2.2 LTS.

## 2.4.8-p3

La version de sécurité 2.4.8-p3 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.8.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-94](https://helpx.adobe.com/security/products/magento/apsb25-94.html).

{{b2b-patches}}

### Faits saillants

Les points forts de cette version sont les suivants :

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

* Correction pour ACP2E-3874 : la réponse de l’API REST pour les détails de commande contient désormais des valeurs correctes pour les attributs `base_row_total` et `row_total` au cas où plusieurs mêmes éléments auraient été commandés.

* Correctif pour AC-15446 : correction d’une erreur dans `Magento\Framework\Mail\EmailMessage`, en raison de laquelle `getBodyText()` tentait d’appeler une méthode `getTextBody()` inexistante sur `Symfony\Component\Mime\Message`, afin d’assurer la compatibilité avec Magento 2.4.8-p2 et `magento/framework` 103.0.8-p2.

{{oct-2025-backports}}

### Problèmes connus

#### La page d’extraction ne parvient pas à charger static.min.js et mixins.min.js.

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.8-p2

La version de sécurité 2.4.8-p2 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.8.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.8-p1

La version de sécurité 2.4.8-p1 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités identifiées dans les versions précédentes de 2.4.8.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Faits saillants

Les points forts de cette version sont les suivants :

* **Amélioration des performances de l’API** : résout la dégradation des performances des points d’entrée d’API web asynchrones en bloc introduits après le correctif de sécurité précédent<!-- AC-14078 -->.

* **Correctif des blocs d’accès CMS**—Résout un problème en raison duquel les utilisateurs administrateurs disposant d’autorisations limitées (comme un accès au marchandisage uniquement) ne pouvaient pas afficher la page de liste [!UICONTROL CMS Blocks].

  Auparavant, ces utilisateurs rencontraient une erreur en raison de paramètres de configuration manquants après l’installation des correctifs de sécurité précédents.<!-- AC-14087 -->

* **Compatibilité des limites de cookies** : résout une modification non rétrocompatible impliquant la constante `MAX_NUM_COOKIES` dans le framework. Cette mise à jour restaure le comportement attendu et assure la compatibilité des extensions ou des personnalisations qui interagissent avec les limites de cookies.<!-- AC-14475 -->

* **Opérations asynchrones** : opérations asynchrones restreintes pour remplacer les commandes précédentes de clients.<!-- AC-13917 -->

* **Correctif pour CVE-2025-47110** : résout une vulnérabilité des modèles d’e-mail.<!-- AC-14695 -->

* **Correctif pour VULN-31547** : résout une vulnérabilité de lien canonique de catégorie.<!-- AC-14713 -->

>[!BEGINSHADEBOX]

Les correctifs pour CVE-2025-47110 et VULN-31547 sont également disponibles en tant que correctif isolé. Pour plus d’informations, consultez l’article [Base de connaissances](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50).

>[!ENDSHADEBOX]

<!-- Last updated from includes: 2026-04-08 15:01:38 -->
