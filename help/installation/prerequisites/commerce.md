---
title: Obtention du logiciel Adobe Commerce
description: Découvrez comment télécharger le logiciel Adobe Commerce.
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Obtenez le logiciel Adobe Commerce

Vous faites partie des 240 000 commerçants dans le monde qui font confiance à notre logiciel de commerce électronique. Nous avons rassemblé quelques informations pour vous aider à commencer votre installation.

## Comment obtenir le logiciel

Vérifiez la disponibilité de nouvelles fonctionnalités et de versions intéressantes et découvrez comment les obtenir sur notre [page de disponibilité des produits](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

Consultez le tableau suivant pour commencer à installer Adobe Commerce.

<table>
    <tbody>
        <tr>
            <th>Besoins des utilisateurs</th>
            <th>Description</th>
            <th>Etapes d'installation et de mise à niveau de haut niveau</th>
            <th>Lien de prise en main</th>
        </tr>
    <tr>
        <td><p>Intégrateur, packager</p></td>
        <td><p>Souhaite un contrôle total sur tous les composants installés, a accès au serveur d’applications, hautement technique, peut recompresser le Magento Open Source avec d’autres composants.</p>
        </td>
        <td><ol><li>Crée un projet</em> Composer <em>qui contient la liste des composants à utiliser.</li>
            <li>Utilise le compositeur pour mettre à jour les dépendances des packages ; utilise <code>composer create-project</code> pour obtenir le métaphorage du compositeur.</li>
            <li>Installe l’application à l’aide de la <a href="../advanced.md">ligne de commande</a>.</li>
        <li>Met à niveau l’application et les extensions à l’aide de la <a href="../../upgrade/implementation/perform-upgrade.md">ligne de commande</a>.</li></ol></td>
        <td><p><a href="../composer.md">Obtention du métappackage</a></p></td>
    </tr>
    <tr>
        <td><p>Développeur contributeur</p></td>
        <td><p>Contribue au code base du Magento Open Source, génère des bogues et personnalise l’application. Très technique, possède son propre serveur de développement, comprend Composer et GitHub.</p>
            <p>Vous <em>ne pouvez pas</em> utiliser l’application dans un environnement de production.</p>
      <p>Vous devez effectuer la mise à niveau à l’aide des <a href="../../upgrade/developer/git-installs.md">commandes Composer et Git</a>.</p></td>
        <td><ol><li>Duplication du référentiel GitHub.</li>
            <li>Utilise le compositeur pour mettre à jour les dépendances de package.</li>
            <li>Installe l’application à l’aide de <a href="../advanced.md">la ligne de commande</a>.</li>
            <li>Met à niveau l’application à l’aide des <a href="../../upgrade/developer/git-installs.md">commandes Composer et Git</a>.</li>
            <li>Personnalise le code sous le répertoire <code>app/code</code>.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">Clonage du référentiel GitHub</a></p></td>
    </tr>
    </tbody>
</table>

## Informations utiles

Utilisez les liens situés à gauche de la page pour parcourir les rubriques de chaque partie de l’installation.

## Autorisations de serveur requises

Les systèmes UNIX nécessitent des `root` privilèges pour installer et configurer des logiciels comme un serveur Web, PHP. Si vous devez installer ce logiciel, assurez-vous d’y avoir `root` accès.

N’installez *pas* l’application dans le serveur Web docroot en tant qu’utilisateur `root` , car le serveur Web pourrait ne pas être en mesure d’interagir avec ces fichiers.

Vous devez disposer `root` de privilèges pour créer le propriétaire[&#128279;](file-system/overview.md) du système de fichiers et ajouter ce propriétaire au groupe du serveur Web. Vous utilisez le propriétaire du système de fichiers pour exécuter `bin/magento` des commandes à partir de la ligne de commande et pour configurer des tâches cron, qui planifient des tâches pour vous.
