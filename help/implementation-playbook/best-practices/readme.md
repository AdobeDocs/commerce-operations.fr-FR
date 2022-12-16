---
source-git-commit: aaf174e5d895ebc60d4937b0214e23a559532942
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---
# Bonnes pratiques : Workflow de création de contenu

L’objectif de ce document est de détailler le processus que les utilisateurs doivent suivre pour demander du contenu des bonnes pratiques.

## Qui peut créer une requête ?

Deux groupes de parties prenantes peuvent mettre une requête, notamment, mais sans s’y limiter :

- Externe : Partenaires
- Interne : CTAG (Groupe consultatif technique client), service clientèle, succès client, équipes d’ingénierie

## Comment créer une requête ?

Les parties prenantes internes doivent effectuer des requêtes en ouvrant un problème Jira dans le projet COMDOX. Les parties prenantes externes doivent effectuer des requêtes en ouvrant un problème GitHub dans ce référentiel. Les parties prenantes peuvent effectuer les requêtes suivantes :

- Demander l’ajout du nouveau contenu
- Demander des modifications pour le contenu déjà publié
- Partager leur propre contenu à publier

## Quel est le processus global ?

Les parties prenantes internes doivent ouvrir un ticket Jira dans le projet de documentation de commerce (COMDOX) et fournir des détails complets, y compris l’exécution d’un modèle. Ces détails aident l’équipe à hiérarchiser les demandes de contenu.

L’équipe surveille régulièrement les demandes en souffrance afin de déterminer la priorité et si le manuel relatif à l’implémentation est le meilleur emplacement pour la demande. L’équipe peut déterminer qu’au lieu de créer une nouvelle rubrique, le contenu demandé doit être ajouté à la documentation du produit existant sur l’Experience League ou le site Adobe Developer.

Si une requête ne contient pas suffisamment d’informations, l’équipe demandera au demandeur de renseigner tous les champs correspondants. Si le demandeur ne répond pas dans un délai de X jours, l’équipe ferme la demande.
Une fois que l’équipe a validé la demande et l’a hiérarchisée, l’étape suivante consiste à créer la rubrique. Cela peut signifier adapter le contenu au format .md ou créer entièrement l’article.

Le contenu est révisé et modifié lors de la création de la rubrique. Le processus de révision se produit par le biais de demandes d’extraction GitHub. Tout le contenu doit passer par une révision éditoriale. La révision technique est facultative et dépend du contenu. Si aucune révision technique n&#39;est nécessaire, le processus se poursuit uniquement par une révision éditoriale. Ce processus peut nécessiter plusieurs itérations jusqu&#39;à ce que le contenu soit validé.

Une fois un article approuvé, l’étape suivante consiste à le fusionner avec la branche de production. La fusion doit être effectuée par l’auteur. La rubrique peut être publiée immédiatement ou attendre l’exécution de la prochaine tâche de publication, qui publie toutes les rubriques approuvées et fusionnées.

Nous allons afficher une nouvelle section sur la page d’accueil des bonnes pratiques sur Experience League afin d’aider les utilisateurs à rester informés des sujets récemment publiés. Ils n’auront donc pas besoin de parcourir différentes pages et portails pour trouver des informations pertinentes. Nous allons également promouvoir le contenu dans les canaux existants, tels que le marketing et les communications internes.

## Arborescence et panorama Kanban

Pour éviter les doublons, les requêtes créées et classées par priorité doivent être visibles dans le journal en souffrance. Les utilisateurs sont encouragés à s&#39;engager avec le système électoral de Jira pour voter les demandes qu&#39;ils jugent nécessaires ou pertinentes. Cela constituera également un bon indicateur pour l’équipe du type de contenu attendu des parties prenantes. Les demandes en attente de hiérarchisation et de révision s’afficheront dans le journal en souffrance jusqu’à ce qu’elles soient déplacées sur les principales voies du panorama Kanban.

Le panorama Kanban est accessible par les utilisateurs internes pour voir (et/ou surveiller) quel contenu est en cours de traitement et quelle est la progression. Seules les demandes principales s’affichent sur ce panorama.
