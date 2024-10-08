---
source-git-commit: ab3401c2629b550655c7b2a382b998ce2c8ac6f0
workflow-type: tm+mt
source-wordcount: '377'
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

## Correctifs B2B {#b2b-patches}

>[!NOTE]
>
>Après avoir installé ce correctif de sécurité, les marchands Adobe Commerce B2B doivent également effectuer une mise à jour vers la dernière version de correctif de sécurité B2B compatible. Voir les [notes de mise à jour B2B](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes).

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

## Clause de non-responsabilité Beta {#beta}

>[!IMPORTANT]
>
>Les versions de Beta peuvent contenir des défauts et sont fournies &quot;EN L’ÉTAT&quot; sans aucune garantie de quelque type que ce soit. Adobe n’a aucune obligation de gérer, corriger, mettre à jour, modifier, modifier ou d’autre manière prendre en charge (depuis les services d’assistance d’Adobe ou tout autre service) les versions bêta. Les clients doivent faire preuve de prudence et ne pas se fier de quelque manière que ce soit au bon fonctionnement ou aux performances correctes des versions bêta et/ou de toute documentation ou matériel connexe. Par conséquent, toute utilisation des versions bêta est entièrement à la charge du client.

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
