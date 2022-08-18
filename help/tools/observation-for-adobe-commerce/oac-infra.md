---
title: '"Le [!UICONTROL Infra] tab"'
description: Le [!UICONTROL Infra] isole les problèmes et les causes des problèmes d’infrastructure.
source-git-commit: b0d80d97f60b24bc801063dc484f3a495cf0a036
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---


# Le [!UICONTROL Infra] tab

Le **[!UICONTROL Infra]** isole les problèmes et les causes des problèmes d’infrastructure. Vous trouverez plus loin la description des cadres que vous pouvez voir dans l’onglet .

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![Alertes de service](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

Le **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** Le graphique affiche les alertes de service collectées par la variable [!DNL New Relic] agent d’infrastructure. Cela permet d’afficher les redémarrages de service, dont beaucoup sont associés aux déploiements.

## [!UICONTROL Inode usage by mount]

![Utilisation des noeuds par montage](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

Le **[!UICONTROL Inode usage by mount]** image affiche l’utilisation du code par montage pendant la période sélectionnée. Même s’il y a beaucoup de stockage gratuit, si un noeud manque d’inodes, cela indiquera un manque de stockage disponible. La suppression de fichiers (en particulier les petits fichiers) libère de l’espace et rend les informations disponibles.

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![Vue au niveau du processeur sur la chronologie SUPÉRIEURE 2 semaines](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

Le **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** image affiche la vue de niveau vCPU sur la période sélectionnée de plus de deux semaines. Ce cadre examine le nombre de vCPU affectés au [!DNL New Relic] nom de l’application affiché.

## [!UICONTROL vCPU tier view over timeline]

![Vue de niveau processeur sur la chronologie](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

Le **[!UICONTROL vCPU tier view over timeline]** image affiche la vue de niveau vCPU sur la période sélectionnée de plus de 24 heures. Ce cadre examine le nombre de vCPU affectés au [!DNL New Relic] nom de l’application affiché. Il affiche à la fois les tailles et les tailles de cluster.

## [!UICONTROL vCPU tier view over timeline BY NODE]

![Vue de niveau vCPU sur la chronologie par NODE](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

Le **[!UICONTROL vCPU tier view over timeline BY NODE]** image affiche les vues de niveau vCPU sur la période sélectionnée par noeud. Ce cadre est utile pour détecter la perte du ou des noeuds ou lorsque ceux-ci sont mis à niveau ou réduits. La vue de niveau processeur sur la chronologie PAR NODE doit examiner la chronologie MOINS de 24 heures.

## [!UICONTROL Instance details]

![Détails de l’instance](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

Le **[!UICONTROL Instance details]** Le tableau affiche les détails de chaque instance [!DNL New Relic] application.

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![non-responsive-node](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

Le **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** cadre affiche les noeuds non réactifs sur une période donnée.
