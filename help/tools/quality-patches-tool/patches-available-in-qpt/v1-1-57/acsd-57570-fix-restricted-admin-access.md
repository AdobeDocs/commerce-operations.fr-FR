---
title: 'ACSD-57570 : correctif pour l’accès restreint des utilisateurs administrateurs aux catalogues partagés'
description: Appliquez le correctif ACSD-57570 pour résoudre le problème d’Adobe Commerce où un utilisateur administrateur restreint ayant accès à un magasin particulier ne peut pas systématiquement afficher tous les catalogues partagés affectés aux produits ou enregistrer les informations client, ce qui entraîne des incohérences du système.
feature: B2B, Companies, Roles/Permissions
role: Admin, Developer
source-git-commit: 6147a028e2ce783809b5c2c32c65784611d03f0e
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---


# ACSD-57570 : correctif pour l’accès restreint des utilisateurs administrateurs aux catalogues partagés

Le correctif ACSD-57570 corrige le problème en raison duquel un utilisateur administrateur restreint ayant accès à un magasin particulier ne peut pas systématiquement afficher tous les catalogues partagés affectés aux produits ou enregistrer les informations client, ce qui entraîne des incohérences du système. Ce correctif est disponible lorsque la version 1.1.57 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-57570. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.4-p9

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un utilisateur administrateur restreint ayant accès à un magasin particulier ne peut pas toujours voir tous les catalogues partagés ou enregistrer les clients, ce qui entraîne des incohérences. Avec plusieurs magasins, l’administrateur restreint ne peut pas voir les nouvelles sociétés ou les catalogues partagés personnalisés.

<u>Procédure à suivre </u> :

1. Configurez les magasins dans l’ordre suivant :
   * Créez un nouveau site web nommé W2.
   * Créez une nouvelle vue de magasin pour le site web par défaut.
   * Créez un magasin nommé W2S2 pour le site Web W2.
   * Créez une vue de magasin nommée W2S2SV1 pour le magasin W2S2.
   * Créez une autre vue de magasin nommée W2S2SV2 pour le magasin W2S2.
   * Créez une entreprise pour W2.
1. Attribuer des produits :
   * Affecter certains produits au W1 uniquement.
   * Attribuer uniquement certains produits à W2.
   * Attribuer certains produits à la fois à W1 et à W2.
1. Créez un catalogue partagé personnalisé et affectez-y tous les produits.
1. Créez un rôle d’administrateur personnalisé ayant accès uniquement à **W2S2**, et non à **W2**.
1. Affectez l’utilisateur administrateur restreint au nouveau rôle d’administrateur personnalisé.
1. Connectez-vous en tant qu’utilisateur administrateur restreint.
1. Vérifier l’accès :
   * Vérifiez quelles entreprises vous pouvez voir.
   * Vérifiez quels catalogues partagés vous pouvez voir.
   * Ouvrez la liste des produits et vérifiez si vous pouvez voir tous les catalogues partagés auxquels les produits sont affectés.

<u>Résultats attendus</u> :

Le comportement doit être cohérent.

<u>Résultats réels</u> :

Si vous créez une seule vue de site web, de magasin et de magasin supplémentaire, l’utilisateur avec accès restreint à l’administration peut voir la société, le catalogue partagé et les deux catalogues partagés dans la liste de produits. Avec la configuration ci-dessus, l’administrateur restreint ne peut pas voir la nouvelle société ou le catalogue partagé personnalisé, et seul le catalogue partagé par défaut s’affiche dans la liste de produits.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-Premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
