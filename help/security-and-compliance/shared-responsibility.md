---
title: Responsabilité partagée
description: Découvrez les responsabilités en matière de sécurité de chaque partie impliquée dans votre projet d’infrastructure cloud Adobe Commerce.
source-git-commit: d216418c69cb972e93c04b5d5cc0a8ab0495653d
workflow-type: tm+mt
source-wordcount: '1562'
ht-degree: 0%

---


# Modèle de sécurité de la responsabilité partagée

Adobe Commerce sur l’infrastructure cloud est une offre de plateforme en tant que service (PaaS) qui repose sur un modèle de sécurité de responsabilité partagée. Adobe, le commerçant, le fournisseur de services cloud et le fournisseur de réseau de diffusion de contenu (CDN) assument chacun une responsabilité distincte pour la maintenance de la sécurité d’Adobe Commerce sur l’application d’infrastructure cloud et sur les extensions et le code spécifiques au marché.

Cette approche permet aux commerçants de concevoir et de mettre en oeuvre une solution hautement flexible, personnalisable et évolutive qui répond le mieux aux besoins de leur entreprise tout en réduisant au minimum les responsabilités et les coûts opérationnels.

En règle générale, Adobe est chargé de développer et de gérer le code de l’application principale sécurisé, de maintenir la sécurité de la plate-forme, d’assurer la conformité de la norme SOC 2 et PCI de la plate-forme et sa compatibilité avec les composants de technologie compatibles PCI (par exemple, PHP, Redis) et de répondre aux problèmes de sécurité concernant la plate-forme principale. Adobe est également chargé de travailler avec les fournisseurs de services cloud et les partenaires CDN pour résoudre les problèmes qui peuvent survenir.

Les commerçants sont chargés de la maintenance de code personnalisé sécurisé et des intégrations avec des applications tierces, de la sécurité du développement des applications, de l’obtention de la certification PCI si le responsable du paiement du commerçant le demande, ainsi que de la réaction et de la réponse aux incidents de sécurité.

## Responsabilités d’Adobe

Adobe est responsable de la sécurité et de la disponibilité d’Adobe Commerce dans l’environnement d’infrastructure cloud et d’Adobe Commerce principal dans le code de solution d’infrastructure cloud. En outre, Adobe est responsable des activités et mécanismes nécessaires pour maintenir la sécurité d’Adobe Commerce sur la solution d’infrastructure cloud, notamment :

- Application de correctifs et de sécurité au niveau du serveur pour les applications prises en charge par Adobe Commerce sur l’infrastructure cloud, telles que le stockage des données dans le cloud et les fonctionnalités de recherche
- Test de pénétration et analyse du code d’infrastructure cloud de base d’Adobe Commerce
- Réaliser des révisions/audits semestriels de la solution de gestion des identités et des accès des fournisseurs de services cloud publics (IAM) et de la gestion des autorisations (exigences de conformité PCI)
- Réaliser des révisions/audits semestriels des utilisateurs autorisés, y compris les employés et les entrepreneurs Adobes (exigence de conformité PCI)
- Exécution de tests annuels et de documentation sur les fonctionnalités de sauvegarde et de restauration
- Configuration des pare-feu du serveur et du périmètre
- Connexion et configuration d’Adobe Commerce dans le référentiel d’infrastructure cloud
- Définir, tester, mettre en oeuvre et documenter les plans de reprise après sinistre pour les zones relevant de la responsabilité de l&#39;Adobe
- Définition des règles de pare-feu d’application web de plateforme globale (WAF)
- Renforcement du système d’exploitation
- Mise en oeuvre et maintenance de l’intégration des solutions CDN (Content Distribution Network) et de gestion des performances des applications (APM) avec Adobe Commerce sur l’infrastructure cloud
- Emission de mises à jour de sécurité périodiques et autres pour le code principal d’Adobe Commerce sur l’infrastructure cloud (l’application de correctifs est de la responsabilité du commerçant)
- Gestion de l’assistance et des contrôles d’accès du commerce (Zendesk, par exemple)
- Surveillance, journalisation et correction des incidents de sécurité concernant l’infrastructure de la plateforme d’infrastructure cloud d’Adobe Commerce
- Surveillance des opérations de la plateforme et prise en charge 24/7 d’Adobe Commerce sur les marchands d’infrastructure cloud
- Mise en service des environnements de production et d’évaluation
- Évaluation des menaces potentielles pour la sécurité des opérations et de l’infrastructure de la plateforme
- Mise à l’échelle de l’informatique, du stockage, de la grille et d’autres ressources, comme décrit dans l’accord de niveau de service (SLA) avec le marchand
- Configuration du DNS (Adobe Commerce sur l’infrastructure de la plateforme d’infrastructure cloud uniquement)
- Test de la plateforme pour détecter des failles de sécurité

Bien qu’Adobe conserve la certification PCI pour l’infrastructure et les services utilisés dans le fonctionnement d’Adobe Commerce sur la solution d’infrastructure cloud, les marchands sont responsables de la conformité du code personnalisé, des processus système et réseau et de l’organisation.

L&#39;Adobe assure également la disponibilité de l&#39;infrastructure du marchand, comme convenu dans le contrat de niveau de service applicable.

## Responsabilités du marché

Le marchand est chargé de suivre les bonnes pratiques de sécurité pour son instance spécifique et personnalisée d’Adobe Commerce sur la solution d’infrastructure cloud, et pour :

- Ajout des fichiers de configuration d’Adobe Commerce nécessaires sur l’infrastructure cloud au référentiel
- Application de correctifs de sécurité et autres à leur Adobe Commerce personnalisé sur la solution d’infrastructure cloud immédiatement après leur publication par Adobe
- Application de correctifs de sécurité et autres à toutes les extensions et codes personnalisés, immédiatement après leur publication par le fournisseur
- Création, déploiement et test de fichiers VCL Varnish personnalisés
- Conception, mise en page, installation, intégration et sécurisation d’Adobe Commerce personnalisé sur la solution d’infrastructure cloud, y compris toutes les extensions personnalisées et le code
- Octroi et révocation de l’accès de l’utilisateur à l’instance du commerçant d’Adobe Commerce sur la configuration, l’application et la plateforme de l’infrastructure cloud
- Gestion des problèmes de sécurité liés au réseau interne, aux serveurs, à l’infrastructure et à toute application personnalisée du site commercial créée sur Adobe Commerce sur la plateforme d’infrastructure cloud
- Installation de l’outil d’intégration de ligne de commande d’Adobe Commerce on Cloud Infrastructure
- Maintenir le niveau requis de conformité PCI de l’application personnalisée et d’autres processus internes, tel que défini par les directives PCI-DSS

  >[!NOTE]
  >
  >La conformité PCI du commerçant repose sur les certifications PCI d’Adobe Commerce sur l’infrastructure cloud et le fournisseur d’hébergement cloud afin de minimiser les zones à examiner.

- Exécution d’analyses ASV PCI et résolution de problèmes dans le noyau d’Adobe Commerce sur le code et la plateforme d’infrastructure cloud
- Surveillance de toutes les activités d’application susceptibles de révéler une menace potentielle pour la sécurité, y compris les tests de pénétration, les analyses des vulnérabilités et les journaux
- Surveillance des incidents de sécurité et intervention en cas d’incident, y compris la médecine légale, la correction et la création de rapports liés à Adobe Commerce du commerçant sur la solution d’infrastructure cloud et les comptes d’utilisateurs
- Obtention d’un fournisseur DNS et configuration et maintenance de tout enregistrement DNS spécifique au détaillant
- Exécution de tests de performance sur l’application personnalisée
- Sécurisation de l’accès aux comptes de la plateforme, à l’accès aux instances et aux applications
- Test et contrôle qualité de l’application personnalisée
- Maintien de la sécurité de tous les systèmes ou réseaux que le commerçant se connecte à Adobe Commerce sur l’application d’infrastructure cloud

## Responsabilités du fournisseur de services cloud

Adobe s’appuie sur des fournisseurs de services cloud bien établis pour héberger l’infrastructure de serveur cloud pour Adobe Commerce sur l’infrastructure cloud. Ces fournisseurs sont chargés de la sécurité du réseau, notamment le routage, le changement et la sécurité du réseau de périmètre par le biais de systèmes de pare-feu et de systèmes de détection d’intrusion (IDS). Les fournisseurs de services cloud sont également responsables de la sécurité physique des centres de données qui hébergent Adobe Commerce sur la solution d’infrastructure cloud et de la sécurité environnementale des centres de données.

Les fournisseurs de services cloud sont également responsables des éléments suivants :

- Maintenance des certifications PCI DSS, SOC 2 et ISO 27001 pour leurs services cloud
- Sécurisation de l’hyperviseur
- Sécurisation du centre de données, y compris l’accès physique et réseau

## Responsabilités du fournisseur CDN

La solution d’infrastructure cloud d’Adobe Commerce utilise les fournisseurs CDN pour accélérer le temps de chargement des pages, mettre en cache le contenu et purger instantanément le contenu obsolète. Ces fournisseurs sont également responsables des problèmes de sécurité directement liés à leur réseau de diffusion de contenu ou affectant celui-ci, ainsi que de la définition et de la maintenance des règles de diffusion de contenu de contenu de diffusion de contenu.

## Graphique des responsabilités en matière de sécurité

Le graphique suivant utilise le modèle de l’IRAC (R — Responsable, A — Responsable, C — Responsable, C — Consulté, I — Informé) pour représenter visuellement chaque partie dans les responsabilités de sécurité de l’écosystème concernant Adobe Commerce sur le modèle de responsabilité partagée de l’infrastructure cloud :

<table>
<thead>
  <tr>
    <th>Tâche</th>
    <th>Adobe</th>
    <th>Marchand</th>
    <th>Fournisseur de services cloud</th>
    <th>fournisseur CDN</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Application d’Adobe Commerce aux correctifs d’infrastructure cloud</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Application de correctifs aux services de support<br>(par exemple, Nginx, MySQL)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Définition des règles WAF d’origine</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Définition des règles CDN WAF</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Déploiement des règles WAF de la plateforme</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Déploiement des règles CDN WAF</td>
    <td>A</td>
    <td>I</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Correction de bogues principaux dans Adobe Commerce sur le code d’infrastructure cloud</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Mise à jour d’Adobe Commerce sur les correctifs d’infrastructure cloud</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Mise à l’échelle (calcul et stockage)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Mise à l’échelle (PaaS/grid)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Garantir l’accès au code source, y compris repo.magento.com</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installation d’Adobe Commerce sur l’outil d’interface de ligne de commande de l’infrastructure cloud</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Ajout de fichiers de configuration d’infrastructure cloud à Adobe Commerce dans le référentiel</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Création d’un projet pour le marchand (interface utilisateur d’intégration)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Connexion du/des référentiel(s) à Adobe Commerce sur l’infrastructure cloud</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Configuration du référentiel source<sup>1</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Création d’un utilisateur pour le gestionnaire de versions (interface utilisateur d’intégration)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Déploiement du code en production</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Déploiement du code dans l’évaluation</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Intégration d’applications et d’extensions externes</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installation d’extensions</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Personnalisation d’Adobe Commerce sur l’infrastructure cloud</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Test des performances d’Adobe Commerce personnalisé sur l’infrastructure cloud</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Test d’une application personnalisée</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Thème et conception d’une application personnalisée</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
    <tr>
    <td>Création, déploiement et test de VCL Varnish personnalisées</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Configuration du DNS (infrastructure de plateforme uniquement)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Développement de l’extension CDN et résolution de bogues</td>
    <td>A</td>
    <td>C</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Intégration au réseau CDN</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Prise en charge de CDN<sup>2</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>Configuration de l’APM/infrastructure New Relic</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installation de New Relic APM/infrastructure</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Support de l’APM/infrastructure New Relic</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Configuration de Nginx<sup>3</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Obtention du fournisseur DNS (pour uniquement)</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Renforcement du système d’exploitation</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Mise en service des environnements de production et d’évaluation</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Accès à Zendesk pour Adobe Commerce sur l’infrastructure cloud</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Résolution des problèmes de sécurité du commerce</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>Résolution des problèmes de sécurité de l’infrastructure cloud d’Adobe Commerce</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Résolution des problèmes de sécurité du réseau CDN</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Résolution des problèmes de sécurité d’APM</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Aider l'Adobe à la recherche sur la sécurité (logiciel)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Aider l'Adobe à la recherche sur la sécurité (analyses/audits)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Exécution de scanners PCI ASV</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Correction d’Adobe Commerce sur les scans PCI de l’infrastructure cloud<sup>4</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Correction des scans PCI PaaS</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Gestion des secrets de système d’exploitation et de plateforme</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Gestion d’Adobe Commerce sur les clés de chiffrement de l’infrastructure cloud</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Analyse d’Adobe Commerce personnalisé sur les instances d’infrastructure cloud</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Surveillance des logs de sécurité</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Gestion de l’IAM et des autorisations pour Adobe Commerce sur l’infrastructure cloud</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Gestion des contrôles d'accès de l'assistance (Teleport)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Contrôle de l’assistance et de l’accès du commerce</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Tests annuels et documentation du plan de sauvegarde et de restauration de l’Adobe DR</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Test annuel et documentation du plan de reprise sur sinistre</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
<tfoot>
  <tr>
    <td colspan="5">
      <p><sup><strong>1</strong></sup> Uniquement si le référentiel Adobe Commerce sur l’infrastructure cloud est utilisé comme référentiel principal. L'utilisation d'autres référentiels externes est la seule responsabilité du marchand.</p>
      <p><sup><strong>2</strong></sup> Adobe fournit une prise en charge de niveau 1 pour les problèmes avec les fournisseurs de réseau de diffusion de contenu.</p>
      <p><sup><strong>3</strong></sup> Certains contrôles Ngnix sont configurés par le commerçant pour leurs applications et sont de leur responsabilité.</p>
      <p><sup><strong>4</strong></sup> Pour les PCI, les exigences de test de pénétration sont partagées entre l’Adobe et le marchand.</p>
    </td>
  </tr>
</tfoot>
</table>
