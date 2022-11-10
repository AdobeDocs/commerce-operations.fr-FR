---
title: Prévention et réponse à un incident de sécurité
description: Découvrez les bonnes pratiques pour éviter et répondre aux incidents de sécurité dans votre projet d’infrastructure cloud Adobe Commerce.
role: Admin, Developer, Leader, User
feature-set: Commerce
feature: Best Practices
source-git-commit: bb9b8cc9993a70ea50667f08c8260759ab0f91dc
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 0%

---


# Bonnes pratiques pour aider à prévenir un incident de sécurité et à y répondre

La sécurité Adobe Commerce fonctionne sous une [Responsabilité partagée](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) modèle. Il est essentiel de comprendre à quel Adobe et à quelles équipes techniques sont responsables. Ci-dessous, un résumé [Bonnes pratiques en matière de sécurité](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf) pour vous assurer que votre projet dispose des meilleurs contrôles de sécurité en place et de la meilleure façon de répondre à un incident de sécurité.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud

## Réponse à un incident

Il y a de nombreuses considérations à prendre en compte lorsque vous répondez à un incident de sécurité. Si vous pensez avoir rencontré un incident de sécurité récent pour votre projet d’infrastructure cloud Adobe Commerce, il est important de contrôler tous les accès des comptes utilisateur admin, d’activer les contrôles d’authentification multifacteur avancé (MFA), de conserver les journaux critiques et de passer en revue les mises à niveau de sécurité de votre version d’Adobe Commerce.

D’autres recommandations sont présentées ci-dessous. Ils peuvent vous aider à empêcher tout accès non autorisé et à lancer le processus d’analyse des incidents.

## Comment empêcher des incidents de sécurité

Suivez ces bonnes pratiques de sécurité pour prévenir de manière proactive les incidents de sécurité qui affectent vos sites et storefronts Adobe Commerce :

- [Activation de 2FA pour l’accès administrateur](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html).
L’authentification à deux facteurs est largement utilisée et il est courant de générer des codes d’accès pour différents sites web sur la même application. Vous êtes ainsi le seul à pouvoir vous connecter à votre compte utilisateur. Si vous perdez votre mot de passe ou si un robot l’anticipe, l’authentification à deux facteurs ajoute une couche de protection.
- [Activation de MFA pour l’accès SSH](https://devdocs.magento.com/cloud/project/project-enable-mfa-enforcement.html).
Lorsque MFA est activé sur un projet, tous les comptes Adobe Commerce sur l’infrastructure cloud disposant d’un accès SSH doivent suivre un workflow d’authentification qui nécessite un code d’authentification à deux facteurs (2FA) ou un jeton API et un certificat SSH pour accéder à l’environnement.
- Effectuez la mise à niveau vers la dernière version d’Adobe Commerce.
Adobe publie des correctifs fonctionnels et de sécurité pour chaque version prise en charge d’Adobe Commerce.
- Configurez et utilisez un [URL d’administration autre que celle par défaut](https://docs.magento.com/user-guide/stores/store-urls-custom-admin.html).
Adobe vous recommande d’utiliser une URL d’administration personnalisée unique au lieu de la valeur par défaut. `admin` ou un terme commun tel que *backend*. Bien que cette modification de configuration ne protège pas directement votre site d’un acteur négatif déterminé, elle peut réduire l’exposition aux scripts qui tentent d’obtenir un accès non autorisé.
- Empêcher la modification ou la mise à jour des valeurs de configuration dans l’Admin à l’aide de la variable  [`bin/magento config:set` Commande de l’interface de ligne de commande avec `lock env` option de configuration](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values.html#set-configuration-values-that-cannot-be-edited-in-the-admin). Cette option verrouille la valeur de configuration afin qu’elle ne puisse pas être modifiée dans l’administrateur ou empêche la modification d’un paramètre déjà verrouillé. Lorsque vous utilisez cette option, les modifications de configuration sont écrites dans la variable `<Commerce base dir>/app/etc/env.php` fichier .
- Configurez et exécutez le [Outil d’analyse de sécurité Adobe Commerce](https://docs.magento.com/user-guide/magento/security-scan.html).
L’analyse de sécurité améliorée vous permet de surveiller chacun de vos sites Adobe Commerce, y compris PWA, les risques de sécurité connus et les logiciels malveillants, ainsi que de recevoir des mises à jour de correctifs et des notifications de sécurité.
- [Vérification et mise à jour de l’accès des utilisateurs administrateurs](https://docs.magento.com/user-guide/system/permissions-users-all.html) et [paramètres de sécurité](https://docs.magento.com/user-guide/stores/security-admin.html).
   - Nous vous recommandons de supprimer tout compte obsolète, inutilisé ou suspect et de faire pivoter les mots de passe pour tous les utilisateurs administrateurs.
   - Vérifiez et mettez à jour les paramètres de sécurité avancés&lt; pour votre projet. La configuration de la sécurité d’administration vous permet d’ajouter une clé secrète aux URL, de demander que les mots de passe soient sensibles à la casse et de limiter la durée des sessions d’administration, y compris la durée de vie des mots de passe, ainsi que le nombre de tentatives de connexion pouvant être effectuées avant le verrouillage du compte utilisateur d’administrateur. Pour une sécurité accrue, vous pouvez configurer la durée d’inactivité du clavier avant l’expiration de la session en cours et exiger que le nom d’utilisateur et le mot de passe soient sensibles à la casse.
- Audit Adobe Commerce sur [utilisateurs de projet cloud](https://devdocs.magento.com/cloud/project/user-admin.html).
Nous vous recommandons de supprimer tout compte obsolète, inutilisé ou suspect et de demander aux utilisateurs de modifier leurs mots de passe.
- Audit [Clés SSH](https://devdocs.magento.com/cloud/before/before-workspace-ssh.html) pour Adobe Commerce sur l’infrastructure cloud.
Nous vous recommandons de passer en revue, supprimer et faire pivoter les clés SSH.
- Mettez en oeuvre la liste de contrôle d’accès (ACL) pour l’administrateur.
Vous pouvez utiliser une liste de listes de contrôle d’accès Fastly Edge conjointement à une liste personnalisée. [Fragment de code VCL](https://devdocs.magento.com/cloud/cdn/fastly-vcl-allowlist.html#vcl) pour filtrer les requêtes entrantes et autoriser l’accès par adresse IP à l’administrateur.

## Analyse d’un incident

La première étape de l&#39;analyse des incidents est de rassembler autant de faits que possible, aussi vite que possible. La collecte d’informations sur l’incident peut vous aider à déterminer la cause potentielle de l’incident. Adobe Commerce fournit les outils ci-dessous pour faciliter votre analyse des incidents.

- [Journaux des actions de l’administrateur d’audit](https://docs.magento.com/user-guide/system/action-log-report.html).
Le rapport Journaux d’actions affiche un enregistrement détaillé de toutes les actions d’administration activées pour la journalisation. Chaque enregistrement est horodaté et enregistre l’adresse IP et le nom de l’utilisateur. Le détail du journal comprend les données utilisateur de l’administrateur et les modifications associées qui ont été apportées pendant l’action.
- Analysez les événements à l’aide de la méthode [Observation pour l’outil Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=en).
L’outil Observation pour Adobe Commerce vous permet d’analyser des problèmes complexes afin d’identifier les causes profondes. Au lieu de suivre des données disparates, vous pouvez passer votre temps à mettre en corrélation des événements et des erreurs afin d’obtenir des informations plus approfondies sur les causes des goulets d’étranglement en termes de performances.
L’outil est conçu pour vous donner une vue d’ensemble claire de certains problèmes potentiels liés au site, afin de vous aider à identifier la cause première et à optimiser les performances des sites. Cliquez sur le lien vers la documentation de l’outil Observation pour Adobe Commerce ci-dessus pour accéder à la documentation de l’outil. Il existe une section dans la documentation qui détaille toutes les informations qui se trouvent sur le **Sécurité** .
- Analyse des journaux avec [Nouveaux journaux de recomposition](https://devdocs.magento.com/cloud/project/new-relic.html#new-relic-logs). Les projets Adobe Commerce sur l’infrastructure cloud Pro incluent [Nouveaux journaux de recomposition](https://docs.newrelic.com/docs/logs/new-relic-logs/get-started/introduction-new-relic-logs) service. Le service est préconfiguré pour agréger toutes les données de journal de vos environnements d’évaluation et de production afin de les afficher dans un tableau de bord de gestion des journaux centralisé.
Vous pouvez utiliser le service New Relic Logs pour effectuer les tâches suivantes :
   - Utilisation [Nouvelles requêtes relatives](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) pour rechercher des données de journal agrégées.
   - Visualisez les données de journal à l’aide de l’application New Relic Logs (Nouveaux journaux de redirection).

## Informations supplémentaires

- [Structure de l’analyse de la cause racine](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
