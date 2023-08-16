---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%

---
# Bonnes pratiques : workflow de création de contenu

Ce document décrit le processus utilisateur pour demander des modifications ou des ajouts au *[Bonnes pratiques](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html* dans le *Manuel de mise en oeuvre Adobe Commerce*.

## Qui peut créer une requête ?

Adobe accepte les demandes des parties prenantes internes et externes, y compris, mais sans s’y limiter, des personnes des groupes suivants :

- Partenaires en Adobe
- Adobe CTAG (Groupe consultatif technique client), service clientèle, succès client, équipes d’ingénierie

## Comment créer une requête ?

**Intervenants internes** Vous pouvez envoyer des requêtes en ouvrant un problème Jira dans le projet COMDOX. **Intervenants externes** peut envoyer des requêtes en ouvrant une [Problème GitHub](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) dans ce référentiel.

Vous pouvez envoyer les types de requêtes suivants :

- Idées pour un nouveau contenu
- Mises à jour du contenu déjà publié
- Publier le nouveau contenu fourni par le partenaire ou la communauté

## Quel est le processus global ?


**Création d’un ticket ou d’un problème Jira**: les parties prenantes internes créent un ticket Jira dans le projet COMDOX. Les parties prenantes externes envoient un problème GitHub. Inclure des détails complets dans la bibliothèque Java ou [Problème GitHub](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) pour aider l’équipe à comprendre le contexte et à prioriser la requête.

**L’équipe de projet Adobe évalue la requête et la établit comme priorité.**: l’équipe surveille régulièrement les demandes afin de déterminer la priorité et d’évaluer les modifications demandées pour inclusion dans les bonnes pratiques du manuel d’implémentation. Par exemple, l’équipe peut déterminer qu’au lieu de créer une nouvelle rubrique Bonnes pratiques, le contenu demandé doit être ajouté à la documentation du produit existant sur Experience League ou le site Adobe Developer.

Si une requête ne contient pas suffisamment d’informations, l’équipe demande des informations supplémentaires au demandeur. Si le demandeur ne répond pas dans les 14 jours, l’équipe ferme la demande.

**Créer ou mettre à jour du contenu**- Le travail de création de contenu est terminé à la suite du processus décrit dans la section [Guide du contributeur Adobe Experience League](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html). Selon la requête, le travail peut inclure la conversion d’un nouveau contenu en Markdown, la création d’une rubrique ou la mise à jour d’une rubrique existante.

**Révision, approbation et publication de contenu**-Le contenu est révisé et modifié lors de la création ou de la mise à jour d’une rubrique à l’aide de [Demandes d’extraction GitHub](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=en#pull-requests). Tout le contenu doit passer par une révision éditoriale. La révision technique est facultative et dépend du contenu. Si aucune révision technique n&#39;est nécessaire, le processus se poursuit uniquement par une révision éditoriale. Ce processus peut nécessiter plusieurs itérations jusqu&#39;à ce que le contenu soit validé.

Une fois un article approuvé, la requête de tirage peut être fusionnée avec la branche de production. La fusion doit être effectuée par l’auteur. Une fois qu’une rubrique est fusionnée, elle peut être publiée en production immédiatement à l’aide d’un processus manuel ou automatiquement lors de la prochaine exécution de la tâche de publication. Les tâches de publication s’exécutent généralement toutes les deux heures.

**Nouvelle notification de contenu**-Adobe fournit un *Nouveautés* de la section [Présentation des bonnes pratiques](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=en) pour tenir les utilisateurs informés des rubriques récemment publiées ou mises à jour. Adobe promeut également le nouveau contenu des bonnes pratiques à l’aide des canaux existants, tels que le marketing et les communications internes.

## Arborescence et panorama Kanban

Pour éviter la duplication, les requêtes créées et classées par priorité seront visibles dans le journal Jira du projet COMDOX et [Projet Problèmes GitHub](https://github.com/orgs/AdobeDocs/projects/6/views/1). Les parties prenantes internes sont encouragées à s&#39;engager avec le système électoral de Jira pour voter les demandes qu&#39;elles jugent nécessaires ou pertinentes. Le vote permet également à l’équipe de projet Bonnes pratiques de comprendre le type de contenu auquel les parties prenantes s’attendent et dont ils apprécient le contenu. Les requêtes en attente de hiérarchisation et de révision sont affichées dans le journal des travaux en souffrance jusqu’à ce qu’elles soient déplacées vers les voies actives dans le panorama Kanban.

Le panorama Kanban est accessible par les utilisateurs internes pour voir (et/ou surveiller) quel contenu est en cours de traitement et quelle est la progression. Seules les requêtes actives s’affichent sur ce panorama.
