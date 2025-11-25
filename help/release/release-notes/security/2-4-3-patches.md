---
title: Notes de mise à jour des correctifs de sécurité d’Adobe Commerce 2.4.3
description: Découvrez les correctifs de sécurité, les améliorations de sécurité et les autres mises à jour liées à la sécurité inclus dans les versions des correctifs de sécurité pour Adobe Commerce version 2.4.3.
exl-id: 72d343cd-83d7-48ce-976a-e26ba1b8db27
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 0%

---


# Notes de mise à jour des correctifs de sécurité d’Adobe Commerce 2.4.3

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## Adobe Commerce 2.4.3-p3

La version de sécurité 2.4.3-p3 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités qui ont été identifiées dans les versions précédentes de 2.4.3. Cette version comprend également des améliorations de sécurité qui améliorent la conformité aux dernières bonnes pratiques de sécurité.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB22-38](https://helpx.adobe.com/fr/security/products/magento/apsb22-38.html).

### Appliquer AC-3022.patch pour continuer à offrir DHL comme transporteur

DHL a introduit la version 6.2 du schéma et abandonnera la version 6.0 dans un avenir proche. Adobe Commerce 2.4.4 et les versions antérieures qui prennent en charge l’intégration DHL ne prennent en charge que la version 6.0. Les commerçants qui déploient ces mainlevées devraient appliquer `AC-3022.patch` dès que possible pour continuer à offrir DHL en tant que transporteur. Consultez l’article de la base de connaissances [Appliquer un correctif pour continuer à proposer DHL en tant que transporteur](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) pour plus d’informations sur le téléchargement et l’installation du correctif.

### Points forts en matière de sécurité

* Les ressources ACL ont été ajoutées à l&#39;inventaire.
* La sécurité des modèles d&#39;inventaire a été améliorée.



## Adobe Commerce 2.4.3-p2

La version de sécurité 2.4.3-p2 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités qui ont été identifiées dans les versions précédentes. Cette version comprend également des améliorations de sécurité qui améliorent la conformité aux dernières bonnes pratiques de sécurité.

Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB22-13](https://helpx.adobe.com/fr/security/products/magento/apsb22-13.html).  La version de correctif résout également la vulnérabilité corrigée par `MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch.zip`, `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch.zip`, `MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch` et `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch`.


### Appliquer AC-3022.patch pour continuer à offrir DHL comme transporteur

DHL a introduit la version 6.2 du schéma et abandonnera la version 6.0 dans un avenir proche. Adobe Commerce 2.4.4 et les versions antérieures qui prennent en charge l’intégration DHL ne prennent en charge que la version 6.0. Les commerçants qui déploient ces mainlevées devraient appliquer `AC-3022.patch` dès que possible pour continuer à offrir DHL en tant que transporteur. Consultez l’article de la base de connaissances [Appliquer un correctif pour continuer à proposer DHL en tant que transporteur](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) pour plus d’informations sur le téléchargement et l’installation du correctif.

### Points forts en matière de sécurité

* L’utilisation des variables d’e-mail a été abandonnée dans la version 2.3.4 dans le cadre d’une réduction des risques de sécurité au profit d’une syntaxe de variable plus stricte. Ce comportement hérité a été entièrement supprimé dans cette version dans le cadre de la réduction des risques de sécurité.

  Par conséquent, les modèles d’e-mail ou de newsletter qui fonctionnaient dans les versions précédentes peuvent ne pas fonctionner correctement après la mise à niveau vers Adobe Commerce 2.4.3-p2. Les modèles concernés sont les remplacements administrateur, les thèmes, les thèmes enfants et les modèles provenant de modules personnalisés ou d’extensions tierces. Votre déploiement peut toujours être affecté, même après avoir utilisé l’outil de compatibilité de mise à niveau [Upgrade](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html?lang=fr) pour corriger les utilisations obsolètes. Voir [Migration de modèles d’e-mail personnalisés](https://developer.adobe.com/commerce/frontend-core/guide/templates/email-migration/) pour plus d’informations sur les effets potentiels et des instructions pour migrer les modèles affectés.

* Les jetons d’accès OAuth et les jetons de réinitialisation de mot de passe sont désormais chiffrés lorsqu’ils sont stockés dans la base de données. <!-- AC-520 1323-->

* La validation a été renforcée pour empêcher le chargement d’extensions de fichier non alphanumériques. <!-- AC-479-->

* Swagger est désormais désactivé par défaut lorsqu’Adobe Commerce est en mode de production. <!-- AC-1450-->

* L’équipe de développement peut désormais configurer la limite de taille des tableaux acceptés par les points d’entrée RESTful Adobe Commerce sur la base de chaque point d’entrée. Voir [Sécurité des API](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-465-->

* Ajout de mécanismes pour limiter la taille et le nombre de ressources qu’un utilisateur peut demander par le biais d’une API web à l’échelle du système et pour remplacer les valeurs par défaut sur des modules individuels. Cette amélioration résout le problème résolu par `MC-43048__set_rate_limits__2.4.3.patch`. Voir [Sécurité des API](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-1120-->


## 2.4.3-p1

La version de sécurité 2.4.3-p1 d’Adobe Commerce fournit des correctifs de sécurité pour les vulnérabilités qui ont été identifiées dans la version précédente (Adobe Commerce 2.4.3 et Magento Open Source 2.4.3). Cette version comprend également des améliorations de sécurité qui améliorent la conformité aux dernières bonnes pratiques de sécurité.


Pour obtenir les dernières informations sur les correctifs de sécurité, consultez le [Bulletin de sécurité Adobe APSB21-86](https://helpx.adobe.com/fr/security/products/magento/apsb21-86.html). La version de correctif fournit également des correctifs pour les extensions développées par le fournisseur [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/braintree.html?lang=fr), [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html) et [Vertex](https://marketplace.magento.com/vertexinc-vertex-tax-module.html).

### Appliquer AC-3022.patch pour continuer à offrir DHL comme transporteur

DHL a introduit la version 6.2 du schéma et abandonnera la version 6.0 dans un avenir proche. Adobe Commerce 2.4.4 et les versions antérieures qui prennent en charge l’intégration DHL ne prennent en charge que la version 6.0. Les commerçants qui déploient ces mainlevées devraient appliquer `AC-3022.patch` dès que possible pour continuer à offrir DHL en tant que transporteur. Consultez l’article de la base de connaissances [Appliquer un correctif pour continuer à proposer DHL en tant que transporteur](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) pour plus d’informations sur le téléchargement et l’installation du correctif.

### Correctifs

Cette version comprend le correctif suivant et tous les correctifs publiés pour la version de correctif précédente.

* Correctif `AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch to address PHP fatal error on upgrade`. Consultez l’article Correctif d’erreur fatale PHP [Adobe Commerce upgrade 2.4.3, 2.3.7-p1](https://support.magento.com/hc/en-us/articles/4408021533069-Adobe-Commerce-upgrade-2-4-3-2-3-7-p1-PHP-Fatal-error-Hotfix) de la base de connaissances pour plus d’informations sur les correctifs et les problèmes.

### Points forts en matière de sécurité

**Les ID de session ont été supprimés de la base de données**. Ce changement de code peut entraîner des modifications avec rupture si les commerçants disposent de personnalisations ou d’extensions installées qui utilisent les ID de session bruts stockés dans la base de données. <!-- MC-40976-->

**Accès administrateur limité aux dossiers de la Galerie de médias**. Les autorisations par défaut de la Galerie de médias n’autorisent désormais que les opérations de répertoire (affichage, chargement, suppression et création) qui sont autorisées explicitement par la configuration. Les utilisateurs administrateurs ne peuvent plus accéder aux ressources multimédias par l’intermédiaire de la Galerie de médias qui ont été chargées en dehors des répertoires `catalog/category` ou `wysiwyg`. Les administrateurs qui souhaitent accéder aux ressources multimédias doivent les déplacer vers un dossier explicitement autorisé ou ajuster leurs paramètres de configuration. Voir [&#x200B; Modifier les autorisations de dossier de Media Library](https://developer.adobe.com/commerce/php/tutorials/backend/modify-image-library-permissions/). <!-- B2B-1897-->

**Limites abaissées à la complexité des requêtes GraphQL**. La complexité maximale autorisée des requêtes dans GraphQL a été réduite afin d’empêcher les attaques par déni de service (DOS). Voir la configuration de la sécurité de [GraphQL](https://developer.adobe.com/commerce/webapi/graphql/usage/security-configuration/). <!-- PWA-1700-->

**Des vulnérabilités récentes du test de pénétration** ont été corrigées dans cette version. <!-- MC-42431-->

L’expression source non prise en charge `unsafe-inline` a été supprimée de la directive `frame-ancestors` de la politique de sécurité du contenu. [GitHub-33101](https://github.com/magento/magento2/issues/33101)<!-- MC-42632-->

<!-- Last updated from includes: 2025-05-28 17:01:56 -->
