---
title: 'ACSD-63326 : correction d’un problème de redirection d’administration après avoir passé une commande depuis le serveur principal'
description: Appliquez le correctif ACSD-63326 pour résoudre le problème Adobe Commerce en raison duquel l’administrateur est redirigé vers une page endommagée après avoir passé une commande sur le serveur principal.
feature: Orders, Admin Workspace
role: Admin, Developer
source-git-commit: 47603deecdf5ac3e6be18efeef38cba52ec936ec
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63326 : correction d’un problème de redirection d’administration après avoir passé une commande depuis le serveur principal

Le correctif ACSD-63326 corrige le problème en raison duquel l’administrateur est redirigé vers une page endommagée après avoir passé une commande à partir du serveur principal. Ce correctif est disponible lorsque la version 1.1.57 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63326. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les administrateurs sont redirigés vers une page avec une disposition rompue après avoir passé avec succès une commande pour un client à partir du serveur principal.

<u>Procédure à suivre </u> :

1. Accédez à la section **[!UICONTROL Customers]** du panneau d’administration.
1. Sélectionnez un client et cliquez sur **[!UICONTROL Edit]**.
1. Sur la page des détails du client, cliquez sur **[!UICONTROL Create Order]** dans le menu supérieur.
1. Sélectionnez le magasin de [!UICONTROL FR French] et ajoutez tout produit disponible à la commande.
1. Renseignez les détails requis lors du passage en caisse et cliquez sur **[!UICONTROL Get shipping methods and rates]**.
1. Cliquez sur **[Soumettre la commande]** pour passer la commande.

<u>Résultats attendus</u> :

L’administrateur est redirigé vers la page de confirmation de commande ou de remerciement avec la mise en page appropriée.

<u>Résultats réels</u> :

L’administrateur est redirigé vers une page avec une disposition rompue. La disposition n’est corrigée qu’après actualisation de la page.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-Premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
