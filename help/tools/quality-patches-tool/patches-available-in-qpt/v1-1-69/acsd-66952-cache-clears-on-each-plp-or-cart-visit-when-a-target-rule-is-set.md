---
title: 'ACSD-66952 : le cache s’efface à chaque visite de PLP ou de panier lorsqu’une règle cible est définie'
description: Appliquez le correctif ACSD-66952 pour résoudre le problème d’Adobe Commerce où le cache était effacé à chaque visite du PLP ou du panier, ce qui entraînait une surcharge de performances inutile, lorsqu’une règle cible était définie.
feature: Shopping Cart, Cache, Price Rules
role: Admin, Developer
type: Troubleshooting
exl-id: abff5761-bcf1-4cfc-b5d9-6a7e1ca907e7
source-git-commit: cf0f5992c7b2a51b270a4a1a81fd50305a92759c
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-66952 : le cache s’efface à chaque visite de PLP ou de panier lorsqu’une règle cible est définie

Le correctif ACSD-66952 corrige le problème où le cache est effacé à chaque visite du PLP ou du panier, ce qui entraîne une surcharge de performances lorsqu’une règle cible est définie. Ce correctif est disponible lorsque la version 1.1.69 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66952. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Problème en raison duquel le cache est effacé à chaque visite d’un PLP ou d’un panier, ce qui entraîne une surcharge des performances lorsqu’une règle cible est définie.

<u>Procédure à suivre </u> :

1. Générez un petit échantillon de jeu de données.
1. Créez des valeurs de règle cible comme ci-dessous :
   1. **[!UICONTROL Rule information]**
      * **[!UICONTROL Rule Name]** = *Produits connexes*
      * **[!UICONTROL Status]** = *Actif*
      * **[!UICONTROL Apply to]** = *Produits connexes*
   1. **[!UICONTROL Products to Match]**
      * Conservez sa valeur par défaut.
   1. **[!UICONTROL Products to Display]**
      * Si **ALL** de ces conditions est *true*, définissez **[!UICONTROL Product Category]** = *Constant Value 111111*
1. Commencez à surveiller les journaux pour les demandes d’invalidation du cache.
1. Rendez-vous sur la page produit.
1. Ajoutez un produit au panier et accédez à la page du panier.

<u>Résultats attendus</u> :

L’application ne doit pas invalider le cache lors de la navigation sur le site.

<u>Résultats réels</u> :

Les balises de cache sont invalidées.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool]
* Adobe Commerce sur les infrastructures cloud : [&#x200B; Mises à niveau et correctifs > Appliquer des correctifs &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
