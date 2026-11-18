---
title: Présentation du processus de mise à niveau
description: Découvrez comment la mise à niveau de votre projet Adobe Commerce garantit la sécurité et l’efficacité de votre storefront. Découvrez les bonnes pratiques de planification et d’exécution de mises à niveau réussies.
exl-id: 40bd97ca-6648-40d4-9c61-7d159391976a
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 16e16980e1b3b021aaaa8c3f1265162f87d5c951
workflow-type: tm+mt
source-wordcount: '942'
ht-degree: 2%
---
# Présentation du processus de mise à niveau

La mise à niveau de votre projet Adobe Commerce est essentielle pour garantir que votre boutique reste sécurisée, compatible PCI et fonctionne à un rendement optimal. Ce guide détaille les points clés à prendre en compte lors de la préparation d’une mise à niveau.

Ce guide présente un aperçu du parcours de mise à niveau d’Adobe Commerce type et des bonnes pratiques à suivre le long de ce parcours. Il décrit également les détails techniques du processus de mise à niveau avec un exemple opportun et des instructions détaillées pour effectuer la mise à niveau vers la dernière version d’Adobe Commerce. Il est important de consulter le planning des versions d’Adobe Commerce [1](../release/schedule.md) et de commencer à préparer les mises à niveau dès que possible. Adobe publie chaque année le calendrier des versions afin de faciliter le processus de planification des commerçants. Il recommande également de mettre à niveau chaque cycle de publication des correctifs. Pour rester conformes à la norme PCI, les commerçants doivent utiliser le dernier correctif ou le dernier correctif de sécurité.

## À qui s&#39;adresse ce guide ?

Le public cible de ce guide comprend :

- **Responsables et directeurs techniques d’e-commerce**—Découvrez le parcours de mise à niveau, l’importance d’une mise à niveau régulière et la meilleure façon de planifier et de préparer une mise à niveau.
- **Équipes d’exploitation et de développement** : découvrez les étapes techniques requises pour effectuer une mise à niveau vers la dernière version d’Adobe Commerce et les outils disponibles qui rendent le processus plus facile, plus rapide et plus abordable.

## Explication du processus de mise à niveau

L’une des raisons pour lesquelles vous avez choisi Adobe Commerce est probablement :

- Large ensemble de fonctionnalités standard
- Fonctionnalités SaaS proposées séparément du code principal
- Offre robuste d’extensions Marketplace
- Une capacité unique pour permettre une flexibilité infinie afin que vous puissiez personnaliser votre site pour mieux répondre aux besoins de votre entreprise et de vos clients

Toutefois, l’avantage d’être un produit hautement extensible et personnalisable peut entraîner des problèmes de mise à niveau potentiels lorsque les personnalisations ne sont pas codées selon les bonnes pratiques, ce qui entraîne des coûts de mise à niveau plus élevés que prévu.

_Alors... pourquoi effectuer une mise à niveau ?_

La mise à niveau permet à votre entreprise de rester agile dans un secteur du commerce électronique en constante évolution et permet à votre plateforme d’être compatible avec les dernières fonctionnalités d’Adobe Commerce qui vous aident à maximiser les ventes et les conversions. Il est essentiel d’inclure des mises à niveau dans vos plans de maintenance réguliers pour vous assurer que votre magasin reste sécurisé, compatible PCI et fonctionne à un rendement optimal.

### Sécurité

La sécurité est l’une des principales raisons de la mise à niveau, car 83 % des incidents de sécurité se produisent sur des logiciels obsolètes. Selon [IBM](https://www.ibm.com/reports/data-breach), le coût moyen d&#39;une violation de données s&#39;élève à 3,86 millions de dollars, soit bien plus que ce qu&#39;il en coûte pour atténuer ce risque par la mise à niveau. Adobe propose deux méthodes pour assurer la sécurité de votre boutique tout au long de l’année :

- **Versions des correctifs**—Incluez la sécurité, les performances, la qualité et des correctifs de priorité élevée.
- **[Versions des correctifs de sécurité](implementation/perform-upgrade.md#example---security-patch)**—Incluez des correctifs et des améliorations qui contribuent à assurer la sécurité de votre site.

Si vous utilisez Adobe Commerce sur Cloud versions 2.4.4 à 2.4.9, consultez l’[Avis de sécurité et de conformité](../release/security-enforcement-policy.md) pour connaître les actions requises et les échéances afin de garantir la sécurité et la conformité de votre environnement.

### Performances

Les performances sont une autre raison majeure de mettre à niveau. Selon [HubSpot](https://blog.hubspot.com/marketing/page-load-time-conversion-rates), les cinq premières secondes de temps de charge ont un effet significatif sur les taux de conversion et chaque seconde de latence par la suite a un impact de -4,4 %. Cela, associé au fait que la vitesse de page est un facteur de classement SEO majeur, démontre pourquoi les performances du site sont un élément essentiel de votre site à maintenir et à améliorer régulièrement. Chaque version de correctif comprend des améliorations des performances. Tirer parti des nouvelles versions permet donc de soutenir vos plans de croissance et de maintenir la compétitivité de votre entreprise.

### Coût du retard

Le report des mises à niveau de la plateforme se résume souvent à un coût immédiat. Cependant, le coût réel de l&#39;exécution d&#39;une version obsolète d&#39;un logiciel est beaucoup plus élevé et peut avoir un impact durable sur une entreprise.

Cela peut sembler contre-intuitif, mais effectuer des mises à jour régulières de la plateforme nécessite moins d’effort global que d’effectuer des mises à jour peu fréquentes en raison de la quantité de dette technique accumulée résultant du retard. Adobe a récemment travaillé avec un partenaire qui a un détaillant qui effectuait des mises à niveau peu fréquemment et de manière incohérente (chaque année ou plus). En transformant son approche de mise à niveau et en suivant un chemin de mise à niveau régulier recommandé par Adobe pendant 12 mois, le partenaire a économisé au client quatre semaines de temps de développement, d’efforts et de coûts, ce qui lui a permis de rediriger ces coûts vers d’autres initiatives stratégiques.

Lorsque des mises à jour sont effectuées régulièrement, les modifications sont incrémentielles, comme le reflète l’effort de mise à niveau correspondant. Lorsque les mises à jour de la plateforme sont différées pendant une période prolongée, elles peuvent devenir un processus beaucoup plus impliqué. En outre, les extensions que vous utilisez à partir de la [place de marché Adobe Commerce](https://commercemarketplace.adobe.com//) et d’autres intégrations tierces peuvent également être affectées. Enfin, le temps nécessaire à l’examen, à la planification et à l’exécution d’une mise à niveau différée est plus long, ce qui ajoute des efforts et des coûts évitables.

Voici quelques-uns des facteurs généraux qui affectent le niveau d’effort nécessaire à la mise à niveau de votre projet :

| Complexité technique | Planification et stratégie |
|-----------------------------------------------------------|--------------------------------------------------------------|
| Étendue des personnalisations | Clarté des exigences, décisions indécises et dérive de la portée |
| Nombre d’extensions | Votre fréquence de mise à niveau |
| Nombre d’intégrations avec des tiers (OMS, ERP) | Votre stratégie de test |
| Codage selon les bonnes pratiques |                                                              |

La croissance continue de l&#39;espace du commerce numérique a exercé une pression accrue sur les entreprises pour qu&#39;elles évoluent plus rapidement, plus souvent et de manière imprévisible. Le fait de ne pas suivre et d&#39;anticiper le comportement d&#39;achat des clients a nivelé le terrain de jeu, même pour les plus grandes marques les plus établies. Vous devez être en mesure de fournir des expériences solides et personnalisées sur tous les points de contact, sans interruption de performances et de disponibilité. Vous devez être en mesure d&#39;innover plus rapidement, sans limites, pour devancer vos concurrents mondiaux. En effectuant la mise à niveau, vous préparez votre entreprise aux besoins futurs et vous vous préparez à mieux répondre aux besoins dynamiques des clients.
