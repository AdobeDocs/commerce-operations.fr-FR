---
title: Sécurité de la responsabilité partagée et modèle opérationnel
description: Découvrez les responsabilités en matière de sécurité de chaque partie impliquée dans votre projet d’infrastructure cloud Adobe Commerce.
exl-id: f3cc1685-e469-4e30-b18e-55ce10dd69ce
source-git-commit: d4ea2f3fe8d30749c96389655ef38cae482afc99
workflow-type: tm+mt
source-wordcount: '2770'
ht-degree: 0%

---

# Sécurité de la responsabilité partagée et modèle opérationnel

Adobe Commerce sur l’infrastructure cloud est une offre de plateforme en tant que service (PaaS) qui repose sur une sécurité de responsabilité partagée et un modèle opérationnel. Ces responsabilités sont partagées entre l’Adobe, le commerçant, le fournisseur de services cloud et le fournisseur de réseau de diffusion de contenu (CDN). Chaque partie a une responsabilité distincte pour la sécurisation et l’exploitation de l’application Adobe Commerce ainsi que du code et des extensions spécifiques au marché déployés sur l’infrastructure cloud.

Ce modèle partagé permet aux commerçants de concevoir et de mettre en oeuvre une solution hautement flexible, personnalisable et évolutive pour répondre aux besoins de leur entreprise tout en réduisant au minimum les responsabilités et les coûts opérationnels.

En règle générale, l’Adobe est responsable des éléments suivants :

- Développement et maintenance d’un code d’application principal sécurisé
- Maintenir la sécurité de la plateforme
- S’assurer que la plate-forme est conforme à la norme SOC 2 et PCI et compatible avec les composants de technologie compatibles PCI (par exemple, PHP, Redis)
- Réagir aux problèmes de sécurité de la plateforme principale
- Utilisation des fournisseurs de services cloud et des partenaires CDN pour résoudre les problèmes qui se produisent

Les commerçants sont responsables des éléments suivants :

- Maintenance de la sécurité pour le code personnalisé et les intégrations avec des applications tierces
- Assurer le développement sécurisé des applications
- Obtention de la certification PCI si le responsable du paiement du site commercial le demande
- Réagir et réagir aux incidents de sécurité

## Responsabilités d’Adobe

Adobe est responsable de la sécurité et de la disponibilité d’Adobe Commerce dans l’environnement d’infrastructure cloud et du code de la solution principale. En outre, Adobe est responsable des activités et mécanismes nécessaires pour maintenir la sécurité d’Adobe Commerce sur la solution d’infrastructure cloud, notamment :

- Application de correctifs et de sécurité au niveau du serveur pour les applications prises en charge par Adobe Commerce sur l’infrastructure cloud, telles que le stockage des données dans le cloud et les fonctionnalités de recherche
- Test de pénétration et analyse du code d’infrastructure cloud de base d’Adobe Commerce
- Réaliser des révisions et des audits semestriels des solutions de gestion des identités et des accès des fournisseurs de services cloud publics (IAM) et de la gestion des autorisations (exigences de conformité PCI)
- Réaliser des révisions et des audits semestriels des utilisateurs autorisés, y compris les employés et les entrepreneurs Adobes (exigence de conformité PCI)
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

Adobe gère la certification PCI pour l’infrastructure et les services utilisés pour la solution Adobe Commerce.  Les commerçants sont responsables de la conformité du code personnalisé, des processus système et réseau, ainsi que de l’organisation.

L&#39;Adobe assure également la disponibilité de l&#39;infrastructure du marchand, comme convenu dans le contrat de niveau de service applicable.

## Responsabilités du marché

Le marchand est responsable des bonnes pratiques de sécurité suivantes pour son instance personnalisée spécifique d’Adobe Commerce sur la solution d’infrastructure cloud :

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
  >Afin de minimiser les zones à examiner, la conformité PCI du commerçant est basée sur les certifications PCI d’Adobe Commerce et du fournisseur d’hébergement dans le cloud.

- Exécution d’analyses ASV PCI et résolution de problèmes dans le noyau d’Adobe Commerce sur le code et la plateforme d’infrastructure cloud
- Surveillance de toutes les activités d’application susceptibles de révéler une menace potentielle pour la sécurité, y compris les tests de pénétration, les analyses des vulnérabilités et les journaux
- Surveillance des incidents de sécurité et intervention en cas d’incident, y compris la médecine légale, la correction et la création de rapports liés à Adobe Commerce du commerçant sur la solution d’infrastructure cloud et les comptes d’utilisateurs
- Obtention d’un fournisseur DNS et configuration et maintenance de tout enregistrement DNS spécifique au détaillant
- Exécution de tests de performance sur l’application personnalisée
- Sécurisation de l’accès aux comptes de la plateforme, à l’accès aux instances et aux applications
- Test et contrôle qualité de l’application personnalisée
- Maintien de la sécurité de tous les systèmes ou réseaux que le commerçant se connecte à Adobe Commerce sur l’application d’infrastructure cloud

## Responsabilités du fournisseur Cloud Service

Adobe s’appuie sur des fournisseurs de services cloud bien établis pour héberger l’infrastructure de serveur cloud pour Adobe Commerce sur l’infrastructure cloud. Ces fournisseurs sont chargés de la sécurité du réseau, notamment le routage, le changement et la sécurité du réseau de périmètre par le biais de systèmes de pare-feu et de systèmes de détection d’intrusion (IDS). Les fournisseurs de services cloud sont également responsables de la sécurité physique des centres de données qui hébergent Adobe Commerce sur la solution d’infrastructure cloud et de la sécurité environnementale des centres de données.

Les fournisseurs de services cloud sont également responsables des éléments suivants :

- Maintenance des certifications PCI DSS, SOC 2 et ISO 27001 pour leurs services cloud
- Sécurisation de l’hyperviseur
- Sécurisation du centre de données, y compris l’accès physique et réseau

## Responsabilités du fournisseur CDN

La solution d’infrastructure cloud d’Adobe Commerce utilise les fournisseurs CDN pour accélérer le temps de chargement des pages, mettre en cache le contenu et purger instantanément le contenu obsolète. Ces fournisseurs sont également responsables des problèmes de sécurité directement liés à leur réseau de diffusion de contenu ou affectant celui-ci, ainsi que de la définition et de la maintenance des règles de diffusion de contenu de contenu de diffusion de contenu.

## Résumé des responsabilités de sécurité

>[!BEGINSHADEBOX]

Le tableau récapitulatif suivant utilise le modèle RACI pour afficher les responsabilités de sécurité partagées entre l’Adobe, le commerçant et le fournisseur de services Cloud :

**R** — Responsable
**A** — Responsable
**C** — Consulté
**I** — Informé

>[!ENDSHADEBOX]

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
    <td>Application de correctifs aux services de support<br>(Par exemple, Nginx ou MySQL.)</td>
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
    <td>Mise à l’échelle (PaaS et grille)</td>
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
    <td>Connexion de référentiels à Adobe Commerce sur l’infrastructure cloud</td>
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
    <td>Test de l’application personnalisée</td>
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
    <td>Configuration des applications New Relic APM et d’infrastructure</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installation des applications New Relic APM et d’infrastructure</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Prise en charge des applications New Relic APM et d’infrastructure</td>
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
    <td>Obtention d’un fournisseur DNS (pour uniquement)</td>
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
      <p><sup><strong>3</strong></sup> Le commerçant est responsable de tout contrôle Ngnix qu’il configure pour ses applications.</p>
      <p><sup><strong>4</strong></sup> Pour les PCI, les exigences de test de pénétration sont partagées entre l’Adobe et le marchand.</p>
    </td>
  </tr>
</tfoot>
</table>

## Résumé des responsabilités opérationnelles

>[!BEGINSHADEBOX]

Les tableaux de synthèse ci-après clarifient les responsabilités opérationnelles d’Adobe et de Merchants lors du développement, du déploiement, de la maintenance et de la sécurisation d’Adobe Commerce sur l’infrastructure cloud.

>[!ENDSHADEBOX]

### Codage et développement

#### Code Adobe Commerce principal

|     | Adobe | Marchand |
| --- | --- | --- |
| Publication de mises à jour et de correctifs sur Adobe Commerce core | R |     |
| Disponibilité et correction du système de fichiers | R |  |
| Publication de mises à jour et de correctifs dans les outils de la CEE | R |     |
| Qualité de l’application Adobe Commerce principale | R |     |

{style="table-layout:auto"}

#### Référentiel de code

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité de repo.magento.com | R |     |
| Disponibilité d’Adobe Commerce sur le serveur Cloud Git | R |     |
| Autres référentiels de code sélectionnés par le marché (GitHub, Bitbucket, serveur Git hébergé) |     | R |

{style="table-layout:auto"}

#### Cloud Docker

|     | Adobe | Marchand |
| --- | --- | --- |
| Mise à disposition des conteneurs Cloud Docker pour téléchargement | R |   |
| Déploiement et configuration de Cloud Docker (facultatif) |     | R |
| Toute autre configuration de développement local |     | R |

{style="table-layout:auto"}

#### CLI COMMERCE CLOUD

|     | Adobe | Marchand |
| --- | --- | --- |
| Qualité et mise à jour continues des outils de la CEE | R |   |
| Installation de la dernière version des outils CEE |     | R |

{style="table-layout:auto"}

#### Personnalisations

|  | Adobe | Marchand |
| --- | --- | --- |
| Modules et code Adobe Commerce personnalisés |     | R |
| Extensions |     | R |
| Intégrations personnalisés |     | R |

{style="table-layout:auto"}

#### Déploiements

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité de l’infrastructure pour créer et déployer le code | R |   |
| Qualité continue du pipeline de configuration de création et de déploiement de l’infrastructure | R |   |
| Configuration de la création et du déploiement de contenu statique |     | R |
| Création et exécution du processus de gouvernance du déploiement : critères et gestion du changement |     | R |
| Déploiement dans l’environnement d’évaluation |     | R |
| Déploiement dans l’environnement de production |     | R |
| Restaurations de production |     | R |

{style="table-layout:auto"}

#### Synchronisation des environnements

Les commerçants sont chargés de synchroniser les données entre les environnements de production et d’évaluation.

#### Patching

|     | Adobe | Marchand |
| --- | --- | --- |
| Installation de mises à jour et de correctifs dans les outils de la CEE |     | R |
| Installation de mises à jour et de correctifs sur Adobe Commerce core |     | R |

#### Disponibilité du site web

|  | Adobe | Marchand |
| --- | --- | --- |
| Application Adobe Commerce personnalisée et sites Web associés |     | R |

#### Performances

|     | Adobe | Marchand |
| --- | --- | --- |
| Optimisation et optimisation des applications principales | R |   |
| Optimisation et réglage du code personnalisé |     | R |
| Code Adobe Commerce personnalisé |     | R |
| Test de charge |     | R |
| Test de performance |     | R |

{style="table-layout:auto"}


#### Journaux et surveillance

|     | Adobe | Marchand |
| --- | --- | --- |
| Rotation des journaux | R |   |
| Application Adobe Commerce personnalisée | | R |
| Disponibilité des services New Relic :<br>intégration de l’application et de l’agent APM, application d’infrastructure,<br>Journalisation et intégration | R |   |
| Configuration des alertes New Relic |     | R |
| Déploiement de l’agent New Relic sur les serveurs PaaS |     | R |

{style="table-layout:auto"}

#### Débogage et isolation des problèmes

|     | Adobe | Marchand |
| --- | --- | --- |
| Débogage et isolation des problèmes | R | R |
| Prise en charge rapide du processus de débogage et d’isolation des problèmes |     | R |

{style="table-layout:auto"}

### Configuration des applications et des services

#### application Commerce

|     | Adobe | Marchand |
| --- | --- | --- |
| Configuration des applications |     | R |
| Ajout de domaines à l’application Adobe Commerce (URL de base) |     | R |
| Configuration du panneau d’utilisation pour utiliser les versions de services prises en charge par la version d’Adobe Commerce déployée<br><br>Par exemple, différentes versions de Commerce sont compatibles avec des versions spécifiques de PHP, Redis, etc. |     | R |

{style="table-layout:auto"}

#### Planification des tâches avec des tâches cron

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité des tâches cron par défaut | R | |
| Qualité continue des tâches cron personnalisées |  | R |

{style="table-layout:auto"}

#### courtier de messages pour la structure de la file d’attente des messages

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité du service RabbitMQ | R |   |
| Configuration des paramètres RabbitMQ par défaut | R |   |
| Qualité et correction continues de RabbitMQ | R |   |
| Soumettre une demande de service pour installer une version RabbitMQ compatible avec la version Adobe Commerce installée |   | R |

{style="table-layout:auto"}

#### service PHP

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité de PHP | R |   |
| Configuration des paramètres PHP par défaut | R |     |
| Configuration des paramètres PHP personnalisés |     | R |
| Configuration du fichier YAML pour aligner les versions PHP compatibles avec la version Adobe Commerce installée |    | R |

{style="table-layout:auto"}

#### Services de base de données

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité des services Galera et MariaDB | R | |
| Maintenance en cours des paramètres par défaut de la base de données<br><br>(indexation et optimisation des tables principales, optimisation des paramètres sys-admin par défaut) | R |   |
| Maintenance continue des données marchandes et des paramètres modifiés<br><br>(configuration des tables normalisées ou plates, indexation et optimisation des tables tierces et personnalisées, archivage ou suppression des données, configuration des paramètres d’administration du système) |     | R |
| Configuration de Galera et MySQL | R |   |
| Qualité et correction continues de Galera et MariaDB | R |   |
| Optimisation continue de l’infrastructure | R |   |
| Identification et correction de requêtes lentes |     | R |
| Envoyez une demande de service pour installer une version MariaDB compatible avec la version Adobe Commerce installée. |     | R |
| Définition et gestion de politiques de conservation des données spécifiques au marché (les politiques de conservation des données de l’Adobe sont définies dans l’accord commercial) |     | R |

{style="table-layout:auto"}

#### Service CDN

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité et qualité du réseau de diffusion de contenu | R |   |
| Configuration de service rapide (via Extension/API) |     | R |
| Qualité d’extension rapide | R |   |
| Qualité des fragments VCL d’intégration rapide (groupés avec l’extension Fastly) | R |   |
| Optimisation du cache de page |     | R |
| Ajout de domaines aux services, au réseau de diffusion de contenu et à l’infrastructure | R |   |
| Fragments de code VCL personnalisés |     | R |
| Règles WAF et WAF | R |   |

{style="table-layout:auto"}

#### Cache Service

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité du service Redis | R |   |
| Configuration des paramètres Redis par défaut | R |   |
| Qualité et correction continues des Redis | R |   |
| Envoyez une demande de service pour installer une version de Redis compatible avec la version d’Adobe Commerce installée. |     | R |

{style="table-layout:auto"}

#### Service de recherche

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité des Elasticsearch | R |   |
| Configuration des paramètres par défaut de l’Elasticsearch | R |   |
| Soumettre une demande de service pour installer une version Elasticsearch compatible avec la version Adobe Commerce installée |  | R |

{style="table-layout:auto"}

#### Service Email

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité du service de messagerie SendGrid et de son intégration | R |   |
| Surveiller l’utilisation de SendGrid du marchand par rapport aux limites | R |   |
| Le commerçant n&#39;est responsable de l&#39;utilisation du service que pour les emails transactionnels sortants.<br>Le service ne prend pas en charge l’envoi d’emails marketing. |     | R |
| Configuration des services de messagerie tiers facultatifs |     | R |

{style="table-layout:auto"}

#### Services tiers

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité et qualité des services tiers |     | R |

{style="table-layout:auto"}

### Extensions Commerce Services

#### Service de création de rapports avancée

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité du service de création de rapports avancé | R |   |
| Configuration des rapports avancés conforme aux conditions générales des rapports avancés |     | R |

{style="table-layout:auto"}

#### Commerce Intelligence

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité des services de Business Intelligence Adobe Commerce | R |   |
| Processus de synchronisation des données de l’IMS | R |   |
| Détection des problèmes de synchronisation des MBI | R |   |
| Configuration de la synchronisation des données MBI avec Adobe Commerce Cloud Pro, Starter, On Premise ou non Adobe Commerce<br>(API, qualité et formatage des données, réseau commercial,<br>Connexions DB à l’intérieur et à l’extérieur de Adobe Commerce Cloud DB, par-dessus les seuils de données) |     | R |
| Configuration de la synchronisation des données MBI avec Adobe Commerce Cloud Pro<br>(Configuration de la base de données Adobe Commerce Cloud) | R |   |

{style="table-layout:auto"}

#### Recommendations de produit

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité du service Recommendations de produit | R |   |

{style="table-layout:auto"}

### Services réseau

#### Optimisation des images

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité et qualité de l’optimisation des images | R |  |
| Configuration de l’optimisation des images |     | R |

{style="table-layout:auto"}

#### Certificats SSL

|     | Adobe | Marchand |
| --- | --- | --- |
| Certificat dédié SSL - Expiration | R |  |
| Approvisionnement des certificats SSL | R |  |
| Achat et maintenance d’un certificat SSL EV/spécifique (autres que les valeurs par défaut fournies) et fournir à Adobe |     | R |

{style="table-layout:auto"}

#### Web Application Firewall (WAF)

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité et configuration du WAF | R |  |
| Traitement des faux positifs de la règle WAF | R | |
| Reporting des faux positifs de la règle WAF |     | R |
| Réglage des règles WAF (NON PRIS EN CHARGE) |     |     |
| Journaux WAF/CDN |     | R |

{style="table-layout:auto"}

#### DDOS

|     | Adobe | Marchand |
| --- | --- | --- |
| Blocage IP proactif |     | R |
| Protection des robots |     | R |
| Détection DDOS - couche 3-4 | R |   |
| Détection DDOS - Couche 7 |     | R |
| Réponse DDOS | R |   |
| Configuration de la limitation de taux d’extension rapide et de la protection des robots (limitée) |     | R |

{style="table-layout:auto"}

#### Lien privé

|     | Adobe | Marchand |
| --- | --- | --- |
| Configuration et maintenance des connexions PrivateLink (le cas échéant) avec un VPC détenu par l’Adobe | R |   |
| Configuration et maintenance des connexions PrivateLink (le cas échéant) avec un VPC détenu par le marchand |     | R |
| Disponibilité du SSH (lien non privé) | R |   |
| Configuration de PrivateLink entrant dans le point d’entrée du service Adobe Commerce Cloud | R |   |
| Acceptation de PrivateLink entrant dans le point d’entrée du service Adobe Commerce Cloud |     | R |
| Configuration de PrivateLink entrant dans le point d’entrée du service VPC du commerçant |     | R |
| Acceptation du lien privé entrant dans le point d’entrée du service VPC du détaillant | R |   |
| Configuration des intégrations PrivateLink (point d’entrée vers compte) |     | R |
| Configuration du VPC détenu par le commerce pour le point d’entrée PrivateLink<br><br> (y compris toute connexion VPN) |     | R |

{style="table-layout:auto"}

### Système et infrastructure

#### Serveur d’applications

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité de Nginx | R |   |
| Configuration de Nginx | R |   |
| Qualité et correction continues de Nginx | R |   |

{style="table-layout:auto"}

#### Système d’exploitation

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité du système d’exploitation | R |   |
| Qualité et correction continues du système d’exploitation | R |   |

{style="table-layout:auto"}

#### Sauvegarde, haute disponibilité et basculement

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité de l’instantané et du processus de sauvegarde | R |   |
| Planification des sauvegardes pour les environnements d’évaluation et de production de Cloud Pro | R |   |
| Planification de sauvegardes pour les environnements Cloud Starter et Pro Integration |     | R |
| Disponibilité de l’architecture HA/basculement | R |   |

{style="table-layout:auto"}
