---
title: Sécurisez votre site et votre infrastructure Commerce
description: Maintenez la sécurité en mettant en oeuvre les bonnes pratiques de sécurité lors de la configuration, de la configuration et de la mise à jour des installations Adobe Commerce.
feature: Best Practices
exl-id: 50d8a464-6496-4e9a-b642-0c6d0eb51ba0
source-git-commit: cbfd19efd9f489fefa16d93cbd8116eefb57a900
workflow-type: tm+mt
source-wordcount: '2008'
ht-degree: 0%

---

# Sécurisez votre site et votre infrastructure Commerce

La création et la maintenance d’un environnement sécurisé pour les projets Adobe Commerce déployés sur l’infrastructure cloud est une responsabilité partagée entre les clients Adobe Commerce, les partenaires de solution et l’Adobe. Ce guide a pour but de fournir des bonnes pratiques pour le côté client de l’équation.

Bien que vous ne puissiez pas éliminer tous les risques de sécurité, l’application de ces bonnes pratiques renforce la position de sécurité des installations Commerce. Un site et une infrastructure sécurisés constituent une cible moins attrayante pour les attaques malveillantes, assurent la sécurité de la solution et des informations sensibles des clients et contribuent à minimiser les incidents liés à la sécurité qui peuvent entraîner des interruptions du site et des enquêtes coûteuses.

>[!NOTE]
>
>Pour plus d’informations sur les rôles et les responsabilités relatifs à la sécurisation et à la maintenance des projets Adobe Commerce sur l’infrastructure cloud, voir la section [Guide de responsabilité partagée](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibilities-guide.pdf) dans le Centre de gestion de l’Adobe.

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Recommandations relatives aux priorités

Adobe considère que les recommandations suivantes ont la priorité la plus élevée pour tous les clients. Mettez en oeuvre ces bonnes pratiques de sécurité clés dans tous les déploiements de Commerce :

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Activer l’authentification à deux facteurs pour votre administrateur et toutes les connexions SSH**

- [Sécurité pour l’administrateur Commerce](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication.html)

- [Connexions SSH sécurisées](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/multi-factor-authentication.html) (infrastructure cloud)

Lorsque MFA est activé sur un projet, tous les comptes d’infrastructure cloud avec accès SSH doivent suivre un workflow d’authentification. Ce workflow nécessite un code d’authentification à deux facteurs (2FA) ou un jeton API et un certificat SSH pour accéder à l’environnement.

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Sécurisation de l’administrateur**

- [Configuration d’une URL d’administration autre que celle par défaut](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) au lieu d’utiliser la valeur par défaut `admin` ou un terme commun, tel que `backend`. Cette configuration réduit l’exposition aux scripts qui tentent d’obtenir un accès non autorisé à votre site.

- [Configuration des paramètres de sécurité avancés](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html): ajoutez une clé secrète aux URL, exigez que les mots de passe soient sensibles à la casse et limitez la durée de session de l’administrateur, l’intervalle de durée de vie du mot de passe et le nombre de tentatives de connexion autorisées avant de verrouiller un compte utilisateur administrateur. Pour une sécurité accrue, configurez la durée d’inactivité du clavier avant l’expiration de la session en cours, en exigeant que le nom d’utilisateur et le mot de passe soient sensibles à la casse.

- [Activer ReCAPTCHA](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/captcha/security-google-recaptcha.html) pour protéger l&#39;administrateur des attaques de force brute automatisées.

- Respectez le principe du moindre privilège lors de l’attribution [Autorisations d’administrateur](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions.html) aux rôles et aux rôles des comptes utilisateurs administrateurs.

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Mise à niveau vers la dernière version d’Adobe Commerce**

Conserver votre code mis à jour par [mise à niveau de votre projet Commerce vers la dernière version](#upgrade-to-the-latest-release) d’Adobe Commerce, de Commerce Services et des extensions, y compris les correctifs de sécurité, correctifs, correctifs logiciels et autres correctifs fournis par Adobe.

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Sécurisation des valeurs de configuration sensibles**

Utilisation [gestion de la configuration](../../../configuration/cli/set-configuration-values.md) pour verrouiller les valeurs de configuration critiques.

La variable `lock config` et `lock env` Les commandes de l’interface de ligne de commande configurent les variables d’environnement pour les empêcher d’être mises à jour à partir de l’administrateur. La commande écrit la valeur dans la variable `<Commerce base dir>/app/etc/env.php` fichier . (Pour Commerce sur les projets d’infrastructure cloud, voir [Gestion des configurations de magasin](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html#sensitive-data).)

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Exécution des analyses de sécurité**

Utilisez la variable [Service d’analyse de sécurité de commerce](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) pour surveiller tous les sites Adobe Commerce et Magento Open Source à la recherche de risques de sécurité et de logiciels malveillants connus, et s’inscrire pour recevoir des mises à jour de correctifs et des notifications de sécurité.

## Garantir la sécurité des extensions et du code personnalisé

Lorsque vous étendez Adobe Commerce en ajoutant des extensions tierces à partir d’Adobe Commerce Marketplace ou en ajoutant du code personnalisé, assurez-vous de la sécurité de ces personnalisations en appliquant les bonnes pratiques suivantes :

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Choisir un partenaire ou un intégrateur de solution (SI) maîtrisant la sécurité**: garantissez des intégrations sécurisées et une livraison sécurisée de code personnalisé en sélectionnant les organisations qui suivent des pratiques de développement sécurisées et qui disposent d’un solide suivi de la prévention et de la résolution des problèmes de sécurité.

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Utilisation d’extensions sécurisées**: identifiez les extensions les plus appropriées et les plus sécurisées pour les déploiements Commerce en consultant votre intégrateur de solution ou votre développeur et en procédant comme suit : [Bonnes pratiques relatives aux extensions d’Adobe](../planning/extensions.md).

- Uniquement les extensions source d’Adobe Commerce Marketplace ou via l’intégrateur de solution. Si l’extension est issue d’un intégrateur, assurez-vous que la propriété de la licence d’extension est transférable, au cas où l’intégrateur changerait.

- Réduisez l’exposition aux risques en limitant le nombre d’extensions et de fournisseurs.

- Si possible, passez en revue le code d’extension pour plus de sécurité avant l’intégration à l’application Commerce.

- Assurez-vous que les développeurs d’extensions PHP suivent les directives de développement, les processus et les bonnes pratiques en matière de sécurité d’Adobe Commerce. Plus précisément, les développeurs doivent éviter d’utiliser des fonctionnalités PHP pouvant entraîner l’exécution de code à distance ou une cryptographie faible. Voir [Sécurité](https://developer.adobe.com/commerce/php/best-practices/security/) dans le *Guide des bonnes pratiques pour les développeurs d’extensions*.

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Code d’audit**: vérifiez les restes de développement de votre serveur et de votre référentiel de code source. Assurez-vous qu’il n’existe pas de fichiers journaux accessibles, de répertoires .git publiquement visibles, de tunnels pour exécuter des instructions SQL, de vidages de base de données, de fichiers d’informations php ou de tout autre fichier non protégé qui n’est pas nécessaire et qui peut être utilisé dans une attaque.

## Mise à niveau vers la dernière version

Adobe publie continuellement des composants de solution mis à jour afin d’améliorer la sécurité et de mieux protéger les clients contre tout compromis possible. La mise à niveau vers la dernière version de l’application Adobe Commerce, les services installés et les extensions et l’application des correctifs actuels est la première et la meilleure ligne de défense contre les menaces de sécurité.

Commerce publie généralement des mises à jour de sécurité sur une base trimestrielle, mais se réserve le droit de publier des correctifs pour les principales menaces de sécurité en fonction de leurs priorités et d’autres facteurs.

Consultez les ressources suivantes pour plus d’informations sur les versions d’Adobe Commerce disponibles, les cycles de publication et le processus de mise à niveau et de correctif :

- [Versions publiées](../../../release/versions.md)
- [Disponibilité du produit](../../../release/product-availability.md) (Services Adobe Commerce et extensions créées par Adobe)
- [Stratégie de cycle de vie Adobe Commerce](../../../release/lifecycle-policy.md)
- [Guide de mise à niveau](../../../upgrade/overview.md)
- [Comment appliquer des correctifs](../../../upgrade/patches/overview.md)

>[!TIP]
>
>Obtenez les informations de sécurité les plus récentes et parvenez à atténuer les problèmes de sécurité connus en vous abonnant au [Adobe Security Notification Service](https://www.adobe.com/subscription/adbeSecurityNotifications.html).

## Développer un plan de reprise sur sinistre

Si votre site Commerce est compromis, contrôlez les dommages et restaurez rapidement les opérations commerciales normales en développant et en mettant en oeuvre un plan complet de reprise sur sinistre.

Si un client nécessite la restauration d’une instance Commerce en raison d’un désastre, Adobe peut fournir au client des fichiers de sauvegarde. Le client et l’intégrateur de solution, le cas échéant, peuvent effectuer la restauration.

Dans le cadre d’un plan de reprise après sinistre, Adobe recommande vivement aux clients de [exporter leur configuration d’application Adobe Commerce ;](../../../configuration/cli/export-configuration.md) pour faciliter le redéploiement, s’il est nécessaire à des fins de continuité d’activité. La raison principale pour laquelle exporter la configuration vers le système de fichiers est que la configuration du système a priorité sur la configuration de la base de données. Dans un système de fichiers en lecture seule, l’application doit être redéployée pour modifier les paramètres de configuration sensibles, fournissant ainsi une couche de protection supplémentaire.

### Informations supplémentaires

**Adobe Commerce déployé sur l’infrastructure cloud**

- [Sauvegarde et reprise après sinistre](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#backup-and-disaster-recovery)

- [Gestion de la configuration du magasin pour Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html)

**Adobe Commerce déployé sur site**

- [Idées de reprise sur sinistre](../../infrastructure/self-hosting/disaster-recovery-ideas.md)

- [Sauvegarde et récupération](../../infrastructure/self-hosting/disaster-recovery-ideas.md)

- [Exportation des paramètres de configuration](../../../configuration/cli/export-configuration.md)

   - [Importation des paramètres de configuration](../../../configuration/cli/import-configuration.md)

   - [Sauvegarde et restauration du système de fichiers, du média et de la base de données](../../../installation/tutorials/backup.md)

## Maintenir un site et une infrastructure sécurisés

Cette section résume les bonnes pratiques relatives à la maintenance de la sécurité du site et de l’infrastructure pour une installation Adobe Commerce. La plupart de ces bonnes pratiques se concentrent sur la sécurisation de l’infrastructure informatique en général. Certaines de ces recommandations peuvent donc déjà être mises en oeuvre.

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Bloquer l’accès non autorisé**: collaborez avec votre partenaire d’hébergement pour configurer un tunnel VPN afin de bloquer l’accès non autorisé au site Commerce et aux données client. Configurez un tunnel SSH pour bloquer l’accès non autorisé à l’application Commerce.

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Utilisation d’un pare-feu d’application web**: analysez le trafic et découvrez des schémas suspects, tels que des informations de carte de crédit envoyées à une adresse IP inconnue à l’aide d’un pare-feu d’application web.

Les installations Adobe Commerce déployées sur l’infrastructure cloud peuvent utiliser les services WF intégrés disponibles avec la variable [Intégration rapide des services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Configuration des paramètres avancés de protection des mots de passe**: configurez les mots de passe difficiles à deviner et modifiez-les au moins tous les 90 jours, comme recommandé par la norme de sécurité des données PCI dans la section 8.2.4. Voir [Configuration des paramètres de sécurité d’administration](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html).

![Liste de contrôle](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Utiliser HTTPS**: si le site Commerce vient d’être mis en oeuvre, lancez l’intégralité du site à l’aide de HTTPS. Google utilise non seulement HTTPS comme facteur de classement, mais de nombreux utilisateurs n’envisagent même pas d’acheter sur un site, sauf s’il est sécurisé avec HTTPS.

## Protect contre les malware

Les attaques de logiciels malveillants ciblant les sites de commerce électronique sont trop courantes, et les acteurs de la menace développent continuellement de nouvelles façons de prélever des cartes de crédit et des informations personnelles sur les transactions.

Cependant, l&#39;Adobe a découvert que la plupart des compromis de site ne sont pas dus à un hacker innovant. Au contraire, les acteurs de la menace profitent souvent de vulnérabilités existantes et non corrigées, de mots de passe médiocres et de paramètres de propriété et d&#39;autorisation faibles dans le système de fichiers.

Dans les attaques les plus courantes, du code malveillant est injecté dans l’en-tête absolu ou dans le pied de page absolu d’une boutique de clients. Là-bas, le code collecte les données de formulaire qu’un client entre dans le storefront, y compris les informations d’identification de connexion et les données de formulaire de passage en caisse. Ces données sont ensuite envoyées à un autre emplacement à des fins malveillantes plutôt qu’au serveur principal Commerce. En outre, les logiciels malveillants peuvent compromettre l&#39;exécution par l&#39;administrateur du code qui remplace le formulaire de paiement d&#39;origine par un faux formulaire qui remplace toute protection définie par le fournisseur de paiement.

Les escrocs de carte de crédit côté client sont un type de logiciel malveillant qui incorpore le code dans le contenu du site web marchand pouvant être exécuté dans le navigateur d’un utilisateur, comme illustré dans la figure suivante.

![Flux de données pour les attaques par logiciels malveillants ciblant les sites de commerce électronique](../../../assets/playbooks/malware-data-flow.svg)

Une fois certaines actions effectuées (par exemple, l’envoi d’un formulaire par un utilisateur ou la modification d’une valeur de champ), la visionneuse sérialise les données et les envoie à des points de terminaison tiers. Ces points de terminaison sont généralement d’autres sites web compromis qui agissent comme un relais pour envoyer les données vers sa destination finale.


>[!TIP]
>
>Si un site Commerce est affecté par une attaque par un logiciel malveillant, suivez les bonnes pratiques d’Adobe Commerce pour [réponse à un incident de sécurité](../maintenance/respond-to-security-incident.md).

### Connaître les attaques les plus courantes

Vous trouverez ci-dessous une liste des catégories courantes d’attaques auxquelles Adobe recommande à tous les clients Commerce d’être informés et de prendre des mesures pour les protéger :

- **Déformation du site**— Un attaquant endommage un site web en modifiant l&#39;aspect visuel du site ou en ajoutant ses propres messages. Bien que l’accès au site et aux comptes d’utilisateurs ait été compromis, les informations de paiement restent souvent protégées.

- **Botnets**: le serveur Commerce du client devient une partie d’un botnet qui envoie des emails de spam. Bien que les données utilisateur ne soient pas généralement compromises, le nom de domaine du client peut être placé sur la liste bloquée par des filtres anti-spam, ce qui empêche la diffusion de tout courrier électronique provenant du domaine. Le site du client peut également faire partie d’un botnet, ce qui entraîne une attaque par déni de service (DDoS) sur un ou plusieurs autres sites. Le botnet peut bloquer le trafic IP entrant vers le serveur Commerce, empêchant ainsi les clients de faire leurs achats.

- **Attaques directes du serveur**: les données sont compromises, les backdoors et les logiciels malveillants sont installés, et les opérations du site sont affectées. Les informations de paiement qui ne sont pas stockées sur le serveur sont moins susceptibles d’être compromises par ces attaques.

- **Capture silencieuse de carte**: dans cette attaque la plus désastreuse, les intrus installent des logiciels malveillants cachés ou des logiciels de capture de carte, ou pire, modifient le processus de passage en caisse pour collecter les données de carte de crédit. Ensuite, les données sont envoyées à un autre site pour être vendues sur le web noir. De telles attaques peuvent passer inaperçues pendant une longue période et entraîner des compromis majeurs entre les comptes clients et les informations financières.

- **Journalisation des clés silencieuse**: l’acteur de menace installe le code de journalisation clé sur le serveur client afin de rassembler les informations d’identification de l’utilisateur administrateur afin qu’il puisse se connecter et lancer d’autres attaques sans être détecté.

### Protect contre les attaques par devinette de mot de passe

Les attaques par devinette force le mot de passe peuvent entraîner un accès administrateur non autorisé. Protect votre site à partir de ces attaques en suivant les bonnes pratiques suivantes :

- Identifiez et protégez tous les points où l’installation de Commerce est accessible depuis l’extérieur.

  Vous pouvez sécuriser l’accès à l’administrateur, qui requiert généralement la plus grande protection, en suivant l’Adobe [recommandations prioritaires](#priority-recommendations) lors de la configuration de votre projet Commerce.

- Contrôlez l’accès au site Commerce en configurant une liste de contrôle d’accès qui autorise uniquement l’accès aux utilisateurs provenant d’une adresse IP ou d’un réseau spécifié.

  Vous pouvez utiliser une liste de contrôle d’accès Edge Fastly avec un extrait de code VCL personnalisé pour filtrer les requêtes entrantes et autoriser l’accès par adresse IP. Voir [VCL personnalisée pour autoriser les requêtes](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-allowlist.html).


  >[!TIP]
  >
  >Si vous employez une main-d’oeuvre distante, assurez-vous que les adresses IP des employés distants sont incluses dans la liste des adresses avec autorisation d’accès au site Commerce.

### Prévention des explosions de détournement de clic

Adobe protège votre magasin des attaques de détournement de clics en fournissant la variable `X-Frame-Options` En-tête de requête HTTP que vous pouvez inclure dans les requêtes de votre storefront. Voir [Prévention des explosions de détournement de clic](../../../configuration/security/xframe-options.md) dans le *Guide de configuration d’Adobe Commerce*.
