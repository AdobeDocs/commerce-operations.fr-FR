---
title: Sécurisation de votre site et de votre infrastructure Commerce
description: Maintenez la sécurité en implémentant les bonnes pratiques de sécurité lors de la configuration et de la mise à jour des installations d’Adobe Commerce.
feature: Best Practices
exl-id: 50d8a464-6496-4e9a-b642-0c6d0eb51ba0
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '2085'
ht-degree: 0%

---

# Sécurisation de votre site et de votre infrastructure Commerce

L’établissement et la maintenance d’un environnement sécurisé pour les projets Adobe Commerce déployés sur l’infrastructure cloud sont une responsabilité partagée entre la clientèle d’Adobe Commerce, les partenaires en solutions et Adobe. Ce guide a pour but de fournir les bonnes pratiques pour les responsabilités du client.

Bien que vous ne puissiez pas éliminer tous les risques de sécurité, l’application de ces bonnes pratiques renforce la position de sécurité des installations Commerce. Un site et une infrastructure sécurisés réduisent le risque d&#39;attaques malveillantes, protègent les informations sensibles et minimisent les incidents de sécurité coûteux.

>[!NOTE]
>
>Pour plus d’informations sur les rôles et les responsabilités en matière de sécurisation et de maintenance des projets Adobe Commerce sur les infrastructures cloud, voir [Modèle de responsabilité partagée](/help/security-and-compliance/shared-responsibility.md#security-responsibilities-chart) dans le _Guide de sécurité et de conformité d’Adobe Commerce_.

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

## Recommandations prioritaires

Adobe considère que les recommandations suivantes sont de la plus haute priorité pour tous les clients. Implémentez ces bonnes pratiques de sécurité clés dans tous les déploiements de Commerce :

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Activez l’authentification à deux facteurs pour votre administrateur et toutes les connexions SSH**

- [Sécurité pour l’administrateur Commerce](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/security/security-admin)

- [Connexions SSH sécurisées](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/project/multi-factor-authentication) (infrastructure cloud)

Lorsque MFA est activé sur un projet, tous les comptes d’infrastructure cloud Adobe Commerce dotés d’un accès SSH doivent suivre un workflow d’authentification. Ce workflow nécessite un code d’authentification à deux facteurs (2FA) ou un jeton API et un certificat SSH pour accéder à l’environnement.

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Sécuriser l’administrateur**

- [Configurez une URL d’administration autre que celle par défaut](https://experienceleague.adobe.com/fr/docs/commerce-admin/stores-sales/site-store/store-urls#use-a-custom-admin-url) au lieu d’utiliser le `admin` par défaut ou un terme courant tel que `backend`. Cette configuration réduit l’exposition aux scripts qui tentent d’obtenir un accès non autorisé à votre site.

- [Configurer les paramètres de sécurité avancés](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/security/security-admin)—Ajoutez une clé secrète aux URL, exigez des mots de passe sensibles à la casse et limitez la durée de la session d&#39;administrateur, la durée de vie du mot de passe et les tentatives de connexion. Pour une sécurité renforcée, configurez la durée d’inactivité du clavier avant l’expiration de la session en cours et assurez-vous que le nom d’utilisateur et le mot de passe soient sensibles à la casse.

- [Activez reCAPTCHA](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/security/captcha/security-google-recaptcha) pour protéger l’administrateur contre les attaques automatisées par force brute.

- Appliquez le principe de moindre privilège lors de l’attribution d’[autorisations d’administrateur](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/user-accounts/permissions) aux rôles et rôles aux comptes utilisateur d’administrateur.

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Effectuez la mise à niveau vers la dernière version d’Adobe Commerce**

Gardez votre code à jour en [mettant à niveau votre projet Commerce vers la dernière version](#upgrade-to-the-latest-release) d’Adobe Commerce, des services Commerce et des extensions, y compris les correctifs de sécurité, les correctifs logiciels et les autres correctifs fournis par Adobe.

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Valeurs de configuration sensibles sécurisées**

Utilisez [gestion de la configuration](../../../configuration/cli/set-configuration-values.md) pour verrouiller les valeurs de configuration critiques.

Les commandes `lock config` et `lock env` de l’interface de ligne de commande configurent les variables d’environnement pour les empêcher d’être mises à jour par l’administrateur. La commande écrit la valeur dans le fichier `<Commerce base dir>/app/etc/env.php`. (Pour Commerce sur les projets d’infrastructure cloud, voir [Gestion de la configuration du magasin](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/configure-store/store-settings#sensitive-data).)

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Exécuter des analyses de sécurité**

Utilisez le service d&#39;analyse de sécurité Commerce [&#128279;](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/security/security-scan) pour surveiller tous les sites Adobe Commerce à la recherche de risques de sécurité et de programmes malveillants connus, et abonnez-vous pour recevoir des mises à jour de correctifs et des notifications de sécurité.

## Assurer la sécurité des extensions et du code personnalisé

Lorsque vous étendez Adobe Commerce en ajoutant des extensions tierces à partir de la Marketplace Adobe Commerce ou que vous ajoutez du code personnalisé, assurez la sécurité de ces personnalisations en appliquant les bonnes pratiques suivantes :

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Choisissez un partenaire soucieux de la sécurité ou un intégrateur de solution (SI)**—Assurez des intégrations sécurisées et du code personnalisé en sélectionnant les organisations ayant des antécédents de développement sécurisé.

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Utiliser des extensions sécurisées**—Identifiez les extensions les plus appropriées et les plus sécurisées pour les déploiements de Commerce en consultant votre intégrateur de solution ou votre développeur et en suivant les [bonnes pratiques relatives aux extensions Adobe](../planning/extensions.md).

- Seules les extensions sources provenant du Marketplace Adobe Commerce ou de l’intégrateur de solution. Si l’extension est sourcée par un intégrateur, assurez-vous que la propriété de la licence d’extension est transférable, au cas où l’intégrateur change.

- Réduisez l&#39;exposition aux risques en limitant le nombre d&#39;extensions et de fournisseurs.

- Si possible, vérifiez le code d’extension pour la sécurité avant de l’intégrer à l’application Commerce.

- Assurez-vous que les développeurs d’extensions PHP suivent les directives de développement, les processus et les bonnes pratiques de sécurité d’Adobe Commerce. Plus précisément, les développeurs doivent éviter d&#39;utiliser les fonctionnalités PHP qui peuvent conduire à l&#39;exécution de code à distance ou à une cryptographie faible. Voir [Sécurité](https://developer.adobe.com/commerce/php/best-practices/security/) dans le *Guide des bonnes pratiques pour les développeurs d’extensions*.

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Code d’audit** : consultez votre serveur et votre référentiel de code source pour identifier les restes de développement. Assurez-vous qu&#39;aucun fichier journal, répertoire .git, tunnel SQL, vidage de base de données ou fichier d&#39;informations php n&#39;est accessible.

## Mettre à niveau vers la dernière version

Adobe publie en permanence des composants de solution mis à jour pour améliorer la sécurité et mieux protéger les clients contre d’éventuels compromis. La mise à niveau vers la dernière version de l’application Adobe Commerce, des services installés et des extensions, ainsi que l’application des correctifs actuels constituent la principale méthode de protection contre les menaces de sécurité.

Commerce publie généralement des mises à jour de sécurité tous les trimestres, mais se réserve le droit de publier des correctifs pour les menaces de sécurité majeures en fonction de la priorité et d’autres facteurs.

Consultez les ressources suivantes pour plus d’informations sur les versions d’Adobe Commerce disponibles, les cycles de publication, ainsi que le processus de mise à niveau et de correctif :

- [Versions publiées](../../../release/versions.md)
- [Disponibilité du produit](../../../release/product-availability.md) (services Adobe Commerce et extensions créées par Adobe)
- [Politique relative au cycle de vie d’Adobe Commerce](../../../release/lifecycle-policy.md)
- [Avis de sécurité et de conformité](../../../release/security-enforcement-policy.md) (Adobe Commerce sur Cloud versions 2.4.4 à 2.4.9)
- [Guide de mise à niveau](../../../upgrade/overview.md)
- [Application de correctifs](../../../upgrade/patches/overview.md)

>[!TIP]
>
>Obtenez les dernières informations de sécurité et atténuez les problèmes de sécurité connus en vous abonnant au service de notification de sécurité [&#128279;](https://www.adobe.com/subscription/adobesecuritynotifications.html).

## Développement d’un plan de reprise après sinistre

Si votre site Commerce est compromis, contrôlez les dommages et restaurez rapidement les opérations normales de l’entreprise en développant et en mettant en œuvre un plan de reprise après sinistre complet.

Si un client ou une cliente a besoin de restaurer une instance Commerce en raison d’une catastrophe, Adobe peut lui fournir des fichiers de sauvegarde. Le client et l’intégrateur de solution, le cas échéant, peuvent effectuer la restauration.

Dans le cadre d’un plan de reprise après sinistre, Adobe recommande vivement aux clients d’[exporter la configuration de leur application Adobe Commerce](../../../configuration/cli/export-configuration.md) afin de faciliter le redéploiement si nécessaire à des fins de continuité d’activité. La principale raison pour laquelle exporter la configuration vers le système de fichiers est que la configuration du système prévaut sur la configuration de la base de données. Dans un système de fichiers en lecture seule, l’application doit être redéployée pour modifier les paramètres de configuration sensibles et offrir ainsi une couche de protection supplémentaire.

### Informations supplémentaires

**Adobe Commerce déployé sur une infrastructure cloud**

- [Sauvegarde et reprise après sinistre](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/architecture/pro-architecture#backup-and-disaster-recovery)

- [Gestion de la configuration des magasins pour Adobe Commerce sur les infrastructures cloud](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/configure-store/store-settings)

**Adobe Commerce déployé sur site**

- [Exporter les paramètres de configuration](../../../configuration/cli/export-configuration.md)

  - [Importer les paramètres de configuration](../../../configuration/cli/import-configuration.md)

  - [Sauvegarde et restauration du système de fichiers, du support et de la base de données](../../../installation/tutorials/backup.md)

## Maintenir un site et une infrastructure sécurisés

Cette section résume les bonnes pratiques de maintenance de la sécurité du site et de l’infrastructure pour une installation Adobe Commerce. Bon nombre de ces pratiques exemplaires visent à sécuriser l&#39;infrastructure informatique en général, de sorte que certaines des recommandations sont déjà mises en œuvre.

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Bloquer l’accès non autorisé**—Pour bloquer l’accès non autorisé au site Commerce et aux données client, collaborez avec votre partenaire d’hébergement pour configurer un tunnel VPN. Pour bloquer tout accès non autorisé à l’application Commerce, configurez un tunnel SSH.

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Utiliser un pare-feu d&#39;application web**—Analysez le trafic et découvrez des schémas suspects, tels que l&#39;envoi d&#39;informations de carte de crédit à une adresse IP inconnue à l&#39;aide d&#39;un pare-feu d&#39;application web.

Les installations Adobe Commerce déployées sur des infrastructures cloud peuvent utiliser les services WAF intégrés disponibles avec l’intégration [Fastly services](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/cdn/fastly)

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Configurer des paramètres de sécurité de mot de passe avancés**—Configurez des mots de passe sécurisés et modifiez-les au moins tous les 90 jours, comme recommandé par la norme PCI Data Security dans la section 8.2.4. Voir [Configurer les paramètres de sécurité d’administration](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/security/security-admin).

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Utiliser HTTPS** : si le site Commerce vient d’être implémenté, lancez l’ensemble du site en utilisant HTTPS. Google utilise HTTPS comme facteur de classement, et de nombreux utilisateurs n’envisagent d’acheter sur un site que s’il est sécurisé par HTTPS.

## Protection contre les programmes malveillants

Les attaques de logiciels malveillants ciblant les sites d&#39;e-commerce sont fréquentes, et les acteurs de la menace développent continuellement de nouvelles façons de récupérer les informations de carte de crédit et les informations personnelles des transactions.

Cependant, Adobe a constaté que la plupart des compromis de site ne sont pas dus à un attaquant innovant. Les acteurs de la menace profitent plutôt des vulnérabilités existantes non corrigées, des mots de passe inadéquats et des paramètres de propriété et d&#39;autorisation faibles du système de fichiers.

Dans les attaques les plus courantes, du code malveillant est injecté dans l’en-tête absolu ou le pied de page absolu d’un magasin client. Là, le code collecte les données de formulaire saisies par un client dans le storefront, y compris les informations de connexion du client et les données du formulaire de passage en caisse. Ensuite, ces données sont envoyées à un autre emplacement à des fins malveillantes plutôt qu’au serveur principal de Commerce. En outre, les logiciels malveillants peuvent empêcher l&#39;administrateur d&#39;exécuter du code qui remplace le formulaire de paiement d&#39;origine par un faux formulaire qui remplace toutes les protections définies par le fournisseur de paiement.

Les fraudeurs de cartes de crédit côté client sont un type de programme malveillant qui incorpore du code dans le contenu du site web du commerçant qui peut être exécuté dans le navigateur d’un utilisateur, comme illustré dans la figure suivante.

![Flux de données pour les attaques de logiciels malveillants ciblant les sites d’e-commerce](../../../assets/playbooks/malware-data-flow.png)

Après des actions telles que l’envoi d’un formulaire ou la modification d’un champ, l’émulateur sérialise les données et les envoie vers des points d’entrée tiers. Ces points d’entrée sont généralement d’autres sites web compromis qui servent de relais pour envoyer les données à leur destination finale.


>[!TIP]
>
>Si une attaque par programme malveillant affecte un site Commerce, suivez les bonnes pratiques d’Adobe Commerce pour [répondre à un incident de sécurité](../maintenance/respond-to-security-incident.md).

### Connaître les attaques les plus courantes

Vous trouverez ci-dessous une liste des catégories courantes d’attaques qu’Adobe recommande à tous les clients Commerce de connaître et contre lesquelles ils doivent prendre des mesures de protection :

- **Endommagement du site** : un attaquant endommage un site web en modifiant l’aspect visuel du site ou en ajoutant ses propres messages. Bien que l&#39;accès au site et aux comptes d&#39;utilisateurs ait été compromis, les informations de paiement restent souvent sécurisées.

- **Réseaux de zombies** : le serveur Commerce du client fait partie d&#39;un réseau de zombies qui envoie des courriers indésirables. Bien que les données utilisateur ne soient généralement pas compromises, les filtres anti-spam placent sur la liste bloquée le nom de domaine du client ou de la cliente, empêchant la diffusion de tout e-mail provenant du domaine. Le site du client peut également faire partie d’un réseau de zombies, ce qui entraîne une attaque par déni de service distribué (DDoS) sur d’autres sites. Le réseau de zombies bloque le trafic IP entrant vers le serveur Commerce, empêchant les clients de faire des achats.

- **Attaques directes du serveur**—Les données sont compromises, des portes dérobées et des logiciels malveillants sont installés et les opérations du site sont affectées. Les informations de paiement qui ne sont pas stockées sur le serveur sont moins susceptibles d&#39;être compromises par ces attaques.

- **Capture de carte silencieuse** - Dans cette attaque des plus désastreuses, les intrus installent un logiciel malveillant ou de capture de carte caché, ou pire, modifient le processus de passage en caisse pour collecter les données de carte de crédit. Ensuite, les données sont envoyées à un autre site pour être vendues sur le web profond. De telles attaques peuvent passer inaperçues pendant une longue période et peuvent entraîner une compromission majeure des comptes clients et des informations financières.

- **Journalisation des clés silencieuse** : l’acteur de la menace installe le code de journalisation des clés sur le serveur du client afin de rassembler les informations d’identification de l’utilisateur administrateur pour qu’il puisse se connecter et lancer d’autres attaques sans être détecté.

### Protection contre les attaques par recherche de mot de passe

Les attaques par recherche de mot de passe forcée peuvent entraîner un accès administrateur non autorisé. Protégez votre site contre ces attaques en suivant ces bonnes pratiques :

- Identifiez et protégez tous les points d’accès externes à l’installation de Commerce.

  Vous pouvez sécuriser l’accès à l’administration, qui nécessite la protection la plus importante, en suivant les [recommandations de priorité](#priority-recommendations) d’Adobe lors de la configuration de votre projet Commerce.

- Contrôlez l’accès au site Commerce en configurant une liste de contrôle d’accès qui autorise uniquement l’accès aux utilisateurs provenant d’une adresse IP ou d’un réseau spécifié.

  Vous pouvez utiliser une liste de contrôle d’accès Fastly Edge avec un fragment de code VCL personnalisé pour filtrer les requêtes entrantes et autoriser l’accès par adresse IP. Voir [Custom VCL for allow requests](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/cdn/custom-vcl-snippets/fastly-vcl-allowlist).


  >[!TIP]
  >
  >Si vous employez une main-d’œuvre distante, assurez-vous que les adresses IP des employés distants sont incluses dans la liste des adresses avec l’autorisation d’accéder au site Commerce.

### Empêcher les exploits de détournement de clic

Adobe protège votre boutique des attaques de détournement de clic en fournissant l’en-tête de requête HTTP `X-Frame-Options` que vous pouvez inclure dans les requêtes à votre storefront. Voir [Empêcher les exploits de détournement de clic](../../../configuration/security/xframe-options.md) dans le *Guide de configuration d’Adobe Commerce*.
