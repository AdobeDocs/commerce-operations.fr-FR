---
title: Bonnes pratiques relatives à la gestion du code
description: Découvrez les bonnes pratiques de gestion du code pour la phase de développement des projets Adobe Commerce.
feature: Best Practices
role: Developer
source-git-commit: 0902997fb0bf862b37a5e29026f462bf8c86c96b
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 0%

---


# Bonnes pratiques relatives à la gestion du code pour Adobe Commerce

Cette rubrique est conçue pour vous aider à décider si vous utilisez Git ou le compositeur pour distribuer du code personnalisé, en tenant compte de la gestion des versions, de la complexité du code et de la gestion des dépendances.

>[!NOTE]
>
>Ces bonnes pratiques sont mieux adaptées aux migrations et aux implémentations, moins au développement de modules uniques.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

Elle couvre les deux [architecture de référence globale (GRA)](../../architecture/global-reference/overview.md) et les installations d’instance unique.

## Définitions

{{$include /help/_includes/gra-definitions.md}}

## Quand utiliser Git ou le compositeur

<table>
<thead>
  <tr>
    <th></th>
    <th>Code géré principalement par Git</th>
    <th>Code géré principalement via le compositeur</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Quand utiliser pour une configuration d’instance unique</td>
    <td>
      <ul>
        <li><strong>Approche standard de gestion du code pour une configuration à instance unique</strong></li>
        <li>Lorsque la base de code ne fera plus partie d’une GRA multimarque à l’avenir</li>
        <li>Lorsque toutes les marques s’exécutent sur une seule instance en tant que sites web</li>
      </ul>
    </td>
    <td>
      <ul>
        <li>Lorsque la base de code peut ou va faire partie d’une configuration multi-instances à l’avenir</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>Quand utiliser une configuration multi-instances</td>
    <td>
      <ul>
        <li>Lorsque la plupart des modules sont interconnectés (non recommandé)</li>
        <li>Lorsque le code est géré par une équipe qui ne connaît pas le compositeur d’expérience</li>
      </ul>
    </td>
    <td>
      <ul>
        <li><strong>Approche standard pour la gestion du code pour une configuration multi-instances</strong></li>
        <li>Lorsqu’Adobe conserve la base de code ou que l’équipe de maintenance connaît bien le compositeur</li>
      </ul>
    </td>
  </tr>
</tbody>
</table>

## Matrice de fonctionnalités

| Fonctionnalité | Git | Compositeur |
|------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Référentiel de code principal | Tout le code réside dans un seul référentiel Git ou dans quelques référentiels Git | Tout le code réside dans les modules d’un référentiel de compositeur<br>Chaque module de compositeur est représenté par un référentiel Git. |
| Emplacement du code | Le développement se produit dans la variable `app/` directory | Le développement se produit dans la variable `vendor/` directory |
| Gestion des mises à niveau Core | Adobe Commerce Core est installé et mis à niveau à l’aide du compositeur, le résultat est validé dans Git | Adobe Commerce Core est installé et mis à niveau à l’aide du compositeur ; le résultat est validé dans Git. |
| Gestion de modules tiers | Les modules tiers sont installés dans `vendor/` s’ils sont installés via le marketplace ou packagist.org. Sinon, ils sont installés dans `app/` | Tous les modules tiers sont installés dans la variable `vendor/` directory |
| Versions | Le relâchement se caractérise par une `git merge` et `git pull` ou `git checkout` Commandes | Le relâchement se caractérise par une `composer update` et `git pull` ou `git checkout` Commandes |
| Nombre de référentiels Git | Peu | Beaucoup |
| Complexité du développement | Simple | Complexe |
| Complexité de requête de tirage | Simple | Complexe |
| Complexité de la révision du code | Simple | Simple |
| Complexité de la mise à jour de l’environnement Dev/QA/UAT | Simple | Complexe |
| Prise en charge GRA | ![Icône Oui](../../../assets/yes.svg) | ![Icône Oui](../../../assets/yes.svg) |
| Les modules peuvent installer automatiquement des bibliothèques externes. | ![Aucune icône](../../../assets/no.svg) | ![Icône Oui](../../../assets/yes.svg) |
| Flexibilité dans la composition de l&#39;Armée de terre | ![Aucune icône](../../../assets/no.svg) | ![Icône Oui](../../../assets/yes.svg) |
| Gestion des dépendances des modules | ![Icône Oui](../../../assets/yes.svg) Uniquement `module.xml`, fonctionnalité limitée | ![Icône Oui](../../../assets/yes.svg) Gestion complète des dépendances via `composer.json` |
| Contrôle de version des modules | ![Icône Oui](../../../assets/yes.svg) Vous pouvez définir une version, mais pas installer une version spécifique. | ![Icône Oui](../../../assets/yes.svg) Prise en charge complète des versions |
| Services payants nécessaires | Référentiel Git | Référentiel Git, Packagist privé (+ 600 € par an) |
| Intégration de Bitbucket avec Jira possible | ![Icône Oui](../../../assets/yes.svg) | ![Icône Oui](../../../assets/yes.svg) |
| Modifications du code immédiatement disponibles pour l’installation | ![Icône Oui](../../../assets/yes.svg) | ![Icône Oui](../../../assets/yes.svg) |

## Solutions à éviter

1. **Combinaison du compositeur et de `app/code` pour vos modules**

   Vous obtenez ainsi tous les inconvénients des deux styles de gestion du code combinés dans votre projet. Cela ajoute une complexité, une instabilité et un manque de flexibilité inutiles.

   Par exemple :
   - Expliquez les workflows Git et Composer (au lieu d’un seul d’entre eux) à l’équipe de développement.
   - Installer les modules incompatibles dans `app/code` car rien n&#39;est en place pour empêcher cela.
   - Déplacement d’un module depuis `app/code` au compositeur (ou inversement) est lourd, en particulier avec le développement en cours.

1. **Satis Package Manager**

   Private Packagist coûte + 600 € par an. Ce coût est pour l&#39;ensemble de la GRA combinée, pas par marque. N&#39;essayez pas d&#39;éviter ces coûts en utilisant la solution gratuite Satis. Satis ne met pas automatiquement à jour vos packages chaque fois que vous poussez des validations sur git. Satis n&#39;a pas non plus d&#39;autorisation. Vous devez gérer un serveur web pour exécuter Satis. Vous finissez par dépenser une multitude des frais d&#39;abonnement des Packagistes privés en conservant Satis.

1. **Commencer avec Git, puis passer au compositeur**

   Choisissez une approche de gestion du code au début de votre projet. Passer de Git au compositeur ou inversement, avec un développement en cours est lourd et pourrait entraîner une perte de code et une perte d’historique de révision.
