---
title: Bonnes pratiques générales de développement
description: Découvrez les bonnes pratiques générales pour le développement de projets Adobe Commerce.
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 0%

---


# Bonnes pratiques générales de développement pour Adobe Commerce

Cette rubrique décrit la ligne de base d’un processus de développement Adobe Commerce sain. Il décrit les processus fondamentaux, les principes de codage et les principes de conception d’application pour guider les développeurs.

>[!NOTE]
>
>Les architectes techniques d’Adobe utilisent ces bonnes pratiques comme référence lors d’engagements impliquant le développement.

Ces bonnes pratiques ont été développées sur la base d’années d’expérience dans le développement et la diffusion de projets Commerce. Adobe recommande que les initiatives techniques suivent ces bonnes pratiques et que vous amélioriez les processus et le code existants pour vous aligner sur ces bonnes pratiques.

## Conventions de texte

Les mots-clés &quot;DOIT&quot;, &quot;NE DOIT PAS&quot;, &quot;OBLIGATOIRE&quot;, &quot;DOIT&quot;, &quot;NE DOIT PAS&quot;, &quot;NE DOIT PAS&quot;, &quot;RECOMMANDÉ&quot;, &quot;PEUT&quot; et &quot;FACULTATIF&quot; dans cette rubrique doivent être interprétés comme décrit dans la section [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119).

## Processus

1. Une méthodologie de projet définie DOIT être convenue avant de commencer les activités du projet. Il peut s’agir de Scrum, de Cascade ou de toute autre méthodologie ou combinaison de méthodologies, à condition qu’elle soit définie.
1. Le développement NE DOIT PAS commencer tant qu’une stratégie d’embranchement pour le système de contrôle de version n’est pas disponible pour l’équipe de développement.
1. Le développement NE DOIT PAS démarrer tant qu’après l’approbation des spécifications techniques, l’approbation des articles d’utilisateurs et des cas d’utilisation et l’approbation des cas de test ne sont pas disponibles pour l’équipe de développement.
1. Développement NE DOIT PAS démarrer tant qu’au moins un environnement de développement et d’assurance qualité n’est pas disponible.
1. Les exigences spécifiques au projet qui sont obligatoires pour que le développement démarre PEUVENT être documentées dans un _Définition des éléments prêts_.
1. L’approbation doit être effectuée par un représentant client autorisé à valider les éléments livrables du projet.
1. Dans les méthodologies de projet agiles, des exigences supplémentaires PEUVENT suivre l’approbation. Ces exigences doivent être traitées comme de nouvelles exigences et doivent être capturées, architecturées et planifiées en conséquence.
1. Tout développement DOIT être testé fonctionnellement par le développeur avant envoi.
1. Tout développement DOIT réussir les tests automatisés avant d’être envoyé pour révision du code. Il PEUT être configuré en tant que processus automatisé à la suite de la création d’une requête de tirage.
1. Tout développement DOIT transmettre une révision manuelle du code par un architecte technique ou un développeur principal avant de l’envoyer pour l’assurance qualité.
1. Tout développement DOIT transmettre l’assurance qualité avant la diffusion au client.
1. Les exigences spécifiques au projet qui sont obligatoires pour la diffusion PEUVENT être documentées dans une &quot;Définition du Terminé&quot;.

## Environnement

1. Tous les développeurs doivent utiliser le même IDE. PhpStorm est l’IDE recommandé pour le développement d’Adobe Commerce.
1. Tous les développeurs doivent développer et tester à l’aide de la même pile technologique que celle utilisée sur les (futurs) serveurs de production. Les versions du logiciel de cette pile technologique DOIVENT correspondre aux versions majeures et mineures du logiciel installé sur les serveurs de production. Voir [configuration requise](../../../installation/system-requirements.md) pour plus d’informations sur la pile de technologies standard pour Adobe Commerce.
1. L’administrateur système ou l’architecte technique PEUT fournir à l’équipe un environnement de développement local géré de manière centralisée pour assurer et promouvoir des environnements locaux égaux et à jour.
1. Les développeurs et les ingénieurs QA DOIVENT avoir accès à la ligne de commande, à la base de données et aux fichiers journaux de l’environnement d’assurance qualité. Cela PEUT nécessiter une connexion VPN.

## Normes de codage

1. Tout code DOIT respecter les conventions en matière d’architecture, de méthodologie et de normes de codage. La créativité est désirée en fonction, pas en forme.
1. Tout le code doit être conforme à la variable [Guide de l’architecture d’Adobe Commerce](https://developer.adobe.com/commerce/php/architecture/){target="_blank}.
1. Tout le code DOIT respecter les [Normes de codage Adobe Commerce](https://developer.adobe.com/commerce/php/coding-standards/).
1. Tout le code DOIT respecter les [Instructions techniques pour Adobe Commerce](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).
1. L’ensemble du code DOIT implémenter la variable [Bonnes pratiques d’Adobe Commerce](../phases.md), le cas échéant.
1. Tout le code DOIT respecter les [Normes du groupe d’interopérabilité du framework PHP (FIG)](https://www.php-fig.org/).
1. Dans la mesure du possible, il est RECOMMANDÉ de prendre [Visions techniques d’Adobe Commerce](https://developer.adobe.com/commerce/php/architecture/technical-vision/) en compte.
1. Toutes les intégrations avec des systèmes externes DOIVENT comporter des tests d’intégration qui valident le processus d’entreprise.
1. Tous les modules DOIVENT avoir une couverture de test. Les éléments à tester doivent être déterminés par l’équipe de développement en collaboration avec l’architecte technique ou le développeur principal. Cette détermination doit être fondée sur des mesures qualitatives et non sur des mesures quantitatives : un pourcentage élevé de couverture du code n’est pas un indicateur de succès et n’implique pas une qualité de code élevée. Déterminez plutôt le risque de ne pas couvrir une partie du code en évaluant la probabilité et la gravité des régressions dans cette partie du programme.

## Contrôle de version

Les versions du module DOIVENT respecter les [Version sémantique 2.0.0 standard](https://semver.org/).
Les dépendances du code base Adobe Commerce DOIVENT suivre la variable [Directives relatives aux dépendances des versions de module](https://developer.adobe.com/commerce/php/development/versioning/dependencies/).

## CONTRÔLE DE RÉVISION

Les validations DOIVENT être accompagnées de messages de validation significatifs.

## Sécurité

1. [Fonctions non sécurisées](https://developer.adobe.com/commerce/php/development/security/non-secure-functions/) NE DOIT PAS être utilisé.
1. [Stratégies de prévention XSS](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/) DOIT être appliqué.
1. [Stratégies de sécurité du contenu](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) DOIT être appliqué.
1. Les nouvelles instances Adobe Commerce DOIVENT être diffusées sur la dernière version de sécurité d’une version qui n’a pas encore atteint la date &quot;Fin des correctifs de sécurité&quot;. Voir [Stratégie de cycle de vie des logiciels Adobe Commerce](../../../release/lifecycle-policy.md).
