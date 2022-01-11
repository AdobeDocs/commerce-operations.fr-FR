---
title: Présentation du processus de mise à niveau
description: Découvrez comment la mise à niveau de votre projet Adobe Commerce et Magento Open Source vous permet de maintenir votre vitrine sécurisée et de fonctionner efficacement.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 0%

---


# Présentation du processus de mise à niveau

La mise à niveau de votre projet Adobe Commerce ou Magento Open Source est essentielle pour garantir la sécurité, la conformité PCI et le bon fonctionnement de votre magasin. Nous avons développé ce guide pour vous guider à travers les points essentiels à prendre en compte lors de la préparation d’une mise à niveau.

Ce guide présente un aperçu du parcours de mise à niveau standard d’Adobe Commerce/Magento Open Source et des bonnes pratiques à suivre le long de ce parcours. Il décrit également les détails techniques du processus de mise à niveau avec un exemple opportun et des instructions détaillées pour la mise à niveau vers Adobe Commerce/Magento Open Source version 2.4.4. La version 2.4.4 du correctif sera généralement disponible le 8 mars 2022. Il est donc important de commencer à préparer cette mise à niveau tôt car la variable [Fin de vie (EOL)](https://devdocs.magento.com/release/lifecycle-policy.html) en 2022, les dates de la ligne 2.3 et des versions 2.4.0 à 2.4.3 approchent. Enfin, nous fournissons des ressources de planification et des outils de mise à niveau qui rendent votre processus de mise à niveau plus efficace.

## Pour qui est ce guide ?

L’audience cible de ce guide comprend :

### Chefs et directeurs techniques d’e-commerce

Ce guide aide les clients qui détiennent ces rôles à comprendre le parcours de mise à niveau, l’importance de la mise à niveau régulière et la meilleure façon de planifier et de préparer une mise à niveau.

### Équipes des opérations et du développement

Ce guide aide ces équipes à découvrir les étapes techniques nécessaires à la mise à niveau vers la version 2.4.4 (ou toute version d’Adobe Commerce/Magento Open Source) et les outils qu’elles peuvent utiliser pour rendre le processus plus facile, plus rapide et plus abordable.

## Explication du processus de mise à niveau

L’une des raisons pour lesquelles vous avez choisi Adobe Commerce/Magento Open Source est probablement la suivante :

- Jeu de fonctionnalités complet d’usine
- Fonctionnalités SaaS proposées indépendamment du code principal
- Offre robuste d’extensions Marketplace
- Capacité unique d’offrir une flexibilité infinie afin que vous puissiez personnaliser votre site pour mieux répondre aux besoins de votre entreprise et de vos clients.

Toutefois, l’avantage d’être un produit hautement extensible et personnalisable peut entraîner des problèmes de mise à niveau potentiels lorsque les personnalisations ne sont pas codées selon les bonnes pratiques, ce qui entraîne des coûts de mise à niveau plus élevés que prévu.

_Alors.. pourquoi un upgrade ?_

La mise à niveau permet à votre entreprise de rester agile dans le secteur du commerce électronique en constante évolution et à rythme rapide et permet à votre plateforme d’être toujours compatible avec les dernières fonctionnalités qui aident à optimiser les ventes et les conversions. L’inclusion de mises à niveau dans vos plans de maintenance standard est également essentielle pour garantir la sécurité de votre magasin, sa conformité PCI et son efficacité maximale.

### Sécurité

La sécurité est l&#39;une des principales raisons de la mise à niveau, puisque 83 % des incidents de sécurité surviennent sur des logiciels obsolètes. Selon [IBM](https://www.ibm.com/security/data-breach)En outre, le coût moyen d’une violation de données s’élève à 3,86 millions $, soit bien plus que ce qu’il coûte pour atténuer ce risque grâce à la mise à niveau. Adobe offre deux façons de sécuriser votre boutique tout au long de l’année :

- **Versions de correctifs**: incluez la sécurité, les performances, la qualité et des correctifs de bogues de priorité élevée.
- **Versions de correctifs de sécurité**: incluez des correctifs et des améliorations afin de préserver la sécurité de votre site et de le mettre en oeuvre plus facilement.

### Performances

Les performances sont une autre raison majeure de la mise à niveau. Selon [HubSpot](https://blog.hubspot.com/marketing/page-load-time-conversion-rates), les cinq premières secondes de temps de chargement ont un effet significatif sur les taux de conversion et chaque seconde de latence par la suite a un impact de -4,4 %. Cela, couplé au fait que la vitesse de page est un facteur de classement d’optimisation pour les moteurs de recherche, montre pourquoi les performances du site sont un élément essentiel de votre site pour le maintenir et l’améliorer régulièrement. Chaque version de correctif inclut des améliorations de performances. Dès lors, tirer parti des nouvelles versions prend en charge vos plans de croissance et maintient votre entreprise compétitive.

### Coût du délai

Le report ou le report des mises à niveau de la plate-forme se résume souvent au coût immédiat. Cependant, le coût réel d’une version obsolète de n’importe quel logiciel est beaucoup plus élevé et peut avoir un impact durable sur une entreprise.

Cela peut sembler contre-intuitif, mais réaliser régulièrement des mises à jour de plateforme nécessite moins d&#39;effort global que d&#39;effectuer des mises à jour peu fréquentes en raison du montant de la dette technique accumulée résultant d&#39;un report. Nous avons récemment travaillé avec un partenaire qui a un commerçant de détail qui effectuait des upgrades peu fréquents et incohérents (annuellement ou plus). En transformant leur approche des mises à niveau et en suivant une procédure de mise à niveau régulière recommandée par l’Adobe sur une période de 12 mois, le partenaire a pu économiser au client quatre semaines de temps de développement cumulé, d’efforts et de coûts associés, qui ont tous été redirigés vers des initiatives qui stimulent la croissance de l’entreprise.

![](../assets/upgrade-guide/waiting-is-not-a-winning-strategy.jpg)

Lorsque des mises à jour sont effectuées régulièrement, les modifications sont incrémentielles et l’opération de mise à niveau correspondante le reflète. Lorsque les mises à jour de plateforme sont différées pendant une longue période, elles peuvent devenir un processus beaucoup plus impliqué. En outre, les extensions que vous utilisez à partir de la fonction [Marketplace](https://marketplace.magento.com/) et toute autre intégration tierce peut également être affectée. Enfin, le temps nécessaire pour enquêter, planifier et effectuer une mise à niveau différée est prolongé, ce qui ajoute des efforts et des coûts évitables.

La croissance continue de l&#39;espace du commerce numérique a exercé une pression accrue sur les entreprises pour qu&#39;elles évoluent plus rapidement, plus souvent et de manière imprévisible. L’incapacité à suivre et à anticiper le comportement d’achat des clients a uniformisé les règles du jeu pour les marques même les plus importantes et les plus établies. Vous devez être en mesure de fournir des expériences robustes et personnalisées sur tous les points de contact, sans perte de performance ni de temps de disponibilité. Vous devez être capable d&#39;innover plus rapidement, sans limites, pour rester en avance sur les concurrents mondiaux. En effectuant une mise à niveau, vous allez à l’avenir vérifier votre activité et vous préparer à mieux répondre aux besoins dynamiques des clients.

## Calendrier des versions 2022

Adobe publie une [calendrier de publication](https://devdocs.magento.com/release/) chaque année pour faciliter le processus de planification des vendeurs et recommande de mettre à niveau chaque cycle de publication de correctifs. Pour rester conforme PCI, les marchands doivent se trouver sur le dernier correctif ou correctif de sécurité. La chronologie suivante présente les principaux événements de mise à jour et de fin de vie en 2022.

![](../assets/upgrade-guide/2022-release-timeline.svg)

Les événements importants à noter sont les suivants :

- La prise en charge de la version 2.3.x se termine après le 22 avril
- La version 2.4.0 à 2.4.3 (basée sur PHP 7.4) arrive à la fin de la prise en charge de la qualité en novembre 2022, lorsque PHP 7.4 atteint la fin de vie (EOL).
- Sur la base de ces deux événements ci-dessus, il est important d&#39;effectuer la mise à niveau vers la version 2.4.4 ou ultérieure d&#39;ici le 22 novembre.
- En ligne avec Adobe Commerce [politique de cycle de vie](https://devdocs.magento.com/release/lifecycle-policy.html), les versions 2.4.4 et 2.4.5 sont prises en charge jusqu’au 24 novembre
