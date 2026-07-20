---
source-git-commit: d8197ca0e1028cb50fae0415843c80ac68e49566
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 0%

---
# Fragments de code

## Remarque sur la configuration du cache de Commerce on Cloud avec référence {#cloud-cache-config}

>[!NOTE]
>
>Pour les projets Adobe Commerce on Cloud, consultez [Bonnes pratiques relatives à la configuration du service Redis and Valkey](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration) pour obtenir des instructions sur la configuration du cache.

## Prise en charge du cache Redis {#redis-cache-support}

Le cache Redis n’est pas pris en charge pour Adobe Commerce 2.4.9 ou pour les versions de correctif ultérieures à 2.4.5-p16, 2.4.6-p14, 2.4.7-p9 et 2.4.8-p5. Si vous effectuez une mise à niveau vers une version qui ne prend pas en charge Redis, vous devez configurer Valkey et mettre à jour la configuration du cache pour l’utiliser. Pour les déploiements sur site, voir [Configuration de Valkey](/help/configuration/cache/config-valkey.md).

## Note de configuration de Commerce sur le vernis cloud avec référence {#varnish-config-cloud}

>[!NOTE]
>
>Si votre projet Commerce est déployé sur le cloud, la mise en cache complète des pages utilise [Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) au lieu de Varnish. Les rubriques de cette section s’appliquent uniquement aux installations sur site.

## Prise en charge des versions du service Adobe {#supported-versions-only}

>[!NOTE]
>
>Adobe ne prend en charge que les déploiements exécutant des versions prises en charge de tous les services et dépendances. Cela s’applique :
>
>* **Services Platform** (y compris, mais sans s’y limiter, PHP, MariaDB/MySQL, Redis, Elasticsearch/OpenSearch, RabbitMQ et Nginx) - les commerçants doivent conserver des versions compatibles avec leur version d’Adobe Commerce déployée. Voir [Configuration requise](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html).
>* **Extensions des services** (y compris, mais sans s’y limiter, Live Search, Product Recommendations et Payment Services) — seule la dernière version publiée est prise en charge.
>* **Extensions personnalisées et intégrations tierces** — Les commerçants sont chargés de s’assurer qu’elles restent sur les versions prises en charge par le fournisseur.
>
>L’exécution de versions non prises en charge peut exposer votre boutique à des vulnérabilités en matière de sécurité. Par ailleurs, Adobe ne peut pas fournir de correctifs de sécurité pour les dépendances qui ne sont plus gérées par leurs fournisseurs.
>
>Pour obtenir la liste complète des versions prises en charge, consultez la [matrice de disponibilité des produits](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

## Correctifs de sécurité pour une prise en charge étendue {#extended-support}

{{$include /help/_includes/release-notes/extended-support-policy-note.md}}

## Commerce uniquement {#commerce-only}

>[!NOTE]
>
>Le [!DNL Upgrade Compatibility Tool] est disponible uniquement pour les instances Adobe Commerce.

<!-- Configuration guide snippets -->

## Propriétaire du système de fichiers {#file-system-owner}

>[!WARNING]
>
>Toutes les commandes de l’interface de ligne de commande Magento doivent être exécutées par le [ propriétaire du système de fichiers](/help/configuration/cli/config-cli.md#prerequisites).

## Commandes de sauvegarde {#tip-backup-command}

>[!TIP]
>
>La commande `support:backup` n’est _pas_ la même sauvegarde de code effectuée par la commande `setup:backup`. La commande `support:backup` est destinée à sauvegarder le code pour examen par le support Adobe Commerce.

## Correctifs B2B {#b2b-patches}

>[!NOTE]
>
>Après avoir installé ce correctif de sécurité, les commerçants B2B d’Adobe Commerce doivent également effectuer la mise à jour vers la dernière version du correctif de sécurité B2B compatible. Voir les notes de mise à jour [B2B](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes).

## Adobe Commerce uniquement {#ee-only}

>[!NOTE]
>
>Cette fonctionnalité est disponible uniquement pour les instances Adobe Commerce.

## Fractionner la base de données obsolète {#deprecate-split-db}

>[!IMPORTANT]
>
>La fonctionnalité de base de données partagée a été abandonnée dans la version 2.4.2 d’Adobe Commerce. Voir [Rétablir une base de données fractionnée en une seule base de données](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Modifications non rétrocompatibles {#bics}

>[!NOTE]
>
>Les versions d’Adobe Commerce peuvent contenir des modifications non rétrocompatibles (BIC). Pour vérifier les modifications non rétrocompatibles, voir [Référence BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). Les principaux problèmes de rétrocompatibilité sont décrits dans [points forts du BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/). Toutes les versions n’introduisent pas de BIC majeurs.

## Clause de non-responsabilité d’Alpha {#alpha}

>[!IMPORTANT]
>
>Les versions d’[](/help/release/versioning-policy.md#alpha-patch-release) peuvent être incomplètes et risquent de contenir des défauts. Ils sont fournis « EN L&#39;ÉTAT » sans garantie d&#39;aucune sorte. Adobe n’a aucune obligation de tenir à jour, corriger, mettre à jour, modifier, remplacer ou prendre en charge d’une autre manière (via les services d’assistance Adobe ou autre) les versions d’Alpha. Les clients ne doivent pas s’appuyer sur le bon fonctionnement ou les performances des versions d’Alpha ou de toute documentation ou documentation d’accompagnement. L’utilisation des versions d’Alpha s’effectue entièrement aux risques et périls du client.

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
>Adobe ne prend pas en charge l’application de correctifs officiels fournis par Adobe à l’aide de cette méthode. Utilisez la méthode suivante à vos risques et périls. Pour appliquer les correctifs officiels, utilisez le [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"} . Effectuez toujours des tests complets avant de déployer un correctif personnalisé.

## Rétroportages de correctif de sécurité d’octobre 2025 {#oct-2025-backports}

<!--These fixes were backported to 2.4.8-pe, 2.4.7-p8, and 2.4.6-p13-->

* **Migration de TinyMCE vers Hugerte.org**

  En raison de la fin de la prise en charge de TinyMCE 5 et 6 et des incompatibilités de licence avec TinyMCE 7, l’implémentation actuelle de l’éditeur WYSIWYG d’Adobe Commerce est migrée de TinyMCE vers l’éditeur open source [HugeRTE editor](https://hugerte.org/).

  Cette migration garantit qu’Adobe Commerce reste conforme aux licences open source, évite les vulnérabilités connues de TinyMCE 6 et offre une expérience de modification moderne et prise en charge pour les commerçants et les développeurs.

* **Ajout de la prise en charge du protocole STOMP d’artémis Apache ActiveMQ**

  Ajout de la prise en charge du courtier de messages open source ActiveMQ Artemis via le protocole STOMP (Simple Text Oriented Messaging Protocol). Il fournit un système de messagerie fiable et évolutif, offrant une flexibilité pour les intégrations STOMP. Voir [Apache ActiveMQ Artemis](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework#apache-activemq-artemis-stomp) dans le Guide de configuration de Commerce **.

## La page d’extraction ne parvient pas à charger static.min.js et mixins.min.js. {#checkout-page-fails-to-load-static-min-js-and-mixins-min-js}

Après les récentes modifications apportées à CSP/SRI, la page de passage en caisse ne charge pas static.min.js et mixins.min.js lorsque le regroupement et la minimisation JavaScript sont tous deux activés en mode de production. Par conséquent, les mixins RequireJS ne s’exécutent pas et les modèles d’exclusion de passage en caisse ne sont pas résolus (par exemple, `"Failed to load the 'Magento_Checkout/shipping' template requested by 'checkout.steps.shipping-step.shippingAddress'"`).

**Solution** :

* Désactivez le regroupement JavaScript ; ou
* Si vous laissez le regroupement JavaScript activé, désactivez la minimisation de JavaScript.

>[!IMPORTANT]
>
>Ne désactivez pas CSP et ne supprimez pas les protections SRI en production. Tout contournement au niveau du plug-in ne doit être utilisé qu’en dernier recours pour un correctif et doit être examiné par l’équipe de sécurité.

**Correctif** :

Un correctif est disponible. Pour plus d’informations sur les correctifs](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27997) consultez la section [L’extraction échoue lorsque la minimisation et le regroupement JS sont activés dans la base de connaissances.

## Valkey Redis CLI note {#valkey-redis-cli-note}

>[!NOTE]
>
>À partir d’Adobe Commerce 2.4.9, Valkey a officiellement remplacé Redis dans l’outil d’interface de ligne de commande. Pour les **versions 2.4.8 et antérieures**, utilisez les commandes équivalentes [Redis CLI](/help/configuration/cache/config-redis.md#set-up-redis-configuration).

