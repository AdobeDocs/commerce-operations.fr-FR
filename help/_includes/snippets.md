---
source-git-commit: 1eaf2329c16e6dbe3e93cb7fff3a6920b4b8379d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---
# Extraits de code

## Commerce uniquement {#commerce-only}

>[!NOTE]
>
>[!DNL Upgrade Compatibility Tool] est disponible uniquement pour les instances Adobe Commerce.

<!-- Configuration guide snippets -->

## Propriétaire du système de fichiers {#file-system-owner}

>[!WARNING]
>
>Toutes les commandes de l’interface de ligne de commande du Magento doivent être exécutées par le [propriétaire du système de fichiers](/help/configuration/cli/config-cli.md#prerequisites).

## Commandes de sauvegarde {#tip-backup-command}

>[!TIP]
>
>La commande `support:backup` est _et non_ la même sauvegarde de code effectuée par la commande `setup:backup`. La commande `support:backup` est destinée à sauvegarder le code pour examen par le support Adobe Commerce.

## Adobe Commerce uniquement {#ee-only}

>[!NOTE]
>
>Cette fonctionnalité est disponible uniquement pour les instances Adobe Commerce.

## Fractionner la base de données obsolète {#deprecate-split-db}

>[!IMPORTANT]
>
>La fonctionnalité de base de données partagée était [obsolète](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) dans la version 2.4.2 d’Adobe Commerce. Voir [Rétablir d’une base de données partagée vers une base de données unique](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Modifications incompatibles avec l’arrière {#bics}

>[!NOTE]
>
>Les versions d’Adobe Commerce peuvent contenir des modifications incompatibles avec l’arrière-plan (BIC). Pour passer en revue les modifications incompatibles avec l’arrière-plan, voir [Référence BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). Les problèmes majeurs d’compatibilité descendante sont décrits dans la section [Mise en évidence BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). Toutes les versions n’introduisent pas de code BIC majeur.

## Avertissement CVE {#cve-notice}

>[!NOTE]
>
>À compter de la version 2.3.2, nous assignerons et publierons des numéros CVE (Vulnérabilités et expositions courantes indexées) avec chaque bogue de sécurité signalé par des tiers externes. Cela permet aux utilisateurs d’identifier plus facilement les vulnérabilités non corrigées dans leur déploiement. Vous pouvez en savoir plus sur les identifiants CVE à l’adresse [CVE](https://cve.mitre.org/).

## Autres informations de mise à jour {#other-release-info}

>[!NOTE]
>
>Bien que le code pour les améliorations et les correctifs décrits dans ces notes de mise à jour soit fourni avec Adobe Commerce, plusieurs de ces projets (par exemple, B2B, Page Builder et Progressive Web Application (PWA) Studio) sont également publiés indépendamment. Les correctifs de bogues pour ces projets sont documentés dans les informations de mise à jour distinctes et spécifiques au projet disponibles dans la documentation de chaque projet. Voir [présentation de la version du produit](/help/release/release-notes/overview.md).

## Contrôle de processus PHP {#php-process-control}

Avant de pouvoir exécuter des indexeurs en mode parallèle, vous devez activer la prise en charge du contrôle des processus (`pcntl`) en PHP. Voir [Installation](https://www.php.net/manual/en/pcntl.installation.php) dans la documentation PHP.
