---
source-git-commit: 74cb55f4552bc1b2dace37d9a6f7e68939d1c262
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---
# Fragments de code

## Commerce uniquement {#commerce-only}

>[!NOTE]
>
>Le [!DNL Upgrade Compatibility Tool] est disponible uniquement pour les instances Adobe Commerce.

<!-- Configuration guide snippets -->

## Propriétaire du système de fichiers {#file-system-owner}

>[!WARNING]
>
>Toutes les commandes de l’interface de ligne de commande du Magento doivent être exécutées par la fonction [propriétaire du système de fichiers](/help/configuration/cli/config-cli.md#prerequisites).

## Commandes de sauvegarde {#tip-backup-command}

>[!TIP]
>
>Le `support:backup` command is _not_ la même sauvegarde de code effectuée par la fonction `setup:backup` . Le `support:backup` est destinée à sauvegarder le code pour examen par l’assistance d’Adobe Commerce.

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

## Avis CVE {#cve-notice}

>[!NOTE]
>
>À compter de la version 2.3.2, nous assignerons et publierons des numéros CVE (Vulnérabilités et expositions courantes indexées) avec chaque bogue de sécurité signalé par des tiers externes. Cela permet aux utilisateurs d’identifier plus facilement les vulnérabilités non corrigées dans leur déploiement. Pour en savoir plus sur les identifiants CVE, voir [CVE](https://cve.mitre.org/).
