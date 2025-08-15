---
title: Procurez-vous le logiciel Adobe Commerce.
description: Découvrez comment télécharger le logiciel Adobe Commerce.
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Procurez-vous le logiciel Adobe Commerce.

Vous faites partie des 240 000 commerçants du monde entier qui font confiance à notre logiciel de commerce électronique. Nous avons rassemblé quelques informations pour vous aider à commencer votre installation.

## Comment obtenir le logiciel

Vérifiez la disponibilité de nouvelles fonctionnalités et versions intéressantes et découvrez comment les obtenir sur notre [page de disponibilité des produits](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

Consultez le tableau suivant pour commencer à installer Adobe Commerce.

<table>
    <tbody>
        <tr>
            <th>Besoins de l’utilisateur</th>
            <th>Description</th>
            <th>Étapes d’installation et de mise à niveau de haut niveau.</th>
            <th>Lien Commencer</th>
        </tr>
    <tr>
        <td><p>Intégrateur, conditionneur</p></td>
        <td><p>souhaite un contrôle total sur tous les composants installés, a accès au serveur d’applications, est hautement technique et peut recompresser Magento Open Source avec d’autres composants.</p>
        </td>
        <td><ol><li>Crée un compositeur <em>projet</em> qui contient la liste des composants à utiliser.</li>
            <li>Utilise le compositeur pour mettre à jour les dépendances de package ; utilise <code>composer create-project</code> pour obtenir le métapaquet du compositeur.</li>
            <li>Installe l’application à l’aide de la <a href="../advanced.md"> ligne de commande </a>.</li>
        <li>Met à niveau l’application et les extensions à l’aide de la <a href="../../upgrade/implementation/perform-upgrade.md"> ligne de commande </a>.</li></ol></td>
        <td><p><a href="../composer.md">Obtenir le métapaquet</a></p></td>
    </tr>
    <tr>
        <td><p>Développeur contributeur</p></td>
        <td><p>Contribue à la base de code Magento Open Source, fichier des bogues et personnalise l’application. Hautement technique, dispose de son propre serveur de développement, comprend Composer et GitHub.</p>
            <p>Vous <em>ne pouvez pas</em> utiliser l’application dans un environnement de production.</p>
      <p>Vous devez effectuer la mise à niveau à l’aide des commandes <a href="../../upgrade/developer/git-installs.md">Composer et Git</a>.</p></td>
        <td><ol><li>Clone le référentiel GitHub.</li>
            <li>Utilise le compositeur pour mettre à jour les dépendances de package.</li>
            <li>Installe l’application à l’aide de <a href="../advanced.md"> ligne de commande </a>.</li>
            <li>Met à niveau l’application à l’aide des commandes <a href="../../upgrade/developer/git-installs.md"> Composer et Git </a>.</li>
            <li>Personnalise le code dans le répertoire <code>app/code</code>.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">Clonage du référentiel GitHub</a></p></td>
    </tr>
    </tbody>
</table>

## Informations utiles

Utilisez les liens situés sur le côté gauche de la page pour parcourir les rubriques de chaque partie de l’installation.

## Autorisations de serveur requises

Les systèmes UNIX nécessitent des privilèges `root` pour installer et configurer des logiciels tels qu&#39;un serveur web, PHP. Si vous devez installer ce logiciel, vérifiez que vous disposez d&#39;un accès `root`.

N’installez *pas* l’application dans le serveur web docroot en tant qu’utilisateur `root`, car le serveur web risque de ne pas pouvoir interagir avec ces fichiers.

Vous avez besoin `root` privilèges pour créer le [propriétaire du système de fichiers](file-system/overview.md) et l&#39;ajouter au groupe du serveur Web. Utilisez le propriétaire du système de fichiers pour exécuter des commandes `bin/magento` à partir de la ligne de commande et configurer des tâches cron, qui planifient des tâches pour vous.
