---
title: Conclusion
description: Consultez à nouveau les concepts du guide Diffuser des expériences de commerce à l’échelle .
source-git-commit: 1cff7359ddb4caeca6773ff74b92048c89676f12
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# Conclusion

Ce contenu est conçu pour être un guide de haut niveau qui fournit certaines zones à étudier au départ lors de la préparation de votre environnement AEM/CIF/Adobe Commerce pour une charge importante. Il existe de nombreux domaines d’Adobe Commerce, CIF et Fastly qui ne sont pas couverts par le guide ci-dessus et qui nécessiteront des optimisations spécifiques à votre environnement. En outre, le code personnalisé et les modules tiers peuvent avoir des effets sur les temps de réponse qui ne peuvent pas être abordés ici.

Pour atténuer le risque de modifications ou d’introduction de code qui affecteront négativement les temps de réponse de l’utilisateur final AEM/CIF/Adobe Commerce, il faut s’assurer qu’une stratégie de test de performance complète et répétable est mise en place, y compris la définition d’indicateurs de performance clés qui peuvent être mesurés au fil du temps. Les tests de performance doivent être effectués non seulement avant la mise en service, mais également après la mise en service, idéalement avant chaque version majeure ou modification de vos environnements de production afin de mesurer les impacts sur les performances.
