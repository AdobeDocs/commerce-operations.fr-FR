---
title: 'MDVA-33606 : les utilisateurs reçoivent une erreur lors de l’enregistrement de la page CMS affectée à la hiérarchie'
description: Le correctif MDVA-33606 résout le problème où les utilisateurs obtiennent l’erreur *violation de contrainte unique trouvée* lors de l’enregistrement d’une page CMS affectée à l’arborescence de hiérarchie. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.3 est installé. L’ID de correctif est MDVA-33606. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.
feature: CMS
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# MDVA-33606 : les utilisateurs reçoivent une erreur lors de l’enregistrement de la page CMS affectée à la hiérarchie.

Le correctif MDVA-33606 résout le problème où les utilisateurs reçoivent l’erreur *Violation de contrainte unique trouvée* lors de l’enregistrement d’une page CMS affectée à l’arborescence de hiérarchie. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.3 est installé. L’ID de correctif est MDVA-33606. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1-2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de l’enregistrement d’une page CMS affectée à l’arborescence, les utilisateurs reçoivent le message d’erreur suivant : *Violation de contrainte unique détectée*.

<u>Étapes à reproduire</u> :

1. Créez une page CMS. Définissez la portée sur Toutes les vues de magasin. Il s’agit de votre page CMS 1.
1. Créez une vue de magasin. Il s’agit de votre vue de magasin 2.
1. Accédez à **Contenu** > **Hiérarchie** > Ajouter la page CMS 1 à l’arborescence de hiérarchie.
1. Définissez la portée sur Affichage du magasin 2.
   * Décochez la case &quot;Utiliser la hiérarchie des noeuds parents&quot;.
   * Ajoutez la page CMS 1 à cette portée et enregistrez-la.
1. Définissez désormais la portée sur Affichage de magasin par défaut.
   * Décochez la case &quot;Utiliser la hiérarchie des noeuds parents&quot;.
   * Ajoutez la page CMS 1 à cette portée et enregistrez-la.
1. Accédez à **Contenu** > **Pages** > **Ajouter une nouvelle page**.
   * Nommez la page Page 2.
   * Dans la section Page des sites web, affectez-vous à Toutes les vues de magasin et aux deux vues de magasin (vue de magasin par défaut et vue de magasin 2), puis cliquez sur **Enregistrer la page**.
1. Dans la page de modification de CMS, ouvrez l’onglet Hiérarchie .
   * Affectez la page 2 au noeud Affichage de magasin 2, au noeud par défaut et au noeud Tous les sites web.

<u>Résultats attendus</u> :

Vous pouvez attribuer la page CMS aux trois noeuds sans erreur.

<u>Résultats réels</u> :

Vous obtenez l’erreur suivante : *Violation de contrainte unique trouvée*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [Outil de correctifs de qualité publié : un nouvel outil pour appliquer des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
