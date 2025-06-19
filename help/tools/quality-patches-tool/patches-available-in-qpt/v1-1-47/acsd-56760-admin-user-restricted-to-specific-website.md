---
title: 'ACSD-56760 : l’utilisateur administrateur est limité à un site web spécifique et ne peut pas trier ni ajouter de nouveaux produits'
description: Appliquez le correctif ACSD-56760 pour résoudre le problème d’Adobe Commerce en raison duquel l’utilisateur administrateur limité à un site web spécifique ne peut pas trier ni ajouter de nouveaux produits à l’intérieur d’une catégorie dans le cas où la boutique web possède sa propre catégorie racine.
role: Admin
exl-id: 2d75164e-c463-4e1a-aa6f-f420dbe0aaeb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-56760 : l’utilisateur administrateur est limité à un site web spécifique et ne peut pas trier ni ajouter de nouveaux produits

Le correctif ACSD-56760 corrige le problème en raison duquel l’utilisateur administrateur restreint à un site web spécifique et ne peut pas trier ni ajouter de nouveaux produits à l’intérieur d’une catégorie dans le cas où la boutique web possède sa propre catégorie racine. Ce correctif est disponible lorsque la version 1.1.47 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-56760. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8-beta1.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur administrateur limité à un site web spécifique ne peut pas trier ni ajouter de nouveaux produits à l’intérieur d’une catégorie dans le cas où la boutique web possède sa propre catégorie racine.

<u>Procédure à suivre </u> :

1. Créez des sites web *2*.
1. Créez un **[!UICONTROL restricted admin user]** ayant accès uniquement au site web *1*.
1. Connectez-vous en tant qu’**[!UICONTROL restricted admin user]** et essayez de modifier la position des produits dans une catégorie.

*Cas 1* :

* magasins *2*.
* Catégories racine *2*, chaque site web étant affecté à sa propre racine de catégorie.

*2e cas* :

* magasins *2*.
* Seule la catégorie racine *1* est affectée aux deux sites web.

<u>Résultats attendus</u> :

* *Cas 1* : l’administrateur restreint doit pouvoir trier les produits dans la catégorie disponible.
* *Cas 2* : l’administrateur restreint ne peut pas trier les produits dans la catégorie disponible, car cela affectera également le magasin restreint.

<u>Résultats réels</u> :

* *Cas 1* : l’administrateur restreint ne peut pas trier les produits dans la catégorie disponible.
* *Cas 2* : l’administrateur restreint peut trier les produits dans la catégorie disponible, ce qui affecte les magasins restreints.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
