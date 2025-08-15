---
title: Assistance et maintenance après le lancement
description: Garantissez des performances et une sécurité optimales pour votre boutique Adobe Commerce grâce à nos bonnes pratiques complètes de maintenance et d’assistance après le lancement.
role: Admin, User, Developer
feature: Best Practices
exl-id: f02a13ca-c851-4508-a2bd-e5bc196a330c
source-git-commit: 60444d3ef7208d12af3f06af6e3cab2cae93700b
workflow-type: tm+mt
source-wordcount: '2116'
ht-degree: 0%

---

# Assistance et maintenance après le lancement d’Adobe Commerce

La prise en charge et la maintenance après le lancement sont essentielles pour garantir le bon fonctionnement de votre boutique Adobe Commerce, ses performances, sa sécurité et la réalisation continue de vos objectifs commerciaux. Cette phase implique une surveillance, une optimisation, une correction des bogues, des mises à jour et une assistance utilisateur continues. Les sections suivantes répartissent **prise en charge après le lancement** en catégories clés :

## Surveillance régulière du site et optimisation des performances

### Suivi des performances

- **Tests de vitesse et de chargement du site** : Adobe Commerce peut nécessiter de nombreuses ressources. Il est donc essentiel de surveiller régulièrement les performances.

   - **Outils à utiliser** : tous les projets d’infrastructure cloud d’Adobe Commerce incluent l’accès à New Relic, qui permet de surveiller les performances et d’enquêter sur les événements dans l’application Commerce et l’infrastructure cloud. Les outils supplémentaires incluent Google PageSpeed Insights et GTMetrix.

   - **Éléments à surveiller** : voici les principaux éléments à surveiller pour Adobe Commerce sur les infrastructures cloud :

      - **Notifications d’intégrité** : alertes pour l’espace disque et l’intégrité de l’environnement.

      - **Observation** : surveillance complète combinant des données de journal provenant de plusieurs sources pour une gestion efficace du site.

      - **Service New Relic** : surveille les performances dans les environnements d’évaluation et de production, en se concentrant sur les mesures clés.

      - **Politique Alertes gérées** : effectue le suivi des mesures avec des seuils prédéfinis pour déclencher des notifications en cas de problèmes d’infrastructure ou d’application affectant les performances.

  >[!TIP]
  >
  >Voir [surveillance des performances](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/monitor/performance) dans le _guide du cloud_.


- **Optimisation des performances de la base de données** : pour optimiser les performances de la base de données dans Adobe Commerce Cloud, implémentez les éléments suivants :

   - **Surveiller et optimiser les requêtes MySQL** : Identifiez et résolvez les requêtes à exécution lente, ce qui peut être fait à l&#39;aide des commandes SHOW FULL PROCESSLIST et EXPLAIN de MySQL. Pour les configurations plus complexes, les utilisateurs de Pro architecture peuvent utiliser le kit d&#39;outils Percona pour analyser les logs de requête pour les problèmes de performance.

   - **Gestion des index** : assurez-vous que chaque table possède une clé primaire et supprimez tous les index en double, car ils peuvent réduire l’efficacité et entraîner des conflits lors des écritures simultanées.

   - **Optimisation des tâches Cron** : les tâches Cron doivent être planifiées en dehors des heures de pointe afin de minimiser l’impact sur les performances, en particulier si les tâches en arrière-plan, telles que l’indexation, sont fréquentes.

  >[!TIP]
  >
  >Voir [Bonnes pratiques pour résoudre les problèmes de performances des bases de données](resolve-database-performance-issues.md).

- **Surveiller le réseau CDN** : pour surveiller les performances du réseau CDN Fastly dans Adobe Commerce Cloud, vous pouvez effectuer les actions suivantes :

   - **Tirez parti de New Relic pour la surveillance** : Adobe Commerce propose New Relic pour surveiller les performances de Fastly et d’autres mesures sur les environnements d’évaluation et de production. Cet outil fournit des informations sur l’intégrité du serveur, la mise en cache du réseau CDN et les requêtes réseau au fil du temps, ce qui permet d’identifier des modèles et d’optimiser les paramètres du réseau CDN.

   - **Analyse des journaux Fastly** : pour les projets Adobe Commerce Cloud Pro, vous pouvez utiliser les journaux New Relic pour examiner et analyser les données des journaux Fastly CDN et WAF afin de suivre les tendances de performances, les événements de sécurité et de diagnostiquer les erreurs ou les problèmes de latence.

   - **Utiliser des commandes cURL** : exécutez des commandes cURL avec des en-têtes spécifiques à Fastly pour inspecter l’état du cache de votre site. Les en-têtes de réponse clés incluent `X-Cache` (HIT/MISS), `Fastly-Module-Enabled`, `Fastly-Magento-VCL-Uploaded` et `Cache-Control` pour vérifier la mise en cache et le statut du module. Adobe fournit des exemples de commandes cURL pour les environnements d’évaluation et de production.

   - **Vérifier les informations d’en-tête** : inspectez les en-têtes tels que `Cache-Control`, `Pragma` et `X-Magento-Tags` pour confirmer le comportement de mise en cache approprié et la gestion des balises sur le contenu mis en cache. Les valeurs d’en-tête appropriées indiquent si les configurations de mise en cache sont appliquées efficacement sur le réseau CDN.

   - **Débogage et test Fastly** : utilisez la fonctionnalité de débogage Fastly pour identifier et résoudre les problèmes liés aux taux d’accès et de non-accès au cache, à la logique de mise en cache ou aux réponses d’en-tête incorrectes, qui peuvent pointer vers des problèmes de configuration ou un mauvais alignement avec les règles de mise en cache attendues.

Ces étapes de surveillance permettent de maintenir des performances de réseau CDN optimales et de résoudre les problèmes qui affectent la vitesse et la fiabilité du site.

>[!TIP]
>
>Voir [Présentation des services Fastly](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/cdn/fastly) dans le _Guide cloud_.

#### Surveillance régulière de la sécurité

Pour maintenir une surveillance régulière de la sécurité dans Adobe Commerce Cloud, Adobe recommande une approche multidimensionnelle impliquant une analyse continue, la journalisation et des pratiques de sécurité proactives. Voici quelques actions essentielles pour garantir une sécurité continue :

- **Analyse de sécurité** : utilisez l’outil Analyse de sécurité d’Adobe pour surveiller les vulnérabilités connues et les programmes malveillants sur vos sites Commerce. Cet outil fournit des alertes pour les risques de sécurité potentiels et les problèmes de conformité.

- **Maintenance régulière des correctifs et des mises à jour** : appliquez les correctifs et les mises à jour de sécurité d’Adobe dès qu’ils sont disponibles. La mise à niveau vers la dernière version d’Adobe Commerce garantit les dernières défenses contre les menaces.

- **Audit et surveillance des journaux** : utilisez des outils tels que les journaux New Relic (disponibles pour les projets Pro) pour centraliser et analyser les journaux de sécurité des environnements d’évaluation et de production, ce qui améliore la visibilité des problèmes de sécurité potentiels et des violations.

- **Gestion des comptes et des accès** : contrôlez régulièrement les comptes des utilisateurs et utilisatrices et des administrateurs afin de supprimer tous les comptes non autorisés ou obsolètes. Renforcez les contrôles d’accès avec l’authentification multifacteur (MFA) pour les utilisateurs administrateurs.

- **Pare-feu d’application web (WAF)** : utilisez le WAF Fastly intégré pour détecter et atténuer les menaces provenant de modèles de trafic malveillants, tels que les tentatives d’extraction de données non autorisées.

- **Code personnalisé et sécurité des extensions** : sécurisez tout code personnalisé ou extension tierce en effectuant des audits de code réguliers et en limitant les extensions à celles approuvées par Adobe.

>[!TIP]
>
>Voir [Sécurité](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/security/security) dans le _Guide des systèmes d’administration_.

#### Journalisation et surveillance des erreurs

Pour surveiller la journalisation des erreurs dans Adobe Commerce Cloud, Adobe propose plusieurs outils et pratiques pour une résolution des problèmes et une gestion des performances efficaces :

- **Agrégation des journaux avec New Relic** : New Relic collecte et centralise les journaux des applications Adobe Commerce, y compris les journaux liés à l’infrastructure, au réseau CDN et à WAF. Cette configuration permet de rationaliser le suivi des erreurs, de créer des tableaux de bord et d’interroger les journaux pour obtenir des informations plus précises sur les performances et les problèmes des applications. L’accès aux journaux New Relic permet de rechercher et de filtrer les journaux en fonction de divers attributs, afin de diagnostiquer rapidement les problèmes.

- **Types de journaux d’erreurs** : les principaux journaux d’erreurs dans Adobe Commerce Cloud incluent `cloud.log`, qui contient les commentaires sur le déploiement, et `cloud.error.log`, qui consigne les avertissements et les erreurs de déploiement. Les autres journaux spécifiques à des fins de débogage comprennent `debug.log`, `system.log` et `exception.log`, chacun servant des rôles distincts dans le suivi des erreurs et des événements sur la plateforme Commerce.

- **Journalisation personnalisée avec Monolog** : Adobe Commerce prend en charge la journalisation personnalisée via Monolog, qui permet aux développeurs d’orienter les messages du journal vers diverses destinations telles que des fichiers, des bases de données et même des alertes. Cette flexibilité est utile pour créer des stratégies de journalisation avancées qui répondent à différents besoins de surveillance dans les environnements de développement et de production.

- **Surveillance des exceptions avec outil d’analyse à l’échelle du site** : l’outil d’analyse à l’échelle du site permet de surveiller et de gérer les journaux d’exceptions, en identifiant les problèmes récurrents dans les événements de déploiement et d’application. Cet outil met en évidence les problèmes fréquents, ce qui facilite la hiérarchisation et la résolution des problèmes critiques affectant les performances.

>[!TIP]
>
>Pour plus d’informations sur les pratiques de journalisation et de suivi des erreurs dans Adobe Commerce Cloud, voir [Gestion des journaux New Relic](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management) et [surveillance des exceptions](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/site-wide-analysis-tool/exceptions).

### Sécurité et mises à jour

#### Correctifs et mises à jour de sécurité

Pour rester à jour et assurer la sécurité de votre système Adobe Commerce Cloud, voici quelques bonnes pratiques pour surveiller les correctifs et les mises à jour de sécurité :

- **Abonnement aux alertes de sécurité d’Adobe Commerce** : restez informé des vulnérabilités de la sécurité en [enregistrement pour recevoir des notifications d’Adobe](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/security/security).

- **Vérifier les notes de mise à jour** : consultez régulièrement les [notes de mise à jour des correctifs de sécurité](https://experienceleague.adobe.com/fr/docs/commerce-operations/release/notes/security-patches/overview), qui sont balisées avec « -pN » pour les versions (par exemple, 2.3.5-p1) et contiennent des correctifs et des améliorations critiques.

- **Application rapide des correctifs de sécurité** : appliquez les correctifs de sécurité dès qu’ils sont disponibles. Cela inclut la mise à jour vers les dernières versions ou l’application de fichiers correctifs spécifiques.

- **Utilisation de correctifs cloud** : pour Adobe Commerce Cloud, les correctifs de sécurité peuvent être regroupés dans la suite d’outils cloud. Veillez à mettre à niveau la suite ou la version Commerce pour recevoir ces correctifs.

- **Gestion automatisée des correctifs** : pensez à utiliser des outils tels que le correctif centralisé pour [gérer et appliquer automatiquement les correctifs sur plusieurs magasins](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale).

>[!TIP]
>
>Pour obtenir des informations détaillées et des instructions détaillées sur l&#39;application de correctifs et le maintien de la sécurité, consultez les sections [Notes de mise à jour des correctifs de sécurité](../../../release/release-notes/security/overview.md) et [Application de correctifs de sécurité](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches). Vous devez également consulter les rapports [Outil d’analyse à l’échelle du site](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/site-wide-analysis-tool/access).

#### Conformité PCI

Pour garantir la conformité PCI dans Adobe Commerce Cloud, suivez ces pratiques clés :

- **Protéger les données du titulaire de carte** : ne stockez jamais les données du titulaire de carte dans Adobe Commerce. Si un stockage est nécessaire, utilisez des méthodes chiffrées et segmentées en unités lexicales pour le protéger.

- **Utiliser des protocoles de transmission sécurisés** : transmettez toujours les données de paiement via des protocoles sécurisés tels que TLS, avec chiffrement et gestion des clés appropriée.

- **Utilisation du pare-feu d’application web (WAF)** : le service WAF optimisé par Fastly répond aux exigences PCI DSS 6.6 et protège contre les vulnérabilités courantes en bloquant le trafic malveillant avant qu’il n’atteigne votre site. Voir plus d’informations [ici](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage) et [ici](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service).

- **Limiter l’accès** : s’assurer que seul le personnel autorisé a accès aux données de paiement sensibles et [appliquer un contrôle d’accès pour réduire le risque d’exposition](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage).

- **Analyse de sécurité régulière** : effectuez des analyses PCI ASV régulières et [surveillez votre environnement](https://experienceleague.adobe.com/fr/docs/commerce-operations/security-and-compliance/shared-responsibility) pour corriger les vulnérabilités potentielles.

>[!TIP]
>
>Pour obtenir des instructions plus détaillées sur le maintien de la conformité PCI avec Adobe Commerce, consultez [Bonnes pratiques de traitement et de stockage des paiements](../planning/payment-processing-storage.md).

### Service clientèle et assistance utilisateur

#### Configuration

- **Canaux d’assistance** : implémentez des canaux d’assistance clientèle tels que :

   - **Chat en direct** : proposez une assistance de chat en direct pour une assistance immédiate. Les solutions populaires comprennent Zendesk, Intercom et Tidio.

   - **Assistance par e-mail** : utilisez un système de ticket d’assistance tel que Freshdesk ou Zoho Desk pour gérer efficacement les demandes des clients.

   - **Assistance téléphonique** : si votre clientèle est nombreuse, pensez à proposer une assistance téléphonique pendant les heures de bureau.

#### Formation des utilisateurs administrateurs

- **Formation interne** : formez votre personnel à l’utilisation d’Adobe Commerce Admin, au traitement des commandes, à la gestion des produits et à la gestion des problèmes de service client.

- **Documentation** : conservez une base de connaissances interne ou un manuel d’utilisation pour les questions fréquentes (FAQ), le dépannage et les tâches courantes.

#### Optimisation de l’expérience client

- **Questionnaires et commentaires** : utilisez les enquêtes pour recueillir les commentaires des clients et clientes et optimiser l’expérience client. Adobe Commerce prend en charge les intégrations à des outils tels que SurveyMonkey ou Google Forms.

- **Gestion des révisions** : gérez les révisions et les évaluations des clients sur vos produits. Encouragez les clients satisfaits à laisser des évaluations tout en répondant de manière appropriée aux évaluations négatives.

- **Personalization** : implémentez des fonctionnalités de personnalisation telles que des recommandations de produits personnalisées ou des promotions ciblées.

### Maintenance et optimisation continues des magasins

#### Optimisation du moteur de recherche (SEO)

- **Optimisation du contenu** : mettez régulièrement à jour les descriptions des produits, les articles de blog et les pages de catégorie pour garder le contenu récent et pertinent pour les moteurs de recherche.

- **Audits SEO** : Effectuez des audits SEO réguliers à l’aide d’outils tels que Google Search Console ou Screaming Frog pour identifier les problèmes d’optimisation du moteur de recherche (par exemple, les liens rompus, les métadonnées manquantes, le contenu en double).

- **Structure d’URL** : conservez une structure d’URL logique et propre et assurez-vous qu’il n’y a pas de liens rompus ou de redirections.

#### Optimisation du taux de conversion (CRO)

- **Tests A/B** : exécutez des tests A/B sur différents éléments de page, tels que les pages de produit ou le processus de passage en caisse, pour améliorer les taux de conversion.

- **Abandon de panier** : implémentez des campagnes par e-mail d’abandon de panier ou des fenêtres contextuelles d’intention de sortie pour récupérer les ventes perdues.

- **Optimisation du passage en caisse** : simplifiez votre processus de passage en caisse en réduisant le nombre d’étapes et en proposant un passage en caisse aux invités pour améliorer les conversions.

#### Intégration du marketing

- **Campagnes par e-mail** : configurez des flux de marketing par e-mail automatisés pour les e-mails de bienvenue, les e-mails de panier abandonnés et les suivis après achat. Les plateformes telles qu’Adobe Marketo, Mailchimp ou Klaviyo s’intègrent bien à Adobe Commerce.

- **Intégration des médias sociaux et des publicités** : intégrez-les à des plateformes telles que Facebook, Instagram et Google Ads pour exécuter des campagnes ciblées et suivre les performances.

#### Optimisation des appareils mobiles

- **Réactivité mobile** : testez régulièrement la réactivité et la convivialité mobiles de votre site. Étant donné que le commerce mobile est en plein essor, une approche mobile-first est essentielle pour continuer à réussir.

- **Performances mobiles** : utilisez les outils de test et de performance compatibles avec les appareils mobiles de Google pour optimiser l’expérience de votre boutique mobile.

### Évolutivité et développement de nouvelles fonctionnalités

- **Mise à l’échelle automatique pour la gestion du trafic** :

   - Adobe Commerce Cloud prend en charge la mise à l’échelle automatique pour ajuster dynamiquement les ressources du serveur (par exemple, les nœuds web) en fonction des demandes de trafic en temps réel, ce qui garantit que votre boutique peut gérer des volumes élevés de visiteurs sans intervention manuelle. Voir [mise à l’échelle automatique](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/architecture/autoscaling) dans le _Guide du cloud_.

   - Les niveaux de web et de service peuvent évoluer indépendamment, ajoutant ainsi des nœuds web pour augmenter le trafic et dimensionnant les nœuds de base de données ou de service pour optimiser les performances du serveur principal pendant les périodes de pointe. Voir [architecture évolutive](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) dans le _guide du cloud_.

- **Suivi des performances** :

   - Utilisez **New Relic** pour surveiller les mesures de performances en temps réel (par exemple, l’utilisation de CPU, les niveaux de trafic) et effectuer des ajustements si nécessaire.

   - Testez les performances dans les environnements d’évaluation avant la mise à l’échelle pour éviter les problèmes de production.

- **Développement de nouvelles fonctionnalités** :

   - Intégrez des fonctionnalités avancées telles que la **personnalisation pilotée par l’IA**, la **gestion des abonnements** et des solutions personnalisées.

   - Testez et affinez continuellement les fonctionnalités dans les environnements d’évaluation avant le déploiement en production afin de minimiser les temps d’arrêt.

- **Maintenance continue du site** :

   - Consultez régulièrement les journaux système et les mesures de performances pour identifier les domaines à améliorer.

   - Faites en sorte que l’infrastructure reste évolutive et adaptable aux nouveaux besoins et à la croissance de l’entreprise.

>[!TIP]
>
>Pour obtenir des conseils détaillés, voir [bonnes pratiques de maintenance](overview.md), [personnalisation](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization) et [développement de fonctionnalités](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization).

### Rapports et analyses

- **Adobe Commerce Intelligence:** Commerce Intelligence, une fonctionnalité clé d’Adobe Commerce, fournit des informations sur les bonnes pratiques pour plusieurs sources de données, ce qui permet aux commerçants de prendre des décisions scientifiques basées sur les données et de prendre des actions claires et informées. Voir le [_Guide de l’utilisateur de Commerce Intelligence_](https://experienceleague.adobe.com/fr/docs/commerce-business-intelligence/mbi/getting-started).

- **Adobe Analytics:** Adobe Analytics offre une solution puissante pour suivre, analyser et optimiser les performances de votre boutique en ligne. Adobe Analytics aide les entreprises d’e-commerce à obtenir des informations plus précises sur le comportement des clients, les performances des produits, les taux de conversion et d’autres mesures clés, ce qui permet une prise de décision axée sur les données.

- **Google Analytics :** utilisez Google Analytics pour suivre le comportement des clients, les sources de trafic et les taux de conversion.

- **Outils Commerce Intelligence supplémentaires :** Adobe Commerce inclut la création de rapports avancés. Cette fonctionnalité vous donne accès à une suite de rapports dynamiques basés sur les données de vos produits, commandes et clients, avec un tableau de bord personnalisé adapté aux besoins de votre entreprise. Pour plus d’informations, consultez la section [Rapports avancés](https://experienceleague.adobe.com/fr/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting) du _Guide d’utilisation de l’administrateur_.

### Conclusion

L’assistance et la maintenance après le lancement sont des efforts continus qui nécessitent une attention régulière pour vous assurer que votre boutique Adobe Commerce continue à fonctionner correctement, reste sécurisée et s’adapte aux besoins de votre entreprise. La mise en œuvre d’une approche structurée de la surveillance des sites, du service clientèle, de l’optimisation et des mises à jour est essentielle pour le succès à long terme.
