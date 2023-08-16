---
title: La variable [!DNL Infra] tab
description: La variable [!DNL Infra] permet d’isoler les problèmes et les causes des problèmes d’infrastructure.
exl-id: 45f24177-3264-4848-99bc-951be32c1f7b
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# La variable [!DNL Infra] tab

La variable **[!DNL Infra]** permet d’isoler les problèmes et les causes des problèmes d’infrastructure. Vous trouverez plus loin la description des cadres que vous pouvez voir dans l’onglet .

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![Alertes de service](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

La variable **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** Le graphique affiche les alertes de service collectées par la variable [!DNL New Relic] agent d’infrastructure. Cela permet d’afficher les redémarrages de service, dont beaucoup sont associés aux déploiements.

## [!UICONTROL Inode usage by mount]

![Utilisation des noeuds par montage](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

La variable **[!UICONTROL Inode usage by mount]** affichage des images [!DNL inode] utilisation par montage pendant la période sélectionnée. Même s’il peut y avoir beaucoup de stockage gratuit, si un noeud est à court de [!DNL inodes], cela indique un manque de stockage disponible. La suppression des fichiers (en particulier les petits fichiers) libère de l’espace et crée des [!DNL inodes] disponible.

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![Vue au niveau du processeur sur la chronologie SUPÉRIEURE 2 semaines](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

La variable **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** image affiche la vue de niveau vCPU sur la période sélectionnée de plus de deux semaines. Ce cadre examine le nombre de vCPU affectés au [!DNL New Relic] nom de l’application affiché.

## [!UICONTROL vCPU tier view over timeline]

![Vue de niveau processeur sur la chronologie](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

La variable **[!UICONTROL vCPU tier view over timeline]** image affiche la vue de niveau vCPU sur la période sélectionnée de plus de 24 heures. Ce cadre examine le nombre de vCPU affectés au [!DNL New Relic] nom de l’application affiché. Il affiche à la fois les tailles et les tailles de cluster.

## [!UICONTROL vCPU tier view over timeline BY NODE]

![Vue de niveau processeur sur la chronologie par NODE](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

La variable **[!UICONTROL vCPU tier view over timeline BY NODE]** image affiche les vues de niveau vCPU sur la période sélectionnée par noeud. Ce cadre est utile pour détecter la perte du ou des noeuds ou lorsque ceux-ci sont mis à niveau ou réduits. La vue de niveau processeur sur la chronologie PAR NODE doit examiner la chronologie MOINS de 24 heures.

## [!UICONTROL Instance details]

![Détails de l’instance](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

La variable **[!UICONTROL Instance details]** Le tableau affiche les détails de chaque instance [!DNL New Relic] application.

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![non-responsive-node](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

La variable **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** cadre affiche les noeuds non réactifs sur une période donnée.
