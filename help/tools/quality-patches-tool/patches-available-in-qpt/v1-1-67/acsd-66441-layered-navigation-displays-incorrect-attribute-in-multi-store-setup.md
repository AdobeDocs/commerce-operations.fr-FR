---
title: 'ACSD-66441 : la navigation par couches affiche des options d’attribut incorrectes dans la configuration multi-magasin'
description: Appliquez le correctif ACSD-66441 pour résoudre le problème d’Adobe Commerce en raison duquel la navigation superposée affiche incorrectement les attributs d’autres magasins dans une configuration multi-magasin.
feature: Catalog Management, Search
role: Admin, Developer
type: Troubleshooting
exl-id: d61c6b9e-bbcf-4285-b97b-b1fee67048e5
source-git-commit: 515e6d1f00c910455a2ffddf70c4a450184e7e81
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-66441 : la navigation par couches affiche des options d’attribut incorrectes dans la configuration multi-magasin

Le correctif ACSD-66441 corrige le problème d’affichage incorrect des attributs d’autres magasins dans une configuration multi-magasin par navigation superposée. Ce correctif est disponible lorsque la version 1.1.67 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66441. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La navigation en couches sur le storefront inclut des valeurs d’attribut d’autres magasins, même si ces produits ne sont pas disponibles dans la vue actuelle du magasin.

<u>Procédure à suivre </u> :

1. Créez un site web secondaire, un magasin et une vue de magasin.
1. Créez un produit configurable à l’aide d’un attribut personnalisé (par exemple, la taille).
1. Attribuez le produit configurable au site web principal et à une catégorie.
1. Réindexez toutes les données.
1. Accédez à la catégorie affectée sur le storefront. Toutes les options de taille s’affichent correctement dans Navigation superposée.
1. Annulez l’affectation de deux produits simples du site web principal et affectez-les au site web secondaire ou supprimez-les du site web principal.
1. Réindexez toutes les données.
1. Revoyez la page de catégorie storefront et vérifiez la navigation superposée.

<u>Résultats attendus</u> :

Le mode de navigation superposé affiche uniquement les options d’attribut des produits affectés au magasin ou au site Web actuel.

<u>Résultats réels</u> :

La navigation superposée affiche les options d’attribut (tailles) des produits affectés à d’autres magasins ou sites web.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
