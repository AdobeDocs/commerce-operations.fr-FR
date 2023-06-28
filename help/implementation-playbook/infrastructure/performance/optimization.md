---
title: Optimisation des performances
description: Découvrez l’optimisation des performances et les étapes à suivre pour passer en revue les performances de votre mise en oeuvre Adobe Commerce.
exl-id: 506ef2cc-c6fd-4401-afa5-a71e7b9871e6
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Optimisation des performances

La performance est un grand sujet. Lorsqu’un site est lent ou ne répond pas aux utilisateurs, la conversion est affectée. Nous vous recommandons de suivre les étapes suivantes afin d’optimiser les performances de votre Adobe Commerce sur la mise en oeuvre de l’infrastructure cloud :

- Évaluer le problème
- Mesure des performances
- Identifier une partie du système essentielle à l’amélioration des performances
- Modification d’une partie du système pour supprimer le goulot d’étranglement
- Mesure des performances après modification
- S’il est préférable de l’adopter ou de l’annuler

## Problèmes de performances standard

L&#39;impact d&#39;une expérience lente est généralement défini par deux indicateurs, et chaque facteur peut être causé pour des tonnes de raisons.

Le délai d’accès au premier octet (TTF) est généralement considéré comme un indicateur qui définit la vitesse de réponse du serveur. Le temps non seulement provient de l’exécution du code source pour gérer la requête, mais il peut également être affecté par les facteurs suivants :

- Recherche DNS
- Requêtes lentes à partir du calque DB
- Temps du processeur depuis chaque couche d’application
- Limite de mémoire
- L’attente d’E/S peut affecter à partir de la lecture et de l’écriture du fichier, le service de connexion via le socket
- Paramètres logiciels (nginx, PHP, MySQL, Redis, Varnish)
- Bande passante réseau
- Mauvaise mise en cache
- Code incorrect
- Mauvaise approche d’intégration
- Dépendance de la réponse lente du service tiers
- Architecture sans évolutivité

Les ressources à chargement lent sont généralement considérées comme un indicateur qui définit la ressource statique (CSS, JavaScript, images, vidéos, réponse d’appel Ajax tiers).

Adobe Commerce peut évoluer avec votre entreprise grâce à ses fonctionnalités :

![Diagramme présentant les fonctionnalités évolutives d’Adobe Commerce](../../../assets/playbooks/scalable-capabilities.svg)

Il existe également des facteurs clés qui déterminent l’échelle du commerce, ce qui a également un impact sur les performances globales.

- Catalogue de produits complexe et volumineux
- Grand nombre d’administrateurs
- Confrontes globales
- Trafic à forte variable
- Développement des points de contact
- Traitements de volume élevé

Pour les architectures en couches et pouvant être mises en cache conçues pour l’échelle, vous pouvez utiliser ce graphique comme référence.

![Diagramme montrant comment utiliser l’API GraphQL d’Adobe Commerce dans une architecture pouvant être mise en cache](../../../assets/playbooks/cacheable-architecture.svg)
