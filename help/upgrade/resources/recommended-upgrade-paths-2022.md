---
title: Chemins de mise à niveau recommandés pour 2022
description: Consultez les recommandations pour planifier la mise à niveau d’Adobe Commerce ou de Magento Open Source en 2022.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '936'
ht-degree: 0%

---


# Chemins de mise à niveau recommandés pour 2022

Une mise en oeuvre d’e-commerce est une évolution qui n’est jamais vraiment terminée. Votre entreprise doit garder une longueur d’avance sur les tendances en introduisant les dernières fonctionnalités qui maintiennent vos clients engagés. Au fil du temps, ces fonctionnalités supplémentaires accroissent l’empreinte numérique et la complexité globale de la mise en oeuvre.

Voici quelques-uns des facteurs généraux qui affectent le niveau d’effort nécessaire à votre projet de mise à niveau :

| Complexité technique | Planification et stratégie |
|-----------------------------------------------------------|--------------------------------------------------------------|
| Étendue des personnalisations | La clarté des exigences, les décisions hésitantes et l’élargissement de la portée |
| Nombre d’extensions | Fréquence de mise à niveau |
| Nombre d’intégrations avec des tiers (OMS, ERP) | Votre stratégie de test |
| Codage vers les bonnes pratiques |  |

Voici les chemins recommandés par Adobe Commerce pour préserver la sécurité et les performances de votre site tout au long de 2022.

## Mise à niveau à partir des versions 2.3.0-2.3.6 (option 1)

![](../../assets/upgrade-guide/2.3.0-2.3.6-option1.png)

Vous pouvez passer de n’importe quelle ligne 2.3.x à 2.4.3. Cependant, plus vous passez de temps sans mise à niveau, plus il est difficile d’accéder directement à la version 2.4.3, car la base de code a changé plus.

Par exemple, si vous utilisez la version 2.3.4 publiée en janvier 2020, vous disposez d’une version vieille de presque deux ans. Par conséquent, la base de code de 2.4.3 par rapport à la version 2.3.4 est beaucoup plus élevée. C’est pourquoi Adobe vous recommande d’effectuer une mise à niveau souvent, car le niveau d’effort tend à être encore plus élevé si vous retardez votre mise à niveau pendant une longue période.

Une fois que vous utilisez la version 2.4.3, au premier trimestre, vous pouvez continuer à être sécurisé en prenant la version 2.4.3-p2, ce qui n’est pas très efficace puisqu’il s’agit d’une version de sécurité légère. Ensuite, au troisième trimestre, vous pouvez prendre le correctif complet 2.4.5 et un autre correctif de sécurité léger pour rester sécurisé au quatrième trimestre. Ce chemin nécessite deux mises à niveau de grande ampleur d’ici la fin de 2022.

## Mise à niveau à partir des versions 2.3.0-2.3.6 (option 2)

![](../../assets/upgrade-guide/2.3.0-2.3.6-option2.png)

Vous pouvez également effectuer une mise à niveau de la version 2.3.x directement vers la version 2.4.4 en mars 2022. A partir de la version 2.4.4, vous pouvez ensuite installer le correctif de sécurité légère au troisième trimestre, puis effectuer la mise à niveau vers la version 2.4.5-p1 du quatrième trimestre, qui inclut toutes les mises à jour de la version 2.4.5 et les correctifs de sécurité supplémentaires.

Considérations clés lors du choix entre ces deux options :

| Option 1 : Mise à niveau vers la version 2.4.3-p1 ou -p2 | Option 2 : Mise à niveau vers la version 2.4.4 ou 2.4.4-p1 |
|--------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| Nécessite 2 mises à niveau significatives avant fin 2022 pour rester en sécurité, conforme PCI et recevoir une assistance qualité | Nécessite 1 mise à niveau importante et 1 mise à niveau à faible niveau d’effort moyen avant la fin de 2022 pour rester sécurisé, conforme PCI et recevoir une assistance qualité |
| Permet d’accéder plus tôt à une version prise en charge et compatible PCI | Faire face à une fenêtre plus longue jusqu’à ce que vous accédiez à une version prise en charge et compatible PCI, puisque la ligne 2.3 atteint la fin de vie en avril 2022 |
| Minutage : peut retarder le passage à une nouvelle version de PHP jusqu’à plus tard dans l’année (août). | Minutage : peut commencer à passer à une nouvelle version de PHP plus tôt dans l’année (mars). |

## Mise à niveau à partir de la version 2.3.7 (option 1)

![](../../assets/upgrade-guide/2.3.7-option1.png)

Comme vous utilisez la dernière version 2.3.7, vous êtes en ligne d’obtenir uniquement des versions de sécurité. Au premier trimestre de 2022, Adobe publie la dernière version de 2.3, qui est 2.3.7-p3, ainsi qu’une version de sécurité (2.4.3-p2) et une version complète (2.4.4).

Votre première option serait de prendre la version 2.3.7-p3 et d&#39;obtenir les derniers correctifs de sécurité. Ensuite, en août, vous pourriez prendre la version 2.4.5. Enfin, au 4e trimestre, vous pouvez utiliser la version de sécurité légère basée sur la version 2.4.5 complète. Dans ce scénario, vous resterez sur une version de fin de vie pendant quelques mois jusqu’à ce que vous preniez la version 2.4.5. Toutefois, la version 2.3.x n’offre actuellement pas de prise en charge de la qualité et vous aurez corrigés les vulnérabilités de sécurité les plus récentes.

## Mise à niveau à partir de la version 2.3.7 (option 2)

![](../../assets/upgrade-guide/2.3.7-option2.png)

Votre deuxième option consiste à utiliser la version 2.3.7-p3 pour obtenir rapidement les derniers correctifs de sécurité, puisque les correctifs de sécurité pour votre ligne actuelle ne font pas beaucoup d’efforts pour implémenter, vous pouvez lancer la mise à niveau vers la version 2.4.4.

En août, vous pouvez prendre la version 2.4.4-p1, qui serait une version de sécurité légère, puis au quatrième trimestre la version 2.4.5-p1, qui inclut toutes les mises à jour incluses dans la version 2.4.5 et les dernières versions de sécurité.

Vous pouvez également passer de 2.3.7-p3 à 2.4.4-p1, mais notez que la version 2.4.4-p1 est un &quot;effet élévateur lourd&quot; puisque vous obtenez essentiellement toutes les mises à jour incluses dans la version 2.4.4 et les mises à jour de sécurité dans la version 2.4.4-p1. C&#39;est à vous et à votre équipe de décider si vous souhaitez démarrer cet effet élévateur plus lourd vers la ligne 2.4.4 en mars ou en août.

Considérations clés lors du choix entre ces deux options :

| Option 1 : Mise à niveau vers 2.3.7-p3 puis 2.4.5 | Option 2 : Mise à niveau vers 2.3.7-p3 puis 2.4.4 |
|--------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| Recevez d’abord les dernières mises à jour de sécurité avec un correctif de sécurité peu coûteux | Recevez d’abord les dernières mises à jour de sécurité avec un correctif de sécurité peu coûteux |
| Nécessite 1 mise à niveau importante avant fin 2022 pour rester sécurisé, conforme PCI et recevoir une assistance qualité | Nécessite 1 mise à niveau importante et 1 mise à niveau à faible niveau d’effort moyen avant la fin de 2022 pour rester sécurisé, conforme PCI et recevoir une assistance qualité |
| Affichez une fenêtre plus longue jusqu’à ce que vous accédiez à une version prise en charge et compatible PCI lorsque la ligne 2.3 atteint la fin de service en avril. | Minutage : peut commencer à passer à une nouvelle version de PHP plus tôt dans l’année (mars). |
| Remarques concernant le minutage : peut retarder la mise à niveau des efforts plus importants jusqu’en août | Remarques concernant le minutage : peut commencer une mise à niveau plus poussée en mars, puis effectuer une mise à niveau vers un niveau vers un niveau vers un bas niveau moyen en octobre. |

## Mise à niveau de la version 2.4.0-2.4.2

![](../../assets/upgrade-guide/2.4.0-2.4.2.png)

Puisque vous utilisez la version 2.4.0-2.4.2, nous vous recommandons de passer à la version 2.4.4 au premier trimestre. Il s’agit d’un effort relativement important dû aux changements de la version 2.4.4 provoqués par le passage à la version 8.1 de PHP. Toutefois, les autres mises à niveau de l’année sont moins nombreuses, vous n’avez donc qu’à effectuer un upgrade de niveau supérieur en 2022.

## Mise à niveau à partir de la version 2.4.3

![](../../assets/upgrade-guide/2.4.3.png)

Puisque vous utilisez la version 2.4.3, prendre 2.4.3-p2 au 1er trimestre serait le moins gros effort. Ensuite, en août, vous pourriez prendre la version 2.4.5. Enfin, au 4e trimestre, vous pouvez utiliser la version de sécurité légère basée sur la version 2.4.5 complète. Dans ce scénario, vous n’effectuez qu’un upgrade d’effort de niveau supérieur en 2022.
