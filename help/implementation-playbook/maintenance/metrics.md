---
title: Mesures d’assistance
description: Surveillez les efforts d’assistance et de maintenance pour votre mise en oeuvre Adobe Commerce à l’aide de mesures courantes.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---


# Mesures d’assistance

Le diagramme suivant affiche les mesures/IPC standard collectés et signalés pour les fonctions L1 :

![Diagramme affichant les mesures SLA](../../assets/playbooks/sla-metrics.svg)

La mesure et la création de rapports des services L2 (améliorations et services facultatifs) sont similaires aux projets de développement. Les performances et la progression des équipes L2 sont mesurées par des mesures telles que la vitesse, la qualité du code, l’efficacité des tests et la productivité.

| Mesure des performances clés | Unité de mesure | Mesures rapportées |
|------------------------------|---------------------|------------------------------------------------------------------------------------|
| Vitesse | Nombre | Non. de points d&#39;histoire que l&#39;équipe a pu livrer pour le sprint |
| Efficacité de l’engagement Sprint | Pourcentage | Nombre total of Story Points validés ou délivrés pour un tirage |
| Densité descendante | Nombre | Graphique (rapport, effectue le suivi de la fin du travail tout au long du sprint) |
| Qualité du code | Nombres, pourcentage | Complexité, LoC, violations, couverture du code pour le sprint |
| La volatilité des exigences | Nombre | Nombre d’exigences de changement/nombre total d’exigences pour le sprint |
| Densité des défauts | Pourcentage | [Non. of valid Defects found/Total No .of Test case execution]*100 for the sprint |
| Efficacité des tests | Pourcentage | [Défauts valides levés/(Défauts valides surmontés + défauts rejetés)]*100 pour le sprint |
| Productivité | Nombre (tendance) | Points d’article délivrés par sprint/capacité |