---
title: Bonnes pratiques
description: Appliquez les bonnes pratiques recommandées par Adobe pour gérer le processus de mise à niveau de vos projets Adobe Commerce.
feature: Upgrade, Best Practices
exl-id: 53c505a3-8b99-4fc3-b1b4-f2f75208a51b
source-git-commit: 6b3afb93770c1d976dd975a484070e0aee730a98
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 0%

---

# Bonnes pratiques de mise à niveau

Cette rubrique répertorie les actions à entreprendre pour gérer la complexité de la mise à niveau des projets Adobe Commerce. Votre équipe doit réfléchir aux mises à niveau à partir du moment où le développement de votre projet commence, et jusqu’à la fin de chaque version. En suivant ces bonnes pratiques, le processus de mise à niveau sera beaucoup plus facile, plus rapide et moins coûteux.

>[!TIP]
>
>Ces recommandations sont basées sur les bonnes pratiques, étayées par des preuves de leur impact et de leur efficacité provenant de partenaires, de commerçants, d’experts d’Adobe et de la communauté.

## Quel est l’impact d’une mise à niveau ?

Il est important de comprendre les variables qui déterminent la complexité d’une mise à niveau. Vous devez tenir compte de ces variables au début de chaque projet, et pas seulement au moment de la mise à niveau. Le développement d’un projet est essentiel pour garantir que les futures mises à niveau se dérouleront sans problème et que vous pourrez contrôler les efforts nécessaires pour les effectuer.

Le niveau d’effort pour mettre à niveau votre instance Adobe Commerce dépend des facteurs suivants :

- **Comment avez-vous construit votre site ?** La quantité de travail personnalisé et le nombre de modules tiers installés affectent considérablement la complexité d’une mise à niveau. La qualité du travail et des modules personnalisés peut déterminer le bon déroulement d’une mise à niveau.

- **Êtes-vous en train d’ignorer plusieurs versions ?** l’omission de versions rend la prochaine mise à niveau plus complexe, la mise à niveau à partir des versions ultérieures rend le processus plus facile et moins coûteux.

- **Quel type de mise à niveau effectuez-vous ?** Une mise à niveau vers une version mineure (de 2.3.x à 2.4.0, par exemple) est plus étendue qu’une mise à niveau entre les versions de correctif (de 2.4.2 à 2.4.3, par exemple). Les mises à niveau de sécurité sont le type le plus facile à implémenter.

## Bonnes pratiques pour la planification des mises à niveau

Si vous travaillez sur un projet déjà en production, les mises à niveau sont l’occasion d’améliorer la qualité de votre code et de vos personnalisations, et d’optimiser les mises à niveau ultérieures. Le temps que vous investissez aujourd&#39;hui est du temps gagné à long terme.

Si vous gérez plusieurs sites pour différents commerçants, la meilleure approche consiste à disposer d’une instance de base avec les principales fonctionnalités et personnalisations que vous utilisez normalement. Utilisez cette instance de base comme site de test pour effectuer une mise à niveau, puis exécutez-la sur d’autres. Cette pratique vous offre la possibilité de réutiliser des modules personnalisés pour différents clients et de simplifier les mises à niveau entre les projets.

Si votre projet est actif, nous vous suggérons d’effectuer un audit pour déterminer sa qualité et comprendre comment l’améliorer afin d’optimiser les mises à niveau.

### Développement avec les mises à niveau en tête

Dès que vous commencez à travailler sur un projet, vous devez tenir compte de l’impact de votre travail actuel sur les futures mises à niveau. Respectez toujours les bonnes pratiques de développement d’Adobe Commerce, comme décrit ici :

- [&#x200B; Bonnes pratiques de développement &#x200B;](https://developer.adobe.com/commerce/php/best-practices/)
- [Normes de codage](https://developer.adobe.com/commerce/php/coding-standards/)

Commencez à adopter la plateforme d’extensibilité d’Adobe Commerce, si vous ne l’avez pas déjà fait. La plateforme vous permet de personnaliser efficacement les processus, d’intégrer les systèmes et de déployer de nouvelles fonctionnalités tout en conservant une évolutivité de type SaaS. Ses fonctionnalités sont les suivantes :

- **Extensibilité de l’interface utilisateur**. Étendez et faites évoluer votre storefront indépendamment de votre serveur principal et du middleware en utilisant [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/).

- **Extensibilité de l’API**. Utilisez [GraphQL](https://developer.adobe.com/commerce/webapi/graphql/index.html) pour étendre la couche API Web en faisant évoluer le modèle de données graphique et en exécutant les fonctions lambda directement à partir de la couche graphique.

- **Intergiciel et services Adobe I/O**. Connectez vos systèmes à Adobe Commerce à l’aide du middleware Adobe et d’une suite de connexions d’applications reposant sur [Adobe I/O](https://www.adobe.io/). En outre, vous pouvez étendre les fonctionnalités de base de Platform en remplaçant le comportement par défaut par votre propre logique commerciale qui s’exécute sur Adobe I/O.

### Planification des mises à niveau

Alors que nous étendons continuellement les fonctionnalités d’Adobe Commerce, il est essentiel que vous développiez sur la dernière version disponible et définissiez une stratégie de mise à niveau dans vos plans de projet. Cela vous aide à rester sécurisé, conforme et à jour sur les dernières améliorations qui vous permettent d&#39;augmenter vos ventes plus rapidement, d&#39;opérer plus efficacement et de devancer vos concurrents, maintenant et à l&#39;avenir.

Pour vous aider à planifier et à budgéter les mises à niveau, vous devez suivre notre [calendrier des versions](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule). Planifiez les tâches de mise à niveau dans la liste d’attente de votre équipe à l’avance. Visez à terminer ce travail avec GA.

- Utilisez la version préliminaire pour en savoir plus sur chaque nouvelle version. La version préliminaire est le code de disponibilité générale qui est disponible pour les commerçants Adobe Commerce et tous les partenaires deux semaines avant la disponibilité générale. Si vous disposez de plusieurs magasins, utilisez la version préliminaire sur votre magasin de base et vérifiez que vos modules et thèmes personnalisés sont compatibles avec celle-ci.

- Consultez la [liste de contrôle du plan de mise à niveau](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/upgrade-checklist) pour Adobe Commerce afin de planifier votre mise à niveau.

- Planifiez les mises à niveau au début de l’année. Vous devez réserver un budget et des ressources pour terminer chaque mise à niveau. N’oubliez pas que la mise à niveau peut varier considérablement d’un projet à l’autre. Utilisez vos expériences et vos connaissances pour créer un plan aussi précis que possible.

- Si vos mises à niveau demandent plus d’efforts que ce que nous décrivons ici, nous vous recommandons d’effectuer un audit de votre projet et d’apporter des ajustements à votre environnement afin de réduire la maintenance à long terme.

### Exécution de mises à niveau

Les mises à niveau doivent être effectuées régulièrement et dans le cadre d’un budget prédéfini. Nous vous recommandons de planifier des mises à niveau préapprouvées au début de l’année afin de vous assurer qu’elles sont planifiées et terminées dans les délais.

Évaluez le travail à effectuer pour la mise à niveau :

- Consultez les [notes de mise à jour](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview) pour comprendre la portée et l’impact de la nouvelle version.

- Utilisez le [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md) pour identifier les problèmes potentiels qui doivent être corrigés dans votre code personnalisé avant d’essayer d’effectuer une mise à niveau vers une version plus récente.

- Si vous utilisez des extensions tierces, validez leur compatibilité avec la version cible vers laquelle vous envisagez d’effectuer la mise à niveau.

### Test après la mise à niveau

Les tests sont la phase d’une mise à niveau qui nécessite le plus de temps. Par conséquent, ce processus doit être aussi automatisé que possible. L’utilisation des outils de test principaux peut vous être bénéfique. Le [&#x200B; Guide de test d’application &#x200B;](https://developer.adobe.com/commerce/testing/guide/) fournit des détails.

Utilisez un environnement d’évaluation pour tester et valider votre mise à niveau avant de passer en production.

Utilisez une **page de maintenance**. La préparation préalable de cette page vous permet de communiquer avec vos clients et clientes, en les informant que du travail est en cours en arrière-plan. Cette page doit être visible pendant quelques minutes, mais en cas de problème, vous devrez peut-être l’utiliser plus longtemps. Disposer du contenu et de la conception appropriés pour votre page de maintenance permet à vos utilisateurs d’obtenir une bonne expérience, même lorsque votre boutique n’est pas disponible.
