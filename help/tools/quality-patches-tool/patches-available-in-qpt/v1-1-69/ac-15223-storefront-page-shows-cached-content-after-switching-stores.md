---
title: 'AC-15223 : la page Storefront affiche le contenu mis en cache après le changement de magasin'
description: Appliquez le correctif AC-15223 pour résoudre le problème Adobe Commerce en raison duquel, après le changement de magasin, la page est diffusée à partir du cache et le magasin n’est pas basculé comme prévu.
feature: Cache
role: Admin, Developer
type: Troubleshooting
source-git-commit: ea3584e180acad1765f5b8105c45170725c71269
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# AC-15223 : la page Storefront affiche le contenu mis en cache après le changement de magasin

Le correctif AC-15223 corrige le problème en raison duquel, après le changement de magasin, la page est diffusée à partir du cache, car le sélecteur de magasin ne fonctionne pas. Ce correctif est disponible lorsque la version 1.1.69 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est AC-15223. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Après le changement de magasin, la page est diffusée à partir du cache (le sélecteur de magasin ne fonctionne pas).

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]**.
2. Créez une vue de magasin.
3. Accédez au storefront, et essayez de changer les vues du magasin.

<u>Résultats attendus</u> :

La vue du magasin a été commutée avec succès.

<u>Résultats réels</u> :

Le nom de la vue du magasin n’est pas modifié dans l’en-tête tant que le cache n’est pas nettoyé du serveur principal.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
