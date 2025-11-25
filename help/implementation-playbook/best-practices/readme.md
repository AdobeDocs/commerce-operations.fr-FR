---
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---
# Bonnes pratiques : workflow de création de contenu

Ce document décrit le workflow de l’utilisateur pour demander des modifications ou des ajouts au contenu *[Bonnes pratiques](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html* du *guide d’implémentation d’Adobe Commerce*.

## Qui peut créer une demande ?

Adobe accepte les demandes des parties prenantes internes et externes, y compris, mais sans s’y limiter, les personnes des groupes suivants :

- Partenaires Adobe
- Adobe CTAG (groupe consultatif technique client), service clientèle, succès client, équipes d’ingénierie

## Comment créer une requête ?

**Les parties prenantes internes** peuvent envoyer des demandes en ouvrant un problème Jira dans le projet COMDOX. **Les parties prenantes externes** peuvent envoyer des requêtes en ouvrant un [problème GitHub](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) dans ce référentiel.

Vous pouvez soumettre les types de demandes suivants :

- Idées de nouveau contenu
- Mises à jour du contenu déjà publié
- Publiez le nouveau contenu fourni par la partie prenante ou la communauté

## Quel est le processus global ?


**Créer un ticket Jira ou un problème**—Les parties prenantes internes créent un ticket Jira dans le projet COMDOX. Les parties prenantes externes soumettent un problème GitHub. Incluez des détails complets dans le problème Jira ou [GitHub](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) pour aider l’équipe à comprendre le contexte et à donner la priorité à la requête.

**L’équipe du projet Adobe évalue et classe par priorité la demande**—L’équipe surveille régulièrement les demandes pour déterminer la priorité et évaluer les modifications demandées pour les inclure dans les bonnes pratiques du manuel de mise en œuvre. Par exemple, l’équipe peut déterminer qu’au lieu de créer une rubrique relative aux bonnes pratiques, le contenu demandé doit être ajouté à la documentation du produit existant sur Experience League ou le site Adobe Developer.

Si les informations fournies dans une requête ne sont pas suffisantes, l’équipe demande des informations supplémentaires au demandeur. Si le demandeur ne répond pas dans les 14 jours, l’équipe ferme la demande.

**Créer ou mettre à jour du contenu**-Le travail de création de contenu s’effectue selon le processus décrit dans le [Guide du contributeur d’Adobe Experience League](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html). Selon la demande, le travail peut inclure la conversion d’un nouveau contenu en markdown, la création d’une rubrique ou la mise à jour d’une rubrique existante.

**Révision, approbation et publication du contenu**-le contenu est révisé et modifié lors de la création ou de la mise à jour de la rubrique à l’aide de [demandes d’extraction GitHub](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html#pull-requests). Tout le contenu doit faire l&#39;objet d&#39;une révision éditoriale. La révision technique est facultative et dépend du contenu. Si aucun examen technique n&#39;est nécessaire, le processus se poursuit avec un examen rédactionnel uniquement. Ce processus peut prendre plusieurs itérations jusqu’à ce que le contenu soit approuvé.

Une fois qu’un article est approuvé, la demande d’extraction peut être fusionnée dans la branche de production. La fusion doit être effectuée par l’auteur. Une fois qu’une rubrique est fusionnée, elle peut être publiée en production immédiatement à l’aide d’un processus manuel ou automatiquement la prochaine fois que la tâche de publication s’exécute. Les tâches de publication s’exécutent généralement toutes les deux heures.

**Notification de nouveau contenu**-Adobe proposera une section *Nouveautés* dans la rubrique [Présentation des bonnes pratiques](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html) pour tenir les utilisateurs informés des rubriques récemment publiées ou mises à jour. Adobe encouragera également le nouveau contenu des bonnes pratiques en utilisant les canaux existants, tels que le marketing et les communications internes.

## Tableau de la liste d’attente et Kanban

Pour éviter la duplication, les requêtes qui ont été créées et hiérarchisées seront visibles dans la liste d’attente Jira du projet COMDOX et du projet [Problèmes GitHub](https://github.com/orgs/AdobeDocs/projects/6/views/1). Les parties prenantes internes sont encouragées à collaborer avec le système de vote de Jira pour voter en faveur des demandes qu’elles jugent nécessaires ou pertinentes. Le vote permet également à l’équipe du projet des bonnes pratiques de comprendre le type de contenu attendu et apprécié par les parties prenantes. Les demandes en attente de hiérarchisation et de révision apparaissent dans la liste d’attente jusqu’à ce qu’elles soient déplacées vers les voies actives du tableau kanban.

Le tableau Kanban est accessible par les utilisateurs internes pour afficher (et/ou surveiller) le contenu sur lequel porte l’application et la progression des travaux. Seules les requêtes actives seront affichées sur ce panorama.
