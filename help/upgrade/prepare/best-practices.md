---
title: Bonnes pratiques
description: Utilisez les bonnes pratiques recommandées par l’Adobe pour gérer le processus de mise à niveau de vos projets Adobe Commerce et Magento Open Source.
feature: Upgrade, Best Practices
exl-id: 53c505a3-8b99-4fc3-b1b4-f2f75208a51b
source-git-commit: 012cba58b336b032b1c911539008c1fb961c2e07
workflow-type: tm+mt
source-wordcount: '1089'
ht-degree: 0%

---

# Bonnes pratiques relatives à la mise à niveau

Cette rubrique répertorie les actions que vous devez entreprendre pour gérer la complexité de la mise à niveau des projets Adobe Commerce et Magento Open Source. Votre équipe doit réfléchir aux mises à niveau dès le début du développement de votre projet et continuer à travailler sur chaque version. En suivant ces bonnes pratiques, le processus de mise à niveau sera beaucoup plus facile, plus rapide et moins coûteux.

>[!TIP]
>
>Ces recommandations sont fondées sur les bonnes pratiques fondées sur les preuves de son impact et de son efficacité de la part des partenaires, des commerçants, des experts en Adobes et de la communauté.

## Quel impact a une mise à niveau ?

Il est important de comprendre les variables qui déterminent la complexité d’une mise à niveau. Vous devez tenir compte de ces variables au début de chaque projet, et pas seulement au moment de la mise à niveau. Le développement d’un projet est essentiel pour garantir que les futures mises à niveau se dérouleront sans problème et que vous pourrez contrôler les efforts nécessaires pour les terminer.

Le niveau d’effort nécessaire à la mise à niveau de votre instance Adobe Commerce dépend des facteurs suivants :

- **Comment avez-vous créé votre site ?** La quantité de travail personnalisé et le nombre de modules tiers installés affectent fortement la complexité d’une mise à niveau. La qualité du travail et des modules personnalisés peut déterminer si une mise à niveau se déroule sans problème.

- **Ignorez-vous plusieurs versions ?** Ignorer les versions rend la mise à niveau suivante plus complexe, la mise à niveau à partir de versions conséquentes rend le processus plus facile et moins coûteux.

- **Quel type de mise à niveau effectuez-vous ?** Une mise à niveau vers une version mineure (de 2.3.x à 2.4.0, par exemple) est plus étendue qu’une mise à niveau entre les versions de correctif (de 2.4.2 à 2.4.3, par exemple). Les mises à niveau de sécurité sont le type le plus facile à mettre en oeuvre.

## Bonnes pratiques pour la planification des mises à niveau

Si vous travaillez sur un projet déjà en production, les mises à niveau sont l’occasion d’améliorer la qualité de votre code et de vos personnalisations et d’optimiser les mises à niveau futures. Le temps que vous investissez aujourd&#39;hui est du temps économisé à long terme.

Si vous gérez plusieurs sites pour différents marchands, la meilleure approche consiste à disposer d’une instance de base avec les fonctionnalités et personnalisations principales que vous utilisez normalement. Utilisez cette instance de base comme site de test pour effectuer une mise à niveau, puis effectuez-la sur d’autres sites. Cette pratique offre la possibilité de réutiliser des modules personnalisés pour différents clients et de simplifier les mises à niveau entre les projets.

Si votre projet est actif, nous vous suggérons d’exécuter un audit afin de déterminer sa qualité et de comprendre comment l’améliorer pour rendre les mises à niveau plus efficaces.

### Développement avec des mises à niveau à l’esprit

Dès que vous commencez à travailler sur un projet, vous devez examiner l’impact de vos travaux actuels sur les futures mises à niveau. Suivez toujours les bonnes pratiques de développement d’Adobe Commerce comme décrit ici :

- [Bonnes pratiques de développement](https://developer.adobe.com/commerce/php/best-practices/)
- [Normes de codage](https://developer.adobe.com/commerce/php/coding-standards/)

Commencez à adopter la plateforme d’extensibilité d’Adobe Commerce, si ce n’est pas déjà fait. La plate-forme vous permet de personnaliser efficacement les processus, d’intégrer les systèmes et de déployer de nouvelles fonctionnalités tout en maintenant une mise à niveau similaire à SaaS. Ses fonctionnalités sont les suivantes :

- **Extensibilité de l’interface utilisateur**. Étendez et développez votre storefront indépendamment de votre backend et de votre middleware à l’aide de [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/).

- **Extensibilité des API**. Utilisation [GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/index.html) pour étendre la couche d’API Web en adaptant le modèle de données graphique et en exécutant des fonctions lambda directement à partir de la couche graphique.

- **Adobe I/O de middleware et services**. Connectez vos systèmes à Adobe Commerce à l’aide du middleware d’Adobe et d’une suite de connexions d’applications reposant sur [Adobe I/O](https://www.adobe.io/). En outre, vous pouvez étendre les fonctionnalités de base de la plateforme en remplaçant le comportement par défaut par votre propre logique métier qui s’exécute sur Adobe I/O.

### Planification des mises à niveau

Alors que nous développons continuellement les fonctionnalités d’Adobe Commerce, il est essentiel que vous développiez la dernière version disponible et définissiez une stratégie de mise à niveau dans vos plans de projet. Cela vous permet de rester sécurisé, conforme et à jour par rapport aux dernières améliorations qui vous permettent d’augmenter plus rapidement les ventes, de fonctionner plus efficacement et de garder l’avance sur votre concurrence maintenant et à l’avenir.

Pour vous aider à planifier et à budgéter les mises à niveau, vous devez surveiller nos [calendrier de publication](https://devdocs.magento.com/release). Planifiez à l’avance les tâches de mise à niveau dans le délai d’attente de votre équipe. Visez à terminer ce travail avec GA.

- Utilisez la version préliminaire pour en savoir plus sur chaque nouvelle version. Une version préliminaire est un code de disponibilité générale disponible pour les marchands Adobe Commerce et tous les partenaires deux semaines avant la disponibilité générale. Si vous disposez de plusieurs magasins, utilisez la version préliminaire de votre magasin de base et vérifiez que vos modules et thèmes personnalisés sont compatibles avec celui-ci.

- Consultez la section [Liste de contrôle du plan de mise à niveau](https://support.magento.com/hc/en-us/articles/360057968951) pour Adobe Commerce afin de vous aider à planifier votre mise à niveau.

- Planifiez les upgrades au début de l&#39;année. Vous devez réserver un budget et des ressources pour terminer chaque upgrade. N’oubliez pas que l’effort de mise à niveau peut varier considérablement d’un projet à l’autre. Utilisez vos expériences et vos connaissances pour rendre un plan aussi précis que possible.

- Si vos mises à niveau font plus d’efforts que ce que nous décrivons ici, nous vous recommandons de vérifier votre projet et d’apporter des ajustements à votre environnement afin de réduire la maintenance à long terme.

### Mise à niveau

Les mises à niveau doivent être effectuées régulièrement et sous la forme d’un budget prédéfini. Nous vous recommandons de planifier les mises à niveau prévalidées au début de l’année afin de vous assurer que les mises à niveau sont planifiées et terminées à temps.

Évaluer le travail à effectuer pour la mise à niveau :

- Consultez la section [notes de mise à jour](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) pour comprendre la portée et l’impact de la nouvelle version.

- Utilisez la variable [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md) pour identifier les problèmes potentiels qui doivent être résolus dans votre code personnalisé avant de tenter une mise à niveau vers une version plus récente.

- Si vous utilisez des extensions tierces, validez leur compatibilité avec la version cible vers laquelle vous envisagez d’effectuer la mise à niveau.

### Test après la mise à niveau

Le test est la phase de mise à niveau qui nécessite le plus de temps. Par conséquent, ce processus doit être aussi automatisé que possible. Vous pouvez bénéficier de l’utilisation des outils de test de base. Le [Guide de test d’application](https://developer.adobe.com/commerce/testing/guide/) fournit des détails.

Utilisez un environnement d’évaluation pour tester et valider votre mise à niveau avant de passer en production.

Utilisez un **page de maintenance**. La préparation préalable de cette page vous permet de communiquer avec vos clients, les informant que le travail est en cours en arrière-plan. Cette page doit être visible pendant quelques minutes, mais en cas de problème, vous devrez peut-être l’utiliser plus longtemps. Disposer du contenu et de la conception appropriés pour votre page de maintenance offre aux utilisateurs une expérience optimale, même lorsque votre boutique n’est pas disponible.
