---
title: Bonnes pratiques relatives à la gestion du code
description: Découvrez les bonnes pratiques de gestion du code pour la phase de développement des projets Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: 0bff4c7a-1082-4b3e-b19c-bc8ad529b131
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---

# Bonnes pratiques de gestion du code pour Adobe Commerce

Cette rubrique est conçue pour vous aider à décider d’utiliser Git ou le compositeur pour distribuer du code personnalisé, en prenant en compte la gestion des versions, la complexité du code et la gestion des dépendances.

>[!NOTE]
>
>Ces bonnes pratiques sont mieux adaptées aux migrations et aux mises en œuvre, et moins au développement de modules uniques.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

## Définitions

{{$include /help/_includes/gra-definitions.md}}

## Quand utiliser Git ou le compositeur

<table>
<thead>
  <tr>
    <th></th>
    <th>Code géré principalement par le biais de Git.</th>
    <th>Code géré principalement par l’intermédiaire du compositeur</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Quand utiliser pour une configuration à instance unique</td>
    <td>
      <ul>
        <li><strong>Approche standard de la gestion du code pour une configuration à instance unique</strong></li>
        <li>Lorsque la base de code ne fera plus partie d’un GRA multi-marque à l’avenir</li>
        <li>Lorsque toutes les marques s’exécutent sur une seule instance en tant que sites web</li>
      </ul>
    </td>
    <td>
      <ul>
        <li>Le moment où la base de code peut ou va faire partie d’une configuration multi-instance à l’avenir</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>Quand utiliser pour une configuration multi-instance</td>
    <td>
      <ul>
        <li>Lorsque presque tous les modules sont interconnectés (non recommandé)</li>
        <li>Lorsque le code est conservé par une équipe qui ne connaît pas le compositeur</li>
      </ul>
    </td>
    <td>
      <ul>
        <li><strong>Approche standard de la gestion du code pour une configuration multi-instance</strong></li>
        <li>Lorsque Adobe conserve la base de code ou que l’équipe de maintenance connaît le compositeur</li>
      </ul>
    </td>
  </tr>
</tbody>
</table>

## Matrice des fonctionnalités

| Fonctionnalité | Git | Compositeur |
|------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Référentiel de code principal | Tout le code réside dans un ou plusieurs référentiels Git uniques | Tout le code réside dans les packages d’un référentiel Composer<br>chaque package Composer est représenté par un référentiel Git |
| Emplacement du code | Le développement se fait dans le répertoire `app/` | Le développement se fait dans le répertoire `vendor/` |
| Gestion de la mise à niveau principale | Adobe Commerce Core est installé et mis à niveau à l’aide du compositeur, le résultat est validé dans Git. | Adobe Commerce Core est installé et mis à niveau à l’aide du compositeur ; le résultat est validé dans Git. |
| Gestion de modules tiers | Les modules tiers sont installés dans `vendor/` s’ils le sont via Marketplace ou packagist.org. Sinon, ils sont installés dans `app/` | Tous les modules tiers sont installés dans le répertoire `vendor/` |
| Versions | La libération se caractérise par des commandes `git merge` et `git pull` ou `git checkout` | La libération se caractérise par des commandes `composer update` et `git pull` ou `git checkout` |
| Nombre de référentiels Git | Peu | Plusieurs |
| Complexité du développement | Simple | Complexe |
| Complexité de la demande d’extraction | Simple | Complexe |
| Complexité de la révision du code | Simple | Simple |
| Complexité de mise à jour de l’environnement Dev/QA/UAT | Simple | Complexe |
| Prise en charge de la loi GRA | ![icône Oui](../../../assets/yes.svg) | ![icône Oui](../../../assets/yes.svg) |
| Les modules peuvent installer automatiquement des bibliothèques externes | ![Aucune icône](../../../assets/no.svg) | ![icône Oui](../../../assets/yes.svg) |
| Flexibilité dans la composition des GRA | ![Aucune icône](../../../assets/no.svg) | ![icône Oui](../../../assets/yes.svg) |
| Gestion des dépendances des modules | ![Icône Oui](../../../assets/yes.svg) Uniquement par le biais de `module.xml` fonctionnalités limitées | ![Icône Oui](../../../assets/yes.svg) Gestion complète des dépendances via `composer.json` |
| Contrôle de version des modules | ![Icône Oui](../../../assets/yes.svg) Vous pouvez définir une version, mais vous ne pouvez pas installer une version spécifique | ![Icône Oui](../../../assets/yes.svg) Prise en charge complète des versions |
| Services payants nécessaires | référentiel Git. | Référentiel Git, Packagiste privé (± 600 € par an) |
| Intégration de Bitbucket à Jira possible | ![icône Oui](../../../assets/yes.svg) | ![icône Oui](../../../assets/yes.svg) |
| Les modifications apportées au code sont immédiatement disponibles pour installation | ![icône Oui](../../../assets/yes.svg) | ![icône Oui](../../../assets/yes.svg) |

## Solutions à éviter

1. **Combinaison du compositeur et du `app/code` pour vos modules**

   Combinez dans votre projet tous les inconvénients des deux styles de gestion de code. Cela ajoute une complexité, une instabilité et un manque de flexibilité inutiles.

   Par exemple :
   - Expliquez les workflows Git et Compositeur (au lieu de l’un d’eux uniquement) à l’équipe de développement.
   - Installez les modules incompatibles dans `app/code`, car rien n’est en place pour empêcher cela.
   - Le déplacement d’un module de `app/code` vers le compositeur (ou inversement) est fastidieux, en particulier avec le développement en cours.

1. **Gestionnaire de packages Satis**

   Le forfait privé coûte ± 600 € par an. Ce coût est pour l&#39;ensemble de la GRA, et non par marque. N&#39;essayez pas d&#39;éviter ces coûts en utilisant la solution gratuite Satis. Satis ne met pas automatiquement à jour vos packages chaque fois que vous envoyez des validations à Git. Satis n&#39;a pas non plus d&#39;autorisation intégrée. Vous devez disposer d&#39;un serveur Web pour exécuter Satis. Vous finissez par dépenser une multitude de frais d&#39;abonnement de Packagiste Privé pour le maintien de Satis.

1. **Commencez par Git, puis passez au compositeur**

   Choisissez une approche de gestion du code au début de votre projet. Le passage de Git au compositeur ou inversement, avec un développement en cours, est fastidieux et peut entraîner une perte de code et/ou une perte d’historique de révision.

<!-- Last updated from includes: 2023-08-23 15:56:59 -->
