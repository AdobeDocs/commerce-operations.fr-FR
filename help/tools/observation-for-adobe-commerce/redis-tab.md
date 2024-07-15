---
title: Onglet [!UICONTROL Redis]
description: Découvrez l’onglet [!UICONTROL Redis] de [!DNL Observation for Adobe Commerce].
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
feature: Configuration, Observability
source-git-commit: 06f015139683f319f11317f8d7f0029cbd2548e3
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Onglet [!DNL Redis]

## [!UICONTROL Redis Node summary]

![Résumé du noeud Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

Le **[!UICONTROL Redis Node summary]** comprend tous les noeuds d’un environnement. L’exemple ci-dessus inclut les noeuds pour l’évaluation partagée. Il y a un primaire et deux secondaires en production et un primaire et deux secondaires en évaluation.

## [!UICONTROL Redis node detail]

![Redis node detail](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

Le cadre **[!UICONTROL Redis node detail]** indique l’environnement, le rôle [!DNL Redis], la version logicielle et la taille du noeud.

## [!UICONTROL Redis node roles timeline]

![Redis node rôles timeline](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

L’image **[!UICONTROL Redis node roles timeline]** indique la perte du service [!DNL Redis] dans des rôles particuliers. Si une ligne s’effondre, cela indique que le rôle particulier représenté par la ligne a perdu un ou plusieurs noeuds.

## [!UICONTROL Connection to Redis]

![Connexion à Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

L’image **[!UICONTROL Connection to Redis]** affiche la valeur net.connectClients de l’exemple de données [!DNL New Relic Redis]. Il affiche le nombre de connexions par l’application [!DNL New Relic] (environnement) et le noeud.

## [!UICONTROL Commands per second by node]

![Commandes par seconde par noeud](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

L’image **[!UICONTROL Commands per second by node]** affiche les commandes [!DNL Redis] par noeud par seconde pendant la période sélectionnée.

## [!UICONTROL Redis % of memory used]

![Redis % de la mémoire utilisée](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

L’image **[!UICONTROL Redis % of memory used]** indique le pourcentage de la mémoire maximale utilisée par les serveurs [!DNL Redis].

## [!UICONTROL Redis used memory]

![Redis used memory](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

L’image **[!UICONTROL Redis used memory]** montre l’utilisation des noeuds de la mémoire en Go/Mo.

## [!UICONTROL Redis changes since last db save]

![Redis les modifications depuis le dernier enregistrement de la base](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] est un résident de la mémoire et enregistre les informations dans le stockage. L’image **[!UICONTROL Redis changes since last db save]** indique le nombre de modifications apportées à la mémoire depuis l’enregistrement de la dernière base de données dans le stockage. Pour plus d’informations sur la persistance [!DNL Redis's], voir [Redis persistence](https://redis.io/docs/latest/operate/oss_and_stack/management/persistence/) .

## [!UICONTROL Redis synchronization from Log]

![Redis synchronisation à partir du journal](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

L’image **[!UICONTROL Redis synchronization from Log]** se concentre sur les erreurs rencontrées lors de la synchronisation [!DNL Redis] ou les erreurs qui se produisent en raison de problèmes de synchronisation. Pour plus d&#39;informations sur [!DNL Redis], consultez la [[!DNL Redis] documentation](https://redis.io/docs/).
