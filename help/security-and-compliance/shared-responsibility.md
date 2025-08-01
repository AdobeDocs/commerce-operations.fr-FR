---
title: Sécurité à responsabilité partagée et modèle opérationnel
description: Découvrez les responsabilités de sécurité de chaque partie impliquée dans votre projet d’infrastructure cloud Adobe Commerce.
exl-id: f3cc1685-e469-4e30-b18e-55ce10dd69ce
source-git-commit: fcaf6ff1dce1c1a5084307cd366ca58d71a8f4e4
workflow-type: tm+mt
source-wordcount: '2850'
ht-degree: 0%

---

# Sécurité à responsabilité partagée et modèle opérationnel

Adobe Commerce sur les infrastructures cloud est une offre PaaS (platform-as-a-service) qui repose sur un modèle opérationnel et de sécurité à responsabilité partagée. Ces responsabilités sont partagées entre Adobe, le commerçant, le fournisseur de services cloud et le fournisseur de réseau de diffusion de contenu (CDN). Chaque partie assume la responsabilité distincte de la sécurisation et de l’exploitation de l’application Adobe Commerce, ainsi que du code et des extensions spécifiques aux commerçants déployés sur l’infrastructure cloud.

Ce modèle partagé permet aux commerçants de concevoir et de mettre en œuvre une solution hautement flexible, personnalisable et évolutive pour répondre à leurs besoins professionnels tout en réduisant les responsabilités et les coûts opérationnels.

>[!VIDEO](https://video.tv.adobe.com/v/3458392/?learn=on&enablevpops)

En règle générale, Adobe est responsable des éléments suivants :

- Développement et maintenance de code d’application principal sécurisé
- Maintien de la sécurité de la plateforme
- S’assurer que la plateforme est conforme à la norme SOC 2 et PCI et compatible avec les composants technologiques compatibles PCI (par exemple, PHP, Redis)
- Réponse aux problèmes de sécurité concernant la plateforme principale
- Travailler avec les fournisseurs de services cloud et les partenaires de réseau CDN pour résoudre tous les problèmes qui se produisent

Les commerçants sont responsables des éléments suivants :

- Maintien de la sécurité du code personnalisé et des intégrations à des applications tierces
- Assurer le développement sécurisé des applications
- Obtention de la certification PCI si demandé par le responsable du traitement des paiements du commerçant
- Réagir et répondre aux incidents de sécurité

## Responsabilités d’Adobe

Adobe est responsable de la sécurité et de la disponibilité d’Adobe Commerce sur l’environnement d’infrastructure cloud et du code de la solution principale. En outre, Adobe est responsable des activités et des mécanismes nécessaires au maintien de la sécurité de la solution Adobe Commerce sur les infrastructures cloud, notamment :

- Application de correctifs et de sécurité au niveau du serveur pour les applications prises en charge par Adobe Commerce sur les infrastructures cloud, telles que les fonctionnalités de stockage de données dans le cloud et de recherche
- Réalisation de tests de pénétration et d’analyses du code de base d’Adobe Commerce sur le cloud infrastructure
- Réalisation d’examens et d’audits semestriels des solutions de gestion des identités et des accès (IAM) et des autorisations des fournisseurs de services cloud publics (exigence de conformité PCI)
- Réalisation d’examens et d’audits semestriels sur les utilisateurs autorisés, y compris les employés et les sous-traitants d’Adobe (exigence de conformité PCI)
- Effectuer des tests annuels et documenter les fonctionnalités de sauvegarde et de restauration
- Configuration des pare-feu de serveur et de périmètre
- Connexion et configuration du référentiel Adobe Commerce sur l’infrastructure cloud
- Définition, test, mise en œuvre et documentation de plans de reprise après sinistre (DR) pour les domaines relevant de la responsabilité d’Adobe
- Définition des règles de pare-feu d’application web de plateforme globale (WAF)
- Renforcement du système d’exploitation
- Mise en œuvre et maintenance de l’intégration des solutions de réseau de distribution de contenu (CDN) et de gestion des performances des applications (APM) avec Adobe Commerce sur les infrastructures cloud
- Émission périodique de mises à jour de sécurité et autres pour le code de base d’Adobe Commerce sur l’infrastructure cloud (l’application de correctifs est de la responsabilité du commerçant)
- Gestion de l’assistance commerciale et des contrôles d’accès à l’assistance (par exemple, Zendesk)
- Surveillance, journalisation et résolution des incidents de sécurité concernant Adobe Commerce sur l’infrastructure de plateforme de l’infrastructure cloud
- Surveillance des opérations de la plateforme et prise en charge 24h/24 et 7j/7 d’Adobe Commerce sur les commerçants d’infrastructure cloud
- Approvisionnement des environnements de production et d’évaluation
- Évaluation des menaces de sécurité potentielles pour les opérations et l&#39;infrastructure de la plateforme
- Évolutivité de l’informatique, du stockage, de la grille et d’autres ressources, comme décrit dans le contrat de niveau de service (SLA) conclu avec le commerçant
- Configuration du DNS (Adobe Commerce sur les infrastructures de plateforme d’infrastructure cloud uniquement)
- Test des vulnérabilités de sécurité de la plateforme

Adobe maintient la certification PCI pour l’infrastructure et les services utilisés pour la solution Adobe Commerce.  Les commerçants sont responsables de la conformité du code personnalisé, des processus du système et du réseau, ainsi que de l&#39;organisation.

Adobe assure également la disponibilité de l’infrastructure du commerçant comme convenu dans le SLA applicable.

## Responsabilités du commerçant

Le commerçant est chargé de suivre les bonnes pratiques de sécurité pour son instance spécifique et personnalisée d’Adobe Commerce sur la solution d’infrastructure cloud :

- Ajout des fichiers de configuration d’Adobe Commerce sur l’infrastructure cloud nécessaires au référentiel
- Application de correctifs de sécurité et d’autres correctifs à leur solution Adobe Commerce on cloud infrastructure personnalisée immédiatement après leur publication par Adobe
- Application de correctifs de sécurité et autres à toutes les extensions et à tout le code personnalisés, immédiatement après leur publication par le fournisseur
- Création, déploiement et test de fichiers VCL Varnish personnalisés
- Conception, définition de thèmes, installation, intégration et sécurisation de la solution personnalisée Adobe Commerce sur l’infrastructure cloud d’, y compris toutes les extensions et le code personnalisés
- Octroi et révocation de l’accès utilisateur à l’instance du commerçant d’Adobe Commerce sur la configuration, l’application et la plateforme de l’infrastructure cloud
- Gestion des problèmes de sécurité liés au réseau interne du commerçant, aux serveurs, à l’infrastructure et aux applications personnalisées reposant sur la plateforme d’infrastructure cloud d’Adobe Commerce
- Installation de l’outil d’intégration de ligne de commande (CLI) Adobe Commerce sur l’infrastructure cloud
- Maintien du niveau requis de conformité PCI de l’application personnalisée et d’autres processus internes, comme défini par les directives PCI-DSS

  >[!NOTE]
  >
  >Pour minimiser les zones à vérifier, la conformité PCI pour le commerçant est basée sur les certifications PCI d’Adobe Commerce et du fournisseur d’hébergement cloud.

- Exécution d’analyses PCI ASV et résolution des problèmes dans le code et la plateforme de base d’Adobe Commerce sur l’infrastructure cloud
- Surveillance de toutes les activités des applications susceptibles de révéler une menace potentielle pour la sécurité, y compris les tests de pénétration, les analyses de vulnérabilité et les journaux
- Surveillance et réponse aux incidents de sécurité, y compris les examens, la correction et le reporting relatifs à la solution d&#39;infrastructure cloud et aux comptes utilisateur Adobe Commerce du commerçant
- Obtention d’un fournisseur DNS et configuration et maintenance de tous les enregistrements DNS spécifiques au commerçant
- Exécution de tests de performance sur l’application personnalisée
- Sécurisation de l’accès aux comptes de la plateforme, à l’instance et à l’application
- Test et assurance qualité de l’application personnalisée
- Maintien de la sécurité de tous les systèmes ou réseaux que le commerçant connecte à l’application Adobe Commerce sur l’infrastructure cloud

## Responsabilités du fournisseur Cloud Service

Adobe s’appuie sur des fournisseurs de services cloud bien établis pour héberger l’infrastructure de serveur cloud pour Adobe Commerce sur l’infrastructure cloud. Ces fournisseurs sont responsables de la sécurité du réseau, y compris le routage, la commutation et la sécurité du réseau de périmètre via les systèmes de pare-feu et les systèmes de détection d&#39;intrusion (IDS). Les fournisseurs de services cloud sont également responsables de la sécurité physique des centres de données qui hébergent la solution d’infrastructure cloud d’Adobe Commerce et de la sécurité environnementale des centres de données.

Les fournisseurs de services cloud sont également responsables des éléments suivants :

- Gestion des certifications PCI DSS, SOC 2 et ISO 27001 pour leurs services cloud
- Sécurisation de l’hyperviseur
- Sécurisation du datacenter, y compris l&#39;accès physique et au réseau

## Responsabilités du fournisseur de réseau CDN

La solution d’infrastructure Adobe Commerce sur cloud utilise des fournisseurs de réseau CDN pour accélérer le temps de chargement des pages, mettre en cache le contenu et purger instantanément le contenu obsolète. Ces fournisseurs sont également responsables des problèmes de sécurité directement liés ou affectant leur réseau CDN, ainsi que de la définition et de la maintenance des règles de WAF CDN.

## Résumé des responsabilités en matière de sécurité

>[!BEGINSHADEBOX]

Le tableau récapitulatif suivant utilise le modèle RACI pour montrer les responsabilités en matière de sécurité partagées entre Adobe, le commerçant et le fournisseur de services cloud :

**R** — Responsable
**A** — Responsabilité
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
    <th>Fournisseur de réseau CDN</th>
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
    <td>Application de correctifs aux services de prise en charge<br> (par exemple, Nginx ou MySQL).</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Définir les règles WAF d'origine</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Définition des règles de WAF CDN</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Déploiement des règles WAF de Platform</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Déploiement des règles WAF du réseau CDN</td>
    <td>A</td>
    <td>I</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Correction des bugs principaux dans Adobe Commerce sur le code de l’infrastructure cloud</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Publication des correctifs d’Adobe Commerce sur l’infrastructure cloud</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Évolutivité (calcul et stockage)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Mise à l'échelle (PaaS et grille)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Accès au code source, y compris repo.magento.com</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installation d’Adobe Commerce sur l’outil CLI de l’infrastructure cloud</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Ajout d’Adobe Commerce sur les fichiers de configuration de l’infrastructure cloud au référentiel</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Créer un projet pour le commerçant (interface utilisateur d’intégration)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Connexion des référentiels à Adobe Commerce sur l’infrastructure cloud</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Configuration du référentiel source <sup>1</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Création d’un utilisateur pour le gestionnaire de version (interface utilisateur d’intégration)</td>
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
    <td>Personnalisation d’Adobe Commerce sur les infrastructures cloud</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Test des performances d’Adobe Commerce personnalisé sur une infrastructure cloud</td>
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
    <td>Création, déploiement et test de VCL Varnish personnalisés</td>
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
    <td>Développement de l’extension CDN et correction des bogues</td>
    <td>A</td>
    <td>C</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Intégration d’un réseau CDN</td>
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
    <td>Configuration des applications New Relic APM et Infrastructure</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installation des applications New Relic APM et Infrastructure</td>
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
    <td>Obtenir un fournisseur DNS (Pro uniquement)</td>
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
    <td>Approvisionnement des environnements de production et d’évaluation</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Accès à Zendesk pour Adobe Commerce sur les infrastructures cloud</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Résolution des problèmes de sécurité des commerçants</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>Résolution des problèmes de sécurité des infrastructures cloud d’Adobe Commerce</td>
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
    <td>Assistance d’Adobe en matière de recherche sur la sécurité (logiciel)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Assister Adobe dans ses recherches sur la sécurité (analyses/audits)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Exécution d’analyses PCI ASV</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Correction des analyses PCI Adobe Commerce sur l’infrastructure cloud <sup>4</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Correction des analyses PCI PaaS</td>
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
    <td>Surveillance des journaux de sécurité</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Gestion de l’IAM et des autorisations pour Adobe Commerce sur les infrastructures cloud</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Gestion des contrôles d’accès au support (Teleport)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Contrôle de l’assistance et de l’accès des commerçants</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Tests annuels et documentation du plan de reprise après sinistre, de sauvegarde et de restauration d’Adobe</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Tests annuels et documentation du plan de reprise après sinistre</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
<tfoot>
  <tr>
    <td colspan="5">
      <p><sup><strong>1</strong></sup> Uniquement si le référentiel d’Adobe Commerce sur l’infrastructure cloud est utilisé comme référentiel principal. L'utilisation d'autres référentiels externes relève de la seule responsabilité du commerçant.</p>
      <p><sup><strong>2</strong></sup> Adobe fournit une prise en charge de niveau 1 pour les problèmes liés aux fournisseurs de réseau CDN.</p>
      <p><sup><strong>3</strong></sup> Le commerçant est responsable des contrôles Ngnix qu'il configure pour ses applications.</p>
      <p><sup><strong>4</strong></sup> Pour PCI, les exigences de test de pénétration sont partagées entre Adobe et le commerçant.</p>
    </td>
  </tr>
</tfoot>
</table>

## Résumé des responsabilités opérationnelles

>[!BEGINSHADEBOX]

Les tableaux de synthèse suivants clarifient les responsabilités opérationnelles d’Adobe et des commerçants lors du développement, du déploiement, de la maintenance et de la sécurisation d’Adobe Commerce sur les infrastructures cloud.

>[!ENDSHADEBOX]

### Codage et développement

#### Code Adobe Commerce principal

|     | Adobe | Marchand |
| --- | --- | --- |
| Publication de mises à jour et de correctifs sur Adobe Commerce Core | R |     |
| Disponibilité et correction du système de fichiers | R |  |
| Publication de mises à jour et de correctifs sur ECE-Tools | R |     |
| Qualité des applications Adobe Commerce principales | R |     |

{style="table-layout:auto"}

#### Référentiel de code

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité de repo.magento.com | R |     |
| Disponibilité d’Adobe Commerce sur le serveur Git Cloud | R |     |
| Autres référentiels de code sélectionnés par le commerçant (GitHub, Bitbucket, serveur Git hébergé) |     | R |

{style="table-layout:auto"}

#### Cloud Docker

|     | Adobe | Marchand |
| --- | --- | --- |
| Mise à disposition des conteneurs Cloud Docker pour le téléchargement | R |   |
| Déploiement et configuration de Cloud Docker (facultatif) |     | R |
| Toute autre configuration de développement local |     | R |

{style="table-layout:auto"}

#### COMMERCE CLOUD CLI

|     | Adobe | Marchand |
| --- | --- | --- |
| Qualité et mise à jour continues des outils de la CEE | R |   |
| Installation de la dernière version de ECE Tools |     | R |

{style="table-layout:auto"}

#### Personnalisations

|  | Adobe | Marchand |
| --- | --- | --- |
| Modules et code Adobe Commerce personnalisés |     | R |
| Extensions |     | R |
| Intégrations personnalisées |     | R |

{style="table-layout:auto"}

#### Déploiements

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité de l’infrastructure pour créer et déployer le code | R |   |
| Qualité continue du pipeline de configuration de création et de déploiement d’infrastructure | R |   |
| Configuration du déploiement de la version et du contenu statique |     | R |
| Création et exécution du processus de gouvernance du déploiement : critères et gestion du changement |     | R |
| Déploiement dans un environnement d’évaluation |     | R |
| Déploiement dans un environnement de production |     | R |
| Restaurations de production |     | R |

{style="table-layout:auto"}

#### Synchronisation des environnements

Les commerçants sont chargés de synchroniser les données entre les environnements.

#### Application de correctifs

|     | Adobe | Marchand |
| --- | --- | --- |
| Installation de mises à jour et de correctifs sur ECE-Tools |     | R |
| Installation de mises à jour et de correctifs sur Adobe Commerce Core |     | R |

#### Disponibilité du site web

|  | Adobe | Marchand |
| --- | --- | --- |
| Application Adobe Commerce personnalisée et sites web associés |     | R |

#### Performances

|     | Adobe | Marchand |
| --- | --- | --- |
| Optimisation et réglage des applications principales | R |   |
| Optimisation et réglage du code personnalisé |     | R |
| Code Adobe Commerce personnalisé |     | R |
| Test de charge |     | R |
| Tests de performance |     | R |

{style="table-layout:auto"}


#### Journaux et surveillance

|     | Adobe | Marchand |
| --- | --- | --- |
| Rotation des journaux | R |   |
| Application Adobe Commerce personnalisée | | R |
| Disponibilité des services New Relic : <br>intégration de l’application APM et de l’agent, application d’infrastructure,<br>Journalisation et intégration | R |   |
| Configuration des alertes New Relic |     | R |
| Déploiement de l’agent New Relic sur les serveurs PaaS | R |  |

{style="table-layout:auto"}

#### Débogage et isolation des problèmes

|     | Adobe | Marchand |
| --- | --- | --- |
| Débogage et isolation des problèmes | R | R |
| Prise en charge en temps voulu du débogage et du processus d’isolation des problèmes |     | R |

{style="table-layout:auto"}

### Configuration des applications et des services

#### Application Commerce

|     | Adobe | Marchand |
| --- | --- | --- |
| Configuration de l’application |     | R |
| Ajout de domaines à l&#39;application Adobe Commerce (URL de base) |     | R |
| Configuration de PaaS pour utiliser les versions de Services prises en charge par la version d&#39;Adobe Commerce déployée<br><br>Par exemple, différentes versions de Commerce sont compatibles avec des versions spécifiques de PHP, Redis, etc. |     | R |

{style="table-layout:auto"}

#### Planification des tâches avec des tâches cron

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité des traitements cron par défaut | R | |
| Qualité continue des tâches cron personnalisées |  | R |

{style="table-layout:auto"}

#### Courtier en messages pour la structure de file d&#39;attente des messages

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité du service RabbitMQ | R |   |
| Configuration des paramètres par défaut de RabbitMQ | R |   |
| Qualité continue et correctifs de RabbitMQ | R |   |
| Envoyez une demande de service pour installer une version de RabbitMQ compatible avec la version Adobe Commerce installée |   | R |

{style="table-layout:auto"}

#### Service PHP

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
| Maintenance continue des paramètres de base de données par défaut<br><br>(indexation et optimisation des tables principales, optimisation des paramètres d’administration système par défaut) | R |   |
| Maintenance continue des données des commerçants et des paramètres modifiés<br><br>(configuration des tables normalisées par rapport aux tables plates, indexation et optimisation des tables personnalisées et tierces, archivage ou suppression des données, configuration des paramètres d&#39;administration du système) |     | R |
| Configuration de Galera et MySQL | R |   |
| Qualité et correction continues de Galera et MariaDB | R |   |
| Optimisation continue de l’infrastructure | R |   |
| Identifier et corriger les requêtes lentes |     | R |
| Envoyez une demande de service pour installer une version de MariaDB compatible avec la version Adobe Commerce installée |     | R |
| Définir et gérer des politiques de conservation des données spécifiques au commerçant (les politiques de conservation des données d’Adobe sont définies dans l’accord du commerçant) |     | R |

{style="table-layout:auto"}

#### Service CDN

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité et qualité du réseau CDN | R |   |
| Configuration du service Fastly (via l’extension/l’API) |     | R |
| Qualité d’extension Fastly | R |   |
| Fragments de code VCL d&#39;intégration Fastly (fournis avec l&#39;extension Fastly) | R |   |
| Optimisation du cache de page |     | R |
| Ajout de domaines aux services, au réseau CDN et à l’infrastructure | R |   |
| Fragments de code VCL personnalisés |     | R |
| Règles WAF et WAF | R |   |

{style="table-layout:auto"}

#### Service de cache

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité du service Redis | R |   |
| Configuration des paramètres Redis par défaut | R |   |
| Qualité continue et correctifs de Redis | R |   |
| Envoyez une demande de service pour installer une version de Redis compatible avec la version d’Adobe Commerce installée |     | R |

{style="table-layout:auto"}

#### Service de recherche

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité d’Elasticsearch | R |   |
| Configuration des paramètres par défaut d’Elasticsearch | R |   |
| Envoyez une demande de service pour installer une version d’Elasticsearch compatible avec la version d’Adobe Commerce installée |  | R |

{style="table-layout:auto"}

#### Service de messagerie

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité du service de messagerie SendGrid et son intégration | R |   |
| Surveiller l’utilisation de SendGrid par le commerçant par rapport aux limites | R |   |
| Le commerçant n’est responsable de l’utilisation du service que pour les e-mails transactionnels sortants<br>Le service ne prend pas en charge l’envoi d’e-mails marketing. |     | R |
| Configuration des services de messagerie tiers facultatifs |     | R |

{style="table-layout:auto"}

#### Services tiers

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité et qualité des services tiers |     | R |

{style="table-layout:auto"}

### Extensions des services Commerce

#### Service de création de rapports avancés

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité du service de création de rapports avancé | R |   |
| La configuration des rapports avancés est conforme aux conditions générales des rapports avancés |     | R |

{style="table-layout:auto"}

#### Commerce Intelligence

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité des services Adobe Commerce Business Intelligence | R |   |
| Processus de synchronisation des données MBI | R |   |
| Détection des problèmes de synchronisation MBI | R |   |
| Configuration de la synchronisation des données MBI vers Adobe Commerce Cloud Pro, Starter, On-Premise ou non-Adobe Commerce<br> <br>(API, qualité et formatage des données, réseau commercial, connexions à la base de données à l’intérieur et à l’extérieur de la base de données Adobe Commerce Cloud, au-delà des seuils de données) |     | R |
| Configuration de la synchronisation des données MBI vers Adobe Commerce Cloud Pro<br> (configuration de la base de données Adobe Commerce Cloud) | R |   |

{style="table-layout:auto"}

#### Recommandations de produit

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité du service de recommandations de produits | R |   |

{style="table-layout:auto"}

#### Recherche en direct

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité du service Live Search | R |   |

{style="table-layout:auto"}

#### Qualité des événements storefront (collecte de données) pour alimenter les recommandations de produits et les sorties Live Search

|     | Adobe | Marchand |
| --- | --- | --- |
| Thème principal (Luma) | R |   |
| Thème personnalisé |  | R |
| Implémentation de PWA principale | R |   |
| Implémentation PWA personnalisée |  | R |
| Implémentation principale d’AEM EDS (modèle standard Commerce) | R |   |
| Implémentation personnalisée d’AEM EDS |  | R |
| Toute autre implémentation de storefront personnalisée |  | R |

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
| Certificat dédié SSL - expiration | R |  |
| Approvisionnement de certificats SSL | R |  |
| Achat et maintenance d’un certificat SSL spécifique au véhicule électrique (autre que les valeurs par défaut fournies) et fourni à Adobe |     | R |

{style="table-layout:auto"}

#### Pare-feu d’application web (WAF)

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité et configuration de WAF | R |  |
| Faux positifs à la règle Addressing WAF | R | |
| Faux positifs de la règle de WAF de création de rapports |     | R |
| Réglage des règles WAF (NON PRIS EN CHARGE) |     |     |
| Journaux WAF/CDN |     | R |

{style="table-layout:auto"}

#### DDOS

|     | Adobe | Marchand |
| --- | --- | --- |
| Blocage proactif d’adresses IP |     | R |
| Protection des robots |     | R |
| Détection DDOS - couche 3-4 | R |   |
| Détection DDOS - couche 7 |     | R |
| Réponse DDOS | R |   |

{style="table-layout:auto"}

#### Lien privé

|     | Adobe | Marchand |
| --- | --- | --- |
| Configuration et gestion des connexions PrivateLink (le cas échéant) avec un VPC détenu par Adobe | R |   |
| Configuration et maintenance des connexions PrivateLink (si utilisées) avec un VPC détenu par le commerçant |     | R |
| Disponibilité de SSH (Lien non privé) | R |   |
| Configuration de la liaison privée entrante vers le point d’entrée Adobe Commerce Cloud Service | R |   |
| Acceptation du point d’entrée PrivateLink entrant vers Adobe Commerce Cloud Service |     | R |
| Configuration de PrivateLink en entrée du service VPC pour les commerçants |     | R |
| Acceptation d’un point d’entrée de lien privé entrant vers le service VPC du commerçant | R |   |
| Configuration des intégrations PrivateLink (point d’entrée vers le compte) |     | R |
| Configuration du VPC détenu par le commerçant pour le point d’entrée PrivateLink<br><br> (y compris les connexions VPN) |     | R |

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
| Qualité et correctifs continus du système d’exploitation | R |   |

{style="table-layout:auto"}

#### Sauvegarde, haute disponibilité et basculement

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité du processus de snapshot et de sauvegarde | R |   |
| Planification des sauvegardes pour les environnements d’évaluation et de production de Cloud Pro | R |   |
| Planification des sauvegardes pour les environnements d’intégration Cloud Starter et Pro |     | R |
| Disponibilité de la haute disponibilité / basculement | R |   |

{style="table-layout:auto"}

#### Serveurs cloud et mise à l’échelle

|     | Adobe | Marchand |
| --- | --- | --- |
| Disponibilité des ressources CPU, du centre de données et de l’espace disque | R |   |
| Disponibilité et exécution de la capacité de pointe ou de la mise à niveau d&#39;urgence | R |   |
| Demande de capacité de pointe |     | R |
| Surveillance de l’utilisation du processeur virtuel par rapport aux limites | R |   |

{style="table-layout:auto"}
