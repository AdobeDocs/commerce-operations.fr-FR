---
title: Bonnes pratiques relatives à la liste de contrôle de mise à niveau
description: Découvrez comment créer et utiliser une liste de contrôle de mise à niveau pour planifier votre stratégie de mise à niveau d’Adobe Commerce.
role: Leader
feature: Best Practices
exl-id: c9b644fa-290c-4f33-b5a7-19f7122ff08e
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# Bonnes pratiques relatives à la liste de contrôle de mise à niveau

Utilisez cette liste de contrôle lors de vos conversations annuelles et trimestrielles avec votre équipe eCommerce. De nombreuses entreprises travaillent à partir de budgets annuels et de feuilles de route. Il est impératif, lors de ces discussions annuelles, que vous parliez de la santé, de la direction et de la stratégie de mise à niveau de votre plateforme pour l&#39;année, ainsi que de la manière dont elle s&#39;inscrit dans les objectifs généraux et les IPC de l&#39;entreprise. Lors des conversations trimestrielles, assurez-vous que le plan annuel que vous avez créé est toujours aligné sur votre situation actuelle ou votre pivot dans le cas contraire. L’objectif de cette liste de contrôle du plan de mise à niveau est de vous aider à planifier et planifier les mises à niveau d’Adobe Commerce pour garantir le succès de la mise à niveau au cours de l’année. Cette liste de contrôle doit être utilisée par les audiences suivantes pour la planification annuelle et l’examen trimestriel :

- Director / Manager IT
- eCommerce Manager
- Partenaire/consultant en solutions

>[!NOTE]
>
>Pour une description détaillée des étapes techniques de mise à niveau réussie, reportez-vous à la section [Conditions préalables à la mise à niveau complètes](../../../upgrade/prepare/prerequisites.md) dans notre documentation utilisateur.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Objectifs

▢ Examinez les indicateurs de performance clés actuels et ajustez-les si nécessaire.

## Extensions et personnalisations

▢ Vérifiez toutes les extensions et personnalisations actuelles et assurez-vous qu’elles sont toujours nécessaires en fonction des besoins de l’entreprise.

▢ Envisagez de remplacer les extensions qui n’ont pas un bon historique de mise à jour des versions d’Adobe Commerce.

## Équipe

▢ Assurez-vous d’avoir la bonne équipe en place avec les certifications et les ensembles de compétences Adobe Commerce appropriés.

## Budget et minutage

▢ Utilisez le [calendrier de publication](../../../release/schedule.md) d’Adobe Commerce pour planifier votre prochaine mise à niveau et préparer l’avance.

▢ Déterminez quelle version vous pensez adopter (complète ou sécuritaire uniquement) en fonction des besoins anticipés.

▢ Conserver un budget et une capacité d’équipe pour l’upgrade.

## Intégrations tierces

▢ Passez en revue les intégrations tierces Adobe Commerce actuelles et leurs fenêtres de maintenance pour l’année en cours et envisagez d’aligner les travaux de mise à niveau sur votre calendrier de maintenance.

## Portée et planification du déploiement

▢ Activités d’accès anticipé

- Le partenaire participe à [Beta](../../../release/beta.md)
- Examen des notes de mise à jour de Beta.

▢ Convenir du budget, du calendrier, de la portée.

▢ Exécutez l’ [outil de compatibilité de mise à niveau](../../../upgrade/upgrade-compatibility-tool/overview.md)

▢ Envisagez d’utiliser la mise à niveau pour résoudre les problèmes identifiés par l’ [outil d’analyse à l’échelle du site](../../../tools/site-wide-analysis-tool/intro.md).

▢ Dépendances des documents et toute modification technique de la pile requise, comme les versions PHP ou Elastic Search.

▢ Rassemblez l’équipe du projet avec les certifications Adobe Commerce.

▢ Créez un plan de communication avec les parties prenantes.

▢ Planifiez la période de maintenance si des temps d’arrêt sont prévus.

▢ Examinez et approuvez la stratégie de test ; envisagez d’utiliser le [framework de test](https://developer.adobe.com/commerce/testing/) d’Adobe Commerce ou une suite d’automatisation tierce.

▢ Vérifiez que toutes les extensions et personnalisations sont compatibles.

▢ Consultez et mettez à jour le manuel de lecture après le lancement ; à utiliser en cas de problèmes détectés pendant ou après la mise à niveau.

## Déploiement de Post

▢ Surveillez le site pour tout problème : performances, traitement des commandes, analyses, etc.

▢ Effectuez une analyse de sécurité Adobe Commerce [1} ou autre analyse tierce et examinez les vulnérabilités de sécurité potentielles.](https://account.magento.com/scanner/dashboard/)

▢ Effectuez une rétrospective avec toutes les parties prenantes et documentez ce qui s’est bien passé, ce qui ne s’est pas passé et comment s’améliorer.

▢ Modifiez votre plan pour la prochaine mise à niveau avec les leçons à tirer.
