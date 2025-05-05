---
title: Réponse à un incident de sécurité
description: Gérez les incidents de sécurité en suivant les bonnes pratiques pour répondre aux problèmes de sécurité qui affectent la disponibilité et les performances du site et y remédier.
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: e63f68dd469564e70269154810cbfbd95d2b2e57
workflow-type: tm+mt
source-wordcount: '1172'
ht-degree: 0%

---

# Bonnes pratiques pour répondre à un incident de sécurité

L’article suivant résume les bonnes pratiques pour répondre à un incident de sécurité et résoudre les problèmes qui affectent la disponibilité, la fiabilité et les performances du site Adobe Commerce.

Le respect de ces bonnes pratiques peut contribuer à prévenir les accès non autorisés et les attaques par des logiciels malveillants. Si un incident de sécurité se produit, ces bonnes pratiques vous aident à préparer une réponse immédiate, à effectuer une analyse des causes premières et à gérer le processus de correction pour restaurer les opérations normales.

>[!TIP]
>
>Adobe a constaté que la plupart des incidents de sécurité se produisent lorsque les acteurs de la menace exploitent des vulnérabilités existantes et non corrigées, des mots de passe inappropriés et des paramètres de propriété et d’autorisation faibles dans l’application Commerce et la configuration de l’infrastructure. Réduisez le nombre d’incidents de sécurité en consultant et en suivant les bonnes pratiques de sécurité d’Adobe lors de la configuration, de la configuration et de la mise à jour des installations Adobe Commerce. Voir [Sécuriser votre site et votre infrastructure Commerce](../launch/security-best-practices.md).


## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Réponse à un incident

Si vous pensez que votre projet d’infrastructure cloud Adobe Commerce est affecté par un incident de sécurité, les premières étapes critiques sont les suivantes :

- Contrôle de tous les accès aux comptes d’utilisateur administrateur
- Activation des contrôles d’authentification multifactorielle avancée (MFA)
- Conserver les logs critiques
- Vérifiez les mises à niveau de sécurité de votre version d’Adobe Commerce.

D’autres recommandations sont présentées ci-dessous.

## Agir immédiatement en cas d&#39;attaque

Dans le malheureux cas d&#39;un compromis de site, voici quelques recommandations essentielles à suivre :

- Contactez votre intégrateur système et le personnel de sécurité approprié pour mener des enquêtes et des efforts de correction.

- Déterminer la portée de l&#39;attaque :
   - Les informations de carte de crédit ont-elles été consultées ?
   - Quelles informations ont été volées ?
   - Combien de temps s&#39;est-il écoulé depuis le compromis ?
   - L&#39;information a-t-elle été cryptée ?

- Essayez de trouver le vecteur d&#39;attaque pour déterminer quand et comment le site a été compromis, en examinant les fichiers journaux du serveur et les modifications de fichiers.

   - Dans certains cas, il peut être conseillé d’effacer et de réinstaller tout ou, dans le cas de l’hébergement virtuel, de créer une nouvelle instance. Des logiciels malveillants pourraient être cachés dans un endroit insoupçonné, attendant de se rétablir.

   - Supprimez tous les fichiers inutiles. Ensuite, réinstallez les fichiers requis à partir d’une source connue et propre. Par exemple, vous pouvez réinstaller à l’aide de fichiers de votre système de contrôle de version ou à partir des fichiers de distribution d’origine d’Adobe.

   - Réinitialisez toutes les informations d’identification, y compris la base de données, l’accès aux fichiers, les intégrations de paiement et d’expédition, les services web et la connexion administrateur. Réinitialisez également toutes les clés d’intégration et d’API et tous les comptes qui peuvent être utilisés pour attaquer le système.

## Analyse d’un incident

La première étape de l&#39;analyse des incidents est de rassembler autant de faits que possible, aussi vite que possible. Rassembler des informations sur l’incident peut aider à déterminer la cause potentielle de l’incident. Adobe Commerce fournit les outils ci-dessous pour faciliter votre analyse des incidents.

- [Journaux d’action de l’administrateur d’audit](https://experienceleague.adobe.com/docs/commerce-admin/systems/action-logs/action-log-report.html?lang=fr).

  Le rapport Journaux d’actions affiche un enregistrement détaillé de toutes les actions d’administration activées pour la journalisation. Chaque enregistrement est horodaté et enregistre l’adresse IP et le nom de l’utilisateur. Le détail du journal comprend les données utilisateur de l’administrateur et les modifications associées qui ont été apportées pendant l’action.

- Analysez les événements avec l’outil [Observation pour Adobe Commerce](../../../tools/observation-for-adobe-commerce/intro.md).

  L’outil Observation pour Adobe Commerce vous permet d’analyser des problèmes complexes afin d’identifier les causes profondes. Au lieu de suivre des données disparates, vous pouvez passer votre temps à mettre en corrélation des événements et des erreurs afin d’obtenir des informations plus approfondies sur les causes des goulets d’étranglement en termes de performances.

  Utilisez l’onglet **Sécurité** de l’outil pour obtenir une vue claire des problèmes de sécurité potentiels afin d’identifier les causes premières et de garder les sites à un niveau optimal.

- Analysez les journaux avec [New Relic Logs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html?lang=fr)

  Les projets Adobe Commerce sur l’infrastructure cloud Pro incluent le service [New Relic Logs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management.html?lang=fr). Le service est préconfiguré pour agréger toutes les données de journal de vos environnements d’évaluation et de production afin de les afficher dans un tableau de bord de gestion des journaux centralisé où vous pouvez rechercher et visualiser des données agrégées.

  Pour d’autres projets Commerce, vous pouvez configurer et utiliser le service [New Relic Logs](https://docs.newrelic.com/docs/logs/get-started/get-started-log-management/) pour effectuer les tâches suivantes :
   - Utilisez [des requêtes New Relic](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) pour rechercher des données de journal agrégées.
   - Visualisez les données de journal à l’aide de l’application New Relic Logs.

## Comptes d’audit, code et base de données

Consultez les journaux et les comptes d’administrateur et d’utilisateur de Commerce, le code de l’application et la configuration de la base de données pour identifier et nettoyer le code suspect et assurer la sécurité de l’accès au compte, au site et à la base de données. Ensuite, redéployez selon les besoins.

Continuez à surveiller de près le site après l&#39;incident, car de nombreux sites sont de nouveau compromis en quelques heures. Assurez-vous que la révision des journaux et la surveillance de l’intégrité des fichiers sont en cours afin de détecter rapidement tout signe de nouveau compromis.

### Comptes d’utilisateurs administrateurs d’audit

- [ Vérifiez l’accès des utilisateurs administrateurs ](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html?lang=fr) : supprimez les comptes anciens, inutilisés ou suspects et faites pivoter les mots de passe de tous les utilisateurs administrateurs.

- [Vérifiez les paramètres de sécurité d’administrateur](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html?lang=fr) : vérifiez que les paramètres de sécurité d’administrateur suivent les bonnes pratiques en matière de sécurité.

- [ Vérifiez les comptes d’utilisateurs d’Adobe Commerce sur les projets d’infrastructure cloud ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=fr) : supprimez les comptes anciens, inutilisés ou suspects et faites pivoter les mots de passe de tous les utilisateurs administrateurs de projet cloud. Vérifiez que les paramètres de sécurité du compte sont correctement configurés.

- [ Audit des clés SSH](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=fr) pour Adobe Commerce sur l’infrastructure cloud : vérifiez, supprimez et faites pivoter les clés SSH.

### Code d’audit

- À partir de l’administrateur, passez en revue la [configuration HTML Header and Footer](https://experienceleague.adobe.com/docs/commerce-admin/content-design/design/page-setup.html?lang=fr) à tous les niveaux de portée, y compris `website` et `store view`. Supprimez tout code JavaScript inconnu des scripts et des feuilles de style, ainsi que des paramètres d’HTML divers. Conservez uniquement le code reconnu tel que les fragments de code de suivi.

- Comparez la base de code de production actuelle à la base de code stockée dans le système de contrôle de version (VCS).

- Mettre en quarantaine tout code suspect.

- S’assurer qu’il n’y a pas de restes de code suspect en redéployant le code base dans l’environnement de production.

### Suivi de la configuration et des journaux de la base de données

- Examinez les procédures stockées pour les modifications.

- Vérifiez que la base de données n’est accessible que par l’instance Commerce.

- Vérifiez que les logiciels malveillants ne sont plus présents en analysant le site à l’aide d’outils de numérisation de programmes malveillants accessibles au public.

- Sécurisez le panneau d’administration en modifiant son nom et en vérifiant que les URL de site `app/etc/local.xml` et `var` ne sont pas accessibles au public.

- Continuez à surveiller de près le site après l&#39;incident, car de nombreux sites sont de nouveau compromis en quelques heures. Assurez-vous que la révision des journaux et la surveillance de l’intégrité des fichiers sont en cours afin de détecter rapidement tout signe de nouveau compromis.

## Suppression des avertissements Google

Si le site a été marqué par Google comme contenant du code malveillant, demandez une révision une fois le site nettoyé. Les analyses pour les sites infectés par un logiciel malveillant prennent quelques jours. Une fois que Google a déterminé que le site est propre, les avertissements des résultats de recherche et des navigateurs doivent disparaître dans les 72 heures. Voir [Demande d’une révision](https://web.dev/articles/request-a-review).

## Consultez la liste de contrôle des résultats malveillants

Si des outils de numérisation de programmes malveillants accessibles au public confirment une attaque de programmes malveillants, enquêtez sur l&#39;incident. Travaillez avec l’intégrateur de solution pour nettoyer le site et suivre le processus de correction recommandé.

## Réaliser des révisions supplémentaires

Lorsque vous traitez d’attaques complexes, la meilleure ligne de conduite consiste à collaborer avec un développeur expérimenté, un expert tiers ou un intégrateur de solutions pour réparer entièrement le site et passer en revue les pratiques de sécurité. Collaborez avec des professionnels de la sécurité expérimentés afin de vous assurer que des mesures complètes et avancées sont prises pour garantir la sécurité de votre entreprise et de ses clients.

## Informations supplémentaires

- [Structure d’analyse de cause racine](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
