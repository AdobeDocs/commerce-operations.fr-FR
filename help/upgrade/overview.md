---
title: Présentation du processus de mise à niveau
description: Découvrez comment la mise à niveau de votre projet Adobe Commerce permet de garantir la sécurité de votre storefront et un fonctionnement efficace.
exl-id: 40bd97ca-6648-40d4-9c61-7d159391976a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 1%

---

# Présentation du processus de mise à niveau

La mise à niveau de votre projet Adobe Commerce est essentielle pour garantir la sécurité, la conformité PCI et le bon fonctionnement de votre magasin. Ce guide vous guide tout au long des points essentiels à prendre en compte lors de la préparation d’une mise à niveau.

Ce guide présente un aperçu du parcours de mise à niveau standard d’Adobe Commerce et les bonnes pratiques à suivre le long de ce parcours. Il décrit également les détails techniques du processus de mise à niveau avec un exemple opportun et des instructions détaillées pour la mise à niveau vers la dernière version d’Adobe Commerce. Il est important de passer en revue Adobe Commerce [calendrier de publication](../release/schedule.md) et commencez à préparer les mises à niveau rapidement. Adobe publie chaque année le calendrier des versions afin de faciliter le processus de planification des vendeurs et recommande de mettre à niveau chaque cycle de publication de correctifs. Pour rester conforme PCI, les marchands doivent se trouver sur le dernier correctif ou correctif de sécurité.

## Pour qui est ce guide ?

L’audience cible de ce guide est la suivante :

- **Chargés d&#39;e-commerce et directeurs techniques**: comprenez le parcours de mise à niveau, l’importance d’une mise à niveau régulière et la meilleure façon de planifier et de préparer une mise à niveau.
- **Équipes des opérations et du développement**: découvrez les étapes techniques nécessaires à la mise à niveau vers la dernière version d’Adobe Commerce et les outils disponibles qui rendent le processus plus facile, plus rapide et plus abordable.

## Explication du processus de mise à niveau

L’une des raisons pour lesquelles vous avez choisi Adobe Commerce est probablement la suivante :

- Jeu de fonctionnalités complet d’usine
- Fonctionnalités SaaS proposées indépendamment du code principal
- Offre robuste d’extensions Marketplace
- Capacité unique d’offrir une flexibilité infinie afin que vous puissiez personnaliser votre site pour mieux répondre aux besoins de votre entreprise et de vos clients

Toutefois, l’avantage d’être un produit hautement extensible et personnalisable peut entraîner des problèmes de mise à niveau potentiels lorsque les personnalisations ne sont pas codées selon les bonnes pratiques, ce qui entraîne des coûts de mise à niveau plus élevés que prévu.

_Alors.. pourquoi un upgrade ?_

La mise à niveau permet à votre entreprise de rester agile dans le secteur du commerce électronique en évolution constante et rapide et permet à votre plate-forme d’être compatible avec les dernières fonctionnalités d’Adobe Commerce qui permettent d’optimiser les ventes et les conversions. L’inclusion de mises à niveau dans vos plans de maintenance standard est essentielle pour garantir la sécurité de votre magasin, sa conformité PCI et son efficacité opérationnelle maximale.

### Sécurité

La sécurité est l’une des principales raisons de la mise à niveau, car 83 % des incidents de sécurité se produisent sur des logiciels obsolètes. Selon [IBM](https://www.ibm.com/reports/data-breach)En outre, le coût moyen d’une violation de données s’élève à 3,86 millions $, soit bien plus que ce qu’il coûte pour atténuer ce risque grâce à la mise à niveau. Adobe offre deux façons de sécuriser votre boutique tout au long de l’année :

- **Versions de correctifs**: incluez la sécurité, les performances, la qualité et des correctifs de bogues de priorité élevée.
- **Versions de correctifs de sécurité**: incluez des correctifs et des améliorations pour préserver la sécurité de votre site et faciliter sa mise en oeuvre.

### Performances

Les performances sont une autre raison majeure de la mise à niveau. Selon [HubSpot](https://blog.hubspot.com/marketing/page-load-time-conversion-rates), les cinq premières secondes de temps de chargement ont un effet significatif sur les taux de conversion et chaque seconde de latence par la suite a un impact de -4,4 %. Cela, couplé au fait que la vitesse de page est un facteur de classement d’optimisation pour les moteurs de recherche, montre pourquoi les performances du site sont un élément essentiel de votre site pour le maintenir et l’améliorer régulièrement. Chaque version de correctif inclut des améliorations de performances. Dès lors, tirer parti des nouvelles versions prend en charge vos plans de croissance et maintient votre entreprise compétitive.

### Coût du délai

Le report ou le report des mises à niveau de la plate-forme se résume souvent au coût immédiat. Cependant, le coût réel d’une version obsolète de n’importe quel logiciel est beaucoup plus élevé et peut avoir un impact durable sur une entreprise.

Cela peut sembler contre-intuitif, mais réaliser régulièrement des mises à jour de plateforme nécessite moins d&#39;effort global que d&#39;effectuer des mises à jour peu fréquentes en raison du montant de la dette technique accumulée résultant d&#39;un report. Adobe a récemment travaillé avec un partenaire qui a un commerçant de détail qui effectuait des upgrades peu fréquents et incohérents (annuellement ou plus). En transformant leur approche des mises à niveau et en suivant un parcours de mise à niveau régulier recommandé par l’Adobe sur une période de 12 mois, le partenaire a pu économiser au client quatre semaines de temps, d’efforts et de coûts associés cumulés pour le développement. Ces coûts pourraient ensuite être réorientés vers des initiatives visant à stimuler la croissance des entreprises.

Lorsque des mises à jour sont effectuées régulièrement, les modifications sont incrémentielles et l’opération de mise à niveau correspondante le reflète. Lorsque les mises à jour de plateforme sont différées pendant une longue période, elles peuvent devenir un processus beaucoup plus impliqué. En outre, les extensions que vous utilisez à partir de la fonction [Adobe Commerce Marketplace](https://marketplace.magento.com/) et d’autres intégrations tierces peuvent également être affectées. Enfin, le temps nécessaire pour enquêter, planifier et effectuer une mise à niveau différée est prolongé, ce qui ajoute des efforts et des coûts évitables.

Voici quelques-uns des facteurs généraux qui affectent le niveau d’effort pour mettre à niveau votre projet :

| Complexité technique | Planification et stratégie |
|-----------------------------------------------------------|--------------------------------------------------------------|
| Étendue des personnalisations | La clarté des exigences, les décisions hésitantes et l’élargissement de la portée |
| Nombre d’extensions | Fréquence de mise à niveau |
| Nombre d’intégrations avec des tiers (OMS, ERP) | Votre stratégie de test |
| Codage vers les bonnes pratiques |                                                              |

La croissance continue de l&#39;espace du commerce numérique a exercé une pression accrue sur les entreprises pour qu&#39;elles évoluent plus rapidement, plus souvent et de manière imprévisible. L’incapacité à suivre et à anticiper le comportement d’achat des clients a uniformisé les règles du jeu pour les marques même les plus importantes et les plus établies. Vous devez être en mesure de fournir des expériences robustes et personnalisées sur tous les points de contact, sans perte de performance ni de temps de disponibilité. Vous devez être capable d&#39;innover plus rapidement, sans limites, pour rester en avance sur les concurrents mondiaux. En effectuant une mise à niveau, vous allez à l’avenir vérifier votre activité et vous préparer à mieux répondre aux besoins dynamiques des clients.
