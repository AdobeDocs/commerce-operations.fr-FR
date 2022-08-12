---
title: '"Le [!UICONTROL Redis] tab"'
description: En savoir plus sur les [!UICONTROL Redis] de [!DNL Observation for Adobe Commerce].
source-git-commit: 3f2a401bb916fc04405f21ba2acfc42f7defdccb
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Le [!DNL Redis] tab

## [!UICONTROL Redis Node summary]

![Résumé du noeud Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

Le **[!UICONTROL Redis Node summary]** est inclus dans tous les noeuds d’un environnement. Cet exemple inclut les noeuds pour l’évaluation partagée. Il y a une Principale et deux secondaires en production et une Principale et deux secondaires en évaluation.

## [!UICONTROL Redis node detail]

![Détails du noeud Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

Le **[!UICONTROL Redis node detail]** frame indique l&#39;environnement, [!DNL Redis] rôle, version logicielle et taille du noeud.

## [!UICONTROL Redis node roles timeline]

![Redis la chronologie des rôles de noeud](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

Le **[!UICONTROL Redis node roles timeline]** frame indique la perte de [!DNL Redis] service en particulier. Si une ligne s’effondre, cela indique que le rôle particulier représenté par la ligne a perdu un ou plusieurs noeuds.

## [!UICONTROL Connection to Redis]

![Connexion à Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

Le **[!UICONTROL Connection to Redis]** Le cadre affiche la valeur net.connectClients de la variable [!DNL New Relic Redis] données d’exemple. Il affiche le nombre de connexions par [!DNL New Relic] application (environnement) et noeud .

## [!UICONTROL Commands per second by node]

![Commandes par seconde par noeud](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

Le **[!UICONTROL Commands per second by node]** affiche la [!DNL Redis] commandes par noeud par seconde pendant la période sélectionnée.

## [!UICONTROL Redis % of memory used]

![Redis % de la mémoire utilisée](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

Le **[!UICONTROL Redis % of memory used]** L’image affiche le pourcentage de la mémoire maximale utilisée par la fonction [!DNL Redis] serveurs.

## [!UICONTROL Redis used memory]

![Redis used memory](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

Le **[!UICONTROL Redis used memory]** frame affiche l’utilisation du noeud de la mémoire en Go/Mo.

## [!UICONTROL Redis changes since last db save]

![Redis les modifications depuis le dernier enregistrement de la base de données](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] est un résident de la mémoire et enregistre les informations dans le stockage. Le **[!UICONTROL Redis changes since last db save]** frame indique le nombre de modifications apportées à la mémoire depuis que la dernière base de données a été enregistrée dans le stockage. [Ces informations](https://redis.io/docs/manual/persistence/) explique [!DNL Redis's] persistance.

## [!UICONTROL Redis synchronization from Log]

![Redis la synchronisation à partir du journal](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

Le **[!UICONTROL Redis synchronization from Log]** frame se concentre sur les erreurs rencontrées lors de la [!DNL Redis] synchronisation ou erreurs survenant en raison de problèmes de synchronisation. Voir [Documentation Redis](https://redis.io/docs/).
