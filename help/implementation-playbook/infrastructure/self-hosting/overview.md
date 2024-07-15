---
title: Présentation de l’auto-hébergement
description: Découvrez les bonnes pratiques d’auto-hébergement à prendre en compte. Les thèmes vont de la sécurité aux catastrophes, en passant par la reprise. Ces rubriques sont ici pour aider une société qui a décidé d’héberger sa propre version d’Adobe Commerce. Les éléments présentés ne sont pas tous inclusifs, mais devraient fournir un large éventail de concepts pour promouvoir un site web sécurisé, stable et résilient.
landing-page-description: Découvrez certains concepts et éléments à prendre en compte lors de l’hébergement d’Adobe Commerce par vous-même.
short-description: Découvrez vous-même les stratégies et les concepts d’hébergement d’Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 1c63d082-c6fb-4795-81cd-75d097c03e6b
feature: Install
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---

# Présentation d’Adobe Commerce auto-hébergé

Lorsque vous envisagez de passer à une plateforme de commerce électronique telle qu’Adobe Commerce, vous avez le luxe d’avoir des options. Toutefois, ces options comportent des coûts, des risques et des passifs supplémentaires à prendre en compte. L’hébergement d’un site Commerce peut être effectué à l’aide d’une solution empaquetée, telle que [Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}, où l’infrastructure, les serveurs, les e-mails, les certificats SSL et bien d’autres sont préconfigurés et prêts à l’emploi. Trouver une bonne solution d’hébergement, telle qu’Adobe Commerce sur l’infrastructure cloud, facilite l’ensemble du processus. Il existe des raisons impérieuses d’auto-hébergement de votre site Commerce. Les pages d’accompagnement contiennent de nombreuses rubriques qui fournissent des informations et des conseils sur les services, les techniques et les concepts fournis par l’auto-hébergement. Les informations ne sont pas exhaustives et il n’est pas prévu que vous mettiez en oeuvre chaque suggestion. Toutefois, ces articles peuvent vous aider à comprendre les idées et les concepts qui peuvent rendre l’auto-hébergement Adobe Commerce aussi stable et sécurisé que possible.

Lorsque vous n’utilisez pas Adobe Commerce sur l’infrastructure cloud, les termes utilisés sont auto-hébergement ou on-premise, ou même on-premise est utilisé. Sur site ne signifie pas seulement dans un centre de données d’un bâtiment appartenant à une entreprise. Ce terme représente tout ce qui n’est pas géré par Adobe Commerce sur son infrastructure. Il existe des sociétés d’hébergement qui prennent en charge Adobe Commerce, elles sont également considérées comme auto-hébergement ou on-premise.

En ce qui concerne Adobe Commerce et Magento Open Source, la plupart des conseils et astuces fournis fonctionnent pour chaque version. Bien qu&#39;il ne le dise pas directement, on s&#39;attend à ce qu&#39;il s&#39;applique aux deux. Dans cette rubrique sur les options d’auto-hébergement pour Adobe Commerce, les deux versions sont prises en compte. Enfin, la plupart des rubriques sont pertinentes pour [Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"} en tant que fournisseur d’hébergement.

## Jeu de niveaux de terminologie

Les termes suivants sont couramment utilisés dans les articles Experience League, lorsque vous parlez à l’équipe DevOps et travaillez avec l’assistance de la société :

* **DevOps** est un terme utilisé pour décrire les équipes qui gèrent la configuration du serveur, la configuration, la gestion, les certificats SSL et tout le reste sur les serveurs et services réels utilisés pour exécuter un site Adobe Commerce. Ce terme permet de désigner le moment où la responsabilité d’un développeur se termine généralement et où commence le triage et le support d’une équipe d’infrastructure.

* **Les concepts de sécurité** englobent plusieurs rubriques et considérations pour établir le code base d’Adobe Commerce, les fichiers et le système de fichiers sur les serveurs, ainsi que toutes les configurations ou mises à jour qui réduisent la surface d’attaque pour de nombreux modèles d’exploitation connus.

* **Outils de surveillance** couvre quelques outils et services existants qui surveillent les sites web Adobe Commerce. Ces outils peuvent parfois fournir des conseils sur la façon d’améliorer les choses, ou de découvrir des problèmes et des vulnérabilités de sécurité.

* **Disaster Recovery** vous aide à fournir quelques concepts et remarques concernant l’événement malheureux d’un projet endommagé ou exploité.

* **Des conseils sur les performances** fournissent des conseils et des conseils pour rendre l’application Adobe Commerce aussi performante que possible.

* **Mauvais acteur** est le terme utilisé pour désigner une personne ou une équipe qui tente de faire quelque chose de malveillant ou d’non autorisé. Il ne se limite pas à l’application commerciale, mais s’étend également à l’infrastructure ou tout composant lié au site web.

* **Le pare-feu d’applications web** (WAF) vous aide à regarder chaque en-tête de demande vers l’application de commerce et bloque les modèles et les exploits connus. Souvent, une méthode WAF est utilisée conjointement avec des filtres et des règles personnalisés pour aider à gérer les attaques DOS.

* **Déni de service distribué** (DDoS) est une méthode d’attaque pour forcer les serveurs exécutant le site web à être consommés avec de fausses demandes avec un volume suffisant pour ne plus pouvoir répondre à une demande légitime.

## Et après ?

Ces rubriques ne sont pas dans un ordre ou une séquence spécifique. Ils sont censés fournir des points de discussion à un ingénieur DevOps, à l’architecte Commerce et à toute personne impliquée dans la prise de cette importante décision sur l’emplacement et la manière d’héberger Adobe Commerce.

{{$include /help/_includes/hosting-related-links.md}}
