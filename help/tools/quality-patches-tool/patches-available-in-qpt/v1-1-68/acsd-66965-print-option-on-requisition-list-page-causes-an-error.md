---
title: 'ACSD-66965 : [!UICONTROL Print] option sur [!UICONTROL Requisition List] page provoque une erreur'
description: Appliquez le correctif ACSD-66965 pour résoudre un problème dans Adobe Commerce où l’option [!UICONTROL Print] sur la page [!UICONTROL Requisition List] provoque une erreur.
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7682a326a6c703a08dd6d0fac5319ac38e1bc3c8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# ACSD-66965 : **[!UICONTROL Print]** option sur **[!UICONTROL Requisition List]** page provoque une erreur

Le correctif ACSD-66965 corrige le problème en raison duquel l’option **[!UICONTROL Print]** sur la page **[!UICONTROL Requisition List]** provoque une erreur. Ce correctif est disponible lorsque la version 1.1.68 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66965. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

**[!UICONTROL Print]** option de la page **[!UICONTROL Requisition List]** provoque une erreur en raison d’une référence d’objet null dans `Grid.php`.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Définissez **[!UICONTROL Enable Company]**, **[!UICONTROL Enable Shared Catalog]** et **[!UICONTROL Enable Requisition List]** sur `Yes`.
1. Créez deux produits simples.
1. Connectez-vous au storefront et ouvrez la page **[!UICONTROL My Account]**.
1. Créez une liste de demandes d&#39;approvisionnement.
1. Affectez les deux produits à la liste des demandes d&#39;approvisionnement.
1. Accédez à la liste des demandes d&#39;approvisionnement et répertoriez les produits.
1. Cliquez sur **[!UICONTROL Print]**.

<u>Résultats attendus</u> :

L’option **[!UICONTROL Print]** de la page **[!UICONTROL Requisition List]** affiche l’aperçu avant impression sans erreur.

<u>Résultats réels</u> :

Le message d’erreur suivant s’affiche : *Une erreur s’est produite lors de l’exécution de l’application. Voir le journal des exceptions pour plus de détails.*

```
Call to a member function setCollection() on null in /vendor/magento/module-requisition-list/Block/Requisition/View/Items/Grid.php:146
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
