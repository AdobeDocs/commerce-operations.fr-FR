---
source-git-commit: 20add0a748e8df38dff48a779c63e1177d2a022d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---
# Extraits de code

## Commerce uniquement {#commerce-only}

>[!NOTE]
>
>La variable [!DNL Upgrade Compatibility Tool] est disponible uniquement pour les instances Adobe Commerce.

<!-- Configuration guide snippets -->

## Propriétaire du système de fichiers {#file-system-owner}

>[!WARNING]
>
>Toutes les commandes de l’interface de ligne de commande du Magento doivent être exécutées par la fonction [propriétaire du système de fichiers](/help/configuration/cli/config-cli.md#prerequisites).

## Commandes de sauvegarde {#tip-backup-command}

>[!TIP]
>
>La variable `support:backup` command is _not_ la même sauvegarde de code effectuée par la fonction `setup:backup` . La variable `support:backup` est destinée à sauvegarder le code pour examen par le support Adobe Commerce.

## Adobe Commerce uniquement {#ee-only}

>[!NOTE]
>
>Cette fonctionnalité est disponible uniquement pour les instances Adobe Commerce.

## Fractionner la base de données obsolète {#deprecate-split-db}

>[!IMPORTANT]
>
>La fonctionnalité de base de données partagée était [obsolète](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) dans la version 2.4.2 d’Adobe Commerce. Voir [Rétablissement d’une base de données partagée en une seule base de données](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Modifications incompatibles avec l’arrière {#bics}

>[!NOTE]
>
>Les versions d’Adobe Commerce et de Magento Open Source peuvent contenir des modifications incompatibles avec le passé (BIC). Pour examiner les modifications incompatibles avec l’arrière-plan, voir [Référence BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). Les principaux problèmes incompatibles avec le passé sont décrits dans la section [Faits saillants de la BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). Toutes les versions n’introduisent pas de code BIC majeur.

## Avertissement CVE {#cve-notice}

>[!NOTE]
>
>À compter de la version 2.3.2, nous assignerons et publierons des numéros CVE (Vulnérabilités et expositions courantes indexées) avec chaque bogue de sécurité signalé par des tiers externes. Cela permet aux utilisateurs d’identifier plus facilement les vulnérabilités non corrigées dans leur déploiement. Pour en savoir plus sur les identifiants CVE, voir [CVE](https://cve.mitre.org/).

## Autres informations de mise à jour {#other-release-info}

>[!NOTE]
>
>Bien que le code pour les améliorations et les correctifs décrits dans ces notes de mise à jour soit fourni avec Adobe Commerce, plusieurs de ces projets (par exemple, B2B, Page Builder et Progressive Web Application (PWA) Studio) sont également publiés indépendamment. Les correctifs de bogues pour ces projets sont documentés dans les informations de mise à jour distinctes et spécifiques au projet disponibles dans la documentation de chaque projet. Voir [présentation de la version des produits](/help/release/release-notes/overview.md).
