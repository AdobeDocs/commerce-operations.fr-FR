---
title: 'MDVA-33606 : les utilisateurs rencontrent une erreur lors de l’enregistrement de la page CMS affectée à la hiérarchie'
description: Le correctif MDVA-33606 résout le problème où les utilisateurs obtiennent l’erreur *Violation de contrainte unique détectée* lors de l’enregistrement d’une page CMS affectée à l’arborescence. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 est installé. L’ID du correctif est MDVA-33606. Notez que le problème a été résolu dans Adobe Commerce 2.4.3.
feature: CMS
role: Admin
exl-id: 19aaa13f-7ee6-49bc-b1d9-c288dc93b951
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# MDVA-33606 : les utilisateurs rencontrent une erreur lors de l’enregistrement de la page CMS affectée à la hiérarchie

Le correctif MDVA-33606 résout le problème où les utilisateurs obtiennent l’erreur *Violation de contrainte unique trouvée* lors de l’enregistrement d’une page CMS affectée à l’arborescence. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 est installé. L’ID du correctif est MDVA-33606. Notez que le problème a été résolu dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1-2.4.2-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de la tentative d’enregistrement d’une page CMS affectée à l’arborescence de hiérarchie, les utilisateurs reçoivent le message d’erreur suivant : *Violation de contrainte unique trouvée*.

<u>Procédure à suivre </u> :

1. Créez une page CMS. Définissez l’étendue sur Toutes les vues de la boutique. Il s’agit de votre page CMS 1.
1. Créez une vue de magasin. Voici votre vue de Boutique 2.
1. Accédez à **Contenu** > **Hiérarchie** > Ajouter la page CMS 1 à l’arborescence.
1. Modifiez l’étendue en vue de magasin 2.
   * Décochez la case « Utiliser la hiérarchie de nœuds parents ».
   * Ajoutez CMS Page 1 à cette étendue et enregistrez-la.
1. Modifiez maintenant la portée en Vue de la boutique par défaut.
   * Décochez la case « Utiliser la hiérarchie de nœuds parents ».
   * Ajoutez CMS Page 1 à cette étendue et enregistrez-la.
1. Accédez à **Contenu** > **Pages** > **Ajouter une nouvelle page**.
   * Donnez au fichier le titre Page 2.
   * Dans la section Page dans les sites web , affectez à Toutes les vues de boutique et aux deux vues de boutique (Vue de boutique par défaut et Vue de boutique 2), puis cliquez sur **Enregistrer la page**.
1. Sur la page de modification de CMS, ouvrez l’onglet Hiérarchie .
   * Affectez la page 2 au nœud Vue de magasin 2, au nœud Par défaut et au nœud Tous les sites web .

<u>Résultats attendus</u> :

Vous pouvez affecter la page CMS aux trois nœuds sans aucune erreur.

<u>Résultats réels</u> :

Vous obtenez l’erreur suivante : *Violation de contrainte unique trouvée*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* [Publication de l’outil de correctifs de qualité : un nouvel outil pour appliquer des correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
