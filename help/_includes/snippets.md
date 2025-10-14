---
source-git-commit: c8a20ad1b0b57724f389cfa5c63f6ae542758c2b
workflow-type: tm+mt
source-wordcount: '488'
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
>Toutes les commandes de l’interface de ligne de commande Magento doivent être exécutées par le [&#x200B; propriétaire du système de fichiers](/help/configuration/cli/config-cli.md#prerequisites).

## Commandes de sauvegarde {#tip-backup-command}

>[!TIP]
>
>La commande `support:backup` n’est _pas_ la même sauvegarde de code effectuée par la commande `setup:backup`. La commande `support:backup` est destinée à sauvegarder le code pour examen par le support Adobe Commerce.

## Correctifs B2B {#b2b-patches}

>[!NOTE]
>
>Après avoir installé ce correctif de sécurité, les commerçants B2B d’Adobe Commerce doivent également effectuer la mise à jour vers la dernière version du correctif de sécurité B2B compatible. Voir les notes de mise à jour [B2B](https://experienceleague.adobe.com/fr/docs/commerce-admin/b2b/release-notes).

## Adobe Commerce uniquement {#ee-only}

>[!NOTE]
>
>Cette fonctionnalité est disponible uniquement pour les instances Adobe Commerce.

## Fractionner la base de données obsolète {#deprecate-split-db}

>[!IMPORTANT]
>
>La fonctionnalité de base de données partagée était [obsolète](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) dans la version 2.4.2 d’Adobe Commerce. Voir [Rétablir une base de données fractionnée en une seule base de données](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Modifications non rétrocompatibles {#bics}

>[!NOTE]
>
>Les versions d’Adobe Commerce peuvent contenir des modifications non rétrocompatibles (BIC). Pour vérifier les modifications non rétrocompatibles, voir [Référence BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). Les principaux problèmes de rétrocompatibilité sont décrits dans [points forts du BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/). Toutes les versions n’introduisent pas de BIC majeurs.

## Clause de non-responsabilité d’Alpha {#alpha}

>[!IMPORTANT]
>
>Les versions d’[Alpha](/help/release/versioning-policy.md#alpha-patch-release) peuvent être incomplètes et risquent de contenir des défauts. Ils sont fournis « EN L&#39;ÉTAT » sans garantie d&#39;aucune sorte. Adobe n’a aucune obligation de tenir à jour, corriger, mettre à jour, modifier, remplacer ou prendre en charge d’une autre manière (via les services d’assistance Adobe ou autre) les versions d’Alpha. Les clients ne doivent pas s’appuyer sur le bon fonctionnement ou les performances des versions d’Alpha ou de toute documentation ou documentation d’accompagnement. L’utilisation des versions d’Alpha s’effectue entièrement aux risques et périls du client.

## Clause de non-responsabilité Beta {#beta}

>[!IMPORTANT]
>
>Les versions de Beta peuvent contenir des défauts et sont fournies « EN L’ÉTAT » sans garantie d’aucune sorte. Adobe n’a aucune obligation de tenir à jour, corriger, mettre à jour, modifier, remplacer ou prendre en charge (à partir des services d’assistance Adobe ou de tout autre service) les versions bêta. Les clients doivent faire preuve de prudence et ne pas se fier, de quelque manière que ce soit, au bon fonctionnement ou aux performances des versions bêta et/ou de la documentation ou du matériel les accompagnant. Par conséquent, toute utilisation des versions bêta s’effectue entièrement aux risques et périls du client.

## Avis CVE {#cve-notice}

>[!NOTE]
>
>À compter de la version 2.3.2, nous attribuerons et publierons des numéros CVE (Common Vulnerabilities and Expositions) indexés avec chaque bogue de sécurité qui nous est signalé par des tiers externes. Cela permet aux utilisateurs et utilisatrices d’identifier plus facilement les vulnérabilités non corrigées dans leur déploiement. Pour en savoir plus sur les identifiants CVE, voir [CVE](https://cve.mitre.org/).

## Autres informations de mise à jour {#other-release-info}

>[!NOTE]
>
>Bien que le code pour les améliorations et correctifs de bugs décrit dans ces notes de mise à jour soit fourni avec Adobe Commerce, plusieurs de ces projets (par exemple, B2B, Page Builder et Progressive Web Applications (PWA) Studio) sont également publiés indépendamment. Les correctifs de bugs pour ces projets sont documentés dans les informations de mise à jour distinctes spécifiques au projet disponibles dans la documentation de chaque projet. Voir [présentation de la version du produit](/help/release/release-notes/overview.md).

## Contrôle de processus PHP {#php-process-control}

Avant de pouvoir exécuter des indexeurs en mode parallèle, vous devez activer la prise en charge de Process Control (`pcntl`) en PHP. Voir [Installation](https://www.php.net/manual/en/pcntl.installation.php) dans la documentation PHP.

## Correctifs personnalisés {#custom-patches-disclaimer}

>[!IMPORTANT]
>
>Adobe ne prend pas en charge l’application de correctifs officiels fournis par Adobe à l’aide de cette méthode. Utilisez la méthode suivante à vos risques et périls. Pour appliquer les correctifs officiels, utilisez le [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr){target="_blank"} . Effectuez toujours des tests complets avant de déployer un correctif personnalisé.
