---
title: Présentation de la politique de sécurité du contenu
description: Découvrez comment améliorer la posture de sécurité de votre Adobe Commerce ou de votre Magento Open Source à l’aide d’une politique de sécurité de contenu.
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: 8bb692518536f5e7403ed308328e6532c020a230
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# Présentation de la politique de sécurité du contenu

Une politique de sécurité du contenu (CSP) peut fournir des niveaux de défense supplémentaires pour les installations d’Adobe Commerce et de Magento Open Source en contribuant à détecter et à atténuer les attaques XSS (Cross-Site Scripting) et les attaques par injection de données associées. Ce vecteur d&#39;attaque courant fonctionne en injectant du contenu malveillant qui prétend faussement provenir du site Web. Une fois le contenu malveillant chargé et exécuté, il peut lancer le transfert non autorisé de données.

La CSP fournit un ensemble normalisé de directives qui indique au navigateur quelles ressources de contenu peuvent être approuvées et lesquelles doivent être bloquées. À l’aide de politiques soigneusement définies, la CSP peut restreindre le contenu du navigateur afin de n’autoriser l’affichage que des ressources whitelistées.

## Configuration

Pour éviter d’interférer avec les opérations du site, la CSP peut être mise en œuvre par phases. CSP propose deux modes de fonctionnement de base : `report-only mode` et `restrict mode`.

**Mode Rapport uniquement**: le navigateur reçoit pour instruction de signaler les violations de politique, mais de ne pas les appliquer. Chaque fois qu’une ressource demandée enfreint la CSP, le navigateur consigne les erreurs résultantes dans la console. Le journal de la console peut ensuite être utilisé pour rechercher la cause de chaque violation.

Il est important d’examiner toutes les erreurs CSP au fur et à mesure qu’elles se produisent et d’affiner les politiques jusqu’à ce que toutes les ressources nécessaires soient whitelistées. Vous pouvez passer en toute sécurité à `restrict mode` lorsqu’aucune autre erreur ne se produit. Dans le cas contraire, une CSP mal configurée peut entraîner l’affichage d’une page vierge dans le navigateur, avec de nombreuses erreurs de console. Une CSP correctement configurée permet de placer le contenu sur la liste autorisée sans aucun impact sur les performances.

**Mode de restriction**: le navigateur a pour instruction d’appliquer toutes les politiques de contenu et de limiter la publication aux ressources whitelistées.

La première phase de la mise en œuvre de la CSP d’Adobe Commerce a été introduite dans Adobe Commerce 2.3.5 et a rendu la CSP disponible dans `report-only mode` par défaut.  Dans Adobe Commerce 2.4.7 et les versions ultérieures, CSP est configuré dans `restrict-mode` par défaut pour les pages de paiement dans les zones storefront et admin, et dans `report-only` pour toutes les autres pages. L’en-tête CSP correspondant ne contient pas le `unsafe-inline` mot-clé dans le `script-src` directive pour les pages de paiement. En outre, seuls les scripts intégrés placés sur la liste autorisée sont autorisés.

Comme la CSP est configurée à partir du serveur plutôt qu’à partir de l’administrateur, la plupart des commerçants ont besoin de l’aide d’un intégrateur système ou d’un développeur pour la configurer correctement. Voir [Politiques de sécurité du contenu](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) dans le _Guide du développeur PHP Commerce_.


## Rapports

Par défaut, la CSP envoie les erreurs à la console du navigateur, mais peut être configurée pour collecter les journaux d’erreurs par requête HTTP. En outre, il existe plusieurs services tiers que vous pouvez utiliser pour surveiller, collecter et signaler les violations de CSP. Les violations de CSP peuvent être signalées à un point d’entrée pour la collecte en ajoutant l’URI à partir de l’administration ou de l’interface utilisateur `config.xml` pour un module personnalisé.  Voir [Configuration de l’URI du rapport](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#report-uri-configuration) dans le _Guide du développeur des extensions PHP Commerce_.

[URI du rapport](https://report-uri.io/) est un service qui surveille les violations de la CSP et affiche les résultats dans un tableau de bord. Les commerçants et les développeurs peuvent utiliser le service pour recevoir des rapports chaque fois que des violations de CSP se produisent.
