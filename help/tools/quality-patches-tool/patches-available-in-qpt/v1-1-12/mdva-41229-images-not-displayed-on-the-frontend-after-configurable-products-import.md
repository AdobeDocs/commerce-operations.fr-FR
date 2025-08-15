---
title: 'MDVA-41229 : les images disponibles sur le serveur principal ne s’affichent pas sur le serveur frontal après l’importation de produits configurables'
description: Le correctif MDVA-41229 résout le problème où les images disponibles sur le serveur principal ne s’affichent pas sur le serveur frontal après l’importation de produits configurables. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-41229. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Data Import/Export, Configuration, Products
role: Admin
exl-id: 894fdc5b-545c-4ed8-ae1b-573d1d8d3cd6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 2%

---

# MDVA-41229 : les images disponibles sur le serveur principal ne s’affichent pas sur le serveur frontal après l’importation de produits configurables

Le correctif MDVA-41229 résout le problème où les images disponibles sur le serveur principal ne s’affichent pas sur le serveur frontal après l’importation de produits configurables. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-41229. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.2-p2 et 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les images disponibles sur le serveur principal ne s’affichent pas sur le serveur frontal après l’importation de produits configurables.

<u>Procédure à suivre </u> :

1. Installez une Adobe Commerce propre.
1. Ajoutez un attribut personnalisé en accédant à **Magasins** > **Attributs** > **Produit** > **Ajouter un nouvel attribut** avec les paramètres ci-dessous :

   * Propriétés :
      * Propriétés d’attribut :

         * Libellé Par Défaut : Définir La Taille
         * Type d’entrée de catalogue pour le propriétaire de la boutique : Échantillon de texte
         * Valeurs Requises : Non
         * Mettre à jour l’image d’aperçu du produit : oui

      * Gérer l’échantillon (valeurs de votre attribut) :

        | Est la valeur par défaut | Échantillon d’administrateurs | Admin Description | Échantillon d’affichage de magasin par défaut | Description de la vue de magasin par défaut |
        |---|---|---|---|---|
        | non | 4 | 4 | 4 | 4 |
        | non | 24 | 24 | 24 | 24 |
        | non | 30 | 30 | 30 | 30 |
        | non | 60 | 60 | 60 | 60 |
        | non | 68 | 68 | 68 | 68 |

      * Propriétés d’attribut avancées :

         * Code d’attribut : set_size
         * Portée : globale
         * Valeur unique : Non
         * Validation des entrées pour le propriétaire de la boutique : aucune
         * Ajouter aux options de colonne : non
         * Utiliser dans les options de filtre : non

   * Gérer les libellés :

      * Gérer les titres (taille, couleur, etc.)

         * Affichage de la boutique par défaut : définir la taille

   * Propriétés du storefront :

      * Utiliser dans la recherche : Oui
      * Poids de la recherche : 1
      * Visible dans la recherche avancée : non
      * Comparable sur Storefront : Oui
      * Utilisation dans la navigation superposée : filtrable (avec résultats)
      * Utiliser dans les résultats de recherche Navigation par couches : Oui
      * Utiliser pour les conditions de règle de promotion : Non
      * Visible sur les pages de catalogue sur Storefront : Oui
      * Utilisé dans la liste des produits : Oui
      * Utilisé pour le tri dans la liste de produits : Non

1. Ajoutez cet attribut au jeu d’attributs par défaut dans le groupe Détails du produit (**Magasins** > **Attributs** > **Jeu d’attributs**).
1. Téléchargez les images définies dans le dossier var du répertoire racine Adobe Commerce.
1. Accédez à **Système** > **Transfert de données** > et importez le fichier à l’aide des options suivantes :

   * Importer les paramètres :

      * Type d’entité : Produits

   * Comportement d’importation :

      * Comportement d’importation : ajouter/mettre à jour
      * Stratégie de validation : arrêter en cas d’erreur
      * Nombre d&#39;erreurs autorisées : 1
      * Séparateur de champs : `;`
      * Séparateur à plusieurs valeurs : `,`
      * Constante de valeur d’attribut : EMPTYVALUE
      * Zone Champs : non cochée

   * Fichier à importer :

      * Sélectionner le fichier à importer
      * Répertoire de fichiers images : laissez-le vide

1. Accédez à storefront pour `/product-set.html` page et basculer entre différentes tailles définies. Pour Set Size 24, il n&#39;y aura pas de galerie.

<u>Résultats attendus</u> :

La galerie pour tous les produits simples à l’intérieur d’un produit configurable est visible avec toutes les images associées.

<u>Résultats réels</u> :

Il n&#39;y a pas de galerie pour les produits.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
