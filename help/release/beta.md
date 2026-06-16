---
title: Versions de Beta
description: Découvrez les versions bêta d’Adobe Commerce et comment y participer.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
badgePaas: label="PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets Adobe Commerce on Cloud (infrastructure PaaS gérée par Adobe) et aux projets On-premise."
badgeSaas: label="SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets Adobe Commerce as a Cloud Service et Adobe Commerce Optimizer (infrastructure SaaS gérée par Adobe)."
source-git-commit: bf0f269900468870a1da7b5360548d49e009097c
workflow-type: tm+mt
source-wordcount: '1400'
ht-degree: 0%

---

# Versions bêta d’Adobe Commerce

Les programmes Beta pour les [solutions de produits Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions) permettent aux commerçants d’accéder aux fonctionnalités et au code de version préliminaire, de faire part de leurs commentaires et de guider l’avenir d’Adobe Commerce. Il existe deux types de programmes bêta :

- Beta publique : un programme bêta public est disponible pour tous les clients et partenaires d’Adobe Commerce
- Private Beta : pour participer à un programme Private Beta, une approbation basée sur des critères de qualification peut être nécessaire

>[!IMPORTANT]
>
>**Clause de non-responsabilité**<br/>
Les versions de >Beta incluent des fonctionnalités de version préliminaire et du code pouvant contenir des défauts et sont fournies « EN L’ÉTAT » sans garantie d’aucune sorte. Adobe dispose de la seule discrétion nécessaire pour rendre les versions bêta généralement disponibles. Adobe n’a aucune obligation de tenir à jour, corriger, mettre à jour, modifier, prendre en charge (via les services d’assistance Adobe ou autre), ou de diffuser ces versions bêta à une date spécifique. Si une version Beta est disponible, elle peut être soumise à des conditions générales supplémentaires, y compris les frais applicables. Les versions de Beta peuvent être modifiées sans préavis, y compris en cas d’interruption. Il est conseillé aux clients d’être prudents et de ne pas se fier, de quelque manière que ce soit, au fonctionnement ou aux performances ininterrompus ou sans erreur des versions bêta.  Par conséquent, toute utilisation des versions bêta s’effectue entièrement aux risques et périls du client.

## Avantages de la participation

L’accès anticipé aux fonctionnalités développées par Adobe permet aux clients et aux partenaires de faire part de leurs commentaires, de façonner le développement des produits et de se préparer à adopter de nouvelles fonctionnalités avant leur disponibilité générale.

## Programmes Beta actuels

Consultez les sections suivantes pour obtenir la liste des programmes bêta actifs.

### Correspondance de recherche et classement (Private Beta)

Adobe améliore la façon dont la découverte de produits classe les résultats de recherche pour les [!DNL Live Search] sur les [!DNL Adobe Commerce] et les [!DNL Adobe Commerce Optimizer]. La mise à jour donne la priorité aux **correspondances exactes et de quasi-expressions**, puis aux correspondances où **tous les termes de requête apparaissent dans le même attribut consultable** et enfin aux correspondances **entre champs** (y compris les comportements qui prennent en charge les suggestions de style de saisie semi-automatique). Ce modèle en couches permet aux requêtes à haute intention de faire apparaître d’abord les produits les plus pertinents tout en renvoyant des alternatives utiles.

Le même modèle de pertinence interagit avec **poids de recherche**, **classement intelligent**, **synonymes** et **règles de marchandisage** (épingler, booster, enterrer). Les vitrines allemandes peuvent utiliser la **décomposition** pour les mots composés, avec la même approche globale de hiérarchisation.

**Principaux avantages**

- Boostez plus fortement les correspondances exactes et proches des expressions (y compris les formes normalisées telles que le singulier et le plural).
- Classement supérieur lorsque tous les mots de requête apparaissent ensemble dans un champ consultable.
- Des attentes plus claires quant à la façon dont les poids, le classement intelligent et les règles manuelles se combinent au moment de la requête.
- Conseils pour valider les requêtes à forte valeur ajoutée et optimiser les règles d’amplification après la modification.

En savoir plus sur la correspondance de recherche et la stratégie de classement dans [Adobe Commerce Optimizer (SaaS)](https://experienceleague.adobe.com/en/docs/commerce/optimizer/manage-results/search-relevance-matching) et [Live Search (PaaS)](https://experienceleague.adobe.com/en/docs/commerce/live-search/live-search-admin/search-relevance-matching).

Pour demander une invitation à cette version bêta privée, envoyez un e-mail à [](mailto:commerce-storefront-services@adobe.com). L’équipe d’Adobe répondra avec les étapes suivantes et les conditions d’éligibilité.

### Filtres de prix recommandés (Beta publique) {#recommendation-price-filters-public-beta}

[!BADGE SaaS uniquement]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets Adobe Commerce as a Cloud Service et Adobe Commerce Optimizer (infrastructure SaaS gérée par Adobe)."}

[!DNL Adobe Commerce Optimizer] ajoute des **filtres de prix** aux recommandations de produits afin que vous puissiez inclure ou exclure des produits recommandés en fonction du prix lorsque vous créez ou modifiez une unité de recommandation. Les filtres utilisent le **prix calculé final** de chaque produit du **catalogue des prix actifs** du storefront, y compris les remises et les promotions de ce catalogue des prix (pas le prix catalogue seul). Les règles de prix affinent le jeu de candidats ; elles ne reclassent pas les produits.

Vous pouvez définir des plages **statiques** avec des valeurs minimales et maximales fixes dans la devise de base de votre magasin ou des règles **dynamiques** sur les pages de détails du produit qui comparent les produits recommandés au **produit actuellement consulté** à l’aide d’opérateurs tels que inférieur ou égal à, supérieur ou égal à, ou dans une plage de valeurs ou de pourcentages du prix d’ancrage. Des filtres dynamiques sont disponibles pour les types de recommandation liés au SKU qui s’exécutent dans le contexte du produit (par exemple, *Affiché ceci* affiché cela et *Plus comme ceci*).

**Principaux avantages**

- Incluez ou excluez des candidats de recommandation par prix à l’aide des règles d’inclusion et d’exclusion de l’étape **Filtrer les produits**.
- Utilisez des fourchettes de prix statiques pour des objectifs de marchandisage fixes (par exemple, des modules complémentaires économiques ou des ventes incitatives).
- Utilisez des règles de prix dynamiques sur la page des détails du produit pour afficher les alternatives à l’intérieur d’une fourchette de prix comparable par rapport au produit affiché.
- Alignez le filtrage sur le prix affiché par les acheteurs, qui est le même prix final du catalogue des prix actifs utilisé pour le filtrage et l’affichage.

Pour en savoir plus, consultez les sections [Filtres de recommandation — Prix](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/recommendations/filters#price) dans le guide destiné aux commerçants et [Configuration des recommandations de produit](https://experienceleague.adobe.com/developer/commerce/storefront/merchants/content-customizations/product-recommendations/) dans le guide de storefront.

Pour partager vos commentaires pendant que vous utilisez cette fonctionnalité bêta, envoyez un e-mail à [](mailto:commerce-storefront-services@adobe.com).

### Service de correctifs de Cloud Automation (Private Beta)

[!BADGE PaaS uniquement]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets Adobe Commerce on Cloud (infrastructure PaaS gérée par Adobe) et aux projets On-premise."}

Le [service d’application de correctifs de Cloud Automation](../tools/caps-tool/intro.md) automatise le processus d’application de correctifs de sécurité isolés à vos environnements [Adobe Commerce sur les infrastructures cloud](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/overview).

En octobre 2025, la version bêta du service de correctifs de Cloud Automation sera ajoutée au tableau de bord de l’outil [Analyse à l’échelle du site](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/dashboard). Ce service prend en charge les administrateurs de projet Commerce grâce à un workflow d’application de correctifs simplifié qui inclut :

- Installation automatisée de correctifs
- Restauration
- Vérification après déploiement.

Ce service garantit que vous pouvez maintenir des environnements sécurisés, stables et mis à jour avec un effort manuel et un risque minimaux.

La version bêta comprend les fonctionnalités suivantes :

- **Automatiser l’installation de correctifs** : simplifiez et automatisez le processus d’application de correctifs aux vulnérabilités critiques dans les environnements.
- **Minimiser les risques** : prévenir les pannes du site grâce aux fonctionnalités de vérification de l’intégrité et de restauration post-déploiement.

>[!NOTE]
>
>Étant donné que le service d&#39;application de correctifs de Cloud Automation applique automatiquement des correctifs de sécurité isolés, vous devez disposer du rôle [Contributeur ou Administrateur de projet](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/user-access) pour l&#39;utiliser.

Pour participer à cette version bêta, remplissez et envoyez le formulaire d’inscription au [Service d’application de correctifs de Cloud Automation - Beta](https://forms.office.com/r/3Wfxj5nPdB).

### Assistant d’IA Productivité des commerçants (Beta publique)

Merchant Productivity AI Assistant est une interface conversationnelle intégrée à Adobe Commerce Admin qui aide les commerçants à effectuer des tâches de routine et à accéder à des informations commerciales à la demande en utilisant un langage naturel. Il permet aux commerçants de gérer les promotions, de mettre à jour les informations du catalogue de produits et de récupérer les données opérationnelles, telles que les commandes récentes ou les promotions actives, directement dans leurs workflows existants. L’assistant fournit également des conseils contextuels pour aider les commerçants à naviguer et à utiliser l’administrateur plus efficacement.

**Principaux avantages**

- Automatisez les tâches de marchandisage courantes, notamment la création de promotions et les mises à jour de métadonnées de catalogue, à l’aide d’instructions en langage naturel.
- Accédez à une assistance et à des conseils contextuels directement dans le workflow Admin.
- Interroger les données de magasin actives à la demande ; par exemple, récupérer les 10 dernières commandes, afficher les promotions actuellement actives ou vérifier l’état de l’inventaire.
- Réduisez le temps consacré aux tâches d’administration répétitives, ce qui permet aux commerçants de se concentrer sur la stratégie et la croissance.

Pour participer à cette version bêta, envoyez un e-mail à [](mailto:commerce-storefront-services@adobe.com).

### Adobe Commerce Foundation (Alpha public/Beta)

[!BADGE PaaS uniquement]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets Adobe Commerce on Cloud (infrastructure PaaS gérée par Adobe) et aux projets On-premise."}

Chaque version alpha et bêta d’Adobe Commerce Foundation comprend toutes les modifications apportées au code principal d’Adobe Commerce à la date de publication prévue, y compris, mais sans s’y limiter, les domaines fonctionnels suivants :

- Derniers correctifs de sécurité
- Améliorations des performances
- Améliorations de GraphQL
- Correctifs de qualité générale
- Contributions de la Communauté
- Modifications requises pour prendre en charge la compatibilité avec les [services ](https://experienceleague.adobe.com/en/docs/commerce/user-guides/home)

#### Convention et planning d’affectation des noms

Adobe publie généralement des correctifs alpha et bêta plusieurs fois par an.

Les packages de version Alpha comportent un suffixe `-alphaX`. Par exemple, les packages de version alpha 2.4.7 d’Adobe Commerce appliquent la convention de nommage suivante :

- `2.4.7-alpha1`
- `2.4.7-alpha2`

Les packages de version Beta comportent un suffixe `-betaX`. Par exemple, les packages de version bêta d’Adobe Commerce 2.4.7 utilisent la convention de nommage suivante :

- `2.4.7-beta1`
- `2.4.7-beta2`

Consultez le [calendrier des versions](schedule.md) pour obtenir la liste des dates des prochaines versions publiques alpha et bêta.

#### Accès aux versions

Les versions alpha et bêta d’Adobe Commerce sont distribuées de la même manière que toute autre version de correctif Adobe Commerce : en tant que métapaquets du compositeur sur `https://repo.magento.com`. Le code source est disponible sur [GitHub](https://github.com/magento/magento2).

Voir [ Démarrage rapide de l’installation du compositeur](../installation/composer.md) pour plus d’informations.

#### Rapports sur les événements

Adobe ne fournit pas le service d’assistance Adobe standard pour les versions alpha et bêta.

Pour envoyer des commentaires sur les versions alpha et bêta, suivez le [flux régulier de création de rapports sur les problèmes](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) sur [GitHub](https://github.com/magento/magento2).

Adobe surveille tous les problèmes critiques signalés par rapport à la dernière version alpha ou bêta et donne la priorité à leur résolution avant la date de publication en disponibilité générale.
