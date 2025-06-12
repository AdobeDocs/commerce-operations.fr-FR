---
title: 'ACSD-51471 : l’utilisateur administrateur ne peut pas enregistrer la mise à jour planifiée pour le produit groupé'
description: Appliquez le correctif ACSD-51471 pour résoudre le problème d’Adobe Commerce où un utilisateur administrateur ne peut pas enregistrer une mise à jour planifiée pour un produit groupé qui utilise un produit simple avec une mise à jour planifiée.
exl-id: d8134111-63f0-4476-a407-677bda52fa90
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-51471 : l’utilisateur administrateur ne peut pas enregistrer la mise à jour planifiée pour le produit groupé

Le correctif ACSD-51471 corrige le problème où un utilisateur administrateur ne peut pas enregistrer une mise à jour planifiée pour un produit groupé qui utilise un produit simple avec une mise à jour planifiée. Ce correctif est disponible lorsque la version 1.1.33 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-51471. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs administrateurs ne peuvent pas enregistrer une mise à jour planifiée pour un produit groupé qui utilise un produit simple ayant lui-même une mise à jour planifiée.

<u>Procédure à suivre </u> :

1. Créez un produit simple.
1. Ajoutez une mise à jour planifiée pour le produit simple avec uniquement la *Date de début* et aucune *Date de fin*.
1. Une fois la mise à jour appliquée, modifiez le SKU du produit.
1. Créez un produit groupé et ajoutez le produit simple créé à l’étape 1 en tant que produit enfant.
1. Créez une mise à jour planifiée pour le produit groupé afin d’activer le produit groupé. Indiquez les deux *Date de début* et *Date de fin* pour la mise à jour planifiée.
1. Enregistrez la mise à jour planifiée.

<u>Résultats attendus</u> :

La mise à jour planifiée a bien été enregistrée.

<u>Résultats réels</u> :

L’erreur suivante se produit lors de l’enregistrement de la mise à jour planifiée : *Le produit demandé n’existe pas. Vérifiez le produit et réessayez.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
