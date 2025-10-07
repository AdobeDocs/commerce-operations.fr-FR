---
title: Onglet [!UICONTROL Redis]
description: En savoir plus sur l’onglet [!UICONTROL Redis] de  [!DNL Observation for Adobe Commerce].
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
feature: Configuration, Observability
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Onglet [!DNL Redis]

## [!UICONTROL Redis Node summary]

![Résumé du nœud Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

La **[!UICONTROL Redis Node summary]** inclut tous les nœuds d’un environnement. L’exemple ci-dessus inclut les nœuds pour l’évaluation partagée. Il y a un primaire et deux secondaires sur la production et aussi un primaire et deux secondaires sur l&#39;évaluation.

## [!UICONTROL Redis node detail]

![Mesures de performances du serveur Redis et détails de configuration du nœud](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

Le cadre de **[!UICONTROL Redis node detail]** indique l’environnement, le rôle de [!DNL Redis], la version du logiciel et la taille du nœud.

## [!UICONTROL Redis node roles timeline]

![Chronologie des rôles de nœud Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

La trame **[!UICONTROL Redis node roles timeline]** indique la perte de service [!DNL Redis] dans des rôles particuliers. Si une ligne baisse, cela indique que le rôle particulier représenté par la ligne a perdu un ou plusieurs nœuds.

## [!UICONTROL Connection to Redis]

![Connexion à Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

L’image **[!UICONTROL Connection to Redis]** affiche la valeur net.connectorClients à partir des données d’exemple [!DNL New Relic Redis]. Il affiche le nombre de connexions par application [!DNL New Relic] (environnement) et nœud.

## [!UICONTROL Commands per second by node]

![&#x200B; Commandes par seconde par nœud &#x200B;](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

L’image **[!UICONTROL Commands per second by node]** affiche les commandes [!DNL Redis] par nœud et par seconde pendant la période sélectionnée.

## [!UICONTROL Redis % of memory used]

![Redis % de la mémoire utilisée](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

L’image **[!UICONTROL Redis % of memory used]** affiche le pourcentage de mémoire maximale utilisé par les serveurs [!DNL Redis].

## [!UICONTROL Redis used memory]

![Redis de la mémoire utilisée](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

L’image **[!UICONTROL Redis used memory]** indique l’utilisation de la mémoire par les nœuds en Go/Mo.

## [!UICONTROL Redis changes since last db save]

![Redis des modifications depuis le dernier enregistrement de la base de données](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] est un résident de la mémoire et enregistre les informations dans le stockage . La trame **[!UICONTROL Redis changes since last db save]** indique le nombre de modifications de mémoire qui se sont produites depuis le dernier enregistrement de la base de données dans le stockage. Voir [Persistance Redis](https://redis.io/docs/latest/operate/oss_and_stack/management/persistence/) pour plus d’explications sur la persistance [!DNL Redis's].

## [!UICONTROL Redis synchronization from Log]

![Synchronisation Redis depuis le journal](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

La trame de **[!UICONTROL Redis synchronization from Log]** se concentre sur les erreurs rencontrées lors de la synchronisation [!DNL Redis] ou sur les erreurs dues à des problèmes de synchronisation. Pour plus d’informations sur les [!DNL Redis], consultez la [[!DNL Redis] Documentation](https://redis.io/docs/).
