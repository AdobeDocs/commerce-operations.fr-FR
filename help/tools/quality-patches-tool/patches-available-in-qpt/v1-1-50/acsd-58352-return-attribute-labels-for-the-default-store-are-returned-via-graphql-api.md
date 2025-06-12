---
title: 'ACSD-58352 : les libellés d’attribut de retour pour le magasin par défaut sont renvoyés via [!DNL GraphQL] API'
description: Appliquez le correctif ACSD-58352 pour résoudre le problème d’Adobe Commerce où les libellés d’attribut de retour pour le magasin par défaut sont renvoyés via [!DNL GraphQL] API lorsqu’une vue de magasin autre que celle par défaut est spécifiée dans l’en-tête de la requête.
feature: GraphQL, Returns
role: Admin, Developer
exl-id: e513039e-42cd-4dac-963b-3068ba8bf7ee
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-58352 : les libellés d’attribut de retour du magasin par défaut sont renvoyés via [!DNL GraphQL] API

Le correctif ACSD-58352 corrige le problème où les libellés d’attribut de retour pour le magasin par défaut sont renvoyés via [!DNL GraphQL]’API lorsqu’une vue de magasin autre que celle par défaut est spécifiée dans l’en-tête de la requête. Ce correctif est disponible lorsque la version 1.1.50 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-58352. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les libellés d’attribut de retour du magasin par défaut sont renvoyés via l’API [!DNL GraphQL].

<u>Procédure à suivre </u> :

1. Activez la **[!UICONTROL Return Merchandising Authorization]**.
1. Créez un *[!UICONTROL Additional Store]* et un *[!UICONTROL Store View]* sous le site web par défaut.
1. Modifiez l’attribut de retour **[!UICONTROL Reason for Return]** et ajoutez des libellés pour toutes les vues de magasin.
1. Créez un *[!UICONTROL Order]*.
1. Créez un *[!UICONTROL Return]* pour cette commande. Assurez-vous que le *[!UICONTROL Return]* a le statut *[!UICONTROL Pending]*.
1. Envoyez une requête de [!DNL GraphQL] client avec les [!UICONTROL Store View] non par défaut spécifiées dans l’en-tête :

   ```
   query {
       customer {
           returns {
               items {
                   items {
                       custom_attributes {
                           label
                           value
                       }
                   }
               }
           }
       }
   }
   ```

1. Observez la réponse.

<u>Résultats attendus</u>

Les étiquettes de retour dans la réponse [!DNL GraphQL] sont pour les [!UICONTROL Store View] définies dans l’en-tête de la requête.

<u>Résultats réels</u> :

Les étiquettes de retour dans [!DNL GraphQL] réponse correspondent à l’[!UICONTROL Store View] par défaut.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
