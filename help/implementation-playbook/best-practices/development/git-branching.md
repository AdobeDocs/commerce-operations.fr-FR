---
title: Bonnes pratiques relatives à l'embranchement Git
description: Découvrez les différentes stratégies d’embranchement pour la gestion du code source.
feature: Best Practices
role: Developer
exl-id: 7d7736e8-7023-4315-9965-71866b0be5c3
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Bonnes pratiques relatives à l&#39;embranchement Git

Le code Source passe par plusieurs phases de stabilité lors du processus de développement :

- Développement actif
- Intégration initiale du code
- Intégration de code pour l’assurance qualité (AQ)
- Intégration de code pour les tests d’acceptation utilisateur final (UAT)
- Intégration du code final pour les versions de production

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Gestion des branches

Chaque phase de développement doit avoir une branche correspondante dans Git pour suivre les modifications du code et faciliter le processus de déploiement :

- **Branche de tâche** : emplacement où les développeurs valident leurs modifications de code individuelles lors de l’implémentation de tâches spécifiques, comme des fonctionnalités et des correctifs de bogues.
- **Branche de développement** : emplacement où plusieurs développeurs fusionnent les modifications de leurs branches de tâches individuelles en une seule branche de développement pour le test d’intégration automatisé. Cette branche est déployée dans un environnement de développement.
- **Branche AQ** : emplacement où les développeurs fusionnent les modifications une fois le développement terminé et où le code a transmis tous les tests d’intégration automatisés et la révision du code. Cette branche est déployée dans l’environnement d’assurance qualité pour les tests d’assurance qualité manuels.
- **Branche Stable/UAT** : emplacement de la fusion du code une fois qu’il a réussi les tests d’assurance qualité manuels. Cette branche est déployée dans un environnement UAT pour les tests d’acceptation utilisateur.
- **Branche de production/publication** : emplacement de la fusion du code après sa transmission de l’UAT. Cette branche est déployée en production pour une version.

>[!TIP]
>
>Adobe Commerce sur les projets d’infrastructure cloud contient des branches spécifiques qui correspondent à différents environnements. Voir les [workflows de projet Pro](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=fr) et [workflow de projet de démarrage](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-develop-deploy-workflow.html?lang=fr) dans le _Guide Cloud_.

## Stratégies de branche

Vous pouvez utiliser plusieurs stratégies d’embranchement. Choisissez une stratégie qui fonctionne le mieux pour votre équipe de développement et la complexité de votre projet.

Pour plus d’informations, voir les ressources externes suivantes :

- [Workflows d&#39;embranchement](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)
- [Workflows distribués](https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows)
- [Modèles de gestion des branches de code source](https://martinfowler.com/articles/branching-patterns.html)
- [Un modèle d&#39;embranchement Git réussi](https://nvie.com/posts/a-successful-git-branching-model/)
- [Flux GitHub](https://docs.github.com/en/get-started/quickstart/github-flow)
- [Flux GitLab](https://about.gitlab.com/blog/2023/07/27/gitlab-flow-duo/)
