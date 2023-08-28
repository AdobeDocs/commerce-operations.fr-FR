---
title: Architecture de référence globale
description: Tirez le meilleur parti de votre implémentation Adobe Commerce en exploitant une architecture de référence globale.
exl-id: a18529a3-da9b-4e1b-8048-0a906e65c740
feature: Deploy
source-git-commit: d33d1e24c38984d0abf0c7f8f5ad2eb804ff621d
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---


# Architecture de référence globale (GRA)

>[!VIDEO](https://video.tv.adobe.com/v/3410528/?quality=12&learn=on)

Lorsque vous gérez des entreprises qui possèdent plusieurs sites pour plusieurs marques sur plusieurs marchés locaux (avec des devises localisées, des langues, des médias, des catalogues partagés et des paniers uniques) et qui souhaitent éviter des coûts inutiles pour la mise en oeuvre des mêmes fonctionnalités et intégrations, l’architecture de référence globale (GRA) est toujours une bonne option.

![Tableau expliquant le coût de la divergence dans l’architecture](../../../assets/playbooks/divergent-architecture.svg)

![Tableau expliquant le coût de la consolidation en architecture](../../../assets/playbooks/consolidated-architecture.svg)

L’évaluation géographique est la suivante :

- Approche de mise en oeuvre
- Une stratégie de déploiement
- Un modèle de gouvernance des processus

L’évaluation géographique n’est pas :

- Une &quot;fonctionnalité&quot; de produit
- Unique à n’importe quelle plateforme commerciale
- Uniquement pour les cas d’utilisation métier globaux

Impact de l’évaluation géographique :

- Diffusion du code

   - Conçus à partir de référentiels de code spécifiques à des fins, qui offrent différentes expériences.

- Comment les systèmes d’entreprise sont intégrés

   - Consolidation des connexions aux systèmes d’entreprise par marque et/ou région.

- Développement et maintenance de la personnalisation

   - Garantit que les personnalisations sont centralisées et spécifiques au domaine, de sorte que tout effort de personnalisation soit effectué d’un point de vue holistique pour l’entreprise.

- Comment les nouveaux marchés sont activés

   - Simplifie le lancement de plusieurs canaux et marchés, qui autrement coûteraient beaucoup plus de temps et d&#39;argent.

>[!TIP]
>
>Voir [Exemples de GRA](examples.md).
