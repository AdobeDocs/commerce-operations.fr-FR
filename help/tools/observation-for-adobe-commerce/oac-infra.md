---
title: Onglet  [!DNL Infra]
description: L’onglet  [!DNL Infra]  isole les problèmes et les causes des problèmes d’infrastructure.
exl-id: 45f24177-3264-4848-99bc-951be32c1f7b
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# Onglet [!DNL Infra]

L’onglet **[!DNL Infra]** isole les problèmes et les causes des problèmes d’infrastructure. Vous trouverez plus loin la description des cadres que vous pouvez voir dans l’onglet .

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![Alertes de service](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

Le graphique **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** montre les alertes de service collectées par l’agent d’infrastructure [!DNL New Relic]. Cela permet d’afficher les redémarrages de service, dont beaucoup sont associés aux déploiements.

## [!UICONTROL Inode usage by mount]

![Utilisation des noeuds par le montage](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

L’image **[!UICONTROL Inode usage by mount]** montre l’utilisation de [!DNL inode] par montage sur la période sélectionnée. Même s’il peut y avoir beaucoup de espace de stockage libre, si un noeud est à court de [!DNL inodes], il affichera un manque de stockage disponible. La suppression de fichiers (en particulier les petits fichiers) libère de l’espace et rend [!DNL inodes] disponible.

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![Vue de niveau vCPU sur la chronologie SUPÉRIEURE 2 semaines](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

L’image **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** affiche la vue de niveau vCPU sur la période sélectionnée de plus de deux semaines. Ce cadre examine le nombre de vCPU affectés au nom d’application [!DNL New Relic] affiché.

## [!UICONTROL vCPU tier view over timeline]

![vue de niveau vCPU sur la chronologie](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

L’image **[!UICONTROL vCPU tier view over timeline]** affiche la vue de niveau vCPU pendant la période sélectionnée de plus de 24 heures. Ce cadre examine le nombre de vCPU affectés au nom d’application [!DNL New Relic] affiché. Il affiche à la fois les tailles et les tailles de cluster.

## [!UICONTROL vCPU tier view over timeline BY NODE]

![Vue de niveau vCPU sur la chronologie par NODE](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

L’image **[!UICONTROL vCPU tier view over timeline BY NODE]** affiche les vues de niveau vCPU sur la période sélectionnée par noeud. Ce cadre est utile pour détecter la perte du ou des noeuds ou lorsque ceux-ci sont mis à niveau ou réduits. La vue de niveau processeur sur la chronologie PAR NODE doit examiner la chronologie MOINS de 24 heures.

## [!UICONTROL Instance details]

![Détails de l’instance](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

La table **[!UICONTROL Instance details]** affiche les détails de chaque instance de chaque application [!DNL New Relic].

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![non-responsive-node](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

L’image **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** affiche les noeuds non réactifs sur une période donnée.
