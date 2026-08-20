---
title: Actions et délais requis pour sécuriser les environnements Commerce
description: Découvrez l’application de la sécurité pour les versions d’Adobe Commerce on Cloud non prises en charge et les dépendances logicielles, y compris les échéances, les actions requises et les risques.
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: c32adafa-ed01-4b31-997e-2413013911b0id: cc250cf1-34eb-4863-80d0-d170d45ea067id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: dac87252-6066-4d6e-a9d2-f6d84c323de7
subfeature_v2: id: f2261633-201d-46c5-8a66-999e70527a83
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: d378ca77-2da1-4f39-ad92-1917fe974a38
badgePaas: label="Adobe Commerce on Cloud 2.4.4 - 2.4.9 uniquement" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement à Adobe Commerce sur Cloud versions 2.4.4 à 2.4.9"
nudge: true
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: 2158
ht-degree: 0%

---


# Actions et délais requis pour sécuriser les environnements Commerce

>[!NOTE]
>
> **S’applique aux :** environnements Adobe Commerce on Cloud (PaaS) exécutant les versions 2.4.4 à 2.4.9 d’Adobe Commerce.

Le paysage de la cybersécurité évolue fondamentalement, et les mécanismes de défense mis en place par les entreprises doivent évoluer rapidement. La sécurité est essentielle pour les entreprises de commerce électronique, car les transactions en ligne exigent qu&#39;elles traitent des données personnelles et commerciales sensibles, les exposant ainsi à des risques financiers et d&#39;identité en cas de violation. Les environnements de commerce électronique PaaS ont un modèle de responsabilité partagée où le client est responsable de la sécurité et de la maintenance des dépendances de la couche d’application, des intégrations à des logiciels tiers et des pipelines de déploiement.

Chez Adobe, nous restons déterminés à gérer l’évolution des risques et à nous assurer que nous configurons nos clients Adobe Commerce sur Cloud selon les normes de sécurité les plus élevées. Cela inclut :

1. Correctifs de sécurité isolés mensuels pour une protection plus rapide et prévisible contre les vulnérabilités critiques

2. Correctifs cloud pour le package Commerce afin de garantir la diffusion de correctifs Adobe et de correctifs logiciels qui améliorent l’intégration aux environnements cloud et permettent de résoudre rapidement les problèmes critiques

3. Politiques d’application du cycle de vie

4. Correctifs hors cycle, si nécessaire

5. Versions annuelles des correctifs avec prise en charge à long terme


Alors qu’Adobe prend les mesures nécessaires pour assurer la sécurité de ses clients, le modèle de responsabilité partagée pour Adobe Commerce sur le cloud exige que ses clients disposent toujours d’une version prise en charge d’Adobe Commerce sur le cloud et de logiciels tiers, appliquent des correctifs d’application, auditent les extensions tierces et sécurisent le code personnalisé. Les logiciels qui ont dépassé la fin de la prise en charge par les fournisseurs ne reçoivent plus de correctifs de sécurité, ce qui laisse les problèmes de sécurité dans le logiciel sans solution. Continuer à exécuter votre storefront e-commerce sur des logiciels non pris en charge crée un risque de sécurité réel et croissant.

Cette page décrit les actions que tous les clients et clientes d’Adobe Commerce on Cloud (versions 2.4.4 à 2.4.9) doivent entreprendre pour s’assurer que leur environnement d’e-commerce reste sécurisé, ainsi que les dates d’application et ce à quoi s’attendre lorsque les exigences de sécurité ne sont pas remplies.

## Actions requises pour maintenir un environnement sécurisé et conforme

Pour garantir la sécurité de votre environnement e-commerce et atténuer les risques, tous les clients d’Adobe Commerce on Cloud (versions 2.4.4 à 2.4.9) doivent utiliser :

1. Versions prises en charge de toutes les dépendances logicielles tierces (PHP, MariaDB, Elasticsearch, OpenSearch, Redis, RabbitMQ)

1. Une version sécurisée et prise en charge d’Adobe Commerce sur le cloud. Les versions entièrement prises en charge sont les versions 2.4.8 et 2.4.9, ou la dernière version disponible. Voir la documentation [Politique de cycle de vie](/help/release/lifecycle-policy.md).

Suivez les instructions ci-dessous pour vérifier si vous devez prendre des mesures pour sécuriser votre environnement Adobe Commerce sur le cloud. Dans les environnements qui ne respectent pas les exigences de sécurité dans les délais indiqués dans le tableau 1 ci-dessous, le trafic entrant sera suspendu, ce qui mettra le storefront hors ligne. Si vous avez des doutes quant au respect de l’échéance, veuillez contacter votre équipe de compte ou [l’assistance ](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket) dès que possible.

>[!NOTE]
>
> Ces conseils ne s’appliquent pas aux environnements [!DNL Adobe Commerce as a Cloud Service] (SaaS) ni aux déploiements sur site d’Adobe Commerce.

**Tableau 1 : Exigences de sécurité et délais**

| Votre version d’Adobe Commerce on Cloud | Mise à niveau vers les dépendances de logiciels tiers prises en charge | Effectuez une mise à niveau vers la dernière version d’Adobe Commerce on Cloud ou migrez vers [!DNL Adobe Commerce as a Cloud Service] |
| --- | --- | --- |
| 2.4.4 ou 2.4.5 | Requis avant le 30 octobre 2026. | Requis pour le 1er juin 2027 |
| 2.4.6 ou 2.4.7 | Requis avant le 30 octobre 2026 ou le 31 mai 2027, selon le logiciel. | Requis pour le 1er juin 2028 |
| 2.4.8 ou 2.4.9 | Requis avant le 30 octobre 2026 ou le 31 mai 2027, selon le logiciel. | Non requis pour le moment |

## Étapes détaillées pour sécuriser votre environnement

Contactez votre administrateur Commerce pour qu’il effectue les étapes suivantes.

### Action 1 : vérification et mise à niveau des dépendances logicielles tierces

Vérifiez que votre environnement exécute des versions prises en charge par des fournisseurs des dépendances logicielles tierces suivantes : PHP, MariaDB, Elasticsearch, OpenSearch, Redis, RabbitMQ. Dans le cas contraire, mettez à niveau la dépendance logicielle vers une version prise en charge.

#### Étape 1 : vérifier les versions de dépendance de logiciels tiers

1. Connectez-vous à la [console cloud](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/start/cloud-console) où vous pouvez voir tous vos projets cloud.
2. Ouvrez le projet approprié, puis sélectionnez l’environnement à réviser.
3. Ouvrez l’onglet « Conteneurs » où vous pouvez voir la liste de tous les services actuellement utilisés dans l’environnement sélectionné.
4. Cliquez sur chaque lien de service pour vérifier la version exacte en cours d’exécution dans l’environnement.
Pour plus d’informations, consultez les instructions de la section [Configurer les services](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml).

Toutes les dépendances logicielles non prises en charge doivent être mises à niveau vers les versions indiquées dans les délais indiqués dans le tableau 2 ci-dessous.

**Tableau 2 : mises à niveau des dépendances requises**

| Dépendance | Version | Doit mettre à niveau vers | Deadline |
| --- | --- | --- | --- |
| PHP | 8.1 et versions ultérieures | 8.2 ou version ultérieure | 31 Mai 2027 |
| MariaDB/Galera | 10.5 et versions ultérieures | 10.6 ou version ultérieure | 30 Octobre 2026 |
| MariaDB/Galera | Supérieur à 10,5 mais inférieur à 10,11 | 10.11 ou version ultérieure | 31 Mai 2027 |
| Elasticsearch | n’importe quelle version | OpenSearch : version 2.19 pour les clients 2.4.4 et 2.4.5. Version 3 pour les clients disposant de la version 2.4.6 ou ultérieure. | 30 Octobre 2026 |
| OpenSearch | 1.x | Version 2.19 pour les clients des versions 2.4.4 et 2.4.5. Version 3 pour les clients disposant de la version 2.4.6 ou ultérieure. | 31 Mai 2027 |
| Redis | 5 et moins | Valkey version 8 ou ultérieure | 31 Mai 2027 |
| RabbitMQ | 3.9 et versions ultérieures | Version 3.13 ou ultérieure | 30 Octobre 2026 |
| RabbitMQ | Supérieur à 3,9 mais inférieur à 3,13 | 4.3 ou version ultérieure | 31 Mai 2027 |

#### Étape 2 : préparation à une mise à niveau de dépendance logicielle tierce

Adobe vous aidera à mettre à niveau directement ces dépendances logicielles.

* **Prise en main :** ouvrez un [ticket d’assistance](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case) répertoriant les environnements à mettre à niveau et les dépendances impliquées. Ouvrez votre ticket au moins 30 jours avant la date d’application afin qu’Adobe puisse planifier le travail.

* **Temps d’arrêt :** Adobe vous confirmera la fenêtre attendue lors de la planification.

* **Tests :** mettre à niveau et valider un environnement hors production avant la production. Validez au minimum le passage en caisse, la recherche, le panier et toutes les intégrations personnalisées. Les exigences s’appliquent à tous vos environnements. Prévoyez donc de mettre à niveau chaque environnement plutôt que de vous concentrer uniquement sur la production.

* **Compatibilité :** la plupart de ces modifications sont des mises à niveau de version au sein du même logiciel et comportent peu de risques. Les changements suivants méritent une attention particulière :

  * **Elasticsearch vers OpenSearch** et **Redis vers Valkey** sont des migrations vers différents logiciels plutôt que des mises à niveau de version. Le code personnalisé, les extensions ou la configuration faisant référence au service d’origine peuvent nécessiter une mise à jour.
  * La mise à niveau de **PHP 8.1 vers 8.2** peut faire apparaître des éléments obsolètes dans le code personnalisé et les extensions tierces.

Si vous utilisez des extensions tierces, vérifiez auprès de vos fournisseurs que leurs versions actuelles prennent en charge vos versions cibles. Si vous travaillez avec un intégrateur de solutions, associez-le à la planification et à la validation.

### Action 2 : vérifiez votre version d’Adobe Commerce on Cloud et effectuez la mise à niveau vers une version prise en charge

#### Étape 1 : vérifier la version d’Adobe Commerce on Cloud et l’action requise

1. Connectez-vous au panneau d’administration d’Adobe Commerce.

   La version actuelle s’affiche dans le coin inférieur droit de toute page d’administration.

1. Si la version est masquée dans le panneau d’administration, utilisez l’Adobe Commerce [outil de ligne de commande](../configuration/cli/config-cli.md) pour afficher la version en exécutant la commande suivante :

   ```shell
   bin/magento --version
   ```

Vérifiez les actions requises pour votre version d’Adobe Commerce dans le tableau ci-dessous.

**Tableau 3 : exigences de mise à niveau de la version d’Adobe Commerce on Cloud**

| Version actuelle d’Adobe Commerce sur le cloud | Action requise | Deadline |
| --- |--- |--- |
| Version 2.4.4 ou 2.4.5 | Effectuez la mise à niveau vers Adobe Commerce sur Cloud version 2.4.9 (ou la dernière version) ou migrez vers [!DNL Adobe Commerce as a Cloud Service].<br>Raison : les versions 2.4.4 et 2.4.5 ne recevront que des correctifs de sécurité limités et isolés pour l’application principale jusqu’au 31 mai 2027. Cela n’inclut pas les correctifs de qualité, la prise en charge de la compatibilité pour les dépendances d’applications (par exemple, PHP) ni les mises à jour des dépendances de plateformes. Voir Adobe [ Politique de cycle de vie ](/help/release/lifecycle-policy.md). | 1er juin 2027 |
| Version 2.4.6 ou 2.4.7 | Mise à niveau vers Adobe Commerce sur Cloud version 2.4.9 (ou la dernière version) ou migration vers [!DNL Adobe Commerce as a Cloud Service].<br>Raison : la version 2.4.6 bénéficiera d’une prise en charge étendue jusqu’au 30 août 2027 et ne recevra que des correctifs de sécurité limités et isolés pour l’application principale jusqu’au 31 mai 2028. La version 2.4.7 recevra une prise en charge standard jusqu’au 31 mai 2027 et une prise en charge étendue jusqu’au 31 mai 2028. Voir Adobe [ Politique de cycle de vie ](/help/release/lifecycle-policy.md). | 1er juin 2028 |
| Version 2.4.8 ou 2.4.9 | Aucune action de mise à niveau de la version d’Adobe Commerce on Cloud n’est nécessaire. Les dates limites de dépendance vis-à-vis des logiciels tiers de l’action 1 s’appliquent toujours.<br>Motif : aucune date limite n’a été fixée. | Sans objet |

#### Étape 2 : déterminer le chemin de mise à niveau ou de migration

Si vous devez mettre à niveau votre version d’Adobe Commerce on Cloud, vous disposez de deux options :

1. Mise à niveau vers une version d’Adobe Commerce on Cloud prise en charge
1. Migration vers [!DNL Adobe Commerce as a Cloud Service] (SaaS)

Le tableau suivant vous aide à comparer vos options et à déterminer le meilleur chemin pour vous.

**Tableau 4 : comparaison d’Adobe Commerce sur le cloud et[!DNL Adobe Commerce as a Cloud Service]**

| | Adobe Commerce on Cloud version 2.4.9 | [!DNL Adobe Commerce as a Cloud Service] |
|---|---|---|
| **Ce que c’est** | La dernière version d’Adobe Commerce avec une couverture de sécurité complète, des correctifs de qualité et des mises à jour des dépendances de plateforme. | Plateforme commerciale entièrement gérée par Adobe, conçue pour une innovation continue sans frais de mise à niveau. [En savoir plus](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview). |
| **Idéal pour vous si** | Vous souhaitez continuer à gérer votre propre infrastructure, vos mises à niveau et vos correctifs. | Vous souhaitez laisser de côté les cycles de mise à niveau pour de bon, réduire votre coût total de possession et obtenir automatiquement les nouvelles fonctionnalités d’Adobe, sans effort supplémentaire. |
| **Avantage clé** | Répond aux exigences de sécurité tout en préservant votre configuration existante. | Une vitrine ultrarapide et performante, un catalogue hautement évolutif, une gestion native des ressources numériques et une IA générative intégrée, le tout sur une infrastructure gérée par Adobe. |

## Que se passera-t-il si aucune mesure n&#39;est prise dans le délai imparti ?

Adobe reste engagé à vous aider à exécuter les étapes que vous devez suivre pour adopter une version prise en charge d’un logiciel tiers, effectuer une mise à niveau vers la dernière version d’Adobe Commerce sur le cloud ou migrer vers Adobe Commerce as a Cloud Service.  Si vous avez des doutes quant au respect de l’échéance et si vous avez besoin d’une courte prolongation, veuillez contacter votre équipe de compte ou [l’assistance ](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket) dès que possible.

Si un environnement ne répond pas aux exigences de sécurité aux dates d’application partagées ci-dessus, Adobe sera forcé de prendre les mesures appropriées pour maintenir la sécurité de la plateforme Adobe Commerce et de ses clients. Cela inclut la suspension du trafic vers l’infrastructure affectée, et par conséquent votre storefront Commerce sera hors ligne.

Si un environnement reste non conforme à la suite de la suspension du trafic, Adobe peut mettre fin aux services cloud et lancer le processus de désaffectation. Après la mise hors service, toutes les données et ressources de l’environnement commercial hébergé, y compris toutes les instances, tous les environnements et toutes les branches, seront définitivement supprimés et ne pourront pas être restaurés.

## Ressources pour vous aider lors des mises à niveau ou de la migration

**Si vous choisissez d’effectuer une mise à niveau vers Adobe Commerce sur le cloud version 2.4.9:**

* **Rapport de compatibilité de mise à niveau :** Adobe fournit un rapport détaillé identifiant exactement ce que nécessite votre mise à niveau vers Adobe Commerce version 2.4.9, y compris l’identification des modules et fichiers nécessitant des mises à jour, le nombre de problèmes critiques, etc. Consultez la documentation [Outil d’analyse à l’échelle du site](/help/tools/site-wide-analysis-tool/access.md) pour plus d’informations sur la génération de votre rapport de compatibilité de mise à niveau.

* **Mise à niveau des dépendances logicielles :** comme vous ne pouvez pas mettre à niveau directement les dépendances logicielles, ouvrez un [ticket d’assistance](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case) afin qu’Adobe gère la mise à niveau pour vous. Pour plus d’informations, voir [Configuration des services](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml).

**Si vous choisissez de migrer vers [!DNL Adobe Commerce as a Cloud Service]:**

Adobe fournit des outils qui réduisent le coût et le temps de migration vers [!DNL Adobe Commerce as a Cloud Service]. Ils sont disponibles gratuitement. Ces outils s’appliquent uniquement à la migration. Ils ne sont pas utilisés pour les mises à niveau de version d’Adobe Commerce on Cloud. Consultez la [présentation de la migration](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/overview) pour obtenir un guide de migration complet, y compris les chemins et les phases de migration.

* **Évaluation de la migration :** évalue la complexité de migration de vos personnalisations. Consultez la [ Présentation de l’outil d’évaluation de la migration ](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/assessment).

* **Migration des données :** l’outil [migration de données en bloc et incrémentielle](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/bulk-data/migration-tool) déplace vos données vers votre nouvel environnement [!DNL Adobe Commerce as a Cloud Service]. Pour y accéder, contactez l’assistance technique d’Adobe [](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket).

* **Migration et outils de développement assistés par l’IA :** le storefront Adobe Developer App Builder et Commerce optimisé par Edge Delivery Services permet d’accélérer la modernisation du storefront et la reconfiguration des extensions.

Pour toute question, contactez l’équipe chargée de votre compte ou les [services d’assistance](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket).

>[!MORELIKETHIS]
>
>* [ Politique relative au cycle de vie ](lifecycle-policy.md)
>* [Politique d’application de la mise à niveau de version pour Adobe Commerce on Cloud](version-upgrade-enforcement-policy.md)
>* [Sécurité de responsabilité partagée et modèle opérationnel](../security-and-compliance/shared-responsibility.md)
