---
title: 'ACSD-65848 : les catégories dans l’administration se chargent très lentement'
description: Appliquez le correctif ACSD-65848 pour résoudre le problème d’Adobe Commerce où le nombre total de produits dans une catégorie était calculé à l’aide d’une sous-sélection, ce qui retardait le temps de chargement de la catégorie.
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
exl-id: 0233db9b-86b1-4320-a566-7e7e207dab84
source-git-commit: 1ccb4c1dda5141934e04509b27fdafbfdc436a15
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-65848 : les catégories dans l’administration se chargent très lentement

Le correctif ACSD-65848 corrige le problème en raison duquel le nombre total de produits dans une catégorie était calculé à l’aide d’une sous-sélection, ce qui retardait le temps de chargement de la catégorie. Ce correctif est disponible lorsque la version 1.1.66 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-65848. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le chargement de la page d’affichage/de modification de la catégorie Admin prend beaucoup de temps. Le retard est dû à la méthode utilisée pour calculer le nombre total de produits dans une catégorie, qui repose sur une requête de sous-sélection. La refactorisation de cette logique pour utiliser une jointure améliore les performances et réduit le temps de chargement.

<u>Procédure à suivre </u> :

1. Créez une instance Adobe Commerce Cloud à l’aide de la version 2.4.8.
1. Créez 2 500 catégories et au moins 10 000 produits :
   1. Copiez le répertoire `setup/performance-toolkit` dans `./var` pour pouvoir modifier les profils.
   1. Ouvrez le profil `small.xml` et mettez-le à jour pour inclure 2 500 catégories et 250 000 produits (pour correspondre à la configuration du commerçant).
   1. Exécutez la commande suivante pour générer les fixations :

      ```bash
      bin/magento 
      setup:performance:generate-fixtures var/setup/performance-toolkit/profiles/ce/small.xml
      ```

1. Une fois les produits et les catégories créés, assurez-vous que toutes les catégories sont définies comme ancres. Exécutez cette requête SQL :

   ```sql
   UPDATE catalog_category_entity_int 
   SET value = 1 
   WHERE attribute_id = (
   SELECT attribute_id 
   FROM eav_attribute 
   WHERE attribute_code = 'is_anchor'
   );
   ```

1. Dans le panneau d’administration, créez une structure de catégorie plus profonde :
   * Déplacez la catégorie 2 sous la catégorie 1 pour l’imbriquer plus profondément dans l’arborescence.
1. Essayez d’ouvrir une page de catégorie dans le panneau d’administration en utilisant une URL de type :
   ```/admin/catalog/category/edit/id/xx/```

<u>Résultats attendus</u> :

Chaque page de catégorie s’ouvre lors du premier essai dans les secondes qui suivent.

<u>Résultats réels</u> :

L’ouverture des pages de catégories prend plus d’une minute.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
