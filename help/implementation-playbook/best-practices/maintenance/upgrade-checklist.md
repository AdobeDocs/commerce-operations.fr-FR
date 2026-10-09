---
title: Bonnes pratiques relatives à la liste de contrôle de mise à niveau
description: Découvrez comment créer et utiliser une liste de contrôle de mise à niveau pour planifier votre stratégie de mise à niveau Adobe Commerce.
role: Leader
feature: Best Practices
exl-id: c9b644fa-290c-4f33-b5a7-19f7122ff08e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%
---
# Bonnes pratiques relatives à la liste de contrôle de mise à niveau

Utilisez cette liste de contrôle lors de vos conversations annuelles et trimestrielles avec votre équipe eCommerce. De nombreuses entreprises travaillent à partir de budgets annuels et de feuilles de route. Au cours de ces discussions annuelles, il est impératif de parler de la stratégie de santé, d’orientation et de mise à niveau de votre plateforme pour l’année, ainsi que de sa compatibilité avec les objectifs généraux et les indicateurs de performance clés de l’entreprise. Au cours des conversations trimestrielles, assurez-vous que le plan annuel que vous avez créé est toujours aligné avec votre situation actuelle ou, dans le cas contraire, modifiez-le. L’objectif de cette liste de contrôle du plan de mise à niveau est de vous aider à planifier et à planifier les mises à niveau d’Adobe Commerce afin de garantir la réussite du processus de mise à niveau au cours de l’année. Cette liste de contrôle est destinée aux publics suivants pour la planification annuelle et l’examen trimestriel :

- Directeur/Responsable informatique
- Gestionnaire eCommerce
- Partenaire/consultant en solution

>[!NOTE]
>
>Pour une description détaillée des étapes techniques de mise à niveau réussie, reportez-vous à la section [Conditions préalables à la mise à niveau complète](../../../upgrade/prepare/prerequisites.md) de notre documentation utilisateur.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

## Objectifs

▢ Examinez les indicateurs de performance clés actuels et ajustez-les si nécessaire.

## Extensions et personnalisations

▢ Examinez toutes les extensions et personnalisations actuelles et assurez-vous qu’elles sont toujours nécessaires en fonction des besoins de l’entreprise.

▢ Envisagez de remplacer toutes les extensions qui n’ont pas une bonne réputation en matière de mise à jour avec les versions d’Adobe Commerce.

## Équipe

▢ Assurez-vous d’avoir la bonne équipe en place avec les certifications et les compétences Adobe Commerce appropriées.

## Budget et minutage

▢ Utilisez le [calendrier des versions](../../../release/schedule.md) d’Adobe Commerce pour planifier votre prochaine mise à niveau et vous préparer à l’avance.

▢ Discutez de la version que vous pensez adopter (complète ou de sécurité uniquement) en fonction des besoins prévus.

▢ Réservez un budget et une capacité d’équipe pour la mise à niveau.

## Intégrations tierces

▢ Passez en revue les intégrations tierces actuelles d’Adobe Commerce et leurs fenêtres de maintenance pour l’année en cours, et envisagez d’aligner le travail de mise à niveau sur votre calendrier de maintenance.

## Portée et planification du déploiement

▢ Activités en accès anticipé

- Le partenaire participe à [](../../../release/beta.md)
- Révision des notes de mise à jour de Beta.

▢ Convenir du budget, du calendrier et de la portée.

▢ exécuter l’outil de compatibilité de [mise à niveau](../../../upgrade/upgrade-compatibility-tool/overview.md)

▢ Envisagez d’utiliser la mise à niveau pour résoudre les problèmes identifiés par l’[outil d’analyse à l’échelle du site](../../../tools/site-wide-analysis-tool/intro.md).

▢ les dépendances de document et toutes les modifications de pile techniques requises, telles que les versions PHP ou Elastic Search.

▢ Rassemblez l’équipe de projet avec les certifications Adobe Commerce.

▢ Créer un plan de communication des parties prenantes.

▢ la fenêtre de maintenance du plan si un temps d’arrêt est prévu.

▢ Examinez et approuvez la stratégie de test. Envisagez d’utiliser la [structure de test](https://developer.adobe.com/commerce/testing/) d’Adobe Commerce ou une suite d’automatisation tierce.

▢ Vérifiez que toutes les extensions et personnalisations sont compatibles.

▢ examiner et mettre à jour le playbook de post-lancement ; à utiliser si des problèmes sont détectés pendant ou après la mise à niveau.

## Après le déploiement

▢ Surveillez les problèmes sur le site (performances, traitement des commandes, analyses, etc.).

▢ Effectuez une analyse de sécurité Adobe Commerce [analyse de sécurité](https://account.magento.com/scanner/dashboard/) ou d’autres analyses tierces et passez en revue les vulnérabilités de sécurité potentielles.

▢ Effectuez une rétrospective avec toutes les parties prenantes et documentez ce qui s’est bien passé et ce qui ne s’est pas passé, ainsi que les améliorations à apporter.

▢ Modifiez votre plan pour la prochaine mise à niveau avec les leçons apprises.
