---
title: Sécurité de l’infrastructure cloud
description: Découvrez comment Adobe protège Adobe Commerce sur l’infrastructure cloud.
exl-id: cd5d1106-c8db-4b70-b1c7-12378d7d77a7
feature: Cloud, Security
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1691'
ht-degree: 0%

---


# Sécurité

L’ [ architecture de plan Pro Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) est conçue pour fournir un environnement hautement sécurisé. Chaque client est déployé dans son propre environnement serveur isolé, séparé des autres clients. Les détails de sécurité de l’environnement de production sont décrits ci-dessous.

## Navigateurs Web

La majeure partie du trafic entrant et sortant de l’environnement cloud provient des navigateurs Web des consommateurs. Le trafic client peut être sécurisé à l’aide du protocole HTTPS pour toutes les pages du site web (en utilisant soit une certification SSL partagée, soit le certificat SSL du client lui-même, moyennant des frais supplémentaires). Les pages de passage en caisse et de compte sont toujours servies à l’aide du protocole HTTPS. La bonne pratique consiste à diffuser toutes les pages sous HTTPS.

## Réseau de diffusion de contenu

Fournit rapidement une protection CDN (Content Delivery Network, réseau de diffusion de contenu) et DDoS (déni de service distribué). Fastly CDN permet d’isoler l’accès direct aux serveurs d’origine. Le DNS public ne pointe que vers le réseau Fastly. La solution Fastly DDoS protège contre les attaques de couche 3 et de couche 4 très perturbatrices, ainsi que contre les attaques de couche 7 plus complexes. Les attaques de couche 7 peuvent être bloquées à l’aide de règles personnalisées basées sur l’ensemble des requêtes HTTP/HTTPS et sur la base de critères clients et de requêtes, y compris les en-têtes, les cookies, le chemin de requête et l’adresse IP du client, ou des indicateurs tels que la géolocalisation.

Voir [la présentation](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html) des services Fastly dans le Guide _Cloud_.

## Pare-feu d’applications web

Le pare-feu d’applications web rapide (WAF) est utilisé pour fournir une protection supplémentaire. Le module WAF basé sur le cloud de Fastly utilise des règles tierces provenant de sources commerciales et open source, telles que le jeu de règles principal OWASP. En outre, Adobe règles spécifiques au Commerce sont utilisées. Les clients sont protégés contre les attaques clés de la couche application, y compris les attaques par injection et les entrées malveillantes, le cross-site scripting, l’exfiltration de données, les violations du protocole HTTP et d’autres menaces OWASP.

Les règles WAF sont mises à jour par Adobe Commerce si de nouvelles vulnérabilités sont détectées, ce qui Managed Services permet de « corriger virtuellement » les problèmes de sécurité avant les correctifs logiciels. Le WAF Fastly ne fournit pas de services de limitation de débit ou de détection de bots. Si vous le souhaitez, les clients peuvent obtenir une licence pour un service de détection de bots tiers compatible avec Fastly.

Voir [Web Application Firewall (WAF)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service.html) dans le _Cloud Guide_.

## Cloud privé virtuel

L’environnement de production de plan Adobe Commerce Pro est configuré en tant que cloud privé virtuel (VPC) afin que les serveurs de production soient isolés et aient une capacité limitée à se connecter à l’environnement cloud et en sortir. Seules les connexions sécurisées aux serveurs cloud sont autorisées. Les protocoles sécurisés tels que SFTP ou rsync peuvent être utilisés pour les transferts de fichiers.

Les clients peuvent utiliser des tunnels SSH pour sécuriser les communications avec l’application. L’accès à AWS PrivateLink peut entraîner des frais supplémentaires. Toutes les connexions à ces serveurs sont contrôlées à l’aide des groupes de sécurité AWS, un pare-feu virtuel qui limite les connexions à l’environnement. Les ressources techniques des clients peuvent accéder à ces serveurs à l’aide de SSH.

## Chiffrement

Amazon Elastic Block Store (EBS) est utilisé pour le stockage. Tous les volumes EBS sont cryptés à l’aide de l’algorithme AES-256, ce qui signifie que les données sont chiffrées au repos. Le système chiffre également les données en transit entre le CDN et l’origine, ainsi qu’entre les serveurs d’origine. Les mots de passe du client sont stockés sous la forme de hachages. Les informations d’identification sensibles, y compris les informations d’identification de la passerelle de paiement, sont chiffrées à l’aide de l’algorithme SHA-256.

L’application Adobe Commerce ne prend pas en charge le chiffrement ou le chiffrement au niveau des colonnes ou des lignes lorsque les données ne sont pas au repos ou ne sont pas en transit entre les serveurs. Le client peut gérer les clés de chiffrement dans l’application. Les clés utilisées par le système sont stockées dans le système de gestion des clés AWS et doivent être gérées par Managed Services pour fournir des parties du service.

## Détection et réponse des points de fin

[!DNL CrowdStrike Falcon], un agent léger de détection et de réponse aux points de terminaison (EDR) de nouvelle génération est installé sur tous les points de terminaison (y compris les serveurs) dans Adobe. Les agents EDR protègent Adobe données et systèmes grâce à une surveillance et une collecte continues en temps réel, ce qui permet une identification et une réponse rapides aux menaces.

## Test d’intrusion

Managed Services effectue régulièrement des tests de pénétration du système Adobe Commerce Cloud avec l’application prête à l’emploi. Les clients sont responsables de tout test de pénétration de leur application personnalisée.

## Passerelle de paiement

Adobe Commerce nécessite des intégrations de passerelle de paiement où les données de carte de crédit sont transmises directement du navigateur du consommateur à la passerelle de paiement. Les données de carte ne sont jamais disponibles dans aucun des environnements Managed Services de plan Adobe Commerce Pro. Les actions sur les transactions effectuées par l’application de commerce électronique sont effectuées à l’aide d’une référence à la transaction à partir de la passerelle.

## application Adobe Commerce

Adobe teste régulièrement le code de l’application principale à la recherche de failles de sécurité. Les correctifs relatifs aux défauts et aux problèmes de sécurité sont fournis aux clients. L’équipe de sécurité des produits valide les produits Adobe Commerce en respectant les directives de sécurité des applications OWASP. Plusieurs outils d’évaluation des vulnérabilités de la sécurité et fournisseurs externes sont utilisés pour tester et vérifier la conformité. Les outils de sécurité incluent :

- Numérisation statique et dynamique des codes postaux
- Analyse du code source RIPS
- Services d’analyse des vulnérabilités de Trustwave et d’Alert Logic
- Burp Suite Pro
- OWASPZAP
- etSqlMap

La base de code complète est analysée avec ces outils toutes les deux semaines. Les clients sont informés des correctifs de sécurité par e-mails directs, notifications dans l’application et dans le Centre](https://helpx.adobe.com/security.html) de [sécurité.

Les clients doivent s’assurer que ces correctifs sont appliqués à leur application personnalisée dans les 30 jours suivant leur publication, conformément aux directives PCI. Adobe fournit également un [outil](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) d’analyse de sécurité qui permet aux commerçants de surveiller régulièrement leurs sites et de recevoir des mises à jour sur les risques de sécurité connus, les logiciels malveillants et les accès non autorisés. L’outil d’analyse de sécurité est un service gratuit qui peut être exécuté sur n’importe quelle version de Adobe Commerce.

Pour encourager les chercheurs en sécurité à identifier et signaler les vulnérabilités, Adobe Commerce dispose d’un [programme](https://hackerone.com/magento) de bug-bounty en plus des tests internes. De plus, le client reçoit le code source complet de l’application pour son propre examen s’il le souhaite.

## Système de fichiers en lecture seule

Tout le code exécutable est déployé dans une image de système de fichiers en lecture seule, ce qui réduit considérablement les surfaces disponibles pour l’attaque. Le processus de déploiement crée une image Squash-FS pour réduire les possibilités d’injection de code PHP ou JavaScript dans le système ou de modification des fichiers d’application Adobe Commerce.

## Déploiement à distance

La seule façon d’obtenir du code exécutable dans l’environnement de production Managed Services consiste à l’exécuter via un processus de provisionnement. L’approvisionnement consiste à pousser le code source de votre référentiel source vers un référentiel distant qui lance un processus de déploiement. L’accès à cette cible de déploiement est contrôlé, vous avez donc un contrôle total sur qui peut accéder à la cible de déploiement. Tous les déploiements de code d’application dans l’environnement hors production sont contrôlés par le client.

## Journalisation

Toutes les activités AWS sont connectées à AWS CloudTrail. Les journaux du système d’exploitation, du serveur d’applications et de la base de données sont stockés sur les serveurs de production et dans des sauvegardes. Toutes les modifications du code source sont enregistrées dans un référentiel Git. L’historique de déploiement est disponible dans l’ [interface web du projet](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/overview) d’Adobe Commerce. Tous les accès à l’assistance sont consignés et les sessions d’assistance sont enregistrées.

Voir [Afficher et gérer les journaux](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) dans le _Guide Cloud_.

## Données sensibles

Les données sensibles peuvent couvrir soit les informations personnelles des consommateurs, soit les données confidentielles de Managed Services clients. La protection des données clients et clients sensibles est une obligation essentielle pour Adobe Commerce Managed Services. Les clients Managed Services et Adobe ont des obligations légales concernant les informations d’identification personnelle. Outre les fonctionnalités de sécurité de l’architecture, il existe d’autres contrôles pour limiter la distribution et l’accès aux données sensibles.

Les clients détiennent leurs données et contrôlent l’emplacement de ces données. Le client spécifie l’emplacement où résident ses instances de production et de développement. Ils spécifient également l’emplacement utilisé pour l’environnement de création de rapports Adobe Commerce avec Commerce et si cette application de création de rapports Adobe Commerce a accès ou non à des informations d’identification personnelle. Les instances de production peuvent se trouver dans la plupart des régions AWS, tandis que les environnements de création de rapports de développement et de commerce Adobe se trouvent actuellement aux États-Unis ou dans l’Union européenne.

Les données sensibles peuvent passer par le réseau de serveurs Fastly CDN mais ne sont pas stockées dans le réseau Fastly. Tous les partenaires inclus dans l’offre Managed Services ont des obligations contractuelles pour assurer la protection des données sensibles. Managed Services ne déplace pas les données sensibles du client ou du consommateur des emplacements spécifiés par le client.

Dans le cadre de la prestation des services inclus dans l’offre Managed Services, le personnel de Managed Services a besoin d’un accès aux systèmes de production contenant des données sensibles. Ces employés sont formés à leurs obligations de protection des données clients et clients sensibles. L’accès à ces systèmes est limité aux employés qui en ont besoin. Ces employés n&#39;ont accès qu&#39;au temps nécessaire pour fournir ces services.

## Règlement général sur la protection des données

Le Règlement général sur la protection des données (RGPD) est un cadre juridique qui établit des lignes directrices pour la collecte et le traitement des informations personnelles des individus dans l’Union européenne (UE). Ces réglementations s’appliquent quel que soit l’endroit où le site est basé, et les visiteurs de l’UE y ont accès.

Les visiteurs doivent être informés des données qu’un site recueille auprès d’eux et consentir explicitement à la collecte d’informations. Sites devez informer les visiteurs en cas de violation des données personnelles détenues par le site.

Le commerçant ou la société exploitant le site doit avoir un délégué à la protection des données dédié qui supervise la sécurité des données du site. Le responsable de la confidentialité des données (ou l’équipe de gestion du site Web) doit être disponible pour contacter si un visiteur demande que ses données soient effacées.

Le RGPD exige que toutes les informations d’identification personnelle (telles que les noms, la race et la date de naissance) collectées soient rendues anonymes ou pseudonymes.

>[!NOTE]
>
>Cette page donne un aperçu général des éléments à prendre en compte pour le RGPD. Pour plus d’informations sur la façon dont Adobe Commerce stocke les informations personnelles, reportez-vous au _[Guide de sécurité et de conformité](../../../security-and-compliance/privacy/gdpr.md)_. Pour déterminer comment votre entreprise doit se conformer à toute obligation juridique, consultez votre service juridique ou reportez-vous au [texte officiel](https://eur-lex.europa.eu/eli/reg/2016/679/oj).

## Sauvegardes

Les sauvegardes sont effectuées toutes les heures pendant les dernières 24 heures de fonctionnement. Après la période de 24 heures, les sauvegardes sont conservées selon un calendrier utilisant le service d’instantané AWS EBS. Voir [Stratégie de rétention](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#retention-policy) dans le _Guide Cloud_.

Le service crée une sauvegarde indépendante sur le stockage redondant. Étant donné que les volumes EBS sont chiffrés, les sauvegardes sont également chiffrées. En outre, Managed Services effectue des sauvegardes à la demande à la demande du client.

Votre approche de sauvegarde et de restauration Managed Services utilise une architecture haute disponibilité combinée à des sauvegardes système complètes. Chaque projet est répliqué (toutes les données, le code et les ressources) dans trois zones de disponibilité AWS distinctes ; chaque zone dispose d’un centre de données distinct.

Voir [Gestion des instantanés et des sauvegardes](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html) dans le _Guide de Cloud_.
