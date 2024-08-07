---
title: Présentation des stratégies de sécurité du contenu
description: Découvrez comment améliorer la posture de sécurité de votre magasin Adobe Commerce à l’aide d’une stratégie de sécurité du contenu.
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# Présentation des stratégies de sécurité du contenu

Une stratégie de sécurité du contenu (CSP) peut fournir des couches de défense supplémentaires pour les installations Adobe Commerce en contribuant à détecter et à atténuer les attaques par script intersite (XSS) et d’injection de données associées. Ce vecteur d&#39;attaque courant fonctionne en injectant du contenu malveillant qui prétend faussement provenir du site web. Une fois le contenu malveillant chargé et exécuté, il peut déclencher le transfert non autorisé de données.

La CSP fournit un ensemble normalisé de directives qui indique au navigateur quelles ressources de contenu peuvent être approuvées et lesquelles doivent être bloquées. En utilisant des stratégies soigneusement définies, la stratégie de sécurité du contenu peut limiter le contenu du navigateur afin de n’autoriser l’affichage que des ressources whitelistées.

## Configuration

Pour éviter toute interférence avec les opérations du site, la stratégie de sécurité du contenu peut être mise en oeuvre par phases. La CSP a deux modes de fonctionnement de base : `report-only mode` et `restrict mode`.

**Mode Rapport uniquement** : le navigateur est invité à signaler les violations de stratégie, mais à ne pas les appliquer. Chaque fois qu’une ressource demandée enfreint la CSP, le navigateur consigne les erreurs résultantes dans la console. Le journal de la console peut ensuite être utilisé pour enquêter sur la cause de chaque violation.

Il est important de passer en revue toutes les erreurs CSP au fur et à mesure qu’elles se produisent et d’affiner les stratégies jusqu’à ce que toutes les ressources nécessaires soient mises en whiteliste. Il est sans risque de basculer vers `restrict mode` lorsqu’aucune autre erreur ne se produit. Sinon, une CSP mal configurée peut entraîner l’affichage d’une page vierge contenant de nombreuses erreurs de console. Une CSP correctement configurée permet la diffusion de contenu whitelisté sans aucun impact perçu sur les performances.

**Restrict mode** : le navigateur est chargé d’appliquer toutes les stratégies de contenu et de limiter la publication aux ressources whitelistées.

La première phase de la mise en oeuvre de la CSP Adobe Commerce a été introduite dans Adobe Commerce 2.3.5 et a rendu la CSP disponible dans `report-only mode` par défaut.  Dans Adobe Commerce 2.4.7 et versions ultérieures, la CSP est configurée dans `restrict-mode` par défaut pour les pages de paiement dans les zones de storefront et d’administration, et en mode `report-only` pour toutes les autres pages. L’en-tête CSP correspondant ne contient pas le mot-clé `unsafe-inline` dans la directive `script-src` pour les pages de paiement. En outre, seuls les scripts intégrés placés sur liste blanche sont autorisés.

Étant donné que la stratégie de sécurité du contenu (CSP) est configurée à partir du serveur plutôt que de l’administrateur, la plupart des marchands ont besoin de l’aide d’un intégrateur système ou d’un développeur pour la configurer correctement. Voir [Stratégies de sécurité du contenu](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) dans le _Guide du développeur PHP de Commerce_.


## Reporting

Par défaut, la CSP envoie les erreurs à la console du navigateur, mais elle peut être configurée pour collecter les journaux d’erreurs par requête HTTP. En outre, il existe plusieurs services tiers que vous pouvez utiliser pour surveiller, collecter et signaler les violations CSP. Les violations CSP peuvent être signalées à un point de terminaison pour la collecte en ajoutant l’URI à partir de l’administrateur ou du fichier `config.xml` pour un module personnalisé.  Voir [Configuration de l’URI de rapport](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#report-uri-configuration) dans le _Guide du développeur des extensions PHP de Commerce_.

[Report URI](https://report-uri.io/) est un service qui surveille les violations CSP et affiche les résultats dans un tableau de bord. Les commerçants et les développeurs peuvent utiliser le service pour recevoir des rapports chaque fois que des violations CSP se produisent.
