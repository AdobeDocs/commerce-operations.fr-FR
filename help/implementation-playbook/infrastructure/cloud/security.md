---
title: Sécurité des infrastructures dans le cloud
description: Découvrez comment sécuriser Adobe Commerce sur l’infrastructure cloud.
exl-id: cd5d1106-c8db-4b70-b1c7-12378d7d77a7
feature: Cloud, Security
source-git-commit: d05629ef21608a017cfbbfcf05e9507375689fa2
workflow-type: tm+mt
source-wordcount: '1689'
ht-degree: 0%

---

# Sécurité

L’architecture du plan Adobe Commerce Pro est conçue pour fournir un environnement hautement sécurisé. Chaque client est déployé dans son propre environnement serveur isolé, séparé des autres clients. Les détails de sécurité de l’environnement de production sont décrits ci-dessous.

## Navigateurs Web

La majeure partie du trafic entrant et sortant de l’environnement cloud provient des navigateurs web des clients. Le trafic client peut être sécurisé à l’aide du protocole HTTPS pour toutes les pages du site web (en utilisant soit une certification SSL partagée, soit le certificat SSL du client lui-même, moyennant des frais supplémentaires). Les pages de passage en caisse et de compte sont toujours servies à l’aide du protocole HTTPS. La bonne pratique consiste à diffuser toutes les pages sous HTTPS.

## Réseau de diffusion de contenu (CDN)

Fournit rapidement une protection CDN et par déni de service distribué (DDoS). Le CDN rapide permet d’isoler l’accès direct aux serveurs d’origine. Le DNS public pointe uniquement vers le réseau Fastly. La solution de DDoS rapide protège contre les attaques de couche 3 et 4 hautement perturbantes, ainsi que contre les attaques de couche 7 plus complexes. Les attaques de couche 7 peuvent être bloquées à l’aide de règles personnalisées basées sur l’ensemble des requêtes HTTP/HTTPS et selon les critères du client et de la requête, y compris les en-têtes, les cookies, le chemin d’accès à la requête et l’adresse IP du client, ou d’indicateurs tels que la géolocalisation.

## pare-feu des applications web (WAF)

Le pare-feu d’applications web Fastly (WAF) est utilisé pour fournir une protection supplémentaire. Le mode WAF basé sur le cloud de Fastly utilise des règles tierces provenant de sources commerciales et open source telles que le jeu de règles principal OWASP. En outre, des règles spécifiques à Adobe Commerce sont utilisées. Les clients sont protégés contre les attaques de couche d’application clés, notamment les attaques par injection et les entrées malveillantes, les scripts intersites, l’exfiltration de données, les violations de protocole HTTP et d’autres menaces OWASP Top 10.

Les règles WAF sont mises à jour par Adobe Commerce si de nouvelles vulnérabilités sont détectées, ce qui permet à Managed Services de &quot;corriger virtuellement&quot; les problèmes de sécurité avant les correctifs logiciels. La méthode Fastly ne fournit pas de services de limitation de vitesse ou de détection de robots. Si vous le souhaitez, les clients peuvent acquérir sous licence un service de détection de robots tiers compatible avec Fastly.

## Cloud privé virtuel (VPC)

L’environnement de production de plan Adobe Commerce Pro est configuré en tant que cloud privé virtuel (VPC) afin que les serveurs de production soient isolés et aient une capacité limitée à se connecter à l’environnement cloud et en sortir. Seules les connexions sécurisées aux serveurs cloud sont autorisées. Les protocoles sécurisés tels que SFTP ou rsync peuvent être utilisés pour les transferts de fichiers.

Les clients peuvent utiliser des tunnels SSH pour sécuriser les communications avec l’application. L’accès à AWS PrivateLink peut entraîner des frais supplémentaires. Toutes les connexions à ces serveurs sont contrôlées à l’aide des groupes de sécurité AWS, un pare-feu virtuel qui limite les connexions à l’environnement. Les ressources techniques des clients peuvent accéder à ces serveurs à l’aide de SSH.

## Chiffrement

Amazon Elastic Block Store (EBS) est utilisé pour le stockage. Tous les volumes EBS sont chiffrés à l’aide de l’algorithme AES-265. Cela signifie que les données seront cryptées au repos. Le système chiffre également les données en transit entre le CDN et l’origine, ainsi qu’entre les serveurs d’origine. Les mots de passe du client sont stockés sous la forme de hachages. Les informations d’identification sensibles, y compris celles de la passerelle de paiement, sont chiffrées à l’aide de l’algorithme SHA-256.

L’application Adobe Commerce ne prend pas en charge le chiffrement ou le chiffrement au niveau des colonnes ou des lignes lorsque les données ne sont pas au repos ou ne sont pas en transit entre les serveurs. Le client peut gérer les clés de chiffrement dans l’application. Les clés utilisées par le système sont stockées dans AWS Key Management System et doivent être gérées par Managed Services afin de fournir des parties du service.

## Détection des points de fin et réponse

[!DNL CrowdStrike Falcon], un agent de détection et de réponse de point d’entrée de nouvelle génération léger installé sur tous les points d’entrée (y compris les serveurs) dans Adobe, protège nos données et nos systèmes grâce à une surveillance et une collecte continues en temps réel qui nous permettent d’identifier rapidement les menaces et de les répondre.

## Test de pénétration

Managed Services effectue des tests de pénétration réguliers du système cloud Adobe Commerce avec l’application prête à l’emploi. Les clients sont responsables de tout test de pénétration de leur application personnalisée.

## Passerelle de paiement

Adobe Commerce nécessite des intégrations de passerelle de paiement où les données de carte de crédit sont transmises directement du navigateur du consommateur à la passerelle de paiement. Les données de carte ne sont jamais disponibles dans aucun des environnements Managed Services de plan Adobe Commerce Pro. Les actions sur les transactions effectuées par l’application de commerce électronique sont effectuées à l’aide d’une référence à la transaction à partir de la passerelle.

## application Adobe Commerce

Adobe teste régulièrement le code de l’application principale à la recherche de failles de sécurité. Les correctifs relatifs aux défauts et aux problèmes de sécurité sont fournis aux clients. L’équipe de sécurité des produits valide les produits Adobe Commerce en respectant les directives de sécurité des applications OWASP. Plusieurs outils d’évaluation des vulnérabilités de la sécurité et fournisseurs externes sont utilisés pour tester et vérifier la conformité. Les outils de sécurité incluent :

- Numérisation statique et dynamique des codes postaux
- Analyse du code source RIPS
- Services d’analyse des vulnérabilités de Trustwave et d’Alert Logic
- Burp Suite Pro
- OWASPZAP
- andSqlMap

La base de code complète est analysée avec ces outils toutes les deux semaines. Les clients sont informés des correctifs de sécurité par le biais d’emails directs, de notifications dans l’application et dans la variable [Centre de sécurité](https://magento.com/security).

Les clients doivent s’assurer que ces correctifs sont appliqués à leur application personnalisée dans les 30 jours suivant la publication, conformément aux directives PCI. Adobe fournit également un [Outil Analyse de sécurité](https://docs.magento.com/user-guide/magento/security-scan.html) qui permet aux commerçants de surveiller régulièrement leurs sites et de recevoir des mises à jour sur les risques de sécurité connus, les logiciels malveillants et les accès non autorisés. L’outil d’analyse de sécurité est un service gratuit qui peut être exécuté sur n’importe quelle version d’Adobe Commerce.

Pour encourager les chercheurs en sécurité à identifier et à signaler des vulnérabilités, Adobe Commerce dispose d’un [bug-bounty program](https://hackerone.com/magento) en plus des tests internes. De plus, le client reçoit le code source complet de la demande pour sa propre révision, le cas échéant.

## Système de fichiers en lecture seule

Tout le code exécutable est déployé dans une image système de fichiers en lecture seule, ce qui réduit considérablement les surfaces disponibles pour attaque. Le processus de déploiement crée une image Squash-FS. Cette approche réduit considérablement les possibilités d’injecter du code PHP ou JavaScript dans le système ou de modifier les fichiers de l’application Adobe Commerce.

## Déploiement à distance

Le seul moyen d’obtenir du code exécutable dans l’environnement de production Managed Services consiste à l’exécuter via un processus d’approvisionnement. Cela implique de transférer le code source de votre référentiel source vers un référentiel distant qui lance un processus de déploiement. L’accès à cette cible de déploiement est contrôlé. Vous contrôlez donc complètement qui peut accéder à la cible de déploiement. Tous les déploiements de code d’application dans l’environnement hors production sont contrôlés par le client.

## Journalisation

Toutes les activités AWS sont connectées à AWS CloudTrail. Les journaux Linux, de serveur d’applications et de base de données sont stockés sur les serveurs de production et dans des sauvegardes. Toutes les modifications du code source sont enregistrées dans un référentiel Git. L’historique de déploiement est disponible dans Adobe Commerce [Interface Web du projet](https://devdocs.magento.com/cloud/project/projects.html#login). Tous les accès à l’assistance sont consignés et les sessions d’assistance sont enregistrées.

## Données sensibles

Les données sensibles peuvent couvrir les informations personnelles des consommateurs ou les données confidentielles des clients Managed Services. La protection des données clients et clients sensibles est une obligation essentielle pour Adobe Commerce Managed Services. Managed Services et nos clients ont des obligations légales concernant les informations d’identification personnelle. Outre les fonctionnalités de sécurité de l’architecture, il existe d’autres contrôles pour limiter la distribution et l’accès aux données sensibles.

Les clients détiennent leurs données et contrôlent l’emplacement de ces données. Le client spécifie l’emplacement où résident ses instances de production et de développement. Ils spécifient également l’emplacement qui sera utilisé pour l’environnement de création de rapports Adobe Commerce conjointement avec Commerce, et si cette application de création de rapports Adobe Commerce a accès ou non à des informations d’identification personnelle. Les instances de production se trouvent dans la plupart des régions d’AWS, tandis que les environnements de développement et de reporting d’Adobe Commerce se trouvent actuellement aux États-Unis ou dans l’Union européenne.

Les données sensibles peuvent passer par le réseau de serveur CDN Fastly, mais ne sont pas stockées dans le réseau Fastly. Tous les partenaires inclus dans l’offre Managed Services d’Adobe Commerce ont des obligations contractuelles pour assurer la protection des données sensibles. Managed Services ne déplace pas les données sensibles du client ou du consommateur des emplacements spécifiés par le client.

Dans le cadre de la prestation des services inclus dans l’offre Managed Services d’Adobe Commerce, le personnel de Managed Services a besoin d’un accès aux systèmes de production contenant des données sensibles. Ces employés sont formés à leurs obligations de protection des données clients et clients sensibles. L’accès à ces systèmes est limité aux employés qui en ont besoin. Ces employés n&#39;ont accès qu&#39;au temps nécessaire pour fournir ces services.

## Règlement général sur la protection des données (RGPD)

Le RGPD est un cadre juridique qui définit des lignes directrices pour la collecte et le traitement des informations personnelles pour les individus dans l’Union européenne (UE). Ces réglementations s’appliquent quel que soit l’endroit où se trouve le site, et les visiteurs de l’UE y ont accès.

Essentiellement, les visiteurs doivent être informés des données que le site leur collecte et donner leur consentement explicite à la collecte d’informations. Les sites doivent informer les visiteurs si les données personnelles détenues par le site sont violées.

Le commerçant ou la société qui gère le site doit également disposer d’un délégué à la protection des données dédié qui supervise la sécurité des données du site. Cette personne (ou l’équipe de gestion de site web) doit être disponible en contact si un visiteur demande que ses données soient effacées.

Le RGPD demande également que toute information d’identification personnelle (comme les noms, la race et la date de naissance) collectée soit rendue anonyme, soit rendue anonyme.

>[!NOTE]
>
> Cette page est simplement destinée à donner un aperçu général des éléments à prendre en compte pour le RGPD. Pour plus d’informations, veuillez consulter votre service juridique ou se référer au[texte officiel](https://eur-lex.europa.eu/eli/reg/2016/679/oj).

## Sauvegardes

Les sauvegardes sont effectuées toutes les heures pendant les dernières 24 heures de fonctionnement. Après la période de 24 heures, les sauvegardes sont conservées selon la planification suivante, à l’aide du service d’instantané AWS EBS :

| Période | Politique de conservation des données |
|----------------|-------------------------|
| Jours 1 à 3 | Chaque sauvegarde |
| Jours 4 à 6 | Une sauvegarde par jour |
| Semaines 2 à 6 | Une sauvegarde par semaine |
| Semaines 8 à 12 | Sauvegarde bihebdomadaire |
| Semaines 12 à 22 | Une sauvegarde par mois |

Cela crée une sauvegarde indépendante sur le stockage redondant. Les volumes EBS étant cryptés, les sauvegardes sont également cryptées. En outre, Managed Services effectue des sauvegardes à la demande des clients.

Votre approche de sauvegarde et de récupération d’Adobe Commerce Managed Services utilise une architecture haute disponibilité associée à des sauvegardes système complètes. Chaque projet est répliqué (toutes les données, le code et les ressources) dans trois zones de disponibilité AWS distinctes ; chaque zone dispose d’un centre de données distinct.
