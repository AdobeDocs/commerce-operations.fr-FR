---
title: 'Politique de sécurité : actions et délais requis'
description: Découvrez l’application de la sécurité pour les versions d’Adobe Commerce on Cloud non prises en charge et les dépendances logicielles, y compris les échéances, les actions requises et les risques.
TQID: 'https://experienceleague.adobe.com/0JX-Z-dRjsiQk5jO-LLRi-J4GWdylTh4pOfXRPOabxs'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: c32adafa-ed01-4b31-997e-2413013911b0
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
subfeature_v2:
  - id: f2261633-201d-46c5-8a66-999e70527a83
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
badgePaas: label="Adobe Commerce on Cloud uniquement" type="Informative" url="https://experienceleague.adobe.com/fr/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement à Adobe Commerce on Cloud version 2.4.4 - 2.4.9"
hide: true
source-git-commit: 0bc5d38693008f2203fe496773aa90c0418d566e
workflow-type: tm+mt
source-wordcount: 1983
ht-degree: 0%

---

# Politique de sécurité : actions requises et délais

Adobe applique les exigences de sécurité pour Adobe Commerce sur les environnements cloud, y compris les versions de dépendance logicielle prises en charge et les versions Adobe Commerce prises en charge. Cette page décrit ce qui est requis, les dates d’application et ce qui se passe si les exigences ne sont pas remplies.

## Que se passe-t-il ?

La politique de sécurité d’entreprise d’Adobe exige que tous les environnements hébergés par Adobe pour Adobe Commerce sur le cloud s’exécutent sur des logiciels sécurisés et conformes, notamment les éléments suivants :

1. Versions prises en charge de toutes les dépendances logicielles tierces (PHP, MariaDB, Elasticsearch/OpenSearch, Redis, RabbitMQ)

1. Une version sécurisée et conforme d’Adobe Commerce on Cloud (version 2.4.8, 2.4.9 ou version la plus récente)

Cela permet de réduire les risques de sécurité pour vos environnements d’e-commerce. Le trafic entrant sera suspendu pour les environnements qui ne respectent pas ces exigences dans les délais indiqués dans le [Tableau 1](#determine-your-required-actions), ce qui mettra le storefront hors ligne. Considérez cette notification comme une exigence de sécurité et de conformité avec des dates d’application.

Il se peut que vous deviez prendre deux mesures.

1. Vérifiez si les dépendances de logiciels tiers sont prises en charge. Dans le cas contraire, effectuez la mise à niveau vers une version prise en charge.

1. Vérifiez si vous devez mettre à niveau votre Adobe Commerce on Cloud vers une version prise en charge.

Recherchez votre version d’Adobe Commerce sur le cloud ci-dessous pour voir ce qui est requis de votre part et consultez les exigences relatives aux éléments suivants :

1. Dépendances de logiciels tiers

1. Version d’Adobe Commerce on Cloud

| Votre version | Mettez à niveau les dépendances de logiciels tiers<br>(PHP, MariaDB, Elasticsearch/OpenSearch, Redis, RabbitMQ)<br>*Voir [Action 1 : Mettre à niveau les dépendances de logiciels tiers](#action-1-upgrade-third-party-software-dependencies) pour plus d’informations et connaître les étapes suivantes.* | Mettez à niveau ou migrez votre version d’<br>*voir [Action 2 : si vous devez mettre à niveau votre version d’Adobe Commerce sur le cloud](#action-2-if-you-need-to-upgrade-your-adobe-commerce-on-cloud-version) pour plus d’informations et connaître les étapes suivantes.* |
| --- | --- | --- |
| 2.4.4 ou 2.4.5 | Requis avant le 30 octobre 2026. | Requis pour le 1er juin 2027 |
| 2.4.6 ou 2.4.7 | Requis avant le 30 octobre 2026 ou le 31 mai 2027, selon le logiciel. | Requis pour le 1er juin 2028 |
| 2.4.8 ou 2.4.9 | Requis avant le 30 octobre 2026 ou le 31 mai 2027, selon le logiciel. | Non requis pour le moment |

**Tableau 1 : Actions requises et délais par version**

## Qui n’a pas besoin d’agir ?

Le présent avis ne s&#39;applique pas :

* Clients utilisant Adobe Commerce sur Cloud version 2.4.8 ou 2.4.9 et dont les environnements exécutent des versions prises en charge de logiciels tiers

* Clients sur [!DNL Adobe Commerce as a Cloud Service]

### Comment vérifier les versions que vous exécutez

Vous avez besoin de l’aide de votre administrateur eCommerce pour passer en revue les étapes suivantes afin de vérifier quelle version vous exécutez.

**Votre version d’Adobe Commerce on Cloud**

1. Connectez-vous au panneau d’administration d’Adobe Commerce.

   La version actuelle doit s’afficher dans le coin inférieur droit de toute page d’administration.

1. Si la version ne s’affiche pas dans Admin, utilisez l’outil de ligne de commande [&#128279;](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cli/config-cli){target="_blank"} pour exécuter la commande version :

   ```shell
   bin/magento --version
   ```

**Vos versions de dépendance logicielle**

1. Connectez-vous à [Cloud Console](https://console.adobecommerce.com/).
1. Ouvrez le projet approprié, puis sélectionnez l’environnement à réviser.
1. Vérifiez la configuration du service pour cet environnement dans le fichier `.magento/services.yaml`, qui définit les noms de service et les versions pris en charge utilisés par Adobe Commerce sur l’infrastructure cloud.
Pour obtenir des instructions détaillées, voir la documentation [Configurer les services](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/services/config-services){target="_blank"}.

## Pourquoi ce mandat en matière de sécurité est important

Les logiciels qui ne sont plus pris en charge par les fournisseurs ne reçoivent plus de correctifs de sécurité, ce qui signifie que les problèmes de sécurité connus de ces logiciels ne peuvent pas être corrigés. En outre, conformément à la politique de cycle de vie [Adobe &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce-operations/release/planning/lifecycle-policy) :

* **Les versions 2.4.4 et 2.4.5 d’** ne reçoivent désormais que des correctifs de sécurité limités et isolés pour l’application principale jusqu’au 31 mai 2027. Cette prise en charge limitée n’inclut pas les correctifs de qualité, la prise en charge de la compatibilité pour les dépendances d’applications (par exemple, PHP) ou les mises à jour des dépendances de plateformes

* **Adobe Commerce 2.4.6** bénéficiera d’une prise en charge étendue jusqu’au 30 août 2027 et ne recevra que des correctifs de sécurité limités et isolés pour l’application principale jusqu’au 31 mai 2028

* **Adobe Commerce version 2.4.7** recevra une prise en charge standard jusqu’au 31 mai 2027 et une prise en charge étendue jusqu’au 31 mai 2028

* **Adobe Commerce sur le cloud version 2.4.8 et 2.4.9** reste pris en charge et ne nécessite aucune mise à niveau de version pour le moment.

Continuer à exécuter votre storefront e-commerce sur des logiciels non pris en charge crée un risque de sécurité réel et croissant pour votre entreprise, y compris votre capacité à maintenir la conformité PCI et à protéger les données de vos clients.

>[!IMPORTANT]
>
>Si votre environnement ne répond pas aux exigences dans les délais détaillés dans le [Tableau 1](#determine-your-required-actions), Adobe suspend le trafic entrant vers l’environnement affecté. Votre storefront eCommerce sera déconnecté et ne servira pas les acheteurs. Voir [&#x200B; Que se passe-t-il si aucune action n’est entreprise &#x200B;](#what-happens-if-no-action-is-taken).

## Détails sur les actions à effectuer

### Action 1 : mise à niveau des dépendances logicielles tierces

En fonction du logiciel, toutes les dépendances de logiciels non prises en charge doivent être mises à niveau selon les chronologies partagées dans le tableau ci-dessous. Vous pouvez afficher vos environnements dans la [console cloud](https://console.adobecommerce.com/) et vérifier les versions dépendantes en cours d’exécution à l’aide de ces [instructions](#check-software-dependency-versions). Les mises à niveau des dépendances logicielles s’appliquent à toutes les versions d’Adobe Commerce on Cloud 2.4.4 à 2.4.9.

| Dépendance | Version | Doit mettre à niveau vers | Date d’application |
| --- | --- | --- | --- |
| PHP | 8.1 et versions ultérieures | 8.2 ou version ultérieure | 31 Mai 2027 |
| MariaDB/Galera | 10.5 et versions ultérieures | 10.6 ou version ultérieure | 30 Octobre 2026 |
| MariaDB/Galera | Supérieur à 10,5 mais inférieur à 10,11 | 10.11 ou version ultérieure | 31 Mai 2027 |
| Elasticsearch | n’importe quelle version | OpenSearch:<br><br>- version 2.19 pour les clients des versions 2.4.4 et 2.4.5<br>- version 3 pour les clients des versions 2.4.6 et ultérieures. | 30 Octobre 2026 |
| OpenSearch | 1.x | version 2.19 pour les clients des versions 2.4.4 et 2.4.5.<br>version 3 pour les clients des versions 2.4.6 et ultérieures. | 31 Mai 2027 |
| Redis | 5 et moins | Valkey 8 ou version ultérieure | 31 Mai 2027 |
| RabbitMQ | 3.9 et versions ultérieures | 3.13 ou version ultérieure | 30 Octobre 2026 |
| RabbitMQ | Supérieur à 3,9 mais inférieur à 3,13 | 4.3 ou version ultérieure | 31 Mai 2027 |

**Tableau 2 : exigences de mise à niveau de la dépendance logicielle**

#### Préparation à une mise à niveau des dépendances logicielles tierces

Adobe vous aidera à mettre à niveau directement ces dépendances logicielles.

* **Prise en main :** ouvrez un [ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) répertoriant les environnements à mettre à niveau et les dépendances impliquées. Ouvrez votre ticket au moins 30 jours avant votre date d&#39;application afin que notre équipe puisse planifier le travail.

* **Temps d’arrêt :** Adobe vous confirmera la fenêtre attendue lors de la planification.

* **Tests :** mettre à niveau et valider un environnement hors production avant la production. Validez au minimum le passage en caisse, la recherche, le panier et toutes les intégrations personnalisées. Les exigences s’appliquent à tous vos environnements. Prévoyez donc de mettre à niveau chaque environnement plutôt que de vous concentrer uniquement sur la production.

* **Compatibilité :** la plupart de ces modifications sont des mises à niveau de version au sein du même logiciel et comportent peu de risques. Les points suivants méritent une attention plus soutenue :

  * **Elasticsearch vers OpenSearch** et **Redis vers Valkey** sont des migrations vers différents logiciels plutôt que des mises à niveau de version. Le code personnalisé, les extensions ou la configuration référençant le service d’origine peuvent nécessiter une mise à jour.
  * **PHP 8.1 à 8.2** peut faire apparaître des obsolètes dans le code personnalisé et les extensions tierces.

Si vous utilisez des extensions tierces, vérifiez auprès de vos fournisseurs d’extensions que leurs versions actuelles prennent en charge vos versions cibles. Si vous travaillez avec un intégrateur de solutions, associez-le à la planification et à la validation.

### Action 2 : si vous devez mettre à niveau votre version d’Adobe Commerce on Cloud :

Vous avez le choix entre (i) effectuer une mise à niveau vers une version d’Adobe Commerce on Cloud prise en charge ou (ii) migrer vers Adobe Commerce as a Cloud Service (plateforme commerciale entièrement gérée d’Adobe)

La date d’application de votre version actuelle s’applique quelle que soit l’option choisie.

| Version actuelle | Action | Date d’application |
| --- | --- | --- |
| Utilisation d’Adobe Commerce sur le cloud version 2.4.4 ou 2.4.5 | Effectuez la mise à niveau vers Adobe Commerce sur Cloud version 2.4.9 (ou la dernière version) ou migrez vers Adobe Commerce as a Cloud Service | 1er juin 2027 |
| Utilisation d’Adobe Commerce sur le cloud version 2.4.6 ou 2.4.7 | Effectuez la mise à niveau vers Adobe Commerce sur Cloud version 2.4.9 (ou la dernière version) ou migrez vers Adobe Commerce as a Cloud Service | 1er juin 2028 |
| Utilisation d’Adobe Commerce sur les versions 2.4.8 ou 2.4.9 de Cloud | Aucune action de mise à niveau de la version d’Adobe Commerce on Cloud n’est nécessaire pour le moment. Les délais de dépendance logicielle de l&#39;action 1 s&#39;appliquent toujours. | s.o. |

**Tableau 3 : consignes et échéances si vous devez mettre à niveau votre version actuelle d’Adobe Commerce on Cloud**

Pour plus d’informations sur Adobe Commerce on Cloud version 2.4.9 et Adobe Commerce as a Cloud Service, consultez le tableau suivant afin de prendre une décision éclairée.

**Tableau 4 : mise à niveau vers Adobe Commerce on Cloud et migration vers Adobe Commerce as a Cloud Service**

| | Adobe Commerce on Cloud version 2.4.9 | Adobe Commerce as a Cloud Service |
| --- | --- | --- |
| Ce que c&#39;est | La dernière version d’Adobe Commerce avec une couverture de sécurité complète, des correctifs de qualité et des mises à jour des dépendances de plateforme. | Plateforme commerciale entièrement gérée par Adobe, conçue pour une innovation continue sans frais de mise à niveau. [En savoir plus](https://experienceleague.adobe.com/fr/docs/commerce/cloud-service/overview). |
| Idéal si | Vous souhaitez continuer à gérer votre propre infrastructure, vos mises à niveau et vos correctifs pour l’instant. Vous pouvez migrer vers Adobe Commerce as a Cloud Service dès que vous êtes prêt(e). | Vous souhaitez laisser de côté les cycles de mise à niveau pour de bon, réduire votre coût total de possession et obtenir automatiquement les nouvelles fonctionnalités d’Adobe, sans effort supplémentaire. |
| Avantage clé | Répond maintenant aux exigences de sécurité tout en préservant votre configuration existante. | Une vitrine ultrarapide et performante, un catalogue hautement évolutif, une gestion native des ressources numériques et une IA générative intégrée, le tout sur une infrastructure gérée par Adobe. |

## Que se passe-t-il si aucune mesure n’est prise ?

Si un environnement ne répond pas à ces exigences d’ici les dates d’application partagées [ci-dessus](#determine-your-required-actions), Adobe prendra les mesures appropriées. Cela inclut la suspension du trafic vers l’infrastructure affectée, ce qui entraîne la déconnexion de votre storefront d’e-commerce.

Si un environnement reste non conforme à la suite de la suspension du trafic, Adobe peut mettre fin aux services cloud et lancer le processus de désaffectation. Suite à la mise hors service, toutes les données et ressources de l’environnement eCommerce hébergé, y compris toutes les instances, tous les environnements et toutes les branches, seront définitivement supprimées et ne pourront pas être restaurées.

## Résumé de l’aide apportée par Adobe

Adobe propose des outils et une assistance pour rendre votre transition aussi fluide que possible, que vous effectuiez une mise à niveau ou une migration.

**Si vous choisissez d’effectuer une mise à niveau vers Adobe Commerce on Cloud version 2.4.9**

* **Rapport de compatibilité de mise à niveau :** Adobe fournit un rapport détaillé identifiant exactement ce dont votre mise à niveau vers Adobe Commerce version 2.4.9 a besoin, y compris la durée et la portée des coûts. [Générez votre rapport de compatibilité de mise à niveau](https://supportinsights.adobe.com/commerce/tab/main).

* **Mise à niveau des dépendances logicielles :** comme vous ne pouvez pas mettre à niveau directement les dépendances logicielles, [ouvrez un ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket){target="_blank"} pour qu’Adobe gère la mise à niveau pour vous. Pour plus d’informations, voir [Configuration des services](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/configuration/overview){target="_blank"}.

**Si vous choisissez de migrer vers Adobe Commerce as a Cloud Service**

Adobe fournit des outils qui réduisent le coût et le temps de migration vers Adobe Commerce as a Cloud Service. Cela ne vous coûte rien. Ces outils s’appliquent uniquement à la migration ; ils ne sont pas utilisés pour une mise à niveau de version sur Adobe Commerce on Cloud. Consultez la [présentation de la migration](https://experienceleague.adobe.com/fr/docs/commerce/cloud-service/migration/overview) pour obtenir un guide de migration complet, y compris les chemins et les phases de migration.

* **Évaluation de la migration :** évalue la complexité de migration de vos personnalisations. Consultez la [&#x200B; Présentation de l’outil d’évaluation de la migration &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce/cloud-service/migration/migration-tools/assessment).

* **Migration des données :** l’outil [migration de données en bloc et incrémentielle](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/bulk-data) déplace vos données vers votre nouvel environnement Adobe Commerce as a Cloud Service.

* Adobe [migration assistée par l’IA et outils de développement](https://developer.adobe.com/commerce/extensibility/developer-agent/), notamment **[!DNL Adobe Developer App Builder]** et **[!DNL Commerce Storefront powered by Edge Delivery Services]**, permet d’accélérer la modernisation du storefront et la reconfiguration des extensions de plateformes.

Pour toute question, contactez l’équipe chargée de votre compte, le gestionnaire de compte de la solution, le spécialiste du renouvellement ou contactez [les services d’assistance](https://experienceleague.adobe.com/fr/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket).
