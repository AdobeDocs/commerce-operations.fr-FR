---
title: Intervention en cas d’incident de sécurité
description: Gérer les incidents de sécurité en suivant les bonnes pratiques pour répondre et résoudre les problèmes de sécurité qui affectent la disponibilité et les performances du site.
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: e63f68dd469564e70269154810cbfbd95d2b2e57
workflow-type: tm+mt
source-wordcount: '1172'
ht-degree: 0%

---

# Bonnes pratiques pour répondre à un incident de sécurité

L’article suivant résume les bonnes pratiques pour répondre à un incident de sécurité et résoudre les problèmes qui affectent la disponibilité, la fiabilité et les performances du site Adobe Commerce.

Le respect de ces bonnes pratiques peut contribuer à prévenir les accès non autorisés et les attaques de programmes malveillants. Si un incident de sécurité se produit, ces bonnes pratiques vous aident à vous préparer à une réponse immédiate, à effectuer une analyse des causes profondes et à gérer le processus de correction pour restaurer les opérations normales.

>[!TIP]
>
>Adobe a constaté que la plupart des incidents de sécurité se produisent lorsque des acteurs malveillants tirent parti de vulnérabilités existantes non corrigées, de mots de passe inappropriés ainsi que de paramètres de propriété et d’autorisation faibles dans la configuration de l’application et de l’infrastructure Commerce. Minimisez l’occurrence des incidents de sécurité en examinant et en suivant les bonnes pratiques de sécurité d’Adobe lors de la configuration, de la configuration et de la mise à jour des installations d’Adobe Commerce. Voir [&#x200B; Sécurisation de votre site et de votre infrastructure Commerce](../launch/security-best-practices.md).


## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

## Réponse à un incident

Si vous pensez que votre projet Adobe Commerce sur l’infrastructure cloud est affecté par un incident de sécurité, les premières étapes critiques sont les suivantes :

- Contrôler l’accès à tous les comptes d’utilisateurs administrateurs
- Activer les contrôles avancés d’authentification multifacteur (MFA)
- Conserver les journaux critiques
- Passez en revue les mises à niveau de sécurité pour votre version d’Adobe Commerce.

D’autres recommandations sont présentées ci-dessous.

## Prendre des mesures immédiates en cas d&#39;attaque

Dans le cas malheureux d’un compromis sur le site, voici quelques recommandations clés à suivre :

- Faites appel à l’intégrateur système et au personnel de sécurité approprié pour mener les enquêtes et prendre les mesures correctives nécessaires.

- Déterminez la portée de l’attaque :
   - Les informations de carte de crédit ont-elles été consultées ?
   - Quelles informations ont été volées ?
   - Combien de temps s&#39;est-il écoulé depuis le compromis ?
   - L&#39;information était-elle chiffrée ?

- Essayez de trouver le vecteur d&#39;attaque pour déterminer quand et comment le site a été compromis, en examinant les fichiers journaux du serveur et les modifications apportées aux fichiers.

   - Dans certains cas, il peut être conseillé de tout effacer et de tout réinstaller ou, dans le cas d’un hébergement virtuel, de créer une nouvelle instance. Les logiciels malveillants peuvent être cachés dans un emplacement insoupçonné juste en attendant de se restaurer.

   - Supprimez tous les fichiers inutiles. Ensuite, réinstallez les fichiers requis à partir d’une source propre connue. Par exemple, vous pouvez réinstaller à l’aide des fichiers de votre système de contrôle de version ou des fichiers de distribution d’origine d’Adobe.

   - Réinitialisez toutes les informations d’identification, notamment la base de données, l’accès aux fichiers, les intégrations de paiement et d’expédition, les services web et la connexion administrateur. Réinitialisez également toutes les clés d’intégration et d’API ainsi que tous les comptes pouvant être utilisés pour attaquer le système.

## Analyse d’un incident

La première étape de l’analyse des incidents consiste à rassembler autant de faits que possible, aussi rapidement que possible. La collecte d&#39;informations sur l&#39;incident peut aider à déterminer la cause potentielle de l&#39;incident. Adobe Commerce fournit les outils ci-dessous pour vous aider à analyser les incidents.

- [Journaux des actions d’administration d’audit](https://experienceleague.adobe.com/docs/commerce-admin/systems/action-logs/action-log-report.html?lang=fr).

  Le rapport Journaux d’actions affiche un enregistrement détaillé de toutes les actions d’administration activées pour la journalisation. Chaque enregistrement est horodaté et enregistre l’adresse IP et le nom de l’utilisateur. Les détails du journal incluent les données utilisateur de l’administrateur et les modifications associées qui ont été effectuées lors de l’action.

- Analysez les événements à l’aide de l’outil [Observation pour Adobe Commerce](../../../tools/observation-for-adobe-commerce/intro.md).

  L’outil Observation pour Adobe Commerce vous permet d’analyser des problèmes complexes afin d’en identifier les causes profondes. Au lieu de suivre des données disparates, vous pouvez passer votre temps à corréler les événements et les erreurs afin d’obtenir des informations plus précises sur les causes des goulots d’étranglement au niveau des performances.

  Utilisez l’onglet **Sécurité** de l’outil pour obtenir une vue claire des problèmes de sécurité potentiels afin d’identifier les causes premières et de garantir des performances optimales des sites.

- Analysez les journaux avec [Journaux New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html?lang=fr)

  Les projets Pro d’Adobe Commerce sur les infrastructures cloud incluent le service [Journaux New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management.html?lang=fr). Le service est préconfiguré pour agréger toutes les données de journal de vos environnements d’évaluation et de production afin de les afficher dans un tableau de bord de gestion des journaux centralisé où vous pouvez rechercher et visualiser des données agrégées.

  Pour d’autres projets Commerce, vous pouvez configurer et utiliser le service [Journaux New Relic](https://docs.newrelic.com/docs/logs/get-started/get-started-log-management/) pour effectuer les tâches suivantes :
   - Utilisez [Requêtes New Relic](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) pour rechercher des données de journal agrégées.
   - Visualisez les données de journal via l’application Journaux New Relic.

## Comptes, code et base de données d’audit

Examinez les comptes d’administration et d’utilisateur Commerce, le code de l’application, la configuration et les journaux de la base de données pour identifier et nettoyer le code suspect et assurer la sécurité de l’accès au compte, au site et à la base de données. Redéployez ensuite l’application selon vos besoins.

Continuez à surveiller de près le site après l&#39;incident, car de nombreux sites sont à nouveau compromis en quelques heures. Garantissez une révision continue des journaux et une surveillance de l’intégrité des fichiers pour détecter rapidement tout signe de nouvelle compromission.

### Comptes utilisateur Audit Admin

- [Vérifier l&#39;accès des utilisateurs administrateurs](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html?lang=fr)—Supprimez les anciens comptes inutilisés ou suspects et faites pivoter les mots de passe pour tous les utilisateurs administrateurs.

- [Vérification des paramètres de sécurité d&#39;administration](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html?lang=fr)—Vérifiez que les paramètres de sécurité d&#39;administration suivent les bonnes pratiques de sécurité.

- [Vérification des comptes utilisateur pour Adobe Commerce dans les projets d’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=fr)—Supprimez les anciens comptes inutilisés ou suspects et faites pivoter les mots de passe pour tous les utilisateurs administrateurs de projets cloud. Vérifiez que les paramètres de sécurité du compte sont correctement configurés.

- [Vérification des clés SSH](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=fr) pour Adobe Commerce sur les infrastructures cloud : révision, suppression et rotation des clés SSH.

### Code audit

- Depuis l’administration, passez en revue la configuration [En-tête et pied de page HTML](https://experienceleague.adobe.com/docs/commerce-admin/content-design/design/page-setup.html?lang=fr) à tous les niveaux de l’étendue, y compris `website` et `store view`. Supprimez tout code JavaScript inconnu des scripts et des feuilles de style, ainsi que divers paramètres d’HTML. Conserver uniquement le code reconnu tel que les fragments de code de suivi.

- Comparez la base de code de production actuelle à la base de code stockée dans le système de contrôle de version (VCS).

- Mettre en quarantaine tout code suspect.

- Assurez-vous qu’il n’existe aucun reste de code suspect en redéployant la base de code vers l’environnement de production.

### Configuration et journaux de la base de données d’audit

- Examinez les procédures stockées pour y apporter des modifications.

- Vérifiez que la base de données n&#39;est accessible que par l&#39;instance Commerce.

- Vérifiez que les logiciels malveillants ne sont plus présents en analysant le site à l&#39;aide d&#39;outils d&#39;analyse de logiciels malveillants accessibles au public.

- Sécurisez le panneau d’administration en modifiant son nom et en vérifiant que les `app/etc/local.xml` du site et les URL `var` ne sont pas accessibles au public.

- Continuez à surveiller de près le site après l&#39;incident, car de nombreux sites sont à nouveau compromis en quelques heures. Garantissez une révision continue des journaux et une surveillance de l’intégrité des fichiers pour détecter rapidement tout signe de nouvelle compromission.

## Supprimer les avertissements Google

Si le site a été marqué par Google comme contenant du code malveillant, demandez une révision une fois le site nettoyé. Les avis pour les sites infectés par un malware prennent quelques jours. Une fois que Google a déterminé que le site est propre, les avertissements des résultats de recherche et des navigateurs doivent disparaître dans les 72 heures. Voir [Demander un examen](https://web.dev/articles/request-a-review).

## Vérifier la liste de contrôle des résultats des programmes malveillants

Si des outils d&#39;analyse de programmes malveillants accessibles au public confirment une attaque de programmes malveillants, enquêter sur l&#39;incident. Collaborez avec l’intégrateur de solutions pour nettoyer le site et suivre le processus de remédiation recommandé.

## Réalisation d’examens supplémentaires

Face à des attaques sophistiquées, la meilleure solution consiste à collaborer avec un développeur expérimenté, un tiers expert ou un intégrateur de solution pour réparer entièrement le site et passer en revue les pratiques de sécurité. Travailler avec des professionnels de la sécurité expérimentés permet de prendre des mesures complètes et avancées pour assurer la sécurité de votre entreprise et de ses clients.

## Informations supplémentaires

- [Structure d’analyse des causes premières](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
