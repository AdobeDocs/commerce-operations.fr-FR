---
title: 'ACSD-52041 : le rendu de Page Builder ne libère pas les verrous'
description: Appliquez le correctif ACSD-52041 pour résoudre le problème d’Adobe Commerce en raison duquel Page Builder effectue le rendu pendant cinq secondes sans libérer les verrous.
feature: Page Builder
role: Admin, Developer
exl-id: 48a7fc36-e98a-4a4e-bed3-248d7d73f6cb
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-52041 : le rendu de Page Builder ne libère pas les verrous

Le correctif ACSD-52041 corrige le problème de rendu de Page Builder pendant cinq secondes sans libérer les verrous. Ce correctif est disponible lorsque la version 1.1.48 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-52041-v2. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p5, 2.4.5 - 2.4.5-p4 et 2.4.6 - 2.4.6-p2.



>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.


## Problème

Le **[!DNL Page Builder]** effectue un rendu de 5 secondes *5* sans relâcher les verrous.

<u>Procédure à suivre </u> :

1. Modifiez une page CMS, une page produit ou tout élément contenant des **[!DNL Page Builder]**.
1. Enregistrez les modifications.
1. Remarquez le gain de temps de la page.

<u>Résultats attendus</u>

Le contenu est enregistré. Aucune erreur n’a été trouvée dans le journal du navigateur.

<u>Résultats réels</u>

L’enregistrement prend plus de temps que d’habitude.
Erreur dans la console : ``Page Builder was rendering for 5 seconds without releasing locks``

## Application du correctif

Pour appliquer des correctifs individuels pour les versions **2.4.4 - 2.4.4-p5, 2.4.5 - 2.4.5-p4 et 2.4.6 - 2.4.6-p2**, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr>) dans le guide de [!DNL Quality Patches Tool].
