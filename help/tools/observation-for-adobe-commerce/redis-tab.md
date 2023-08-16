---
title: La variable [!UICONTROL Redis] tab
description: En savoir plus sur les [!UICONTROL Redis] de [!DNL Observation for Adobe Commerce].
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# La variable [!DNL Redis] tab

## [!UICONTROL Redis Node summary]

![Résumé du noeud Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

La variable **[!UICONTROL Redis Node summary]** est inclus dans tous les noeuds d’un environnement. L’exemple ci-dessus inclut les noeuds pour l’évaluation partagée. Il y a un primaire et deux secondaires en production et un primaire et deux secondaires en évaluation.

## [!UICONTROL Redis node detail]

![Détails du noeud Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

La variable **[!UICONTROL Redis node detail]** frame indique l&#39;environnement, [!DNL Redis] rôle, version logicielle et taille du noeud.

## [!UICONTROL Redis node roles timeline]

![Redis la chronologie des rôles de noeud](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

La variable **[!UICONTROL Redis node roles timeline]** frame indique la perte de [!DNL Redis] service en particulier. Si une ligne s’effondre, cela indique que le rôle particulier représenté par la ligne a perdu un ou plusieurs noeuds.

## [!UICONTROL Connection to Redis]

![Connexion à Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

La variable **[!UICONTROL Connection to Redis]** Le cadre affiche la valeur net.connectClients de la variable [!DNL New Relic Redis] données d’exemple. Il affiche le nombre de connexions par [!DNL New Relic] application (environnement) et noeud .

## [!UICONTROL Commands per second by node]

![Commandes par seconde par noeud](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

La variable **[!UICONTROL Commands per second by node]** Le cadre affiche la [!DNL Redis] commandes par noeud par seconde pendant la période sélectionnée.

## [!UICONTROL Redis % of memory used]

![Redis % de la mémoire utilisée](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

La variable **[!UICONTROL Redis % of memory used]** L’image affiche le pourcentage de la mémoire maximale utilisée par la fonction [!DNL Redis] serveurs.

## [!UICONTROL Redis used memory]

![Redis used memory](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

La variable **[!UICONTROL Redis used memory]** frame affiche l’utilisation du noeud de la mémoire en Go/Mo.

## [!UICONTROL Redis changes since last db save]

![Modifie depuis le dernier enregistrement de la base de données](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] est un résident de la mémoire et enregistre les informations dans le stockage. La variable **[!UICONTROL Redis changes since last db save]** frame indique le nombre de modifications apportées à la mémoire depuis que la dernière base de données a été enregistrée dans le stockage. Voir [Réinitialiser la persistance](https://redis.io/docs/manual/persistence/) pour plus d’informations sur [!DNL Redis's] persistance.

## [!UICONTROL Redis synchronization from Log]

![Redis la synchronisation à partir du journal](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

La variable **[!UICONTROL Redis synchronization from Log]** frame se concentre sur les erreurs rencontrées lors de la [!DNL Redis] synchronisation ou erreurs survenant en raison de problèmes de synchronisation. Pour plus d’informations sur [!DNL Redis], voir [[!DNL Redis] Documentation](https://redis.io/docs/).
