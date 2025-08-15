---
title: Bonnes pratiques en matière d’embranchement Git
description: Découvrez les différentes stratégies d’embranchement pour la gestion du code source.
feature: Best Practices
role: Developer
exl-id: 7d7736e8-7023-4315-9965-71866b0be5c3
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Bonnes pratiques en matière d’embranchement Git

Le code Source passe par plusieurs phases de stabilité au cours du processus de développement :

- Développement actif
- Intégration de code initiale
- Intégration du code pour l’assurance qualité (QA)
- Intégration de code pour le test d’acceptation par l’utilisateur final (UAT)
- Intégration de code finale pour les versions de production

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce on-premise

## Gestion des succursales

Chaque phase de développement doit comporter une branche correspondante dans Git pour suivre les modifications de code et faciliter le processus de déploiement :

- **Branche de tâche** : où les développeurs valident leurs modifications de code individuelles lors de l’implémentation de tâches spécifiques, telles que des fonctionnalités et des correctifs de bugs.
- **Branche de développement** : plusieurs développeurs fusionnent les modifications de leurs branches de tâches individuelles en une seule branche de développement pour les tests d’intégration automatisés. Cette branche est déployée dans un environnement de développement.
- **Branche QA** : où les développeurs fusionnent les modifications une fois le développement terminé et le code terminé avec succès tous les tests d’intégration automatisés et la révision du code. Cette branche est déployée dans l’environnement d’assurance qualité pour les tests d’assurance qualité manuels.
- **Branche stable/UAT**—Où le code est fusionné après avoir passé le test d’assurance qualité manuel. Cette branche est déployée dans un environnement UAT pour les tests d’acceptation des utilisateurs.
- **Branche de production/publication** : emplacement où le code est fusionné après avoir passé l’UAT. Cette branche est déployée en production pour une version.

>[!TIP]
>
>Les projets d’infrastructure cloud d’Adobe Commerce contiennent des branches spécifiques qui correspondent à différents environnements. Reportez-vous aux sections [Workflow de projet Pro](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html) et [Workflow de projet Starter](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-develop-deploy-workflow.html) du _Guide cloud_.

## Stratégies des branches

Vous pouvez utiliser plusieurs stratégies d’embranchement. Choisissez la stratégie qui convient le mieux à votre équipe de développement et à la complexité de votre projet.

Pour plus d’informations, consultez les ressources externes suivantes :

- [Workflows d’embranchement](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)
- [Workflows distribués](https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows)
- [Modèles de gestion des branches de code source](https://martinfowler.com/articles/branching-patterns.html)
- [Un modèle d’embranchement Git réussi](https://nvie.com/posts/a-successful-git-branching-model/)
- [Flux GitHub](https://docs.github.com/en/get-started/quickstart/github-flow)
- [Flux GitLab](https://about.gitlab.com/blog/2023/07/27/gitlab-flow-duo/)
