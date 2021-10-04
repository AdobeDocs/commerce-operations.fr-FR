---
title: Planification efficace du cache
description: Pour garantir la réussite de votre site en cours de chargement, reportez-vous aux points de référence recommandés pour la mise en cache.
exl-id: 275eb21d-fa52-4b97-9453-8f8553128b53
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Planification d’une mise en cache efficace pour le succès du commerce électronique en cours de chargement

La diffusion d’une expérience d’achat en cours de chargement nécessite une stratégie de mise en cache bien planifiée. Bien que, dans un premier temps, les parties prenantes de l’entreprise demandent peut-être de toujours présenter des données de produit en temps réel aux clients, il ne s’agit pas d’une utilisation optimale des ressources système, et l’impact des performances du site des utilisateurs finaux l’emporterait largement sur les avantages d’afficher systématiquement des informations en temps réel.

L’étape initiale de la stratégie de mise en cache doit donc être de définir avec les parties concernées une matrice des délais de mise en cache acceptables pour les différentes zones du site, par exemple :

| Zone de mise en cache | À quelle fréquence change-t-on ? | Impact si du contenu obsolète diffusé à partir du cache | Durée de vie (TTL) de la mise en cache acceptable ? |
|---------------------------------------------------------------|--------------------|-------------------------------------------|-----------------------------------------------------|
| Pages HTML de contenu de site, mises à jour via CMS | Infréquemment | Faible | 1 jour |
| Média/ressources du modèle de contenu du site - logo, conception CSS, images | Infréquemment | Faible | 1 semaine |
| Pages de liste de produits (PLP) | Infréquemment | Volume moyen | 1 jour |
| Page Détails du produit (PDP) | Parfois | Volume moyen | 1 heure |
| Catégories de produits | Infréquemment | Volume moyen | 1 jour |
| Prix | Fréquemment | Élevée | Pas de cache |
| Inventaire/stock | Fréquemment | Élevée | Pas de cache |
| Recherche de site | La plupart des utilisateurs uniques | Volume moyen | Résultats du cache des 100 meilleures expressions de recherche pour 1 jour |
| Passage en caisse | Chaque utilisateur unique | Très élevée | Pas de cache |
| Panier | Chaque utilisateur unique | Très élevée | Pas de cache |
| Pages de paiement | Chaque utilisateur unique | Très élevée | Pas de cache |

Une fois cette planification initiale terminée, la configuration technique peut commencer à être mise en place pour configurer les caches en fonction de ces exigences.

Même si le contenu est mis à jour et qu’il doit être rendu actif dans le délai d’activation de la mise en cache, il est, dans la plupart des cas, possible d’effacer manuellement les caches du dispatcher AEM et du cache de commerce Adobe de manière sélective pour ce contenu, ce qui signifie que les modifications urgentes seront immédiatement répercutées. Le processus relatif à l’effacement manuel du cache doit également être planifié et testé à l’avance afin que, s’il est nécessaire de forcer manuellement une mise à jour d’un contenu, il soit documenté dans un runbook d’exploitation de site et indique comment et qui doit être impliqué dans cette action. Un exemple d’opération manuelle de vidage du cache pour AEM et Adobe Commerce est présenté ici.
