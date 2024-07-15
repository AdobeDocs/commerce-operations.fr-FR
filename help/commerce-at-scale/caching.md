---
title: Planification efficace du cache
description: Pour garantir la réussite de votre site en cours de chargement, reportez-vous aux points de référence recommandés pour la mise en cache.
exl-id: 275eb21d-fa52-4b97-9453-8f8553128b53
feature: Integration, Cache
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Planification d’une mise en cache efficace pour le succès du commerce électronique en cours de chargement

La diffusion d’une expérience d’achat en cours de chargement nécessite une stratégie de mise en cache bien planifiée. Bien que, dans un premier temps, les parties prenantes de l’entreprise demandent peut-être de toujours présenter des données de produit en temps réel aux clients, il ne s’agit pas d’une utilisation optimale des ressources système, et l’impact des performances du site des utilisateurs finaux l’emporterait largement sur les avantages d’afficher systématiquement des informations en temps réel.

L’étape initiale de la stratégie de mise en cache doit donc être de définir avec les parties concernées une matrice des délais de mise en cache acceptables pour les différentes zones du site, par exemple :

| Zone de mise en cache | À quelle fréquence change-t-on ? | Impact si du contenu obsolète diffusé à partir du cache | Durée de vie (TTL) de la mise en cache acceptable ? |
|---------------------------------------------------------------|--------------------|-------------------------------------------|-----------------------------------------------------|
| Pages d’HTML du contenu du site, mises à jour via CMS | Infréquemment | Faible | 1 jour |
| Média/ressources du modèle de contenu du site - logo, conception CSS, images | Infréquemment | Faible | 1 semaine |
| Pages de liste de produits (PLP) | Infréquemment | Medium | 1 jour |
| Page Détails du produit (PDP) | Parfois | Medium | 1 heure |
| Catégories de produits | Infréquemment | Medium | 1 jour |
| Prix | Fréquemment | Élevée | Pas de cache |
| Inventaire/stock | Fréquemment | Élevée | Pas de cache |
| Recherche de site | La plupart des utilisateurs uniques | Medium | Résultats de la mise en cache des 100 meilleures expressions de recherche pour 1 jour |
| Passage en caisse | Chaque utilisateur unique | Très élevée | Pas de cache |
| Panier | Chaque utilisateur unique | Très élevée | Pas de cache |
| Pages de paiement | Chaque utilisateur unique | Très élevée | Pas de cache |

Une fois cette planification initiale terminée, la configuration technique peut commencer à être mise en place pour configurer les caches en fonction de ces exigences.

Même si le contenu est mis à jour et qu’il doit être rendu actif dans la mise en cache TTL, il est, dans la plupart des cas, possible d’effacer manuellement les caches pour le [Dispatcher d’AEM](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html?lang=en) et le cache [Adobe Commerce](../configuration//cli/manage-cache.md#clean-and-flush-cache-types) de manière sélective pour ce contenu, ce qui signifie que les modifications urgentes seront immédiatement répercutées. Le processus relatif à l’effacement manuel du cache doit également être planifié et testé à l’avance afin que, s’il est nécessaire de forcer manuellement une mise à jour d’un contenu, il soit documenté dans un runbook d’exploitation de site et indique comment et qui doit être impliqué dans cette action.
