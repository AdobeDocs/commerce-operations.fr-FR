---
title: Bonnes pratiques générales de développement
description: Découvrez les bonnes pratiques générales pour le développement de projets Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: 35de9849-2d19-4bb6-b920-9ce3838bc8bc
source-git-commit: 68dc4635df9fc411925fe0d48a578edece8895dc
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Bonnes pratiques générales de développement pour Adobe Commerce

Cette rubrique décrit les principes de base d’un processus de développement Adobe Commerce sain. Il décrit les processus fondamentaux, les principes de codage et les principes de conception d’applications pour guider les développeurs.

>[!NOTE]
>
>Les architectes techniques Adobe utilisent ces bonnes pratiques comme référence lors des missions de développement.

Ces bonnes pratiques ont été développées sur la base d’années d’expérience dans le développement et la diffusion de projets Commerce. Adobe recommande que les initiatives techniques respectent ces bonnes pratiques et que vous amélioriez les processus et le code existants pour les respecter.

## Conventions de texte

Les mots clés « MUST », « MUST NOT », « REQUIRED », « SHALL », « SHALL NOT », « SHOULD », « SHOULD NOT », « RECOMMENDED », « MAY » et « OPTIONAL » dans cette rubrique doivent être interprétés comme décrit dans la [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119).

## Processus

1. Une méthodologie de projet définie DOIT être convenue avant de commencer les activités du projet. Il PEUT s’agir de Scrum, Waterfall ou de toute autre méthodologie ou combinaison de méthodologies, à condition qu’elle soit définie.
1. Le développement NE DOIT PAS commencer tant qu’une stratégie d’embranchement pour le système de contrôle de version n’est pas disponible pour l’équipe de développement.
1. Le développement NE DOIT PAS commencer avant que l’approbation des spécifications techniques, l’approbation des histoires d’utilisateurs et des cas d’utilisation et l’approbation des cas de test ne soient disponibles pour l’équipe de développement.
1. Le développement NE DOIT PAS commencer tant qu’un environnement de développement et d’assurance qualité n’est pas disponible.
1. Les exigences spécifiques au projet qui sont obligatoires pour que le développement démarre PEUVENT être documentées dans une _Définition de prêt_.
1. L’approbation DOIT être effectuée par un représentant du client autorisé à approuver les livrables du projet.
1. Dans les méthodologies de projet Agile, des exigences supplémentaires PEUVENT suivre l’approbation. Ces exigences DEVRAIENT être traitées comme de nouvelles exigences et devraient être saisies, conçues et planifiées en conséquence.
1. Tous les développements DOIVENT être testés fonctionnellement par le développeur avant envoi.
1. Tous les développements DOIVENT passer avec succès les tests automatisés avant d’être soumis à la révision du code. Ceci PEUT être configuré en tant que processus automatisé suite à la création d’une demande de tirage.
1. Tous les développements DOIVENT passer la révision manuelle du code par un architecte technique ou un développeur en chef avant d&#39;être soumis pour l&#39;assurance qualité.
1. Tous les développements DOIVENT passer l&#39;assurance qualité avant la livraison au client.
1. Les exigences spécifiques au projet qui sont obligatoires pour la livraison PEUVENT être documentées dans une « Définition de Terminé ».

## Environnement

1. Tous les développeurs DOIVENT utiliser le même IDE. PhpStorm est l’IDE recommandé pour le développement Adobe Commerce.
1. Tous les développeurs DOIVENT développer et tester à l’aide de la même pile technologique que celle utilisée sur les (futurs) serveurs de production. Les versions du logiciel de cette pile technologique DOIVENT correspondre à la version majeure et mineure du logiciel installé sur les serveurs de production. Consultez [configuration requise](../../../installation/system-requirements.md) pour plus d’informations sur la pile technologique type d’Adobe Commerce.
1. L’administrateur système ou l’architecte technique PEUT fournir à l’équipe un environnement de développement local géré de manière centralisée afin d’assurer et de promouvoir des environnements locaux égaux et à jour.
1. Les développeurs et les ingénieurs et ingénieures en assurance qualité DOIVENT avoir accès à la ligne de commande, à la base de données et aux fichiers journaux de l’environnement d’assurance qualité. Ceci PEUT nécessiter une connexion VPN.

## Contrôle de version

Les versions des modules DOIVENT respecter la norme [Semantic Versioning 2.0.0](https://semver.org/).
Les dépendances de la base de code Adobe Commerce DOIVENT suivre les instructions [Dépendances de version du module](https://developer.adobe.com/commerce/php/development/versioning/dependencies/).

## CONTRÔLE DE RÉVISION

Les validations DOIVENT être accompagnées de messages de validation significatifs.

## Sécurité

1. [Fonctions non sécurisées](https://developer.adobe.com/commerce/php/development/security/non-secure-functions/) NE DOIVENT PAS être utilisées.
1. [Stratégies de prévention XSS](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/) DOIVENT être appliquées.
1. [Politiques de sécurité du contenu](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) DOIT être appliqué.
1. Les nouvelles instances d’Adobe Commerce DOIVENT être diffusées à la version de sécurité la plus récente d’une version qui n’a pas encore atteint la date de « Fin des correctifs de sécurité ». Voir [Politique relative au cycle de vie du logiciel Adobe Commerce](../../../release/lifecycle-policy.md).
