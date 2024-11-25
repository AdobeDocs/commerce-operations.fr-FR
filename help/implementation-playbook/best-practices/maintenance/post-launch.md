---
title: Assistance et maintenance après le lancement
description: Assurez des performances optimales et de la sécurité de votre boutique Adobe Commerce grâce à nos bonnes pratiques de maintenance et de prise en charge après le lancement.
role: Admin, User, Developer
feature: Best Practices
source-git-commit: bcb45d53aba4a73a5730989e9bf29ccba6e9bf35
workflow-type: tm+mt
source-wordcount: '2116'
ht-degree: 0%

---


# Assistance et maintenance après le lancement pour Adobe Commerce

La prise en charge et la maintenance après le lancement sont essentielles pour garantir le bon fonctionnement de votre boutique Adobe Commerce, ses performances, sa sécurité et la poursuite des objectifs de votre entreprise. Cette phase implique une surveillance, une optimisation, une correction de bogues, des mises à jour et une prise en charge continue des utilisateurs. Les sections suivantes répartissent la **prise en charge post-lancement** en catégories clés :

## Surveillance régulière du site et optimisation des performances

### Suivi des performances

- **Test de vitesse et de chargement du site** : Adobe Commerce peut nécessiter de nombreuses ressources. Il est donc essentiel d’effectuer une surveillance régulière des performances.

   - **Outils à utiliser** : tous les projets Adobe Commerce sur l’infrastructure cloud incluent l’accès à New Relic, qui permet de surveiller les performances et d’enquêter sur les événements dans l’application Commerce et l’infrastructure cloud. Les outils supplémentaires incluent Google PageSpeed Insights et GTMetrix.

   - **Que surveiller** : voici les principaux éléments à surveiller pour Adobe Commerce sur l’infrastructure cloud :

      - **Notifications d’intégrité** : alertes pour l’espace disque et l’intégrité de l’environnement.

      - **Observation** : surveillance complète combinant des données de journaux provenant de plusieurs sources pour une gestion efficace du site.

      - **Service New Relic** : surveille les performances en évaluation et en production, en se concentrant sur les mesures clés.

      - **Stratégie d’alertes gérées** : effectue le suivi des mesures avec des seuils prédéfinis pour déclencher des notifications pour les problèmes d’infrastructure ou d’application affectant les performances.

  >[!TIP]
  >
  >Voir [surveillance des performances](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance) dans le _Guide de Cloud_.


- **Optimisation des performances de la base de données** : pour optimiser les performances de la base de données dans Adobe Commerce Cloud, implémentez les éléments suivants :

   - **Surveillez et optimisez les requêtes MySQL** : identifiez et résolvez les requêtes à exécution lente, ce qui peut être effectué à l’aide des commandes AFFICHER la LISTE COMPLÈTE et EXPLAIN de MySQL. Pour les configurations plus complexes, les utilisateurs d’architecture Pro peuvent utiliser le kit d’outils Percona pour analyser les journaux de requêtes en cas de problèmes de performances.

   - **Gestion des index** : assurez-vous que chaque table dispose d’une clé primaire et supprimez les index en double, car ils peuvent réduire l’efficacité et entraîner des conflits lors des écritures simultanées.

   - **Optimisation des tâches Cron** : les tâches Cron doivent être planifiées pendant les heures creuses afin de minimiser l’impact sur les performances, en particulier si les tâches en arrière-plan comme l’indexation sont fréquentes.

  >[!TIP]
  >
  >Voir les [bonnes pratiques pour résoudre les problèmes de performances de la base de données](resolve-database-performance-issues.md).

- **Surveiller le réseau de diffusion de contenu** : pour surveiller rapidement les performances du réseau de diffusion de contenu dans Adobe Commerce Cloud, vous pouvez effectuer les actions suivantes :

   - **Utilisation de New Relic pour la surveillance** : Adobe Commerce propose New Relic pour surveiller les performances et d’autres mesures rapides sur les environnements d’évaluation et de production. Cet outil fournit des informations sur l’intégrité du serveur, la mise en cache du réseau de diffusion de contenu et les requêtes réseau au fil du temps, ce qui permet d’identifier les modèles et d’optimiser les paramètres du réseau de diffusion de contenu.

   - **Analyse des journaux rapides** : pour les projets Adobe Commerce Cloud Pro, vous pouvez utiliser les journaux New Relic pour passer en revue et analyser rapidement les données des journaux CDN et WAF afin de suivre les tendances de performances, les événements de sécurité et de diagnostiquer les erreurs ou les problèmes de latence.

   - **Utiliser les commandes cURL** : exécutez les commandes cURL avec des en-têtes spécifiques Fastly pour examiner l’état du cache de votre site. Les en-têtes de réponse clés comprennent `X-Cache` (HIT/MISS), `Fastly-Module-Enabled`, `Fastly-Magento-VCL-Uploaded` et `Cache-Control` pour vérifier la mise en cache et l’état du module. Adobe fournit des exemples de commandes cURL pour les environnements d’évaluation et de production.

   - **Vérifiez les informations sur l’en-tête** : les en-têtes Inspect tels que `Cache-Control`, `Pragma` et `X-Magento-Tags` pour confirmer le comportement de mise en cache approprié et la gestion des balises sur le contenu mis en cache. Les valeurs d’en-tête appropriées indiquent si les configurations de mise en cache sont effectivement appliquées sur le réseau de diffusion de contenu.

   - **Débogage et test rapides** : utilisez la fonction de débogage de Fastly pour identifier et résoudre les problèmes liés aux taux d’accès au cache et MISS, à la logique de mise en cache ou aux réponses d’en-tête incorrectes, qui peuvent pointer vers des problèmes de configuration ou un mauvais alignement avec les règles de mise en cache attendues.

Ces étapes de surveillance permettent de maintenir des performances de réseau de diffusion de contenu optimales et de résoudre les problèmes qui affectent la vitesse et la fiabilité du site.

>[!TIP]
>
>Voir [Présentation des services rapides](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) dans le _Guide Cloud_.

#### Surveillance régulière de la sécurité

Pour maintenir une surveillance de sécurité régulière dans Adobe Commerce Cloud, Adobe recommande une approche à plusieurs facettes impliquant l’analyse continue, la journalisation et des pratiques de sécurité proactives. Voici quelques actions principales pour assurer la sécurité en cours :

- **Analyse de sécurité** : utilisez l’outil d’analyse de sécurité d’Adobe pour surveiller les vulnérabilités connues et les logiciels malveillants sur vos sites Commerce. Cet outil fournit des alertes pour les risques potentiels de sécurité et les problèmes de conformité.

- **Maintenance régulière des correctifs et mises à jour** : appliquez les correctifs de sécurité et les mises à jour d’Adobe dès qu’ils sont disponibles. La mise à niveau vers la dernière version d’Adobe Commerce garantit les dernières défenses contre les menaces.

- **Suivi et surveillance des journaux** : utilisez des outils tels que les journaux New Relic (disponibles pour les projets Pro) pour centraliser et analyser les journaux de sécurité à partir des environnements d’évaluation et de production, ce qui améliore la visibilité des problèmes et des violations de sécurité potentiels.

- **Gestion des comptes et des accès** : contrôlez régulièrement les comptes d’utilisateurs et d’administrateurs pour supprimer tout compte non autorisé ou obsolète. Renforcer les contrôles d’accès avec l’authentification multifactorielle (MFA) pour les utilisateurs administrateurs.

- **Pare-feu d’application web (WAF)** : utilisez le WAF Fastly intégré pour détecter et atténuer les menaces provenant de schémas de trafic malveillants, tels que les tentatives d’extraction de données non autorisées.

- **Sécurité du code personnalisé et de l’extension** : sécurisez tout code personnalisé ou les extensions tierces en effectuant des audits de code standard et en limitant les extensions à celles contrôlées par Adobe.

>[!TIP]
>
>Voir [Security](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security) dans le _Guide des systèmes d’administration_.

#### Journalisation et surveillance des erreurs

Pour surveiller la journalisation des erreurs dans Adobe Commerce Cloud, Adobe propose plusieurs outils et pratiques pour un dépannage et une gestion des performances efficaces :

- **Agrégation des journaux avec New Relic** : New Relic collecte et centralise les journaux des applications Adobe Commerce, y compris les journaux liés à l’infrastructure, au réseau de diffusion de contenu et à WAF. Cette configuration permet un suivi des erreurs simplifié, la création de tableaux de bord et l’interrogation des journaux pour obtenir des informations plus détaillées sur les performances et les problèmes de l’application. L’accès aux journaux New Relic permet de rechercher et de filtrer les journaux selon différents attributs afin de diagnostiquer rapidement les problèmes.

- **Types de journaux d’erreurs** : les journaux d’erreurs clés dans Adobe Commerce Cloud comprennent `cloud.log`, qui contient les commentaires de déploiement et `cloud.error.log`, qui consigne les avertissements et les erreurs de déploiement. `debug.log`, `system.log` et `exception.log` sont d’autres journaux spécifiques pour le débogage, chacun d’eux servant des rôles distincts dans le suivi des erreurs et des événements sur la plateforme Commerce.

- **Journalisation personnalisée avec Monolog** : Adobe Commerce prend en charge la journalisation personnalisée via Monolog, ce qui permet aux développeurs de rediriger les messages de journal vers différentes destinations, telles que les fichiers, les bases de données et même les alertes. Cette flexibilité est utile pour créer des stratégies de journalisation avancées qui répondent à différents besoins de surveillance dans les environnements de développement et de production.

- **Surveillance des exceptions avec l’outil d’analyse à l’échelle du site** : l’outil d’analyse à l’échelle du site permet de surveiller et de gérer les journaux des exceptions, en identifiant les problèmes récurrents dans les événements de déploiement et d’application. Cet outil met en évidence les problèmes fréquents, ce qui facilite la hiérarchisation et la résolution des problèmes critiques affectant les performances.

>[!TIP]
>
>Pour plus d’informations sur les pratiques de journalisation et de suivi des erreurs dans Adobe Commerce Cloud, voir [Gestion des journaux de New Relic](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management) et [surveillance des exceptions](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/exceptions).

### Sécurité et mises à jour

#### Correctifs et mises à jour de sécurité

Pour rester à jour et garantir la sécurité de votre système Adobe Commerce Cloud, voici quelques bonnes pratiques pour surveiller les correctifs de sécurité et les mises à jour :

- **Abonnez-vous aux alertes de sécurité Adobe Commerce** : restez informé des vulnérabilités de sécurité en [vous enregistrant pour les notifications d’Adobe](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security).

- **Vérifiez les notes de mise à jour** : consultez régulièrement les [notes de mise à jour des correctifs de sécurité](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/overview), qui sont balisées avec &quot;-pN&quot; pour les versions (par exemple, 2.3.5-p1) et contiennent des correctifs et améliorations critiques.

- **Appliquez les correctifs de sécurité promptement** : appliquez les correctifs de sécurité dès qu&#39;ils sont disponibles. Cela inclut la mise à jour vers les versions les plus récentes ou l’application de fichiers correctifs spécifiques.

- **Utilisez les correctifs de cloud** : pour Adobe Commerce Cloud, les correctifs de sécurité peuvent être regroupés dans la suite Cloud Tools. Veillez à mettre à niveau la suite ou la version de Commerce pour recevoir ces correctifs.

- **Gestion automatisée des correctifs** : envisagez d’utiliser des outils tels que le répartiteur centralisé pour [gérer et appliquer automatiquement des correctifs dans plusieurs magasins](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale).

>[!TIP]
>
>Pour plus d’informations et des instructions détaillées sur l’application de correctifs et la maintenance de la sécurité, voir les [notes de mise à jour sur les correctifs de sécurité](../../../release/release-notes/security/overview.md) et [Comment appliquer des correctifs de sécurité](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches). Vous devez également consulter les rapports [Outil d’analyse à l’échelle du site](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access) .

#### Conformité PCI

Pour garantir la conformité PCI dans Adobe Commerce Cloud, suivez ces pratiques clés :

- **Données du détenteur de carte Protect** : ne jamais stocker les données du détenteur de carte dans Adobe Commerce. Si le stockage est nécessaire, utilisez des méthodes cryptées et segmentées en unités lexicales pour le protéger.

- **Utiliser des protocoles de transmission sécurisés** : transmettez toujours les données de paiement par le biais de protocoles sécurisés tels que TLS, avec cryptage et gestion correcte des clés.

- **Utilisation du pare-feu d’applications web (WAF)** : le service WAF à vitesse élevée permet de répondre aux exigences de la norme PCI DSS 6.6 et de protéger contre les vulnérabilités courantes en bloquant le trafic malveillant avant qu’il n’atteigne votre site. Voir plus d&#39;informations [ici](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage) et [ici](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service).

- **Limiter l&#39;accès** : assurez-vous que seul le personnel autorisé a accès à des données de paiement sensibles et [appliquez un contrôle d&#39;accès pour réduire le risque d&#39;exposition](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage).

- **Balayage de sécurité régulier** : effectuez des analyses ASV PCI standard et [surveillez votre environnement](https://experienceleague.adobe.com/en/docs/commerce-operations/security-and-compliance/shared-responsibility) pour répondre à des vulnérabilités potentielles.

>[!TIP]
>
>Pour obtenir des instructions plus détaillées sur la maintenance de la conformité PCI avec Adobe Commerce, voir [Bonnes pratiques pour le traitement et le stockage des paiements](../planning/payment-processing-storage.md).

### Assistance utilisateur et clientèle

#### Configuration

- **Canaux d’assistance** : implémentez des canaux d’assistance clientèle tels que :

   - **Chat en direct** : offre une prise en charge en direct du chat pour une assistance immédiate. Les solutions les plus populaires sont Zendesk, Intercom et Tidio.

   - **Support par e-mail** : utilisez un système de tickets d’assistance tel que Freshdesk ou Zoho Desk pour gérer efficacement les demandes de renseignements des clients.

   - **Assistance téléphonique** : si vous disposez d’une grande base de clients, envisagez d’offrir une assistance téléphonique pendant les heures ouvrables.

#### Formation des utilisateurs administrateurs

- **Formation interne** : apprenez à votre personnel à utiliser l’administrateur Adobe Commerce, à traiter les commandes, à gérer les produits et à gérer les problèmes de service client.

- **Documentation** : conservez une base de connaissances interne ou un manuel d’utilisation pour les questions fréquentes, le dépannage et les tâches courantes.

#### Optimisation de l’expérience client

- **Enquêtes et commentaires** : utilisez les enquêtes pour collecter les commentaires des clients et optimiser l’expérience client. Adobe Commerce prend en charge les intégrations avec des outils tels que SurveyMonkey ou Google Forms.

- **Gestion des révisions** : gérez les avis et évaluations des clients sur vos produits. Encourager les clients heureux à laisser des révisions tout en répondant de manière appropriée aux révisions négatives.

- **Personalization** : implémentez des fonctionnalités de personnalisation telles que des recommandations de produits personnalisés ou des promotions ciblées.

### Maintenance et optimisation continues du magasin

#### Optimisation du moteur de recherche (SEO)

- **Optimisation du contenu** : mettez régulièrement à jour les descriptions de produit, les publications de blog et les pages de catégorie afin de préserver le contenu actualisé et pertinent pour les moteurs de recherche.

- **Audits d’optimisation pour les moteurs de recherche** : effectuez régulièrement des audits d’optimisation pour les moteurs de recherche à l’aide d’outils tels que Google Search Console ou Screaming Frog pour identifier les problèmes d’optimisation pour les moteurs de recherche (liens rompus, métadonnées manquantes, contenu en double, par exemple).

- **Structure d’URL** : conservez une structure d’URL logique propre et assurez-vous qu’il n’y a pas de liens ou de redirections rompus.

#### Optimisation du taux de conversion (CRO)

- **Test A/B** : exécutez des tests A/B sur différents éléments de page, tels que les pages de produits ou le processus de passage en caisse, afin d’améliorer les taux de conversion.

- **Abandon de panier** : implémentez des campagnes par e-mail d’abandon de panier ou des fenêtres contextuelles d’intention de sortie pour récupérer les ventes perdues.

- **Optimisation du passage en caisse** : simplifiez votre processus de passage en caisse en réduisant le nombre d’étapes et en offrant un passage en caisse des invités pour améliorer les conversions.

#### Intégration marketing

- **Campagnes par e-mail** : configurez des flux de marketing par e-mail automatisés pour les e-mails de bienvenue, les e-mails abandonnés du panier et les suites après achat. Les plateformes telles qu’Adobe Marketo, Mailchimp ou Klaviyo s’intègrent bien à Adobe Commerce.

- **Intégration des médias sociaux et des publicités** : intégrez à des plateformes telles que Facebook, Instagram et Google Ads pour exécuter des campagnes ciblées et suivre les performances.

#### Optimisation mobile

- **Réactivité mobile** : testez régulièrement la réactivité mobile et la convivialité de votre site. Dans la mesure où le commerce mobile est en croissance, une approche axée sur la téléphonie mobile est essentielle à la poursuite du succès.

- **Performances de l&#39;appareil mobile** : utilisez les outils de test et de performances compatibles avec les appareils mobiles Google pour optimiser votre expérience de magasin mobile.

### Mise à l’échelle et développement de nouvelles fonctionnalités

- **Mise à l’échelle automatique pour la gestion du trafic** :

   - Adobe Commerce Cloud prend en charge la mise à l’échelle automatique afin d’ajuster dynamiquement les ressources du serveur (noeuds web, par exemple) en fonction des demandes de trafic en temps réel, ce qui garantit que votre boutique peut gérer des volumes de visiteurs élevés sans intervention manuelle. Voir [mise à l’échelle automatique](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/autoscaling) dans le _Guide Cloud_.

   - Les niveaux web et de service peuvent se mettre à l’échelle indépendamment, en ajoutant d’autres noeuds web pour augmenter le trafic et en mettant à l’échelle les noeuds de base de données ou de service pour des performances d’arrière-plan pendant les périodes de pointe. Voir [architecture mise à l’échelle](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) dans le _Guide Cloud_.

- **Surveillance des performances** :

   - Utilisez **New Relic** pour surveiller les mesures de performances en temps réel (par exemple, l’utilisation du processeur, les niveaux de trafic) et effectuer des ajustements si nécessaire.

   - Testez les performances dans les environnements d’évaluation avant de procéder à la mise à l’échelle pour éviter des problèmes en production.

- **Développement de nouvelles fonctionnalités** :

   - Intégrez des fonctionnalités avancées telles que la **personnalisation pilotée par l&#39;IA**, la **gestion des abonnements** et des solutions personnalisées.

   - Testez et affinez continuellement les fonctionnalités dans les environnements intermédiaires avant le déploiement en production afin de minimiser les temps d’arrêt.

- **Maintenance en cours du site** :

   - Examinez régulièrement les journaux du système et les mesures de performances pour identifier les améliorations à apporter.

   - Assurez-vous que l’infrastructure reste évolutive et adaptable aux nouveaux besoins et à la croissance de l’entreprise.

>[!TIP]
>
>Pour obtenir des conseils détaillés, reportez-vous aux [bonnes pratiques de maintenance](overview.md), [personnalisation](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization) et [développement de fonctionnalités](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization).

### Rapports et analyses

- **Adobe Commerce Intelligence :** Commerce Intelligence, une fonctionnalité essentielle d’Adobe Commerce, fournit des informations sur les bonnes pratiques de plusieurs sources de données, ce qui permet aux marchands de prendre des décisions scientifiques basées sur les données et de prendre des mesures claires et éclairées. Voir le [_Guide de l’utilisateur de Commerce Intelligence_](https://experienceleague.adobe.com/en/docs/commerce-business-intelligence/mbi/getting-started).

- **Adobe Analytics :** Adobe Analytics offre une solution puissante pour suivre, analyser et optimiser les performances de votre boutique en ligne. Adobe Analytics permet aux entreprises de commerce électronique d’obtenir des informations plus approfondies sur le comportement des clients, les performances des produits, les taux de conversion et d’autres mesures clés, ce qui permet une prise de décision orientée sur les données.

- **Google Analytics :** utilisez des Google Analytics pour effectuer le suivi du comportement des clients, des sources de trafic et des taux de conversion.

- **Outils Commerce Intelligence supplémentaires :** Adobe Commerce inclut le reporting avancé. Cette fonctionnalité vous donne accès à une suite de rapports dynamiques basés sur vos données de produit, de commande et de client, avec un tableau de bord personnalisé adapté aux besoins de votre entreprise. Pour plus d’informations, reportez-vous à la section [création de rapports avancés](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting) du _Guide de l’utilisateur d’administration_ .

### Conclusion

La prise en charge et la maintenance après le lancement sont des efforts constants qui nécessitent une attention particulière pour s’assurer que votre boutique Adobe Commerce continue de fonctionner correctement, reste sécurisée et s’adapte aux besoins de votre entreprise. La mise en oeuvre d’une approche structurée de la surveillance du site, de l’assistance clientèle, de l’optimisation et des mises à jour est essentielle au succès à long terme.
