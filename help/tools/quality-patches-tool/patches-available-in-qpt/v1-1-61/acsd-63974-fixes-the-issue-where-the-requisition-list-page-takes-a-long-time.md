---
title: 'ACSD-63974 : corrige le temps de chargement des [!UICONTROL Requisition List] lents avec la pagination.'
description: Appliquez le correctif ACSD-63974 pour résoudre le problème où le chargement de la page [!UICONTROL Requisition List] prend beaucoup de temps lorsqu’il y a trop d’éléments.
feature: B2B
role: Admin, Developer
exl-id: 1798baa3-da2f-44eb-8312-1f1b3f75b24d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-63974 : corrige le temps de chargement des [!UICONTROL Requisition List] lents avec la pagination.

Le correctif ACSD-63974 corrige le problème en raison duquel le chargement de la page **[!UICONTROL Requisition List]** prend beaucoup de temps lorsqu’il y a trop d’éléments. Ce correctif est disponible lorsque la version 1.1.61 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63974. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le chargement de la page **[!UICONTROL Requisition List]** est long lorsqu’il y a de nombreux éléments (2 000+). Cela est dû à l’absence de pagination, ce qui entraîne le chargement simultané de tous les éléments.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > *[!UICONTROL General]* > **[!UICONTROL B2B features]**.
1. Définissez **[!UICONTROL Enable Requisition List]** sur *Oui*.
1. Générez plus de 2 000 produits en modifiant `simple_products` nœud dans `setup/performance-toolkit/profiles/ce/small.xml`.
1. Exécutez la commande :

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. Créer un client et se connecter.
1. Ajoutez tous les produits à la **[!UICONTROL Requisition List]**.
1. Affichez les **[!UICONTROL Requisition List]** sur le Storefront.


<u>Résultats attendus</u> :

La page doit se charger dans un délai raisonnable.


<u>Résultats réels</u> :

Le temps de chargement de la page augmente avec le nombre d’éléments, car tous les éléments sont chargés en même temps en raison de l’absence de pagination.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : mises à niveau et correctifs > Appliquer des correctifs dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
