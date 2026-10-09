---
title: Onglet [!DNL Infra]
description: L’onglet [!DNL Infra] isole les problèmes et les causes des problèmes d’infrastructure.
exl-id: 45f24177-3264-4848-99bc-951be32c1f7b
feature: Configuration, Observability
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%
---
# Onglet [!DNL Infra]

L’onglet **[!DNL Infra]** isole les problèmes et les causes des problèmes d’infrastructure. Vous trouverez plus loin la description des images visibles dans l’onglet.

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![&#x200B; Alertes de service &#x200B;](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

Le graphique **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** affiche les alertes de service collectées par l’agent d’infrastructure [!DNL New Relic]. Elle affiche les redémarrages du service, dont beaucoup sont associés aux déploiements.

## [!UICONTROL Inode usage by mount]

![Utilisation des nœuds par montage](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

L’image **[!UICONTROL Inode usage by mount]** affiche [!DNL inode] utilisation par montage sur la période sélectionnée. Même s’il peut y avoir beaucoup de stockage disponible, si un nœud est à court de [!DNL inodes], il affichera un manque de stockage disponible. La suppression de fichiers (en particulier les petits fichiers) libère de l’espace et [!DNL inodes] rend disponible.

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![vue de niveau processeur virtuel sur la chronologie SUPÉRIEURE à 2 semaines](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

La période **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** affiche la vue de niveau processeur virtuel sur la période sélectionnée de plus de deux semaines. Cette image examine le nombre de vCPU affectées au nom d’application [!DNL New Relic] affiché.

## [!UICONTROL vCPU tier view over timeline]

![vue de niveau vCPU sur la chronologie](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

L’image **[!UICONTROL vCPU tier view over timeline]** affiche la vue de niveau processeur virtuel sur la période sélectionnée de plus de 24 heures. Cette image examine le nombre de vCPU affectées au nom d’application [!DNL New Relic] affiché. Elle affiche à la fois les tailles supérieures et inférieures des clusters.

## [!UICONTROL vCPU tier view over timeline BY NODE]

![vue de niveau processeur virtuel sur la chronologie par NODE](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

L’image **[!UICONTROL vCPU tier view over timeline BY NODE]** affiche les vues de niveau processeur virtuel sur la période sélectionnée par nœud. Cette image est utile pour détecter la perte de nœud(s) ou lorsque les nœuds sont surdimensionnés ou réduits. La vue au niveau du processeur virtuel sur la chronologie BY NODE doit afficher une chronologie INFÉRIEURE à 24 heures.

## [!UICONTROL Instance details]

![Détails de l’instance](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

Le tableau **[!UICONTROL Instance details]** affiche les détails des instances de chaque application [!DNL New Relic].

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![nœud-non-réactif](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

L’image **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** affiche les nœuds qui ne répondent pas sur une période donnée.
