---
title: Notes de mise à jour des correctifs de sécurité Adobe Commerce 2.4.3
description: Découvrez les correctifs de sécurité, les améliorations de sécurité et d’autres mises à jour relatives à la sécurité inclus dans les versions des correctifs de sécurité pour Adobe Commerce version 2.4.3.
exl-id: 72d343cd-83d7-48ce-976a-e26ba1b8db27
source-git-commit: 1eaf2329c16e6dbe3e93cb7fff3a6920b4b8379d
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 0%

---

# Notes de mise à jour du correctif de sécurité Adobe Commerce 2.4.3

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.3-p3

La version de sécurité Adobe Commerce 2.4.3-p3 fournit des correctifs de sécurité pour les vulnérabilités identifiées dans la version précédente (Adobe Commerce 2.4.3 et Magento Open Source 2.4.3). Cette version comprend également des améliorations de sécurité qui améliorent la conformité aux dernières bonnes pratiques en matière de sécurité.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, voir [Bulletin de sécurité Adobe APSB22-38](https://helpx.adobe.com/security/products/magento/apsb22-38.html).


### Appliquer `AC-3022.patch` continuer à proposer DHL comme opérateur de transport

DHL a introduit la version 6.2 du schéma et va abandonner la version 6.0 dans un avenir proche. Adobe Commerce 2.4.4 et les versions antérieures qui prennent en charge l’intégration DHL ne prennent en charge que la version 6.0. Les commerçants qui déploient ces versions doivent s’appliquer `AC-3022.patch` dès leur première convenance de continuer à proposer DHL comme transporteur. Voir [Appliquez un correctif pour continuer à proposer DHL comme opérateur de transport](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Article de la base de connaissances pour plus d’informations sur le téléchargement et l’installation du correctif.

### Mise en évidence de la sécurité

* Des ressources de liste de contrôle d’accès ont été ajoutées à l’inventaire.
* La sécurité du modèle d’inventaire a été améliorée.

## Adobe Commerce 2.4.3-p2

La version de sécurité Adobe Commerce 2.4.3-p2 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans les versions précédentes. Cette version comprend également des améliorations de sécurité qui améliorent la conformité aux dernières bonnes pratiques en matière de sécurité.

Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, voir [Bulletin de sécurité Adobe APSB22-13](https://helpx.adobe.com/security/products/magento/apsb22-13.html).  La version de correctif résout également la vulnérabilité corrigée par `MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch.zip`, `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch.zip`,`MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch`, et `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch`.


### Appliquer `AC-3022.patch` continuer à proposer DHL comme opérateur de transport

DHL a introduit la version 6.2 du schéma et va abandonner la version 6.0 dans un avenir proche. Adobe Commerce 2.4.4 et les versions antérieures qui prennent en charge l’intégration DHL ne prennent en charge que la version 6.0. Les commerçants qui déploient ces versions doivent s’appliquer `AC-3022.patch` dès leur première convenance de continuer à proposer DHL comme transporteur. Voir [Appliquez un correctif pour continuer à proposer DHL comme opérateur de transport](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Article de la base de connaissances pour plus d’informations sur le téléchargement et l’installation du correctif.


### Mise en évidence de la sécurité

* L’utilisation des variables de messagerie a été abandonnée dans la version 2.3.4 dans le cadre d’une limitation des risques de sécurité au profit d’une syntaxe de variable plus stricte. Ce comportement hérité a été complètement supprimé dans cette version en tant que prolongement de cette limitation des risques de sécurité.

  Par conséquent, les modèles de courrier électronique ou de newsletter qui fonctionnaient dans les versions précédentes peuvent ne pas fonctionner correctement après la mise à niveau vers Adobe Commerce 2.4.3-p2. Les modèles concernés incluent des remplacements d’administrateur, des thèmes, des thèmes enfants et des modèles provenant de modules personnalisés ou d’extensions tierces. Votre déploiement peut encore être affecté même après l’utilisation de la variable [Outil de compatibilité de mise à niveau](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html?lang=en) pour corriger les utilisations obsolètes. Voir [Migration de modèles de courrier électronique personnalisés](https://developer.adobe.com/commerce/frontend-core/guide/templates/email-migration/) pour plus d’informations sur les effets potentiels et les directives relatives à la migration des modèles concernés.

* Les jetons d’accès OAuth et les jetons de réinitialisation de mot de passe sont désormais chiffrés lorsqu’ils sont stockés dans la base de données. <!-- AC-520 1323-->

* La validation a été renforcée afin d’empêcher le téléchargement d’extensions de fichiers non alphanumériques. <!-- AC-479-->

* Swagger est désormais désactivé par défaut lorsqu’Adobe Commerce est en mode de production. <!-- AC-1450-->

* Les développeurs peuvent désormais configurer la limite de taille pour les tableaux acceptés par les points d’entrée RESTful d’Adobe Commerce selon chaque point d’entrée. Voir [Sécurité des API](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-465-->

* Ajout de mécanismes permettant de limiter la taille et le nombre de ressources qu’un utilisateur peut demander via une API web à l’échelle du système, ainsi que de remplacer les valeurs par défaut sur des modules individuels. Cette amélioration résout le problème résolu par `MC-43048__set_rate_limits__2.4.3.patch`. Voir [Sécurité des API](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-1120-->


## 2.4.3-p1

La version de sécurité Adobe Commerce 2.4.3-p1 fournit des correctifs de bogues de sécurité pour les vulnérabilités identifiées dans la version précédente (Adobe Commerce 2.4.3 et Magento Open Source 2.4.3). Cette version comprend également des améliorations de sécurité qui améliorent la conformité aux dernières bonnes pratiques en matière de sécurité.


Pour obtenir les informations les plus récentes sur les correctifs de bogues de sécurité, voir [Bulletin de sécurité Adobe APSB21-86](https://helpx.adobe.com/security/products/magento/apsb21-86.html). La version de correctif fournit également des correctifs pour les [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/braintree.html), [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html), et [Vertex](https://marketplace.magento.com/vertexinc-vertex-tax-module.html) extensions développées par des fournisseurs.


### Appliquer `AC-3022.patch` continuer à proposer DHL comme opérateur de transport

DHL a introduit la version 6.2 du schéma et va abandonner la version 6.0 dans un avenir proche. Adobe Commerce 2.4.4 et les versions antérieures qui prennent en charge l’intégration DHL ne prennent en charge que la version 6.0. Les commerçants qui déploient ces versions doivent s’appliquer `AC-3022.patch` dès leur première convenance de continuer à proposer DHL comme transporteur. Voir [Appliquez un correctif pour continuer à proposer DHL comme opérateur de transport](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Article de la base de connaissances pour plus d’informations sur le téléchargement et l’installation du correctif.

### Correctifs

Cette version inclut le correctif suivant, ainsi que tous les correctifs qui ont été publiés pour la version précédente du correctif.

* Correctif `AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch to address PHP fatal error on upgrade`. Voir [Correctif d’erreur fatale PHP de la mise à niveau Adobe Commerce 2.4.3, 2.3.7-p1](https://support.magento.com/hc/en-us/articles/4408021533069-Adobe-Commerce-upgrade-2-4-3-2-3-7-p1-PHP-Fatal-error-Hotfix) Article de la base de connaissances pour plus d’informations sur les correctifs et les problèmes.

### Mise en évidence de la sécurité

**Les ID de session ont été supprimés de la base de données.**. Ce changement de code peut entraîner des modifications rompues si les marchands disposent de personnalisations ou d’extensions installées qui utilisent les ID de session bruts stockés dans la base de données. <!-- MC-40976-->

**Accès restreint de l’administrateur aux dossiers de la galerie multimédia**. Les autorisations de galerie de médias par défaut autorisent désormais uniquement les opérations de répertoire (affichage, chargement, suppression et création) autorisées explicitement par la configuration. Les utilisateurs administrateurs ne peuvent plus accéder aux ressources multimédia par le biais de la galerie de médias qui ont été chargées en dehors de la section `catalog/category` ou `wysiwyg` répertoires. Les administrateurs qui souhaitent accéder aux ressources multimédia doivent les déplacer vers un dossier explicitement autorisé ou ajuster leurs paramètres de configuration. Voir [Modification des autorisations de dossier Media Library](https://developer.adobe.com/commerce/php/tutorials/backend/modify-image-library-permissions/). <!-- B2B-1897-->

**Limites réduites à la complexité des requêtes GraphQL**. La complexité de requête maximale autorisée par GraphQL a été réduite afin d’éviter les attaques par déni de service (DOS). Voir [Configuration de la sécurité GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/security-configuration.html). <!-- PWA-1700-->

**Vulnérabilités des tests de pénétration récents** ont été corrigés dans cette version. <!-- MC-42431-->

Expression source non prise en charge `unsafe-inline` a été supprimé de la stratégie de sécurité du contenu. `frame-ancestors` de . [GitHub-33101](https://github.com/magento/magento2/issues/33101)<!-- MC-42632-->

